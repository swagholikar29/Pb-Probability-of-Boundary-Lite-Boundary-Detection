# Pb-lite edge detection algorithm.

## About
Boundary detection is an important, well-studied computer vision problem. A simple method to find boundaries is to look for 
intensity discontinuities in the image, also known of edges. Classical edge detection algorithms, including the Canny and Sobel 
baselines, look for these intensity discontinuities. The more recent pb (probability of boundary) boundary detection algorithm 
significantly outperforms these classical methods by considering texture and color discontinuities in addition to intensity 
discontinuities. Qualitatively, much of this performance jump comes from the ability of the pb algorithm to suppress false positives 
that the classical methods produce in textured regions. This project is a simplified version of pb, which finds boundaries by examining 
brightness, color, and texture information across multiple scales (different sizes of objects/image). The output of the algorithm is a 
per-pixel probability of boundary which outperforms the Canny and Sobel Edge Detectors.\
This project implements a simpler version of the algorithm presented in this 
[paper](https://www2.eecs.berkeley.edu/Research/Projects/CS/vision/grouping/papers/amfm_pami2010.pdf)

## Filters
### 1. Oriented Derivative of Gradient filter
The first order derivative is computed by convolving the Gaussian with Sobel in respect to horizontal and vertical axes. The resultant derivative of Gaussian is then oriented by given number of orientations. This oriented Derivatives of Gaussian are appended to form the DoG filterbank. For the code implementation, 2 scales and 16 orientations were used resulting in 2 ×16 filters

### 2. Leung-Malik filter
The implemented Leung-malik filterbank has 48 filters in total. Two versions of Filterbanks are implemented for the scope of the assignment: LM Large and LM Small. The basic flow for generating a LM filter is to start with generating a gaussian filter. Then the computation of Laplacian of Gaussian is done. While calculating the LoG, The Gaussian Filter is convolved with the Laplacian Negative matrix to get the LoG filter matrix. The other Derivative of Gaussian and Second derivative of Gaussian are added to the filterbank in the next step.

### 3. Gabor filter
A 2-D Gabor filter is a Gaussian kernel function modulated by a sinusoidal plane wave. A Gabor filter can be used to automatically extract features using a filter bank.


## Libraries Required:
1. Numpy
2. OpenCV
3. Matplotlib
4. Scikit-Learn

## Running
```sh
cd Phase1
python Wrapper.py
```
