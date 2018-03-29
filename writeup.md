# **Finding Lane Lines on the Road**

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/output_gray_solidWhiteCurve.jpg "Grayscale"
[image2]: ./test_images/output_canny_solidWhiteCurve.jpg "Cannyedges"
[image3]: ./test_images/output_masked_solidWhiteCurve.jpg "Maskededges"
[image4]: ./test_images/output_lines_solidWhiteCurve.jpg "Drawedlines"
[image5]: .test_images/output_solidWhiteCurve.jpg "Finaloutput"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, convert the images to grayscale, then apply Gaussian smoothing and Canny edges, then define a four sided polygon region,  then apply Hough transform function and draw the lines, and finally, add the lines to the original images.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding four arrays to collect the value of right slope, left slope, right center and left center from each lines, which are not vertical, created by the HoughLinesP functions. Based on the sign of the slope, assign the values to left side and right side. Using the equation (y' - y) = m*(x' - x) to calculate the starting point at y' at the bottom and the ending point at y' around the middle of the images. In the end, draw the right and left lines from the starting points and ending points from both sides.

If you'd like to include images to show how the pipeline works, here is how to include an image:

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be that the code would be broken if the vehicle in the middle of the lane while switching lines.

Another shortcoming could be that when other edges with strong gradient show up in the four sided polygon region, the lines would not match the lanes on the road.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to control the shape of the four sided polygon region that it should be the minimum shape to draw the lines that match the lanes on the road.

Another potential improvement could be to calculate the average center and slope of the lines in a more efficient algorithm.
