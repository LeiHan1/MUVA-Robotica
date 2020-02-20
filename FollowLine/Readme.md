# FOLLOW LINE
Student: Lei Han


The goal of this exercise is to perform a PID reactive control capable of following the line painted on the racing circuit.


Week 10/02/20 - 16/02/20
------------------
The first step is to detect the red line. For this, we use OpenCV to filter the red color from the image and get its contours (by applying moments, check this [link](https://stackoverflow.com/questions/22470902/understanding-moments-function-in-opencv) referenced by [jderobot academy](https://jderobot.github.io/RoboticsAcademy/exercises/follow_line/)). 
Then we take the center of the largest contour as a reference point, we compare its X position in each frame of images to measure the desviation of the driving direction.

![Illustration of color filtering](https://github.com/LeiHan1/MUVA-Robotica/blob/master/FollowLine/img/moments.png)
