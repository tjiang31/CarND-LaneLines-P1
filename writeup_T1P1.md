#**Finding Lane Lines on the Road** 

##By Tianyu Jiang

####Email: pkujiangty@gmail.com

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[image0]: ./test_images/region_of_interest.jpg "ROI"
[image1]: ./test_images/detected_solidWhiteCurve.jpg "SWC"
[image2]: ./test_images/detected_solidWhiteRight.jpg "SWR"
[image3]: ./test_images/detected_solidYellowCurve.jpg "SYC"
[image4]: ./test_images/detected_solidYellowCurve2.jpg "SYC2"
[image5]: ./test_images/detected_solidYellowLeft.jpg "SYL"
[image6]: ./test_images/detected_whiteCarLaneSwitch.jpg "WCLS"
[image7]: ./test_images/frame100.jpg "frame"
[image8]: ./test_images/frame100Gray.jpg "gray"
[image9]: ./test_images/frame100Filtered.jpg "filter"
[image10]: ./test_images/frame100FilteredGray.jpg "filtergray"
[image11]: ./test_images/detected_frame100.jpg "F100"

---

### Reflection

###1. Description of the pipeline.

My pipeline consisted of 6 steps and they are encapsulated into the _**laneFinding(image, colorFilter=0)**_ function.

1.1 Determine if the image need addtional color filtering/extraction with the _**colorExt(image)**_ function, this is especially useful for the **Optional Challenge**. Then, the image is being converted to grayscale.

  Shown below (From top to bottom: Raw image; unfilted grayscale; Filtered RGB; Filtered grayscale)

![image7] ![image8] ![image9] ![image10]


1.2 The region of interest is also tuned with the test image, but to make these parameters more adaptive to different resolution, it is being converted to ratio factors time by the image.shape (the [x, y] range of the image). 

  Same logic is also used in the draw_lines() when the annotation lanes need to be computed from the fitted slope, the two ends points (y component) are also determined by only considering the bottom 1/3 of the frame.
  
  The **Region of Intrest** is like this:
  
![image0]

1.3 Detect the line with _**Canny()**_ function with lower/upper threshold = 1:3 (50:150)

1.4 The parameters for the Hough-Transform are tuned to cover the case in **Optional Challenge** (e.g., smaller minimum length/gap)

1.5 In order to draw a single line on the left and right lanes, I modified the _**draw_lines()**_ function by using a grouping method based on the slope (positive/negative) of the detected edges. Addtional constraint of 20^o - 45^o is also used to filter out segment of noise. 

1.6 Finally, the addWeighted function is used to combine the lines with the raw image/frame.


The final annotated test-images, plus one frame from the challenge video are shown below.

![image1] ![image2] ![image3] ![image4] ![image5] ![image6]

![image11]

###2. Potential shortcomings with current pipeline


One potential shortcoming would be the case when faced a T-intersection or sharp turn, due to the slope constraint we added in determining the left/right lanes, it will make the annotated lines keeping forward.

Another shortcoming could be the capability of dealing with night and narrow street scenarios, becasue in these two cases, the edges and layers are heavily contamenated by the background/near by objects, and since the parameters are mostly pre-determined, that will make the pipeline unable to adapt the complicated cases.


###3. Possible improvements to the pipeline

A possible improvement would be add addition ratio parameters to make the model automatically normalize the image to filter out the background objects.

Another potential improvement could be using a higher order slope to capture the turning of the slope. \

Thanks!
