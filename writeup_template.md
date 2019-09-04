# **Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report



### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consist of the following 5 steps. First, I converted the images to grayscale, then I .... 
(1) Convert the input image to the grayscale image
(2) Apply the gaussian blur to reduce the spurious noise (with kernel size as 50
(3) Apply the canny function to detect the edges
(4) Mask out edges outside the lane region to reduce the complexity
(5) Apply hough transformation in order to obtain the lines along the lane (left/right line of the lane)
(6) Calculate the full extent length of the lane 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function:
(1) For each line segment, determine the slope of the line.
(2) The slope will provide info on which side of the lane.
    The negative slope is for the left lane, while positive is for the right lane.
(3) Once which side is determined, combine the line with the accumlated lane (either left or right).
    For left lane, take the left_most x and down_most y for x1/y1, and take the right_most x and up_most y for x2/y2.
    For right lane, take the left_most x and up_most y for x1/y1, and take the right_most x and down_most y for x2/y2.
(4) Extrapolate the line from the bottom of the image to the upper part of the lane position by using 
    the line equation; y = mx + b.



### 2. Identify potential shortcomings with your current pipeline


The shortcoming of my current pipeline is as follows.
(1) The algorithm for combining each side of the lines from hough transformation is not robust. 
(2) When the image size changes, the draw_line algorithm results in incorrect drawing.     



### 3. Suggest possible improvements to your pipeline

The improvement should be made based on the shortcoming identified as above.
It should handle different size of images which requires the lane region algorithm to be modified. 

After hough transformation, the lines should be more classified and combined into the line information with more sense and better approximation. 


