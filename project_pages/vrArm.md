### VR-Controlled 6DOF Robotic Manipulator

This was my latest project and the original goal was to design and build a 6DOF robotic arm, similar in style to the UR3 commerical robot. I then came up with the concept of integrating a VR controller to enable teleoperation for data collection purposes.

I completed this project during my senior year, but I haven't updated this page with code or videos of the system. If you're interested in learning more, please feel free to contact me at sulkunte@gmail.com!

#### Quick Physics Demo With IK Solver

<video src="https://github.com/SachinSulkunte/SachinSulkunte.github.io/assets/41236722/7fe8b703-a5cf-4ffa-86b7-94d05fccbf6c" data-canonical-src="https://github.com/SachinSulkunte/SachinSulkunte.github.io/assets/41236722/7fe8b703-a5cf-4ffa-86b7-94d05fccbf6c" controls="controls" muted="muted" class="d-block rounded-bottom-2 width-fit" style="max-height:300px;"></video>


#### Notes
- Integrated with Meta Quest 2 for VR-based control
- Physical robot designed in Autodesk Fusion360, 3D printed in ABS, and run with NEMA stepper motors
- Sim-to-real tested with both Isaac Lab and PyBullet
- Tested planning via CuRobo (GPU-accelerated motion planning)