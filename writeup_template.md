# **Finding Lane Lines on the Road** 

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:

1. Converting the image to grayscale
2. Applying Gaussian smoothing with a Kernel size of 5
3. Applying Canny Edges
4. Creating masked edges parametrizing the vertices to make the mask indipendent from the image size and proportion
5. Creating the lane lines using the hough transform
6. Drawing the lane lines on top of the original image


In order to draw a single line on the left and right lanes, I modified the draw_lines() function as following:

1. Creating two groups of points: right and left groups
2. Allocating the points to the right group by loking at the slope (negative or positive) and filtering only the feasible slopes (e.g. between 0.5 and 0.8 for the left slope)
3. Creating the parameters of the two linear polynomial passing in the groups
4. Drawing two new lines, from the bottom till the 60% of the image, made with the parameters found previously


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming can be if the camera in the car is located in a different position or angle, the image proportions could be different and the mask could filter the original image in a wrong way.

Another shortcoming could be in a situation with faded lanes, the hough transform could not work properly and find no lines.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to preprocess the original image to increase the contrast of the relevant colors (e.g. yellow and white) and decreasing the contrast of the not relevant colors (e.g. green, violet, brown).

Another potential improvement could be to fit a polynomial of an higher degree, that could map and define curves instead of lines and could make the drawing of the lane lines more accurate.