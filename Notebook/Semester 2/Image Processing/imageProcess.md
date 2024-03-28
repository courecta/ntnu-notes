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

## Chapter 1: Introduction
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

## Chapter 2 - Image Files and file types

- An image is essentially a binary file, we can see this in a hexadecimal dump

An Image file contains 2 elements

1. A header which represents all of the metadata of an image, such as its size, color, and compression method
2. Its image data with its index and pixel values

There are many image file types such as:

- BMP ( Microsoft Bitmap Pattern )
  - No compression, needs larger storage
- JPEG ( Joint Photo-Graphics Experts Group )
  - lossy compression, needs less storage
- GIF ( Graphics Interchange Format )
  - lossless compression
- TIFF ( Tagged Image File Format )
  - Multiple images
- PNG ( Portable Network Graphics )
  - lossless compression

> [!NOTE] BMP File
> Usually isn't compressed. Its header consists of 14 bytes and with information of 40 bytes

> [!NOTE] PNG Format
> Supports Gamma correction and has alpha channels that can associate various transparencies with the image ( it can be split into foreground and background, etc. )

> [!IMPORTANT] What is Gamma Correction?
> Uses the non-linear nature of perceived light and color with the formula of V<sub>out</sub> = AV<sub>in</sub><sup>&gamma;</sup>

## Chapter 3 - Image Display

### How good an image looks is dependent on multiple factors such as:

1. Image quality
   - Spatial resolution
   - Grayscale resolution
2. Display Device
   - What display are you using? Monitor types, resolution, or graphics card
3. The working environment such as ambient lighting

#### Image quality

There are also bit images. Whereas the traditional grayscale image has 256 values ( 0 ~ 255 ) represented by 8 bits ( 2<sup>8</sup> ) , a bit image consists of 8 bit planes, where its values are only 0 and 1.

> [!CAUTION] Bit image order
> the most significant bit image plane has the most important data at the 7th bit plane
>
> the least significant bit plane is the 0th bit plane with the least important data

There are 2 phenomena that occur from using digital images as we have already mentioned

- The grid effect which comes from spatial resolution
- False contours which comes from quantization, which is a consequence of grayscale resolutions
- Another is uniform quantization, which depends on the printers or the display device

> [!IMPORTANT] Dithering
> The process of reducing the number of gray levels in a image using patterns of dots to simulate those replaced shades of gray. Possible with techniques such as Half-toning

> [!CAUTION] Half-toning
> Representing an images with 2 tones ( Black & White )

#### Dithering process

## Chapter 4 - Point Processing

#### Image processing: Transforms the values of pixels

> [!NOTE] Point processing vs Neighborhood processing
> Point: applies a function to each pixel
> Neighborhood: applies a function to a group of pixels

Point processing y = f ( x )

- Addition and subtraction
  - y = f ( x ) = x + C
  - y = f ( x ) = x - C

```
if( y > 25 )
   = 255
else if( y < 0 )
   = 0
```

- Multiplication y = f ( x ) = Cx
- Complementation y = 255 - x

#### 4.3 Histogram

A histogram here plots the

- x - value to be the grayscale value from 0 to 255
- y - value to be how much times a pixel with that exact value appears in the image

They can be classified as

- Dark images
- bright images
- low contrast images
- high contrast images ( colors pop best )

Contrasts can be stretched with a transform function of the general form

> [!example] General Form Equation
> $$
> y = (\dfrac{x-a}{b-a})^y(d-c)+c
> $$
#### 4.3.2 Histogram Equalization

- Change the histogram of an image to a much more uniform distribution using the transform function to form the accumulative histogram of the image

Theorem: Let T be a monotonic differentiable function. let r be a continuous random variable with density p<sub>r</sub>. Let s = T ( r ) with density p<sub>r</sub>. Thus,

> [!IMPORTANT] Theorem
> $$
> P_{s}(s) = P_{r}(r) \mid\dfrac{dr}{ds}|
> $$

- note that in real world problems, usually, the transform function can be used even if the function is not strictly monotonic

## Chapter 5 - Neighborhood Processing

- While point processing applies a function to each pixel
- Neighborhood processing applies a function to each neighborhood of pixels

Neighborhoods have masks that can have different shapes and sizes

Every mask has a reference point

A mask + function = filter

#### But what is a filter?

- 1-D mask of a 3 contiguous pixel shape with a 1/3 function takes those 3 pixels and applies the 1/3 function to them
- 2-D applies the same but with 2 dimensional masks and functions

- An example is spatial filtering which applies a function to take a fraction of the original discrete function and allow them to become more even
- This is actually a type of noise filtering, or removal

- Image filtering uses a reference point filter to process
1. Using an input image
2. it looks at the current pixel under consideration
3. then it identifies its pixel neighborhood
4. then it applies the filter
5. The entire neighborhood is then applied with the filter
6. then the sum of all products is obtained
7. Then value replacement takes place
8. The output pixel is then used to replace the original pixel in (2)
9. Thus, an output image is produced


Review of convolution on a 1-D spatial field

$$
\int_{-\infty}^{\infty} f(a)g(x-a) \, da 
$$

Smoothing & Averaging filters

techniques for using mask values and applying functions that can extend, i.e. from a 3x3 input and applying a mask that is bigger. However, it may eventually lead to being blurry.

Gaussian filter

1-D :
$$
g(x) = \dfrac{1}{\sqrt{ 2\pi\sigma }}e^\dfrac{x-\bar{x}}{2\sigma^2}
$$

 Frequency domain filters

Spatial filters applied to the spatial domain of the image can be converted to frequency filters ( using Fourier transformations ) are applied to the frequency domain of the image.

High frequency components &rarr; edges, noises
Low frequency components &rarr; regions

1-D case: A spatial domain being Fourier transformed into a  frequency domain

2-D case: takes an input an applies the same high/low pass filter except on a 2-D plane

### Edge Sharpening or Enhancement

Unsharp Masking takes an image and makes it more smooth by taking the original image $$f(x,y)$$ and its blurred
$$
\tilde{f}(x,y)
$$

and uses it to subtract
$$
g_{mask}(x,y)
$$
then scales it with k
$$
k \times g_{mask}(x,y)
$$
finally adding,
$$
g(x,y)
$$
and scales it for display

The original image is of the signal $$f(x,y)$$
The blurred signal is essentially a smoothed version of the original image

The unsharp mask g then is such that,$$g_{mask}(x,y) = f(x,y) - \tilde{f}(x,y)$$
Thus, the sharpened signal is obtained by adding$$k \times (c) to (a) s.t. g(x,y) = f(x,y) + k \times g_{mask}(x,y)$$
There are alternatives to this process such as using a high boost filter

### Non-linear smoothing filters

takes the$$x_{1} \leq x_{2} \leq x_{3} \leq \dots x_{n} $$
such that,$$x_{i} = \text{neighborhood elements}$$
We can then have the choice of applying the maximum filter by taking the nth, which is the highest element, or the first element for a minimum filter to apply to the rest of the image, usually resulting in a higher, if max, and a darker image if minimum.

### Median filter

- noise removal
- yet, edge preserving

this is a very useful filter method technique due to the fact that it preserves edges, and edges are usually very useful information that needs to be preserved

### Kuwahara filter

The output is the mean of the region with the lowest variance

### K-nearest neighbors

Simply just taking K neighbors and averaging them to get a filter value

### Geometric mean filter
$$
\prod_{(i,j)\in M}x(i,j)^\dfrac{1}{|M|}
$$
### Alpha-trimmed mean filter

1. Order elements
2. trim off m end elements
3. take the mean,

$$\sum_{i=m+1}^{n-m}\dfrac{x_{i}}{n-2m}$$
Lastly, there is region of interest processing that takes a specific point and applies one of three, usually,

1. Average filtering
2. unsharp masking
3. Laplacian of Gaussian

## Chapter 6 - Image Geometry

> [!abstract] Objective
> Consider the transformations of the shape, size, position, and orientation of an image

There are 2 types of transformations

- Rigid transformations
	- e.g. translation and rotation
- Deformable transformations
	- e.g. shape change ( warping ) scale ( size ) change

There are 2 major steps for performing a geometrical transformation of an image,

1. Sampling - determine the positions to-be-filled values
2. Interpolation - determine values to fill the positions
	- Nearest-neighbor interpolation
	- linear interpolation

But what if we were to apply interpolation on a 2D plane, we have to apply *Bilinear Interpolation*

Step 1: $$f(x,y')=\mu f(x,y+1)+(1-\mu)f(x,y)$$
Step 2: $$f(x+1,y')=\mu f(x+1,y+1)+(1-\mu)f(x+1,y)$$
Step 3:$$f(x',y')=\lambda f(x+1,y')+(1-\lambda)f(x,y')$$
Step 4:$$f(x',y')=\lambda f(x+1,y')+(1-\lambda)f(x,y')$$
There is a General Interpolation that follows the interpolation function

$$R(\cdot),0\leq\lambda\leq 1$$
of which, x1 and x2 represent the locations whose values f ( x1 ) and f ( x2 ) are available, and x' is the location of the value f ( x' ) is to be determined

Thus, given those above 2 function points, we can conclude that, Linear Interpolation can be represented as

$$f(x')=(1-\lambda)f(x_{1})+\lambda(x_{2})$$
while General Interpolation can be represented as $$f(x')=R(-\lambda)f(x_{1})+R(1-\lambda)f(x_{2})$$
There is also the cubic interpolation function, where 4 points are needed.

Bicubic Interpolation is the application of cubic interpolation along the rows and then down the columns of the points of the image respectively

### Image enlargement

Steps
1. Zero Interleave
2. Filling
	- For each pixel, apply NN ( Nearest neighbor ) interpolation
	- or, apply Bilinear interpolation
	- or, Bicubic interpolation

### Image Reduction

- Subsampling
- Edge following

### Image Rotation

$$
\begin{bmatrix}
x \\ y
\end{bmatrix} = \begin{bmatrix}
\cos\theta & -\sin\theta \\ \sin\theta & \cos\theta
\end{bmatrix} \begin{bmatrix}
x \\ y
\end{bmatrix}
$$
and

$$\begin{bmatrix}
x \\ y
\end{bmatrix} = \begin{bmatrix}
\cos\theta & \sin\theta \\ -\sin\theta & \cos\theta
\end{bmatrix} \begin{bmatrix}
x' \\ y'
\end{bmatrix}
$$

Drawbacks:

1. Out of Range
2. Truncation error
3. Holes

Solutions

1. Enlarge image size to solve the out of range problem
2. Perform an inverse transformation ( to fix holes and truncation error )

> [!note] Anamorphisis
> Stretch or distort shape of object for artistic or dramatic effect

## Chapter 7 - Fourier Analysis

Fourier Analysis = Fourier Series + Fourier transform

- Fourier Series - A periodic ( T ) function that can be written as the sum of sines and cosines of varying amplitudes and frequencies mathematically
- Some functions are formed by a finite number of sinusoidal / sinuous functions
- Some functions may require an infinite number of sinusoidal / sinuous functions to compose

- A Fourier transform preserves the information of the signal function

$$F(u)=\int_{-\infty}^{\infty}f(x)\exp(-j_{2}\pi ux) dx $$
while the inverse Fourier transform of F( u ) is

$$f(x)=\int_{-\infty}^{\infty}F(u)\exp(j_{2}\pi ux) dx$$

and there are the discrete versions of both as well, and the vector-matrix form bases off of the discrete form instead