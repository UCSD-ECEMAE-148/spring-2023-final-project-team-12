
# DIY Robocars Race - Team 12
<p align="center">
  <img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/008e64bb-85bd-4459-ad25-0c31773ff353" width = "550">
</p>

<p align="center">
  <img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/e5e29197-17f3-4b9f-b6f5-b40c419082cf"
</p>

## Team Members

<p align="left">
  <img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/d92e02f2-502b-45cb-a707-6ad5d4f0bbb0" width="500">
</p>

- Maxamillian Miller - ECE (left)
 
- Nicholas Felix Sudi - MAE (right)

- Nicholas Vo - MAE (middle)




## Robot Schematic
Connections Schematic

<img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/93ff8ccf-f560-4e07-954e-79a7349056ee" width="550">

Early Iterations

![d7](https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/ae1a0723-30df-4738-bf8e-9bea885a8819)

Final Iterations

![d6](https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/0d391b2e-c01d-4f0b-a76a-01e242841ca1)

Optimized Body

<img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/1cfeed3c-b2c4-4d25-87c2-12d4c7d99497" width="575">

3D Files

<img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/26fa852b-b14d-436e-98af-5f970058f0de" width="200">
<img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/d96113dc-ec26-4e3c-bc32-a9ef4e75de50" width="200">
<img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/94bfb155-58e2-4867-8d33-d434eee093ab" width="200">


## Autonomous Laps Videos

### Team 12 Youtube Playlist
https://youtube.com/playlist?list=PLRzEsmfrMLwh-KDtstVKR3EGWf1wxY4qj
### DonkeyCar GNSS
https://youtu.be/js35wH198ws
### DonkeyCar AI
https://youtu.be/7cZigr_Hb0k
### Lane Detection
https://youtu.be/GnItAcpV_7A

## Final Project
### Project Proposal

The goal for our project was to create a car capable of racing in the DIY Robocar Race held in Oakland California at the end of the quarter. We would use lidar and camera to establish which is best in producing an autonomous vehicle that is capable of racing at speed. We would also streamline the design of our car, refining it and moving it from a prototype stage to a more 

### Project Overview

The focus of our project started with the lidar. This is because after viewing how SLAM (Simultaneous Localization and Mapping) worked we believed that it would be the more flexible and consistent option of the two. SLAM works by using a combination of lidar and odometer data in order to create a map of its surroundings using multiple transforms which can be considered reference points to triangulate location. We started with generating the map in ROS using the Hector SLAM. This went pretty well and we were able to generate a good looking map by doing some basic troubleshooting like relocating the lidar and going slow while mapping.We then attempted to use the generated map in NAV1 in order to allow the robot to localize itself in the map and then move itself autonomously. This is where we started encountering significant issues. The robot would not be able to localize itself within NAV1 and as a result could not move within the map. Attempting to find documentation that could help us troubleshoot NAV1 was almost non-existent so we moved on to another option which was to use the SLAM toolbox which is a separate SLAM algorithm that operates in ROS2. We did this as there was far more comprehensive documentation for this compared to Hector SLAM. However, the problem we encountered was the fact that the transforms created for the robot were specifically designed to work with Hector SLAM and not SLAM toolbox which meant that the robot was not able to find the reference points needed to determine its location while mapping, preventing us from even mapping. We tried numerous methods to try to solve this problem like adjusting the urdf file for the machine and trying to track down the transforms causing problems but despite our best efforts we were unable to get SLAM toolbox to a point where it would be able to generate a proper map. Due to the difficulties with SLAM we decided to pivot our main focus to the camera which would use donkey car AI training in order to autonomously race. We attempted to integrate the depth function for the OakD lite with the color camera in order to allow for the car to detect obstacles in front of it. We were able to get the robot to recognize the orange traffic cones in front of it and avoid them. However this is unfortunately where our endeavors ended as we did not have enough time to refine the training in order to create an autonomous race car that could race at speed.

### Gantt Chart 
<p align="center">
  <img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/08888e16-98e5-41c3-b30c-a7ba28e0d3d1" width="500">
</p>

### Implementation 
#### Including DonkeyCar Depth
In jetson:
```
gedit projects/donkeycar/donkeycar/parts/camera.py
```
Copy and paste camera.py (Changing the blue color to take depth input) (Credit: Girish from DSC 178)

To remove old data and record:
```
cd projects/d4
rm -r data
mkdir data
python manage.py drive
```

After recording:
Scp to computer and train it in your computer, copy the model back to jetson, and
```
cd projects/d4
python manage.py drive --model=./models/model_name.h5 --type=linear
```

### Pictures and Videos
<p align="center">
  <img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/7f6b30d8-e508-48d5-ba33-9d4fb6226fee" width="400">
</p>
DonkeyCar allows 3 channel from the camera so Red and Green is used with Blue to visualize depth

https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/9fe1a51f-9874-41fa-ab0a-ea6c5f6554a9


## Presentations

### Weekly Presentations 
https://docs.google.com/presentation/d/10cdow0kZToZQNKFimAG8-7LkItVgFZkWeKg42pyX16M/edit?usp=sharing

### Final Presentation
https://docs.google.com/presentation/d/1ykZrViwCvIwv0nYjjEKjMLFS0MpZMi5blVBvs2Jc6pE/edit?usp=sharing

## Failed Attempt on SLAM
### Instructions for Installation 

#### SLAM Toolbox
(Credit: Raymond from DSC 178)

Follow the instructions in docs

https://docs.google.com/document/d/1eUxEY5loVYTPH8-Mi8he468MwqytkhGQesTpLuJlpZI/edit?usp=sharing

Might need to change joy_teleop or vesc_odom in controls and actuators to recalibrate transformations

#### Pure Pursuit Algorithm from Steven Gong 

git clone to your src (we can get rid of the other ones and just keep pure pursuit)

https://github.com/CL2-UWaterloo/f1tenth_ws/tree/main

if given more time, create waypoints, change map, and use this algorithm

https://stevengong.co/notes/F1TENTH-Field-Usage/
