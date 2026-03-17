## Low-level vision 
At this stage the computer does not understand objects yet. It only works with pixels and basic image information.

**Example:** Before detecting a face, the computer first processes the image to find edges, patterns, and features.   


## Image Formation
Image formation explains how a real-world scene becomes a digital image inside a camera. In the real world, objects reflect light. When a camera takes a picture, light from the scene enters the camera lens and is focused onto the image sensor. The sensor converts the incoming light into electrical signals, and those signals are converted into pixels that form the digital image.

For example, imagine taking a photo of a tree with your smartphone. Sunlight reflects from the tree and travels toward the camera. The camera lens focuses that light onto the sensor. Each small cell in the sensor measures the intensity of light and converts it into numbers. These numbers become pixel values in the image. The result is a 2-dimensional grid of pixels representing the tree.

Different camera parameters such as focal length, aperture, and exposure time affect how the image is formed. For instance, if the exposure time is long, the sensor collects more light and the image becomes brighter. If the camera moves during exposure, the image may become blurred.



## What is **Filtering** in Image Processing?
In **Computer Vision** and **Digital Image Processing**, **filtering** is the process of **modifying pixel values in an image using neighboring pixels** to improve or extract useful information.

An image can contain problems such as:

* noise (random dots)
* blur
* poor contrast
* unnecessary details

Filtering helps **remove unwanted information or highlight important structures**.

Think of filtering like **looking at an image through a mathematical lens**. The filter processes the pixels and produces a **new improved image**.


# Why We Use Filtering
Filtering is used in the **early stage of computer vision** to prepare images for further processing like **Edge Detection**, **Feature Detection**, and **Image Segmentation**.

### Removing Noise
Medical images or satellite images often contain **random noise**. Filtering removes these unwanted pixels.

Example:
An X-ray image may contain small white dots. Filtering smooths the image so doctors can see structures clearly.

### Smoothing Images
Sometimes images are too sharp or contain tiny variations. A smoothing filter averages nearby pixels to create a cleaner image.


### Enhancing Edges
Some filters emphasize boundaries of objects, helping algorithms detect shapes.

Example:
Edge filters highlight the outline of a car in an image.

# Types of Filtering
Filtering is mainly divided into **two categories**.

1. **Linear Filtering**
2. **Non-Linear Filtering**

The difference is **how pixel values are mathematically combined**.

# Linear Filtering
In **linear filtering**, the new pixel value is computed as a **linear combination of neighboring pixels**.

- This means we multiply pixel values by numbers and **add them together**.
- Mathematically, linear filtering uses a **convolution operation**.

If an image is represented by:
```
[I(x,y)]
```
and the filter kernel is:
```
[K(i,j)]
```
then the filtered image is:
```
[
I'(x,y) = \sum_{i=-n}^{n} \sum_{j=-n}^{n} K(i,j), I(x-i, y-j)
]
```
This equation means:

1. Take neighboring pixels.
2. Multiply them with kernel values.
3. Add the results.
4. Assign the result to the new pixel.

The small matrix used for filtering is called a **kernel** or **mask**.


## Example of Linear Filtering
Suppose we have a **3×3 neighborhood**:
```
[100  102  98 
101  103  97 
99  100  102]
```
If we apply an averaging kernel:
```
[1  1  1 
1  1  1 
1  1  1]
```
We multiply each pixel by the kernel value and sum them.
```
[1/9{100+102+98+101+103+97+99+100+102}]
= 
[ {902}/{9} = approx 100]
```
So the center pixel becomes **100**, which smooths the region.


# Types of Linear Filters
Several important filters fall into this category.


## Mean Filter (Averaging Filter)
The **mean filter** replaces each pixel with the **average of its neighbors**.

Example kernel:
```
1/9[ 1  1  1
     1  1  1
     1  1  1  ]
```
### What it does
It **smooths the image** and reduces noise.

Example:

If an image has random pixel values:

```
50 200 48
49 52 210
51 50 49
```

The average reduces extreme values like **200 and 210**, making the image smoother.


## Gaussian Filter
The **Gaussian Filter** is a smoothing filter that uses **weighted averaging**.

Instead of treating all pixels equally, it gives **higher weight to the center pixel**.

Example kernel:
```
1/16[1  2  1
     2  4  2
     1  2  1]
```
Here the center pixel contributes more.

### Why it is better
- The Gaussian filter produces **natural smoothing** without blurring edges too much.
- It is heavily used before **Canny Edge Detection**.


## Laplacian Filter
The **Laplacian Operator** detects **areas where intensity changes rapidly**, which corresponds to edges.

Example kernel:
```
[0 -1  0
-1  4  -1
0  -1  0]
```
When applied to an image, it highlights edges.

## Box Filter
A **box filter** is actually a **special type of mean filter**.

**Kernel example:**
```
1 1 1
1 1 1
1 1 1
```

Sometimes the division (normalization) is done **after convolution**, which is why it is called a box filter.

Box filters are commonly used for **fast smoothing**.

## High-Pass Filter
A **high-pass filter** keeps **high-frequency information** and removes low-frequency parts.

High frequency = edges and sharp transitions.

Example kernel:
```
-1 -1 -1
-1  8 -1
-1 -1 -1
```
- Flat regions become near **0**, but edges become **large values**.
- So edges are highlighted.
- High-pass filters are often used in **edge detection algorithms**.


## Sharpen Filter
A sharpen filter enhances edges while keeping the original image.

**Example kernel:**
```
0 -1 0
-1 5 -1
0 -1 0
```

Mathematically:
```
[{Sharpened Image} = {Original Image} + {Edge Information}]
```
Example:

Original pixel:

```
100
```

Edge value:

```
20
```

Sharpened pixel:

```
120
```

Edges become clearer.




# Non-Linear Filtering
In **non-linear filtering**, the output pixel is **not computed using simple multiplication and addition**.

Instead, the filter uses operations like:

* sorting
* selecting maximum or minimum values
* ranking pixels

Because of this, the relationship between input and output pixels is **not linear**.

Non-linear filters are especially good for **removing certain types of noise**.


## Median Filter
The most famous non-linear filter is the **Median Filter**.

Instead of averaging, it replaces a pixel with the **median value of its neighbors**.   
**Example**  

Suppose a 3×3 region contains:

```
10 12 11
13 200 12
11 12 10
```

Here **200 is noise**.

Step 1 — sort values:

```
10 10 11 11 12 12 12 13 200
```

Step 2 — choose the middle value (median):

```
12
```

So the center pixel becomes **12**, removing the noise.

Median filters are excellent for removing **salt-and-pepper noise**.


## Max Filter
The **maximum filter** replaces a pixel with the **largest value in the neighborhood**.

**Example:**
```
10 12 11
13 8 12
11 12 10
```

The maximum value is **13**, so the center becomes **13**.

This filter helps **enhance bright regions**.

## Min Filter
The **minimum filter** selects the **smallest value in the neighborhood**.

**Example:**

```
10 12 11
13 8 12
11 12 10
```

The minimum value is **8**, so the center pixel becomes **8**.

This filter enhances **dark regions**.



# How Filtering Works Step by Step
Consider a small grayscale image:

```
10 12 11
13 14 12
11 12 10
```

Step 1 — place the filter kernel on the image.

Step 2 — multiply corresponding values.

Step 3 — sum the results.

Step 4 — assign the result to the center pixel.

Step 5 — slide the kernel across the image.

This sliding process is called **convolution**.



# Real-World Example of Filtering
In **self-driving cars**, cameras capture road images.

Before detecting lanes:

1. The image is smoothed using a **Gaussian filter**.
2. Noise is removed.
3. Then **edge detection** finds road boundaries.

Without filtering, noise could create **false edges**, confusing the system.


Your understanding is **partly correct**, but we need to refine it a little.


# Cross-Correlation
Cross-correlation is one way to apply a filter.

The kernel is placed on the image and **multiplied directly without flipping**.

Example image patch:

```
1 2 3
4 5 6
7 8 9
```

Kernel:

```
0 1 0
1 0 1
0 1 0
```

Operation:

```
1×0 + 2×1 + 3×0
+ 4×1 + 5×0 + 6×1
+ 7×0 + 8×1 + 9×0
```

Result:

```
2 + 4 + 6 + 8 = 20
```

So the new center pixel becomes **20**.

Cross-correlation is widely used in **image template matching**.



# Convolution
Convolution is very similar to cross-correlation, but **the kernel is flipped horizontally and vertically before multiplication**.

Example kernel:

```
1 2 3
4 5 6
7 8 9
```

After flipping:

```
9 8 7
6 5 4
3 2 1
```

Then multiplication is performed like normal filtering.

Convolution is extremely important because it is the main operation used in **Convolutional Neural Network**.



# What is Thresholding?
Thresholding is a **non-linear image processing technique** used to **separate objects from the background**.

* The idea is very simple: we **choose a threshold value (T)**.
* Every pixel in the image is compared to T:
```
[
I'(x,y) = 255  \text{if } I(x,y) \geq T \
0 & \text{if } I(x,y) < T
\end{cases}
]
```
* **I(x,y)** = original pixel intensity
* **I'(x,y)** = new pixel intensity
* **T** = threshold value (e.g., 128 for an 8-bit image)

So after thresholding, the image becomes **binary**: pixels are either **white (255)** or **black (0)**.

## Example
Original 3×3 image:

```text
120 130 100
140 150 90
80  110 160
```

Let threshold **T = 120**.

* Compare each pixel with 120:

```text
120 >= 120 → 255
130 >= 120 → 255
100 < 120 → 0
140 >= 120 → 255
150 >= 120 → 255
90  < 120 → 0
80  < 120 → 0
110 < 120 → 0
160 >= 120 → 255
```

Resulting binary image:

```text
255 255   0
255 255   0
0    0   255
```

This is a **segmented image**, where bright pixels are separated from dark pixels.

# Why Thresholding is Non-Linear
Thresholding is **non-linear** because:

* The output is **not a linear combination of input pixels**.
* Linear operations satisfy the **superposition principle**:
```
[
f(aX + bY) = a f(X) + b f(Y)
]
```
* Thresholding does **not** satisfy this property. For example:

```text
X = 100 → threshold 120 → 0
Y = 200 → threshold 120 → 255
```

[
f(X+Y) = f(300) = 255 \neq f(X)+f(Y) = 0+255 = 255 \text{(coincidentally same here but not in general)}
]

* Also, thresholding **creates jumps in intensity**, which cannot be produced by **linear weighted sums of pixels**.

# Why We Don’t Use Linear Filters for Thresholding
Linear filters, like **mean, Gaussian, Laplacian**, work by **weighted sums of pixels**:
```
[
I'(x,y) = \sum K(i,j) I(x+i,y+j)
]
```
* This **blends pixel values**, producing continuous values.
* Thresholding, however, **needs a hard decision: either 0 or 255**.
* A linear filter **cannot create sharp 0/255 jumps**; it will only smooth or blur pixel intensities.

So thresholding is inherently **non-linear** and cannot be implemented with linear filters.


# Types of Thresholding
1. **Global Thresholding** – One threshold value T for the entire image
2. **Adaptive Thresholding** – Threshold depends on local neighborhood (useful for uneven lighting)
3. **Otsu’s Method** – Automatically chooses T based on **image histogram**

