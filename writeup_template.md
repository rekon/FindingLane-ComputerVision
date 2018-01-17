# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on my work in a written report


[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve.jpg "solidWhiteCurve"
[image2]: ./test_images/solidYellowCurve.jpg "solidYellowCurve"
[image3]: ./test_images_output/solidWhiteCurve.jpg "solidWhiteCurve"
[image4]: ./test_images_output/solidYellowCurve.jpg "solidYellowCurve"

---

### Reflection

### 1. As part of the description, explain how I modified the draw_lines() function.

My pipeline consisted of following steps.
1. First I made a copy of the image passed to the function.
2. Then I convert the image to grayscale.
3. Next I applied gaussian blur to the image to remove unwanted distortions.
4. Then Canny edge transformation was applied to the image.
5. Then the resutlting image is masked to the region-of-interest (preferably a quadrilateral)
7. Next Hough Transform. Draw lines function is called inside this function.
8. Finally the original image is merged with the image containing lane markings.

The images are transformed as follows

Initial
![alt text][image1]
Final
![alt text][image3]

Initial
![alt text][image2]
Final
![alt text][image4]

### 2. Potential shortcomings with my current pipeline

1. My pipeline is unable to detect lines correctly when there are curvatures in road
2. Pipeline may fail if there are pot-holes in the road
3. Pipeline may also fail if there are shadows on the road.
4. In case of vehicles coming in view area, pipeline may show distortions.

### 3. Suggest possible improvements to your pipeline

Possible improvements can be:

1. I have used some hardcoded values for 'Canny-edge-detection' and 'Hough-transform'. Whereas these values should be adapt according to environment conditions like Clear-Sky or Cloudy-Sky
2. I have calculated the slope using top-most and bottom-most point in a lane and extrapolated the rest, upto top and bottom. This calculation for left/right lane can be averaged over the slopes-of-lines which are obtained from left/right lane.