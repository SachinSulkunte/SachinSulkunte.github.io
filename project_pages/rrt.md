## Path Planning - Rapidly Expanding Random Tree (RRT) Algorithm

**Project description:** I wanted to explore different methods of path planning. I decided to start by implementing the RRT algorithm as it both creates a graph and identifies a path. While this path is nonoptimal, the algorithm is relatively simple to implement and is typically faster than an algorithm like A* although A* finds shorter paths.
<video src="https://user-images.githubusercontent.com/41236722/142127729-16ac21de-564f-4f91-8f2d-2fa2e3fe116e.mp4" data-canonical-src="https://user-images.githubusercontent.com/41236722/142127729-16ac21de-564f-4f91-8f2d-2fa2e3fe116e.mp4" controls="controls" muted="muted" class="d-block rounded-bottom-2 width-fit" style="max-height:300px;"></video>

### 1. Defining the Map
In order to implement this algorithm, I created several functions dedicated to generating a random series of obstacles (represented by grey squares) placed on the map. A start position and goal position are also defined and identified on the map as green circles. 
```python
def makeobs(self):
        obs = []
        for i in range(0, self.obs_num):
            rect = None
            startgoal = True
            while startgoal: # check if start or goal is inside obstacle
                upper = self.makeRandomRect()
                rect = pygame.Rect(upper,(self.obs_dim, self.obs_dim))
                if rect.collidepoint(self.start) or rect.collidepoint(self.goal):
                    startgoal = True
                else:
                    startgoal = False
            obs.append(rect)
        self.obstacles = obs.copy()
        return obs
 ```

### 2. Defining the RRT Functions
There are several functions dedicated to creating and removing nodes as well as edges. The overall nodes are managed in three lists which contain their x-position, y-position, and parent node indexed. There are also functions to calculate the distance between nodes using simple trigonometry as well as identifying which nodes are closest. Lines are interpolated between nodes and checked to see if they cross through an obstruction which removes the edge. Finally, once the end goal has been reached a function is called to identify the actual path leading from the start node to the goal position.
```python
def waypoints2path(self):
        oldpath = self.get_path_coords()
        path = []
        for i in range(0, len(self.path) - 1):
            print(i)
            if i >= len(self.path):
                break
            x1, y1 = oldpath[i]
            x2, y2 = oldpath[i + 1]
            print('---------')
            print((x1, y1), (x2, y2))
            for i in range(0, 5):
                u = i / 5
                x = int(x2 * u + x1 * (1 - u))
                y = int(y2 * u + y1 * (1 - u))
                path.append((x, y))
                print((x, y))
```

### 3. Running the Program and Next Steps
The program runs extremely quickly, generating a path in a very short period of time. My next goal is to integrate the generated path with my differential drive robot simulation in order to get the robot to follow the identified path from the start to goal points. I also aim to implement further path planning algorithms and compare efficiency and the optimization of paths.
