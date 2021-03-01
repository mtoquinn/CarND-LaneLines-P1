# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

I used the basic pipeline from the lessons as a starting point. First, I grayscaled the image and then applied a gaussian blurring filter before running canny. Then I applied a mask before running it through a hough transform. Then the weighted_image function was applied and the result was output. 

To get a single line on on the left and right I found the average slope for each side by splitting the pts at the center of the mask. I then found the midpoint for each side and used that and the slope to find the point at the very bottom of the image and the top of the mask (denoted left_bot_x and left_top_x). I then added line from the bottom point to the midpoint and the midpoint to the top point for each side. 

In general it works well as a rudimentary system. Image was included to show how the system works 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


A major potential shortcoming is how well this system would work on a sharp corner, I am not certain that it would keep the lines nearly as well as it does with the slight corners. 

There is some jutter with the line tracking, especially as the lines extend farther away from the midpoint. 


### 3. Suggest possible improvements to your pipeline

Fixing the jutter would be the first major improvement, I tried using multiple points along the line and did not get any better results. I am unsure at this time how to improve its performance. 
