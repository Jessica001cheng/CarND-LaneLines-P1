# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/line_on_Test_Images.png "Pipeline with test images"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale. Then I use Gaussian blur function to smooth my grayscale image. 3rd step is to use Canny to detect edges. 4th step is masking an area for line detection. And the last step is finding line in interested area with Hough lines. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:

1. find all x,y in left /right line and also calculate all slopes for each line.
2. calculate mean value of left/right slope.
3. use top bottom y value and left/right slope to calculate top bottom x value for left/right line.
4. draw left/right lines.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there is curved lane. As Hough transform is only used to detect straight line, curve line will not be detected correctly. 

Another shortcoming could be line color change or line is covered by shadow. As gray scale is only sensitive to light change, color change or shadow will cause edge detection not work properly.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to change image to HLS color space and handle S channel.

Another potential improvement could be to use curve detection not only straight line detection.
