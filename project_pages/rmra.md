## RMRA Management System: MySQL Based Tool for Improving Organization Coordination and Efficiency
<img src="../images/login.png?raw=true"/>

**Project description:** I completed this project during my time as President of the Rockville-Montgomery Robotics Association, a student-run nonprofit dedicated to providing STEM education to underrepresented and unprivileged populations. As the President of the nonprofit, I knew firsthand how difficult it was to coordinate the various outreach events that were running throughout the week and ensure that volunteers were engaged with the organization by signing up to present at events. This led me to the decision to develop a management system extended from the organization's public website that would enable authenticated users to access various functionalities.

### 1. Provide Access to Organization-Wide Objectives and Goals

I wanted all of our volunteers to be fully aware of the organization's current goals and what we were seeking to achieve so that in the event members missed a meeting, they would be able to see what the organization wants to achieve and in what timeline that goal was to be achieved. I built a page using PHP and CSS as well as a connection to a MySQL relational database that permitted the addition of "goals" and their parameters. Users could mark the goal as completed and also view the goals in a sorted list of those still needing to be completed.
<img src="../images/goals.png?raw=true"/>

### 2. Volunteer Registration
Users can sign up for any events that have been added to the event list. Selecting the event and choosing to submit alters the event list to include the volunteer's name on the event listing to indicate the number of volunteers signed up for an event. 
<img src="../images/volunteer.png?raw=true"/>

### 3. Event List: Attending Volunteers, Location, Date
A list of events sorted by date are displayed for users to view. Each list entry contains the location of the event, the date, the volunteers attending, as well as a description of what the event entails. The attending volunteers parameter is updated when a user registers to volunteer at an event through the registration page.
<img src="../images/events.png?raw=true"/>

```php
 <!--print out existing events-->
    <?php
    require_once 'config.php';
    //store all data
    $sql = "SELECT * FROM events ORDER BY event_sTime ASC"; //sets events in date order oldest to newest
    $result = mysqli_query($link, $sql) or die(mysqli_error($link));
  
    print("<h2>Events</h2>");
    
    //upcoming events
    while($row = mysqli_fetch_array($result)){ 
            echo "<div class='goal'>";
            echo "<a href='delete_Event.php?id=" . $row['event_id'] . "'><button class='btnComplete'>Delete</button></a><strong>";
            echo $row['event_Name'] . "</strong><p>" . $row['event_Location'] . "</p>" . "Event Date: " . $row['event_sTime'];
            echo "<p>Volunteers: ";
            $attribute = $row['event_Name'];
            $user = "SELECT username FROM eventUsers WHERE event_Name = '$attribute'";
            $volunteers = mysqli_query($link, $user) or die(mysqli_error($link));
            while($u_row = mysqli_fetch_array($volunteers)){
              echo $u_row['username'] . ",     ";
            }
            echo "</div>";
    }
  ?>   
```

For more details see [App Demonstration Video](https://vimeo.com/295086496).
