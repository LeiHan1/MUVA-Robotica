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

Here is the first lap with controllers PD (02m24s of simulation time)
[![Watch the video](https://github.com/LeiHan1/MUVA-Robotica/blob/master/FollowLine/img/cover.PNG)](https://www.youtube.com/watch?v=7jyP9tny44g)

This first lap is executed with a low velocity (v=3).


Week 17/02/20 - 23/02/20
------------------
To improve the efficiency of our car, we set our new reference at a  point which is further than the old center from the view of the car. This is implemented by cutting the color mask and preserving the top part of it, the new center of reference is the center of the top part.
![Illustration of the new center](https://github.com/LeiHan1/MUVA-Robotica/blob/master/FollowLine/img/new_center.png)

By adjusting the parameters of controllers PD and velocity, our car can run faster. 

Here is the lap by calculating the new center of reference (00m43s of simulation time)
[![Watch the video](https://github.com/LeiHan1/MUVA-Robotica/blob/master/FollowLine/img/cover.PNG)](https://www.youtube.com/watch?v=_Bwfmptw_8Q)

This lap is executed with a higher velocity than the first lap (v=10).


Week 24/02/20 - 01/03/20
------------------
