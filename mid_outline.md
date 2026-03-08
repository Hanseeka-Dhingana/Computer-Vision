What is computer vision
Why we read computer vision
Application of Computer Vision
- Face Detection
- Face analysis and recognition
- vision basd biometrics
- Finger Print scanner
- Special effects: shape and motion capture
- 3D face tracking w/ consumer cameras
- Smart cars
- Safety features in many cars
- Self Driving Cars
- Robotics
- Medical Imaging
- Virtual & Augmented Reality
  
Image synthesis 
Models & Metrics used in Image Synthesis

Why is computer vision difficult? (Challenges)
- View point variation
- scale
- Illimunation
- intra scale variation
- motion
- occulation
- Background clutter
- local ambiguity
  
Image processing 
Low-Level Vision (Image Processing)
This stage focuses on processing raw images and extracting basic information.

Image Formation

Filtering

Edge Detection

Feature Detection

Feature Extraction

Feature Matching

Hybrid Images

Mid-Level Vision (Geometry & Appearance)
This stage focuses on understanding the structure of the scene.

Creating Panoramas

Homography

High-Level Vision (Recognition & Generative Models)
This stage focuses on understanding what the objects are.

Image Classification

CNN

Image Generation

Diffusion Models

Neural Radiance Fields (NeRFs)




1) Low Level Vision
- Edge Detection
- Feature Extraction
- Filtering
- Image Formation
- Hybrid Images
- Feature Detection & matching
1) geometry & appearance
- Creating panoramas
     - what is homography
- Project: Neural Radiance Fields (NeRFs)
1) Recognition & generative models
- Image Classification
- CNN
- Image Generation
- Image diffusion model


Lecture 2:
What is an Image
Image Transformation
Filters 
What is the filtering?
Why why use filtering?
Canonical Image Processing problems
- Image Restoration
  - denoising
  - deblurring
- Image Compression
  - JPEG, HEIF, MPEG, …
- Locating Structural Features
  - corners
  - edges

Noise reduction
- How to reduce noice from image
Image Filtering
- Linear Filtering (kernal or Mask or filter)
  - Cross Correlation
  - Convolution
  - Mean Filtering
  - Box Filter
  - Gaussian Filter (using Gaussian Kernel)
  - Mean VS Gaussian Filter
  - Moving Average
- Applications
  - Sharpening
  - Smoothing with box filter
  
High-Pass Filter 
Sharpen Filter
Thresholding 
Can Thresholding be implemented with linear filter?
Hybrid images 

Lecture 3:
What is the Edge Detection (Important)
- Origin of egdes
    - Surface normal discontinuity
    - Depth discontinuity
    - Surface color discontinuity
    - Illumination discontinuity
Characterizing edges
Images as functions
- for grey scale image 
- color full images

Image derivatives
Image gradient
Effects of noise
- Smooth first
Associative property of convolution
The 1D Gaussian and its derivatives
2D edge detection filters
Derivative of Gaussian filter
The Sobel operator
- Finding edges
- Get Orientation at Each Pixel
- Non-maximum supression
  
Thresholding edges
Connecting edges
Canny edge detector
Scale space
