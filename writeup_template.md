# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

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

The pipeline has 3 major steps. First step is to detect the edges in the image using canny edge detection.
The image is converted to grayscale and smoothed using Gaussian filter before applying canny edge detection.
Second step is to create a four-sided polygon edges to mask out the edges in the area of interest from 
the detected canny edges. Third step is to get lines from edges using hough transform and draw the lines.

Since output of cv2.HoughLinesP are the points corresponding to staright lines, I modified the draw lines 
function to get points corresponding to positive slope between 30 and 60, and negative slope between -30 and -60.
Using these values I used np.polyfit to fit straight lines to these points one for negative slope and one for
positive slope. 
![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
