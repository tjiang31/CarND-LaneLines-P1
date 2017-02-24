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

My pipeline consisted of 5 steps and they are encapsulated into the _**laneFinding(image, colorFilter=0)**_ function

1.1 Determine if the image need addtional color filtering/extraction with the _**colorExt(image)**_ function, this is especially useful for the **Optional Challenge**. Then, the image is being converted to grayscale.

  Shown below (From top to bottom: Raw image; unfilted grayscale; Filtered RGB; Filtered grayscale)

![image7] ![image8] ![image9] ![image10]


1.2 The region of interest is also tuned with the test image, but to make these parameters more adaptive to different resolution, it is being converted to ratio factors time by the image.shape (the x-y range of the image). 

  Same logic is also used in the draw_lines() when the annotation lanes need to be computed from the fitted slope, the two ends points (y component) are also determined by only considering the bottom 1/3 of the frame.
  
  The **Region of Intrest** is like this:
  
![image0]

1.3 In order to draw a single line on the left and right lanes, I modified the draw_lines() function by using a grouping method based on the slope (positive/negative) of the detected edges. Addtional constraint of 20^o - 45^o is also used to filter out segment of noise. The final annotated test-images, plus one frame from the challenge video are shown below.

![image1] ![image2] ![image3] ![image4] ![image5] ![image6]

![image11]

###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
