## Autonomous Vehicle

Videos and Code - Uploaded Soon

**Project description:** <br>
I completed this project in order to apply a variety of skills towards the development of a complex electromechanical system with autonomous capabilities. This "self-driving car" was built as a 4-motor differential drive robot for mechanical simplicity. A Jetson Nano is used for high-level decision making based on input from a RGBD-camera (Kinect Sensor). An Arduino is used for low-level motor control - receiving instructions from the Nano. The system uses ROS for efficient feature implementation, with individual nodes representing features such as object detection and lane detection. RViz is used for 3D visualization. The controller subscribes to these nodes and makes steering and throttle decisions based upon a rule-based motion planning scheme. The RRT path planning algorithm is used for navigation to desired waypoints.
<br>

***Implemented Features:*** <br>
- Rule-Based Planning with Object Recognition and Detection <br>
- SLAM <br>
- End-to-End Learning-Based Lane Detection <br>
- Adaptive Cruise Control <br>
- PID Controller <br>
- Path Planning using RRT Algorithm

**Future Features**
- GUI for Simple Mapping and Setting Waypoints
- PID Control Alternatives - [Predictive Functional Control](https://ieeexplore.ieee.org/document/7526765)
- Automated Parking
- Ackermann Steering System
