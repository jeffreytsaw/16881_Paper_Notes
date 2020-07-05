# Control of a Biped Somersault in 3D

3 ways of performing reorientations in flight with no angular momentum changes: Changing moment of inertia to influlence rotation rate (i.e figure skater spins), momentum free rotations through folding and unfollding, reorient principle axis of inertia to the fixed angulalr momentum vector (used often to induce twists in somersaults)

Reroienting body relative to angular momentum vector helps initiate twists. Reorientations instigated through asymmetric motions of arms or legs.

Timing of movements more crucial thaan speed at which reorientaations occur.

Mechanics of the somersault relates time of flight and time to rotate through desired change in body orientation. More specifically, it finds the ratio of required change in pitch to successfully land somersaualt to pitch change rate at lift off by relating height and vertical velocity of com at lift-off, and desired height of com at touchdown.

One strategy is to precisely control initial conditions (pitch rotation rate, vertical velocity and position of com) to satisfy the somersault mechanics equation. This would create a somersault to desired pitch rotation. Problem is changes to these initial conditions would drastically affect performance. Instead a feedback system is employed that regulates motion based on measure of success (i.e mechanics of somersault relation) through conrolling pitch rate.
T
Controlling moment of inertia can reduce or increase pitch rotaation rate (through conservation of angulaar momentum relations). If time to land is known, landing attitude is controlled by pitch rotaation rate.

Controller to control moment of inertia (i.e leg lengths) to achieve required pitch rotation for aa landable attitude is a modified version of somersault mechanics equaation. A function f calculates the difference between landing attitude of current pitch rate and the desired landing pitch rate. The sign of f is used to increase or decrease pitch rate to make f = 0. f is a non-linear function of leg length so Newton search recursively solves for desired leg length.

At a high level, each control cycle first measures state, estimates f, computes the change in leg leg length (a function of f and derivative of f w.r.t leg length), estimates next value of f using updated leg length, if sufficiently accurate, sets leg length to final value. 

At liftoff maximum hip torque and leg thrust is applied, so maximum pitch rotation rate is measured at initial takeoff. Tuck servo then alters pitch rate and leg length to ensure desired body attitude is achieved on landing.

Paper: [Control of a Biped Somersault in 3D](https://ieeexplore-ieee-org.proxy.library.cmu.edu/stamp/stamp.jsp?tp=&arnumber=587396)
