# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./assets/result.png

[image2]: ./assets/challenge_with_noise.PNG


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.


My pipeline consisted of 5 steps:

  * Converte the images to *grayscale*.
  * Apply *Gaussian Blur*.
  * Performe *Canny Edge Detection*.
  * Apply a *mask of interest*.
  * Performe *Hough transformation* and draw the **hough lines**.


    
In order to draw a single line on the left and right lanes, I first included a new helper function **get_coordinates()** and modified the **draw_lines()**:

  1. **get_coordinates()**
  
  First, I was using np.polyfit() to get a line equation to calculate the four vertices I needed. It works well with the first two tasks. But the result for the challenge will be very funny. So I did some research online and used this new method. So the idea is to *first* set the Y coordinates. Then use Y coordinates to calculate X coordinates based on current frame and previous frame. 
  
  This function will return the calculated coordinates (X, Y) and update the previous frame
  
  2. **draw_lines()**
  
  I first separate the *lines* into left_lines and right_lines. And then call get_coordinates() to calculate the coordinates. Then I draw two lines and one filled polygon using the four coordinates.

    

Test on image:


![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the image got significant noise (e.g. the challenge). I tried to solve the challenge using my new method of calculating the coordinates. But the result is still not good. Maybe the method of calculating the current coordinates still needs improved.

![alt text][image2]


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use more advanced computer vision techniques to get rid of noise as I guessed. Some studies mention about techniques of convertting the original image to HSL first before grayscale. I am quite new to computer vision and hopefully I will be equipped with more advanced computer vision techiques soon to get a perfect result for this challenge.

