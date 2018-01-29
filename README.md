# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.


Describe the pipeline
---
1. Convert rgb image to grayscale image.
2. Apply a Gaussian Noise kernel.
3. Apply the Canny transform.
4. Select the region of interest.
5. Use Hough transformation to find lines in the image.
6. Draw a single, solid line over the left lane line and a single, solid line over the right lane line instead of Hough line segments.
  6.1. Caculate the slope of each line.
  6.2. It's a left line if slope > 0. Otherwise, it's a right line. Besides, in order to make the pipeline work better in the challenge.mp4, I only keep the lines when left lines slopes are between 0.5 and 0.7 and right lines slopes are between -0.8 and -0.6.
  6.3. Average the position of each of the lines and extrapolate to the top and bottom of the lane.
  6.4. Draw lines.
7. Show images.

Identify any shortcomings
---
1. The region of interest is fixed so that it can not fit other scenes.
2. It can not work well when the white segments are too short.
3. It can only draw straight lines.

Suggest possible improvements
---
1. Choose the region of interest automatically.
2. Use curve fitting instead of straight line.
