# rm-controls Code Style Guidelines

We use the [ROS C++ Style guide](http://wiki.ros.org/CppStyleGuide) for all C++ development and the [ROS Python Style guide](http://wiki.ros.org/PyStyleGuide) for Python, you can use [ros_best_pracitces](https://github.com/leggedrobotics/ros_best_practices) as a template.

To ease your development, we recommend the automated code formatter ``clang-format`` with a ROS configuration - to use see below.

In addition rm-controls has some extra style preferences:

## C++

 - We use C++14
 - Use the C++ standard library (``std::``) whenever possible
 - Avoid C-style functions such as ``FLT_EPSILON`` - instead use ``std::numeric_limits<double>::epsilon()``
 - Boost is an encouraged library when functionality is not available in the standard library
 - Use "pragma once" in headers instead of include guards.

## Inline Documentation

 - We use Doxygen-style comments
 - To document future work, use the format ``TODO(username): description``
 - Add extensive comments to explain complex sections of code
 - Prefer full, descriptive variable names over short acryonms - e.g. ``robot_state_`` over ``rs_``
 - Avoid ``auto``, if the variable type doesn’t become clear immediately from the context (e.g. from ``make_shared<...>``)

## Deprecation

 - Deprecate functions using C++14 [``[[deprecated]]``](https://en.cppreference.com/w/cpp/language/attributes/deprecated) attribute
 - Add a useful message describing how to handle the situation:

        [[deprecated("use bar instead")]] void foo() {}

   Which will result in:

         warning: 'foo' is deprecated: use bar instead [-Wdeprecated-declarations] foo(); ^ note: 'foo' has been explicitly marked deprecated here void foo() {} ^

 - Add an associated TODO describing when to remove the feature (date and/or ROS version)

## Exceptions

 - Catch known exceptions and log them in detail. Avoid using ``catch (...)`` as it hides information about a possible fault. We want to know if something goes wrong.
 - We don't catch exceptions that don't derive from ``std::exception`` in rm-controls. It is the responsibility of the plugin provider to handle non-``std::exception``-derived exceptions locally.

## Logging

 - The ROS logging functionality is utilized and namespaced. i.e. ``ROS_INFO_NAMED(LOGNAME, "Starting listener...``.
   - This makes it easier to understand where output is coming from on the command line and allows for more fine-grained filtering of terminal output noise.
   - Your logging namespace is defined as a ``const`` variable. (eg: ``constexpr char LOGNAME[] = "robot_state";``)
   - The use of the file name as the NAMED namespace is best practice, i.e. rm_hw.cpp would use ``"rm_hw"``
   - Avoid using the package name as the namespace as this is already output by the logger

## pre-commit Formatting Checks

In many of our repos we have a [pre-commit](https://pre-commit.com/) check that runs in CI.
You can use this locally and set it up to run automatically before you commit something.
To install, use pip:

    pip3 install pre-commit

To run over all the files in the repo manually:

    pre-commit run -a

To run pre-commit automatically before committing in a local repo, install git hooks:

    pre-commit install

## clang-format Auto Code Formatting

Note that if you use pre-commit as described above, clang-format is applied automatically before each commit (if `clang-format-10` is installed). This section describes how to use it manually.

You can run **clang-format** in several ways. To install on Ubuntu simply run:

    sudo apt install clang-format-10

Please note that we rely on clang-format version **10**. Sadly, newer versions are not fully backward compatible.

clang-format requires a configuration file in the root of your catkin workspace. All rm-controls repo provides same file on repo root file.
.

### Command Line

Format a single file:

    clang-format-10 -i -style=file MY_FLIE_NAME.cpp

Format an entire directory recursively including subfolders:

    find . -name '*.h' -or -name '*.hpp' -or -name '*.cpp' | xargs clang-format-10 -i -style=file $1

### Exceptions to clang-format

Occasionally the auto formatting used by clang-format might not make sense e.g. for lists of items that are easier to read on separate lines. It can be overwritten with the commands:

    // clang-format off
    ... some untouched code
    // clang-format on

Use this sparingly though.

> [!Tip]
>
> The command Line tools are troublesome? Try [CLion IDE Configuration]().


## clang-tidy Linting

**clang-tidy** is a linting tool for C++. Where **clang-format** will fix the formatting of your code
(wrong indentation, line length, etc), **clang-tidy** will fix programming errors to make your code
more modern, more readable, and less prone to common bugs.

You can install clang-tidy and other clang related tools with
`sudo apt install clang-tidy clang-tools`

Similarly to clang-format, clang-tidy uses the configuration file `.clang-tidy` that is found first when traversing the source folder hierarchy upwards. All rm-controls repo provides this file on repo root file.

Unlike clang-format, clang-tidy needs to know the exact compiler options used to build your project.
To provide them, configure cmake with ``-DCMAKE_EXPORT_COMPILE_COMMANDS=ON`` and cmake will create in the package's build
folder a file called ``compile_commands.json``. _After_ building, you can run clang-tidy to analyze your code and even
**fix** issues automatically as follows:

```sh
for file in $(find $CATKIN_WS/build -name compile_commands.json) ; do
	run-clang-tidy -fix -header-filter="$CATKIN_WS/.*" -p $(dirname $file)
done
```

You can run it also on selected folders or files of a package by specifying regular expressions to match the file names:
```sh
run-clang-tidy -fix -header-filter="$CATKIN_WS/.*" -p $CATKIN_WS/build/moveit_core collision
```

Note that if you have multiple layers of nested ``for`` loops that need to be converted, clang-tidy
will only fix one at a time. So be sure to run the above command a few times to convert all code.

If you are only interested in the warnings, clang-tidy can also run directly during your build.
You can make a specific clang-tidy build with:
```
catkin config --cmake-args -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DCMAKE_CXX_CLANG_TIDY=clang-tidy
catkin build
```

> [!Tip]
>
> The command Line tools are troublesome? The CLion IDE has [Clang-Tidy integration](https://www.jetbrains.com/help/clion/clang-tidy-checks-support.html).


### Exceptions to clang-tidy

It is possible to suppress undesired clang-tidy checks by using **NOLINT** or **NOLINTNEXTLINE** comments. Please specify the check names explicitly in parentheses following the comments:
```c++
const IKCallbackFn solution_callback = 0; // NOLINT(modernize-use-nullptr)

// NOLINTNEXTLINE(performance-unnecessary-copy-initialization)
robot_state::RobotState robot_state(default_state);
```
Note that `modernize-loop-convert` check may convert `for (...; ...; ...)` loops to `for (auto & ... : ...)`.
However, `auto` is not an expression highly readable.
Please explicitly specify the variable type, if it doesn't become clear immediately from the context:
```c++
for (const int & item : container)
  std::cout << item;
```

## Credits
This file is modified by [MoveIt Code Style Guidelines](https://moveit.ros.org/documentation/contributing/code/).