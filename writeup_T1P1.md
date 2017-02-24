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
[image7]: ./examples/grayscale.jpg "gray"

---

### Reflection

###1. Description of the pipeline.

My pipeline consisted of 5 steps and they are encapsulated into the **laneFinding(image, colorFilter=0)** function

1.1 Determine if the image need addtional color filtering/extraction with the , this is especially useful for the **Optional Challenge**

1.1 Convert the images to grayscale, as shown in the example:

![image7]

1.2 In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![image0]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
