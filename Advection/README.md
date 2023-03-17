The files `*.dat` contain the L2 norm $\left( ||u||_2 \equiv \sqrt{\frac{\sum u_i^2}{N}} \right)$ of the solution $u$ of the advection equation ($u_t+u_x=0$) solved on a grid with resolution dx=0.1, extension 10, 101 points, and different numerical methods:
- FTCS = Forward in Time, Centered in Space
- LAX = Lax-Friedrichs
- LAXWENDROFF = Lax-Wendroff
- LEAPFROG = Leapfrog

The initial data was given by $u(x,t=0)=\exp{[-(x-x_0)^2]}$ with $x_0=5$.

A Courant factor of 0.5 and periodic boundary conditions were used in the simulation.

The code implementing these methods was written by me in C++ and it is not included in this repository.