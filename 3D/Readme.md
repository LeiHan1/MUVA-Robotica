
# 3D RECONSTRUCTION
Student: Lei Han


The goal of this exercise is to generate a 3D reconstruction of the scene that it is receiving throughout its left and right cameras.

Steps
------------------
In this exercise we will follow the steps as indicated in the website of [JdeRobot Academy](https://jderobot.github.io/RoboticsAcademy/exercises/ComputerVision/3d_reconstruction):

1. Detect the feature points in one image plane
2. Detect the feature point corresponding the one found above
3. Triangulate the point in 3d space


Feature points
------------------
In this step we use Canny detection algorithm provided by OpenCV to get the feature point (the borders)
![Illustration of canny detection](https://github.com/LeiHan1/MUVA-Robotica/blob/master/3D/imgs/left_orig.jpg)


Calculating Correspondences
------------------
Now we calculate matching points by using the function 'matchTemplate()' of OpenCV.
We take the left image as template to match in the right image, and we only search in the epiline in the second image, due to the epipolar restriction. 
But, in this case our epiline is just the parallel line iterpolation from left image to right image plane.

![Illustration of template matching](https://github.com/LeiHan1/MUVA-Robotica/blob/master/3D/imgs/right.jpg)


Triangulate point 3d
------------------
Once we obtain the matching point, we can use the function 'TriangulatePoints()' to retrieve the 3D coordinate of a pair of matching points.
