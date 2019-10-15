# Dense-Optical-Flow
Thanks to Adrian Rosebrock for the [tutorial](https://www.pyimagesearch.com/2015/09/14/ball-tracking-with-opencv/)
The goal is to calculate dense optical flow for a video with moving cars using Gunnar Farneback algorithm.

Initial video was taken from [here](https://www.pexels.com/video/cars-on-the-road-854745/)  
  
![alt text](https://media.giphy.com/media/LrX95dL1DsDPxYKi6V/giphy.gif)

## Prepare the video and read first frame
For working with video and images OpenCV will be used.  
First of all, we will create a VideoCapture object and read first frame.  
Input video can be of different sizes, so we have to resize it.  
Also, it is useful to create a mask (will be used later in HSV format) and set it's saturation to maximum value.  

## Calculate dense optical flow for subsequent frames
While video is playing, we will read frames each 10 ms.  
Each read frame should be converted to gray scale format and resized.  
The actual calculation will be performed by **cv2.calcOpticalFlowFarneback()**  
You can find more info about this function in opencv [documentation](https://docs.opencv.org/2.4/modules/video/doc/motion_analysis_and_object_tracking.html#calcopticalflowfarneback)
If you want to read more about algorithm we will use, please, refer to [Two-Frame Motion Estimation Based on
Polynomial Expansion](http://www.diva-portal.org/smash/get/diva2:273847/FULLTEXT01.pdf) paper  
We also need to calculate magnitude and angle of 2D vectors, using **cv2.cartToPolar()**.    
Then we apply these values to the mask, so we could have different colors for different colors for different movement direction.  
Finally, we will combine mask and initial frame to get dense optical flow image.  
![alt text](https://media.giphy.com/media/kyiUNnxHG2TKMOjZd1/giphy.gif)
