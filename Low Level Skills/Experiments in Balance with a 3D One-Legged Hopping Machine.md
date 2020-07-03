# Experiments in Balance with a 3D One-Legged Hopping Machine

Challenge is to design actively stabillized legged systems that can move on a narrow base of support allowing travel if path is narrow and filled with obstacles.

Previous control algorithms in 2D are comprised of 3 parts: one control system to control the forward running velocity, one to maintain the body in an erect posture, and one to regulate the hopping height. Authors argue extensions to 3D can be done with relatively little complexity

Repeated pressuring of air and exhausting in lower chamber of leg piston causes the 'springiness' of the leg. Timing between pressurizing and exhausting is timed to excite mass-spring oscillator formed by leg and body.

During flight, controller chooses forward position for foot appropriate to machine's travel. During stance controller generates torques at hip to maintain upright attitude.

3D algorithms decompose into same 3 parts as 2D algorithms. Running velocity control is done by positioning the foot w.r.t center of gravity during the flight phase. Attitude control is done by controlling hip torque during stance when foot is held in place by friction. Hopping height control is done by controllilng the thrust deilvered by the leg on each hop.

Forward velocity control is dependent on 2 factors. One factor finds the foot position that would result in no acceleartion of the body. The other factor calculates dispalcement of foot from zero-acceleartion foot position (factor 1) that will generate the desired acceleration. Acceleration is required as it allows changes to running vellocity, and helps stabillilze forwarad velocity against errors. 2 factors combine to give next foot position.

Finding nominal non-zero accelearation point of leg is analagous to finding a balance point on inverted pendulum. It is the position of the foot with equal amounts of forward and rearword tipping such that any tipping force is balanced by equal horizontal forces acting on the ground. No net forward acceleration is achieved when foot is symmetric about a vertical line passing through the center of mass. Between stances, foot spends equal time in front of COM and behind to balance tipping forces and achieve no net acceleration.

CG print is the locus points that the center of gravity will travel between stances. Symmetric motion is satisfied if foot stays directly in line with CG print. Forward displacement results in more time ahead of CG-print and a rearword tipping force. Vice versa is true for rearword displaacement. CG print is precalculated as aa function of current forward velocity. Current forward velocity is done by differentiating foot position during stance w.r.t time (recall foot position can be found by querrying actuator lengths).

Next foot position is calculated as a function of forward velocity, and velocity error (difference between forward velocity and desired forward velocity. Foot possitions are used to find aactuaator lengths that will correctly position foot. Since foot doesn't move, forward velocity is negative velocity of foot w.r.t hip. 

Body attitude is adjusted during stances by torque servos as angular momentum is conserved in flight. Pitch and roll torques are a function of position and velocity feedback gains, and pitch and roll error (desired pitch and roll is 0). Angles are with reference to the coordinate system of the body and rotaate and move with it. Velocity and position are with reference to the lab fraame coordinate system and body measurements must be adjusted to account for this.

Hopping height is regulated by applying fixed thrust to offset energy loss for each hopping cycle

Position control was achieved by using a controller to transfrom position errors and current velocity into desired velocity. This controller gives desired velocity and is a function of diagonal postiion and velocity gain matrices, position error current velocity. This desired velocity is clipped to a maximum value. Position can be found by integrating forward velocity estimate.

Paper: [Experiments in Balance with a 3D One-Legged Hopping Machine](https://journals.sagepub.com/doi/pdf/10.1177/027836498400300207)
