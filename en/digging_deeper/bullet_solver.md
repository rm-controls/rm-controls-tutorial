# Model derivation
Air resistance is proportional to speed, and the target point moves at a constant speed.
**2D Model**: In the xz plane, assuming that the bullet launching point is the coordinate origin, the actual position of the bullet is equivalent to a vector in the xoz plane.
![示意图](https://s1.ax1x.com/2020/10/23/BEarLj.png)
Use to represent the component of the bullet position vector in the X direction, $\vec{v_x}, \vec{v_z}$ represent the component of the bullet velocity on the x axis and z axis, respectively,and use $\vec{z}$ to represent the component of the bullet position vector in the z direction; $v_0$ represents the initial launch velocity of the bullet, k is the air resistance coefficient, g is the acceleration of gravity, m is the weight of the bullet, and $f_x$ is the position of the bullet. The component of air resistance in the X direction.Based on physical knowledge:
$$\vec{f_x}=-k\vec{v_x}=m\frac{d\vec{v_x}}{dt}\tag{1}$$
Sort (1) to get:
$$-\frac kmdt=\frac{d\vec{v_x}}{v_x}$$
Taking the time of bullet launching as time 0, the component of the initial launch velocity in the x direction is $\vec{v_x}$, Integrate the above formula:
$$\int_0^t-\frac kmdt=\int_{v_{x0}}^{v_x}\frac{dv_x}{v_x}\tag{2}$$
Solved by (2): $$v_x=\frac{dx}{dt}=v_{x0}e^{-\frac kmt}$$ Integrate both sides of the above formula to obtain:
$$x=\frac mk v_{x0}(1-e^{-\frac kmt})\tag{3}$$
At the same time, the resistance of the bullet in the z-axis direction can be obtained as:
$$\vec{f_z}=-k\vec{v_z}-mg=m\frac{d\vec{v_z}}{dt}$$
Sort out the differential equation:
$$\frac{dv_z}{dt}+\frac kmv_z+g=0\tag{4}$$
Solutions have to:
$$z=\frac km\left(v_{z0}+\frac{mg}k\right)\left(1-e^{-\frac kmt}\right)-\frac{mg}kt\tag{5}$$
Target point motion model: Suppose the starting position of the target point is $\left(x_{t0}, z_{t0}\right)$, The speed of the target point in the x-axis direction is $v_{tx}$, the speed in the z-axis direction is $v_{tz}$, the component of the actual position of the target point in the x-axis direction is $x_t$, in the z-axis The component of the direction is $z_t$.
$$x_t=x_{t0}+v_{tx}t\\z_t=z_{t0}+v_{tz}t$$ 