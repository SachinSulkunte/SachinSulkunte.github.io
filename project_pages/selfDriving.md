## Autonomous Vehicle

Videos and Code - Uploaded Soon

**Project description:** <br>
I completed this project in order to apply a variety of skills towards the development of a complex electromechanical system with autonomous capabilities. This "self-driving car" was built as a 4-motor differential drive robot for mechanical simplicity. A Jetson Nano is used for high-level decision making based on input from a RGBD-camera (Kinect Sensor). An Arduino is used for low-level motor control - receiving instructions via serial connection from the Nano. The system uses ROS for efficient feature implementation, with individual nodes representing features such as object detection and lane detection. RViz is used for 3D visualization. The controller subscribes to these nodes and makes steering and throttle decisions based upon a rule-based motion planning scheme. The RRT path planning algorithm is used for navigation to desired waypoints.
<br>

**Design Process:**

#### 1. Physical Assembly of Robot
  - Soldering connections between H-bridges and motors
  - Connecting to Arduino and Jetson Nano
  - Assembling onto two-tiered frame

> #### Initial Work with Camera
> - Communication between Kinect camera and Jetson Nano using libfreenect library to get RGB and Depth data
> - Build cameraUpdate() function into ROS node that publishes to ROS topic
> - Visualize point cloud data in RViz by reading from ROS topic

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

<br>
Visualization:
<img src="../images/RViz.png?raw=true"/>
<br>
Vehicle with Kinect Sensor, Jetson Nano, and Arduino Uno:
<img src="../images/MobileRobot.jpeg?raw=true"/>
