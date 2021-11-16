## LIDAR Sensor Simulation Using Python

**Project description:** I completed this project in order to use it as a base point for more complex robotics projects. Primarily, my goal was to develop a SLAM (simultaneous localization and mapping) program which utilized a LIDAR sensor. Using the pygame package (due to easy visualization tools), I was able to simulate a LIDAR sensor which follows the location of the user's mouse, sending out beams at customizable intervals. The sensor can also be fed an uncertainty value which follows a Gaussian distribution in order to better simulate the data received by a real LIDAR sensor. 

Demonstration: <video src="https://user-images.githubusercontent.com/41236722/141938673-df14ddb2-e90c-416c-8ab5-5776c6a73c04.mp4" data-canonical-src="https://user-images.githubusercontent.com/41236722/141938673-df14ddb2-e90c-416c-8ab5-5776c6a73c04.mp4" controls="controls" muted="muted" class="d-block rounded-bottom-2 width-fit" style="max-height:600px;"></video>

### 1. Defining the Sensor Class
The Laser class was built to handle the various parameters associated with the sensor. A created object can be given a maximum range the sensor is capable of as well as a tuple to define the uncertainty distribution. The class contains a method to calculate the absolute distance between the current position and the "reflected" point which the laser is hitting. There is also a method which defines behavior for when an obstacle is sensed. Black pixels are considered to be objects as the map fed to the program is black and white. If the sensor hits a black pixel between its position and its max range then a data point is created with uncertainty added to it. The datapoint is added to a point cloud which is displayed as the red dots on the screen.
```python
def sense_obstacles(self):
        data = []
        x1, y1 = self.position[0], self.position[1]
        for angle in np.linspace(0, 2*math.pi, 60, False): # resolution determined by number of sampling angles
            x2, y2 = (x1 + self.Range * math.cos(angle), y1 - self.Range * math.sin(angle)) # end of max length line segment
            for i in range(0, 100): # interpolation of defined line
                u = i / 100
                x = int(x2 * u + x1 * (1 - u))
                y = int(y2 * u + y1 * (1 - u))
                if 0 < x < self.W and 0 < y < self.H:
                    color = self.map.get_at((x,y))
                    if ((color[0], color[1], color[2]) == (0, 0, 0)): # black detected along line
                        distance = self.distance((x,y))
                        output = uncertainty_add(distance, angle, self.sigma)
                        output.append(self.position)
 ```

### 2. Defining the Environment
The Environment class is a simple class created to handle the map data as well as update the map with the point cloud data from the sensor. The class contains a point_cloud variable which holds (x,y) positions for detected obstacles. Another function extracts the x and y coordinates from the given distance and angle measurements. The last function updates an overlay map with the point_cloud data - creating the red dots seen on the map.

```python
def AD2pos(self, distance, angle, robotPosition): # convert distance to x and y position
        x = distance * math.cos(angle) + robotPosition[0]
        y = -distance * math.sin(angle) + robotPosition[1]
        return (int(x), int(y))

    def dataStorage(self, data):
        if data is not None:
            for element in data:
                point = self.AD2pos(element[0], element[1], element[2]) # get coordinates
                if point not in self.pointCloud:
                    self.pointCloud.append(point)
    
    def show_sensorData(self):
        self.infomap = self.map.copy()
        for point in self.pointCloud:
            self.infomap.set_at((int(point[0]), int(point[1])), (255, 0, 0)) # create red dots at position
```

### 3. Running the Program
The program is run via creating an environment and laser object. Desired parameters such as the map to be used as well as the uncertainty and range of the sensor are provided in these initializations. The map is then blacked out so that no information is known regarding the wall/obstacle positions and displayed to the user. While the mouse is on the window, the sensor is considered to be on and will be functioning at the specified rate indicated by the laser object. Red dots appear as the sensor impacts the "walls" and over time a complete map is formed.
```python
environment = env.buildEnv((600, 1200))
environment.originalMap = environment.map.copy()
laser = sensors.LaserSensor(200, environment.originalMap, uncertainty=(0.5,0.01))
environment.map.fill((0, 0, 0))
environment.infomap = environment.map.copy()

running = True

while running:

    sensorOn = False
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        if pygame.mouse.get_focused(): # mouse on window
            sensorOn = True
        elif not pygame.mouse.get_focused():
            sensorOn = False
        
    if sensorOn:
        position=pygame.mouse.get_pos()
        laser.position = position
        sensor_data = laser.sense_obstacles()
        environment.dataStorage(sensor_data)
        environment.show_sensorData()
    environment.map.blit(environment.infomap, (0,0)) # update map with infomap containing sensor data
    pygame.display.update()

```
