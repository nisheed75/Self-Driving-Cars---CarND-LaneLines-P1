# **Finding Lane Lines on the Road** 


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

My pipeline consisted of 8 steps. 

1. I get the shape if the image so I can get the width and length.

2. I then create an array of vertices so that I point to use in determining my region of interest.

3. I convert the image to grey scale.

4. Using the Gaussian function to smooth and blur.

5. The canny function helps me find the edges and parameters I set it can find the edges of lines I'm interested in.

6. Once I have a canny image I use the vertices to find my region of interest.

7. I use the Hough transform to draw lines. In this section I've modified the draw_lines function to do the following:
    7.1 I find the slope of the line and use this to determine if it is a right or left line.
    7.2 Using the slope I add all the x and y points into an array.
    7.3 Once I have these arrays I use poly fit to get a polynomial function that gives me a regression line.
    7.4 Since I have a fixed camera position I use the top and bottom of the image to get the top and bottom of the y values and then use the polynomial function to get the lower and upper x values for the right and left x lines.
    7.5 I then use the numpy linespace to get all the x values for the right and left line
    7.6 I use the polynomial function to find the corresponding y values for the right and left lines.
    7.7 I generate a new set of points with the new x and y values. 
    7.8 This is the points I use to draw the line then. 
    7.9 This is my attempt to extend the line when we have dashed lines.

8. Once I have this lines draw on a new image, I use the weight function to generate a new image with the lines marked on the original image.

Here are the resultant images produced.

![alt text][image1]: test_images_output/with_lines-solidWhiteCurve.jpg
![alt text][image1]: test_images_output/with_lines-solidWhiteRight.jpg
![alt text][image1]: test_images_output/with_lines-solidYellowCurve.jpg
![alt text][image1]: test_images_output/with_lines-solidYellowCurve2.jpg
![alt text][image1]: test_images_output/with_lines-solidYellowLeft.jpg
![alt text][image1]: test_images_output/with_lines-whiteCarLaneSwitch.jpg

### 2. Identify potential shortcomings with your current pipeline

Since i using hardcoded values for some of my poisitons my algoritm won't work well if the image size changes. 

### 3. Suggest possible improvements to your pipeline

I should look at changing my code to use the imshape properties and the max on the line y vlues i found to set the top property  and use the imshape to find the bottom of the image.


