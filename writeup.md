# **Finding Lane Lines on the Road** 

___

In this project, I utilized the tools what I learned in the Lesson 1 to detect lane lines on the road. 

updated: 07/30/2017
___


### 1. Reflection

My pipipleline is as following:

**1. Utuilize a Gaussian kernel to filter the image:**
    It helps filtering noisy parts of image which helps to improve in edge dectection.

**2. Employ Canny edge detection:**
This step finds the edges in the image based on the intensity gradient, doubple threshold, and hsteresis.
    (solidWhite & solidYellow: min_threshold = 100, max_threshold = 200)
    (OptionalChallenge: min_threshold = 180, max_threshold = 220)

**3. Mask with polygon: **
The edges images is maksed with poygon, defined with vertices.
    (solidWhite & solidYellow: [[(0,imshape[0]), (int(imshape[1]*0.45), int(imshape[0]*0.6)), (int(imshape[1]*0.55), int(imshape[0]*0.6)), (imshape[1],imshape[0])]] )
    (OptionalChallenge: [[(int(imshape[1]*0.22),int(imshape[0]*0.92)), (int(imshape[1]*0.40), int(imshape[0]*0.65)), (int(imshape[1]*0.60), int(imshape[0]*0.65)), int(imshape[1]*0.90),int(imshape[0]*0.92))]] )
    
**4. Perfom Hough transformation tofind lines from the edges:**
Each point of edges are transfromed to sinosoidal lines and find their intersections to show the presence of lines in image domain. 
    (solidWhite & solidYellow: rho = 1, theta = np.pi/180, threshold = 10, min_line_len = 20, max_line_gap = 20)
    (OptionalChallenge: rho = 1, theta = np.pi/180, threshold = 20, min_line_len = 50, max_line_gap = 200)
    
**5. Connecting points for each lane lines:**
    5.1 Get the slopes of each line and filter them with minimum and maximum values of slope (0.4, 2).
    5.2 Based on the sign of slopes, divide the lines to 2 groups with the sign of slope; left and right lane lines.
    5.3 Average the slopes and mid-points of lines at each groups.
    5.5 Calculate moving-averages of slopes and mid-points with specific number of frames (solidWhite & solidYellow: 10)
(OptionalChallenge: 5)
    5.6 Find the intersecting points with lanes with the moving-averages at the edges of mask and extrapolate the lines.
    
### 2. Identify potential shortcomings with your current pipeline

Edge detection technique is not enough. I hope to learn special filtering skills for each color of lanes (ex. white or yellow). It would be improved in accuracy to find edges of lanes and draw lines with Hough transformation. 

### 3. Suggest possible improvements to your pipeline

* Filtering images with specific colors

