# **Finding Lane Lines on the Road**

## Introduction

Imperative for a self-driving car is its able to wield its senses. The sensors with which the vehicle is equipped attempt to provide similar as well as augmented information intake as a human. Visual feedback is the paramount aspect of driving which includes monitoring where one is on the road, reacting to events happening or to reading traffic signs. Initially, we will focus on finding the lane lines on a highway.

This report will convey methods used in achieving the task of *finding lane lines on the road*. It consists of two parts:

1. **Approach**: Here the steps or *pipeline* to arrive at having the drawn lines appearing to fluidly follow the actual lane lines on the road.
1. **Drawbacks**: Robustness follows careful consideration of as many scenarios which may occur.  The developed pipeline proves to work for the given assumptions, but it could fail when these assumptions are not met.
1. **Improvements**: Even though the task has been achieved, we cannot assume that the single correct answer has been applied; time for research followed by implementation is restricted. Therefore, where improvements could arise are conveyed.

## Approach


---

**Finding Lane Lines on the Road**



[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I ....

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image:

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ...

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
