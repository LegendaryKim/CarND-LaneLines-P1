# **Finding Lane Lines on the Road** 

___

In this project, I utilized the tools what I learned in the Lesson 1 to detect lane lines on the road. 

___


### 1. Reflection

My pipipleline is as following:

**1. Utuilize a Gaussian kernel to filter the image:**
    It helps filtering noisy parts of image which helps to improve in edge dectection.

**2. Employ Canny edge detection:**
    This step finds the edges in the image based on the intensity gradient, doubple threshold, and hsteresis. (min_threshold =100, max_threshold = 200)
    
**3. Perfom Hough transformation tofind lines from the edges:**
    Each point of edges are transfromed to sinosoidal lines and find their intersections to show the presence of lines in image domain. (rho = 2, theta = np.pi/180, threshold = 30, min_line_len = 20, max_line_gap = 20)
    
**4. Connecting points for each lane lines:**

    4.1 Get the slopes of each line and filter them with the minimum value of slope (0.5).
    4.2 Based on the sign of slopes, divide the lines to 2 groups; left and right lane lines.
    4.3 Polynomial fitting for end-points of the lines in the each group, and get the 1st-order polynomial coefficients, and we got each polynomial fitting equation for left and right lanes. [numpy.polyfit & numpy.polyval]
    
### 2. Identify potential shortcomings with your current pipeline

A lot of limitations are identified in "Optional Challenge". In the vidoe, there are problem-causing factors; lots of shadows, chaging color of surface from asphalt to concrete, and curved lanes. Because ot these problems, the output of "optional challenge" was not made.

I try to find optimal parameters in Canny edge detection and Hough transformation, but it failed. Sometimes, there are too many lines filtered out, or opposite.

Also, the original lanes are curved but, my order of polynomial fitting is just 1. (I tried to change the order to 2, it altered the lanes to semicircles.

Finally, my method to connecting points are not perfect. The result in videos show that the detected lanes are somewhat shaking. 

### 3. Suggest possible improvements to your pipeline

* Find improved ways in connecting points
* Find the perfect parameters for Canny edge detection and Hough transformation, or utilize better algorithms
* A non-liner fitting will improve the result.
* If I use the smoothing windows method for frames in vidoes, it will have smoother detected lanes.

