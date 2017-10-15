# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

The pipeline has 3 major steps. First step is to detect the edges in the image using canny edge detection.
The image is converted to grayscale and smoothed using Gaussian filter before applying canny edge detection.
Second step is to create a four-sided polygon to mask out the edges in the area of interest from the detected 
canny edges. Third step is to get lines from edges using hough transform and draw the lines.

Since output of cv2.HoughLinesP are the points corresponding to staright lines, I modified the draw lines 
function to get points corresponding to positive slope line between 30 and 60 degrees, and negative slope line
between -30 and -60 degrees. Using these values I used np.polyfit to fit straight lines to these points one 
for negative slope and one for positive slope. 


### 2. Identify potential shortcomings with your current pipeline

One of the shortcomings is the classification of hough lines based on slope to draw a single lane. This will not 
generalize well for all cases. Since there can be a lot of small lines or horizontal lines this may effect the 
final output line. To avoid this I used only specific range of slopes and a larger minimum line length value in 
hough_lines function but this may eliminate all lines in some cases. Also it doesn't consider background color, 
shadows or other objects on the road.


### 3. Suggest possible improvements to your pipeline

One possible improvement is to instead of using hough transform use a different kind of transform that can directly 
detect lane lines instead of detecting several straight lines and extrapolating them to match lane lines.
