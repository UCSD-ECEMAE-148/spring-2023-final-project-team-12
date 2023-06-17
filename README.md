
# DIY Robocars Race - Team 12
<p align="center">
  <img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/008e64bb-85bd-4459-ad25-0c31773ff353" width = "550">
</p>

<p align="center">
  <img src="https://github.com/UCSD-ECEMAE-148/spring-2023-final-project-team-12/assets/130114883/e5e29197-17f3-4b9f-b6f5-b40c419082cf"
</p>

## Team Members

<p align="center">
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
### Overview


### Proposal

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

Follow the instructions in pdf

https://docs.google.com/document/d/1eUxEY5loVYTPH8-Mi8he468MwqytkhGQesTpLuJlpZI/edit?usp=sharing

Might need to change joy_teleop or vesc_odom in controls and actuators to recalibrate transformations

#### Pure Pursuit Algorithm from Steven Gong 

git clone to your src (we can get rid of the other ones and just keep pure pursuit)

https://github.com/CL2-UWaterloo/f1tenth_ws/tree/main

if given more time, create waypoints, change map, and use this algorithm

https://stevengong.co/notes/F1TENTH-Field-Usage/
