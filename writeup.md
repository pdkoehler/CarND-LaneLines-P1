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
1. The final step was to drawn the estimated lane lines on the original image.  This consists of a few sub steps
  1. Separating the left and right Hough lines based upon their slopes.
  1. Selecting only viable lines, i.e. lines whose slopes remained within a certain range.
  1. From the points that constructed the Hough lines, estimate the lines through a line fitting function.
  1. Run these lines through a smoothing function to reduce jerky motion.
  1. Finally, from the results of the line fitting algorithm while observing the vertices of the region of interest, the estimated left and right lane lines were constructed. This gave the result
  ![alt text][lane_lines_image]

***

## **2. Drawbacks**

There are a few drawbacks which come to mind when contemplating my approach.  These were immediately observed when applying my pipeline to the *challenge*.
* Exception handling was not considered.  Numerical issues would arise especially where the zero division would be perform.
* The region of interest is too hard coded.  Yes, there are parameters that can be tuned to define it yet these do not provide enough freedom.  For example, I assume an *isosceles trapezoid*. Next, again after attempting the challenge, the resolution of the image dramatically affected the region of interest.
* The *smoothing* algorithm may not be applicable for more dramatic movements.
* The parameters for the edge and line detection were set for the first two scenarios, which present quite an ideal environment.  Changes to lighting to texture of the road managed to throw off my pipeline quite quickly.

***

## **3. Improvements**

The crux of my focus would be of course to address the aforementioned drawbacks.  These drawbacks caused my pipeline to fail with the final challenge.


Investing the *region of focus* and its flexibility with regards to handle different resolutions as well as lane line behavior (curves in the road) would be a start.

What would also interest me following what I witnessed in the *challenge*, would be to avoid not detecting the lines whatsoever.  The shadows did not play a crucial role in disturbing the pipeline; the texture and color of the road caused unwanted lines to be detected and the lane lines themselves not be detected. This could have resided on the parameter choice for the detection, yet the choice of these parameters may have been better determined by the image itself.

Due to very late submission of this project, I could not spend any more time to arrive at a level were the pipeline could robustly handle all the scenarios with as little manual intervention.

[//]: # (Image References)

[gray_image]: ./test_images_output/solidYellowCurve2_gray_image.jpg
[region_of_interest_image]: ./test_images_output/solidYellowCurve2_region.jpg
[masked_image]: ./test_images_output/solidYellowCurve2_masked_image.jpg
[masked_edges_image]: ./test_images_output/solidYellowCurve2_masked_image_edges.jpg
[raw_lines_image]: ./test_images_output/solidYellowCurve2_raw_lines.jpg
[lane_lines_image]: ./test_images_output/solidYellowCurve2_lane_line_image.jpg
