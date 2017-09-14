# **Finding Lane Lines on the Road** 

[//]: # (Image References)

[image1]: ./assets/result.png

[image2]: ./assets/challenge_with_noise.PNG

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

This project is from Udacity Self-Driving Car Nanodegree. The goal of this project is to build a pipeline that finds the lane lines on the road.

The expectations of this project.


<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />


My pipeline consisted of 5 steps:

  * Converte the images to *grayscale*.
  * Apply *Gaussian Blur*.
  * Performe *Canny Edge Detection*.
  * Apply a *mask of interest*.
  * Performe *Hough transformation* and draw the **hough lines**.


In order to draw a single line on the left and right lanes, I first included a new helper function **get_coordinates()** and modified the **draw_lines()**:

  1. **get_coordinates()**
  
  First, I was using np.polyfit() to get a line equation to calculate the four vertices I needed. It works well with the first two tasks. But the result for the challenge will be very funny. So I did some research online and used this new method. So the idea is to *first* set the Y coordinates. Then use Y coordinates to calculate X coordinates based on current frame and previous frame. 
  
  This function will return the calculated coordinates (X, Y) and update the previous frame.
  
  2. **draw_lines()**
  
  I first separate the *lines* into left_lines and right_lines. And then call get_coordinates() to calculate the coordinates. Then I draw two lines and one filled polygon using the four coordinates.

    

Test on image:


![alt text][image1]


The final result I got *(click image below to play):*

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/wQDmzXM9tRg/0.jpg)](https://www.youtube.com/watch?v=wQDmzXM9tRg)


## Reflection

This pipeline's performance will drop if the input image/video got significant noise such as road color. I believe more advanced computer vision techniques can help get rid of the noise and get better results. I will dive into that soon.
