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

Instead of modifying the original *draw\_lines* function, I put my pipeline - *mark\_lane\_on_image* in the cell right under "Build a Lane Finding Pipeline."

My pipeline consisted of 8 steps:
1. convert to grayscale
2. apply Gaussian blur 
3. apply Canny edge detection
4. apply mask
5. run Hough lines to get the short lines
6. extrapolate multiple short lines to generate two long lines that mark the lane using linear regression (implemented in *extrapolate\_lines* helper function)
7. draw the extrapolated lines in red and overlay on top of the original image
8. generate plots


### 2. Identify potential shortcomings with your current pipeline

1. First potential shortcoming is that the mask as well as some other parameters are hard coded in pixel numbers, which will not work if the resolution of input image changes.
2. Another shortcoming is that the lane detection algorithm assumes straight lane marks therefore will not work when the cars enters a curved road.


### 3. Suggest possible improvements to your pipeline

1. Change to ratio based masking (also other parameters) in order to work for images with different resolution than those used in the course.
2. Try using color masking before grayscaling to better separate the lane markers (in white and yellow) from the background, which might also reduce the overall computing load in successive steps.
3. Assume that lane markers can be curves and use higher dimensional regression when extrapolating the lane markers from short line segments.

