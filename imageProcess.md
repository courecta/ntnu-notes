# Image Processing

### EOS Presentation

> EOS project report consists of
> - PDF files of the project papers
> - Journal/Conference papers w/ years
> - Brief review (techniques, applications)
> - comments
> 
> Libraries needed for this class
> - SciPy
> - Numpy
> - Matplotlib
> - opencv-python
> 
> (just pip3 install)
> 
> Other libraries
> - OpenCV
> - Scikit-Image
> - Scikit-Learn

### Lecture 1: Introduction
What is image processing?

Image Processing is for humans.

- Low-level processing
  - ex. threshold or noise removal 
- Mid-level processing
  - ex. grouping or clustering
- High-level processing
    
### Sampling

This process digitizes a cont. function into a discrete one
However, a side-effect may be under-sampling, which comes from not sampling enough discrete data points to reconstruct a fluid, continuous data stream. (As such, there are criterion to standardize sampling practices from data. ex. Nyquist, Whittaken-Shannon)
    
### Images as 2-D functions

When phenomena such as under-sampling occur, it may produce a grid effect, this is due to not enough data being

There may also be false contours or "false quantization" is produced by insufficient quantization of gray levels

### 1.4 Images and Digital Images

- A scene is a 3-D continuous function [ g(x, y, z) ]
- An image is a 2-D continuous function [ f(x, y, z) ]
- A digital image is a 2-D discrete function [ I(r, c) ]

- A pixel is a picture element
- Thus, gray level can be determined by 256 values from 0 ~ 255

### 1.8 Types of digital images

#### Typically for photography
- Grayscale Images
- Binary Image
- Color Images
- Multi-spectral Images

#### Usually for medical uses

- Radio Images
- Ultrasound Images
- Ultraviolet Images
- X-ray Images
- Gamma-ray Images
- X-ray transmission computerized tomography (CT) Images
- Magnetic Resonance Imaging (MRI) Images
- Other types of general and special images produced by medical tools and machines

#### For physical object scanning

- Range Images
- Moire Images
- Structure light Images

#### However, there are many types as well found in nature in the form of *Biological eyes*

### 1.9 The human eye

We perceive using cones in our eyes

We have three types of cones
- **g( &alpha;, &beta;, &gamma; )**
- **RGB**
- **LMS**

### 1.10 Image Perception

-- We here remark the limitations of the human visual system

As a biological organism, we are susceptible to *optical illusions* and *subjective objects*

There exists types such as,

- Simultaneous contrasts
- Overshoots / Undershoots
- Distance illusions
- Imaginary shapes or faces ( where there aren't any )
- 