[//]: # (Image References)
[image_0]: img/img0.png
[image_1]: img/img1.png
[image_2]: img/img2.png

# SFND_3D_Object_Tracking

![alt text][image_0]

## Introduction

The idea of the project is to build the 3D object tracking system by using the camera image information and Lidar point clouds for computing the time to collision of each tracked objects. Evaluated detectors and descriptors pairs from mid term project are used for keypoint matching and YOLO object detection framework is used to detect the vehicles. The final project consists of five parts:

  1) The first part is focus on the matching of 3D Object bounding boxes using the matched key points.

  2) Second part compute the lidar based time to collision.

  3) In the third part, prepare the TTC computation based on camera measurements by
associating keypoint correspondences to the bounding boxes which encloses them.

  4) The fourth part compute the camera based time to collision.

  5) The final part mainly focuses on the performance evaluations.

## Project Rubric

#### Match 3D Objects
This task is to implement the method "matchBoundingBoxes", which takes as input both the previous and the current data frames and provides as output the ids of the matched regions of interest (i.e. the boxID property). Matches must be the ones with the highest number of keypoint correspondences. std::multimap is used to store the matched IDs of previous and current BBs.

#### Compute Lidar-based TTC
Compute the time-to-collision in second for all matched 3D objects using only Lidar measurements from the matched bounding boxes between current and previous frame. Median distance ratio is used to remove the outlier lidar points.

#### Associate Keypoint Correspondences with Bounding Boxes
Prepare the TTC computation based on camera measurements by associating keypoint correspondences to the bounding boxes which enclose them. All matches which satisfy the condition is added to a kptMatches in the respective bounding box. Median distance ratios are used in next TTC calculation to remove outliers.

#### Compute Camera-based TTC
Compute the time-to-collision in second for all matched 3D objects using only keypoint correspondences from the matched bounding boxes between current and previous frame. Median distance ratio is used to remove outliers influence.

#### Performance Evaluations
#### Performance Evaluation 1
Time to collision computations from Lidar points are better than the camera based TTC results and they are quite accurate. Some of the frames where outliers present can be neglected and solved by finding the median point instead of the closest point. Below are some frames with outliers.

![alt text][image_1]

#### Performance Evaluation 2
Best 3 detector/ descriptor combinations from mid term project shall be used to evaluate the accuracy of time to collision from both camera and lidar sensors. Below are the some TTC results. As we can see, since the detector/descriptor combinations are chosen based on the speed, TTC results from camera are not accurate enough compared to lidar results.

![alt text][image_2]

## Dependencies for Running Locally
* cmake >= 2.8
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* OpenCV >= 4.1
  * This must be compiled from source using the `-D OPENCV_ENABLE_NONFREE=ON` cmake flag for testing the SIFT and SURF detectors.
  * The OpenCV 4.1.0 source code can be found [here](https://github.com/opencv/opencv/tree/4.1.0)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory in the top level project directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./3D_object_tracking`.
