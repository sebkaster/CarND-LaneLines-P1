# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goal of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1) Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of ten steps:

1. Convert RGB to HSL
2. Extract Yellow and White Colors
3. Grayscale Transform
4. Gaussian Smoothing
5. Canny Edge Detection
6. Region of Interest
7. Line Detection by Hough Transformation
8. Construct Boundary Lines
9. Smoothing of Lines
10. Annotate Image by Boundaries

In the following these steps are explained and demonstrated by this example image: 

![Example Image](test_images/solidWhiteCurve.jpg)
**Figure 1** - Input Image

#### 1. Convert RGB to HSL

I converted the image to HSL because working with HSL values is much easier to isolate colors.
In the HSL representation of color, hue determines the color you want, saturation determines how intense the color is and lightness determines the lightness of the image.
The input RGB image converted to the HSL colorspace looks like this:

![Example Image](test_images_hsl/solidWhiteCurve.jpg)

#### 2. Extract Yellow and White Colors

Lane lines can be yellow or white. Therefore, I extracted these two colors from the image.
For the white color, I chose high light value (205 - 255). I did not filter hue, saturation values.
For the yellow color, I chose hue between 10 and 40 to choose yellow color. I chose relatively high saturation and did not filter light value for he yellow color selection.
The result of the color selection is shown below.

![Example Image](test_images_extracted_colors/solidWhiteCurve.jpg)

#### 3. Grayscale Transform

The resulting image is converted into gray scaled image in order to detect shapes. In a greyscale image the value of each pixel is a single sample representing only an amount of light,

![Example Image](test_images_grayscale/solidWhiteCurve.jpg)

#### 4. Gaussian Smoothing

Before detecting the edges, a Gaussian filter is executed on the image. I applied the Gaussian filter to smooth out the noise and also smooth the edges.
Thus, I used Gaussian Smoothing with a kernel size of 7. The blurred image is shown below.

![Example Image](test_images_gaussian/solidWhiteCurve.jpg)

#### 5. Canny Edge Detection

The Canny algorithm is used for the edge detection. This function takes as input a lower and an upper threshold. 
If a pixel gradient is higher than the upper threshold, the pixel is accepted as an edge
If a pixel gradient value is below the lower threshold, then it is rejected. 
If the pixel gradient is between the two thresholds, then it will be accepted only if it is connected to a pixel that is above the upper threshold.
Instead of selecting a fixed lower and upper bound I determine the thresholds dynamically for every image. 


In practice, ```sigma=0.33``` tends to give good results on most images.

![Example Image](test_images_edges/solidWhiteCurve.jpg)

#### 6. Region of Interest

![Example Image](test_images_roi_mask/solidWhiteCurve.jpg)

![Example Image](test_images_roi_mask_applied/solidWhiteCurve.jpg)

#### 7. Line Detection by Hough Transformation

![Example Image](test_images_hough_lines/solidWhiteCurve.jpg)

#### 8. Construct Boundary Lines

![Example Image](test_images_lane_boundaries/solidWhiteCurve.jpg)

#### 9. Smoothing of Lines


#### 10. Annotate Image by Boundaries

![Example Image](test_images_output/solidWhiteCurve.jpg)

First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, 




### 2) Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3) Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
