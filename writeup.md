# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied gaussian blur on images to make them prepared for Canny function. I choose 5 as Kernel size for my Gaussian blur function. Then I send image to Canny function with thresholds 50 and 150 to get points with high difference with other points around them. Then I calculated region of interest and send it to Hough lines function to get lines, my 1 as rho, pi/180 as theta , 35 as threshold for grid, 5 as min line length and 10 as max line gap. If I decrease the threshold, than the resulting line is appearing and disappearing. 35 works fine except extra challange.  

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by I first calculate and get the sums of all slopes of lines generated by Hough lines function. I classify the lines according to their slope, I got negatives to left and positives to right. And also I defined I height to the single line which is rational to height of the video. In here I faced a lot of dividing by zero error in here. I tried to eliminate some of the lines which has more slope than expected to get rid of unexpected lines appering in video.

Then from y-y1=m(x-x1) equation I calculated upper and bottom points of lines and drawed the line.


### 2. Identify potential shortcomings with your current pipeline


It failed in optional challange. I think it is because of defining region of interest and setting the max line gap parameter of Hough lines function, I examined the video after canny function and observed that points that are expected to form line are too sparse.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to developing a better method to define region of interes since it will be changed according to road and camera position on the car.
