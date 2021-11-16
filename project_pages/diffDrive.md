## Differential Drive Simulation in Python

**Project description:** I completed this project in order to use it as a base point for more complex robotics projects. Primarily, my goal was to integrate this robot with other projects such as the LIDAR sensor for SLAM as well as for path planning algorithms. Using the pygame package (due to easy visualization tools), I was able to simulate a differential drive robot controlled by user commands with a display for wheel velocities as well as the robot's angle.

Demonstration: <video src="https://user-images.githubusercontent.com/41236722/141938673-df14ddb2-e90c-416c-8ab5-5776c6a73c04.mp4" data-canonical-src="https://user-images.githubusercontent.com/41236722/141938673-df14ddb2-e90c-416c-8ab5-5776c6a73c04.mp4" controls="controls" muted="muted" class="d-block rounded-bottom-2 width-fit" style="max-height:640px;"></video>

### 1. Defining the Enviroment Class
The Environment class is a simple class created to handle the map data as well as update the labels representing wheel velocities and robot angle. The class also contains a function used to draw the trail left behind the robot which allows for better visual understanding of the robot's movement relative to previous positions.
```python
def trail(self, pos):
    for i in range(0, len(self.trail_set) - 1):
        pygame.draw.line(self.map, self.yel, (self.trail_set[i][0], self.trail_set[i][1]), (self.trail_set[i+1][0], self.trail_set[i+1][1]))

    if self.trail_set.__sizeof__()>3000: # adjustable length of trail
        self.trail_set.pop(0)
    self.trail_set.append(pos)
 ```

### 2. Defining the Robot
The Robot class is given the starting position, the robot "image", and the size of the robot in pixels. Two functions are defined in this class, the simpler one being the draw() method which updates the map with the robot's new position. The move method detects user input and determines how to adjust the individual wheel velocities of the left and right "motors" of the robot. The angle of the robot is also calculated.
```python
# Portion of the Robot.move() function
# dt represents the change in time since last moving
      self.x += ((self.vl + self.vr)/2)*math.cos(self.theta)*dt
      self.y -= ((self.vl + self.vr)/2)*math.sin(self.theta)*dt
      self.theta += (self.vr - self.vl)/self.w*dt

      if self.theta > 2*math.pi or self.theta < -2*math.pi:
          self.theta = 0

      self.rotated = pygame.transform.rotozoom(self.img, math.degrees(self.theta), 1)
      self.rect = self.rotated.get_rect(center=(self.x, self.y))
```
