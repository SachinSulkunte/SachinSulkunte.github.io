## RMRA Management System: MySQL Based Tool for Improving Organization Coordination and Efficiency

**Project description:** I completed this project during my time as President of the Rockville-Montgomery Robotics Association, a student-run nonprofit dedicated to providing STEM education to underrepresented and unprivileged populations. As the President of the nonprofit, I knew firsthand how difficult it was to coordinate the various outreach events that were running throughout the week and ensure that volunteers were engaged with the organization by signing up to present at events. This led me to the decision to develop a management system extended from the organization's public website that would enable authenticated users to access various functionalities.

### 1. Provide Access to Organization-Wide Objectives and Goals

I wanted all of our volunteers to be fully aware of the organization's current goals and what we were seeking to achieve so that in the event members missed a meeting, they would be able to see what the organization wants to achieve and in what timeline that goal was to be achieved. I built a page using PHP and CSS as well as a connection to a MySQL relational database that permitted the addition of "goals" and their parameters. Users could mark the goal as completed and also view the goals in a sorted list of those still needing to be completed.
<img src="images/EBRTPage.png?raw=true"/>

### 2. Volunteer Registration
Users can sign up for any events that have been added to the event list. Selecting the event and choosing to submit alters the event list to include the volunteer's name on the event listing to indicate the number of volunteers signed up for an event. 
<img src="images/TreatmentsPage.png?raw=true"/>


### 3. Event List: Attending Volunteers, Location, Date
Program has a radiation calculator which is regulated by a dictionary, allowing users to select the type of treatment/test they are expecting to get and then returning an approximate radiation amount based on collected data. The application also characterizes this information in an easier, more digestible fashion by developing simple comparisons for the radiation result such as "Radiation Amount = Taking XX Plane Trips".
```Swift
 //Sample Code Section
 let naturalBackgroundDose = 3.1  //average value - see sources page
 let dosage = usedDose/naturalBackgroundDose
 var str = ""
 let doseFrac = rationalApproximation(of: dosage)  //conversion to rational value
 if(dosage < 1){
   if(doseFrac.den < 10){
     str = fractionToString(fraction: doseFrac)
   }
   else {
     str = String((dosage * 100).rounded() / 10)
   }
}
```

For more details see [App Demonstration Video](https://vimeo.com/295086496).
