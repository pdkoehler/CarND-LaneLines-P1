# **Finding Lane Lines on the Road**

***

## **1. Introduction**

Imperative for a self-driving car is its able to wield its senses. The sensors with which the vehicle is equipped attempt to provide similar as well as augmented information intake as a human. Visual feedback is the paramount aspect of driving which includes monitoring where one is on the road, reacting to events happening or to reading traffic signs. Initially, we will focus on finding the lane lines on a highway.

This report will convey methods used in achieving the task of *finding lane lines on the road*. It consists of two parts:

1. **Approach**: Here the steps or *pipeline* to arrive at having the drawn lines appearing to fluidly follow the actual lane lines on the road.
1. **Drawbacks**: Robustness follows careful consideration of as many scenarios which may occur.  The developed pipeline proves to work for the given assumptions, but it could fail when these assumptions are not met.
1. **Improvements**: Even though the task has been achieved, we cannot assume that the single correct answer has been applied; time for research followed by implementation is restricted. Therefore, where improvements could arise are conveyed.

***

## **2. Approach**

The approach taken within this project reflects much of what was discussed throughout the video lectures.  As I was developing, I soon decided that the achieve what I had in mind, I would need to collect everything within an object, rather than global functions and variables. Thus, I defined the class

<p align="center">
  <b>LaneLineFinder</b>
</p>

This allowed me the ability to initialize and change the parameters at my will as well as perform actions and save states during the entire pipeline. The class contains the function **find_lanes**, which takes an image as its argument and goes through the sequence of events to arrive at the final image.

This sequence is comprised of
1. Converting the image to grayscale. ![alt text][gray_image] In this format all the analysis was performed, allowing the pipeline to be void of the inhibitions of color-based analysis.
1. Of course the entire image is not relevant, thus the *region of interest* was defined to have the focus on where the lane lines would be appearing and is seen here:
![alt text][region_of_interest_image]
After removing everything outside the polygon the result was
![alt text][masked_image]
1. The edges within the *region of interest* then were obtained providing the following result
![alt text][masked_edges_image]
1. Now the Hough lines were needed.  The extracted Hough lines drawn upon the original image can be seen below
![alt text][raw_lines_image]
1. The final step was to drawn the estimated 

**Finding Lane Lines on the Road**





---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I ....

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image:




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ...

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

[//]: # (Image References)

[gray_image]: ./test_images_output/solidYellowCurve2_gray_image.jpg
[region_of_interest_image]: ./test_images_output/solidYellowCurve2_region.jpg
[masked_image]: ./test_images_output/solidYellowCurve2_masked_image.jpg
[masked_edges_image]: ./test_images_output/solidYellowCurve2_masked_image_edges.jpg
[raw_lines_image]: ./test_images_output/solidYellowCurve2_raw_lines.jpg
