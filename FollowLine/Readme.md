# FOLLOW LINE
Student: Lei Han


The goal of this exercise is to perform a PID reactive control capable of following the line painted on the racing circuit.


Week 10/02/20 - 16/02/20
------------------
The start the excercise, first we need to detect the red line. For this, we use OpenCV to filter the red color from the image and get its contours (by applying moments, check this [link](https://stackoverflow.com/questions/22470902/understanding-moments-function-in-opencv) referenced by [jderobot academy](https://jderobot.github.io/RoboticsAcademy/exercises/follow_line/)). 
Then we take the center of the largest contour as a reference point, we compare its X position in each frame of images to measure the desviation of the driving direction.

![Illustration of color filtering](https://github.com/LeiHan1/MUVA-Robotica/blob/master/FollowLine/img/moments.png)


Next step is to add PID reactive control that complements the car's driving system, we need to modify the w parameter of the system to make the car rotate when we are on curves.

First we implement the P controller. P controller gets the w parameter by calculating the error between two center's X position and multiply it by a constant coefficient K.

The controller P is low at reacting facing high error and it has a problem of the oscilation
![Oscillation of the car](https://github.com/LeiHan1/MUVA-Robotica/blob/master/FollowLine/img/oscilation-problem.gif)

To solve this, we adjust the coefficient of the controller P and we add another controller called D. Controller D calculates the derivative of the output error.

Here is the firs lap with controllers PD
[![Watch the video](https://github.com/LeiHan1/MUVA-Robotica/blob/master/FollowLine/img/cover.PNG)](https://www.youtube.com/watch?v=7jyP9tny44g)


Week 17/02/20 - 23/02/20
------------------
