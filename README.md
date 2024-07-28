# ImageStitching_Using_HarrisCornerDetection
**Implementing Harris Corner Detection from Scratch for Image Stitching**

**Author**
Tammy L. Ralte 

**Project Overview**
This project focuses on image stitching using a custom implementation of Harris Corner Detection to identify keypoints and feature matching techniques to generate homography matrices. Unlike many implementations, this project implements Harris Corner Detection from scratch, without using inbuilt functions. The ultimate goal is to blend multiple images into a seamless panorama.

**Table of Contents**
Dependencies
Setup
Code Description
Custom Harris Corner Detection
Image Stitching using Harris Corner Detection
Running the Code
Conclusion


**Dependencies**
Python 3.x
OpenCV
NumPy
Matplotlib
Scipy
Scikit-Image


**Setup**
1.Install required packages:
pip install opencv-python-headless numpy matplotlib scipy scikit-image

2.Clone the repository
git clone <repository_url>
cd <repository_directory>


**Code Description**
Custom Harris Corner Detection
The Harris corner detection algorithm involves smoothing the image, computing gradients, calculating the structure tensor, determining the corner response, and finally identifying corner points through thresholding. This enables the detection of key feature points in images, which is crucial for image stitching.


**Key Steps:**
Gaussian Smoothing: Applied to the image to reduce noise and ensure robustness in subsequent gradient computations.
Gradient Computation: The Sobel operator is used to compute the image gradients in both the x and y directions, helping to capture variations in intensity and identify edges.

Structure Tensor Calculation: The elements of the structure tensor are computed by convolving the squared gradients and gradient products with a Gaussian kernel, providing information about local image structure.

Corner Response Function: Computed using the structure tensor, evaluating the likelihood of a pixel being part of a corner based on the determinant and trace of the structure tensor.

Thresholding: Applied to the corner response function to identify pixels with high corner responses, distinguishing corners from non-corner regions.

Corner Localization: The precise locations of detected corners are determined based on the thresholded corner response image.


**Image Stitching using Harris Corner Detection**
The image stitching process involves several steps:
Feature Detection and Description: Harris corners are detected in the input images, and keypoints are described using ORB descriptors. This computes descriptors for the keypoints identified in the previous step.

Feature Matching: The computed descriptors are used to match keypoints. Keypoints from the source and destination images are matched using a feature matcher based on the Brute Force algorithm.

Homography Estimation: A homography matrix is estimated using RANSAC to align the source image with the destination image.

Warping and Blending: The source image is warped and blended with the destination image to create a seamless panorama.

Cropping: The resulting panorama is cropped to remove black regions and obtain the final stitched image.

**Running the Code**
Read Images:
Load the images you want to stitch together.

Display Images:
Display the images side by side to visualize the input.

Generate Panorama:
Use the ImageStitcher class to warp, blend, and crop the images to create a panorama.

Plot Keypoints and Matches:
Visualize the detected keypoints and matched features between the images.

Display Results:
Display the stitched panorama and compare it with the ground truth image.

Calculate Image Similarity:
Evaluate the accuracy of the stitched image using similarity metrics like MSE and SSI.

**Conclusion**
This project demonstrates the process of image stitching using a custom implementation of Harris Corner Detection from scratch and feature matching to create a panorama. The accuracy of the stitched image can be evaluated using similarity metrics like MSE and SSI.
