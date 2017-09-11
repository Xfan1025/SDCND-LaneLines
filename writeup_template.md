# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

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

      



If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use more advanced computer vision techniques. 
Such as convert the original image to HSL first before grayscale.

Another potential improvement could be to ...
