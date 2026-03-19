# What is Edge Detection?
An **edge** is the location in an image where the **intensity (brightness) changes suddenly**.

Edge detection is a fundamental technique used in **Digital Image Processing** and **Computer Vision** to identify boundaries of objects inside an image. 

For example, imagine a picture where half of the image is dark and the other half is bright. The line separating them is called an **edge**.

Suppose we have a grayscale image represented by pixel values:

```
10   10   10   10
10   10   10   10
200  200  200  200
200  200  200  200
```

In this image:
* The first two rows are dark.
* The last two rows are bright.

- The **boundary between 10 and 200 is an edge**.
- Edge detection algorithms try to **find these intensity changes automatically**.


## Basic Idea Behind Edge Detection
Edge detection works by measuring **how quickly the intensity changes between neighboring pixels**.

If the change is small, it means the area is smooth.
If the change is large, it means an **edge exists**.

This concept is based on the **Image Gradient**, which measures the rate of change of pixel intensity.

Mathematically:
* Small gradient → smooth region
* Large gradient → edge

## First Derivative Edge Detection
Most edge detection techniques use the **first derivative** of intensity.
The derivative measures how fast the brightness changes between pixels.

Example of intensity values:

```
10   10   10   10   10
10   10   10   10   10
10   10   10   10   10
200  200  200  200  200
200  200  200  200  200
```

Between row 3 and row 4 there is a **large change**:

```
200 − 10 = 190
```

This large difference indicates an **edge**.

To calculate these changes automatically, we use **edge detection operators**.



### Sobel Operator
One of the most widely used operators is the **Sobel Operator**.

The Sobel operator detects edges in **horizontal and vertical directions** using two kernels.

The horizontal Sobel kernel detects vertical edges:

```
-1   0   1
-2   0   2
-1   0   1
```

The vertical Sobel kernel detects horizontal edges:

```
-1  -2  -1
 0   0   0
 1   2   1
```

These kernels move across the image using **convolution**.

#### Sobel Example
Suppose the image is:

```
10   10   10
10   10   10
200  200  200
```

We place the Sobel kernel over the image and multiply each element.
Using the vertical kernel:

```
-1  -2  -1
 0   0   0
 1   2   1
```

Now multiply pixel values:

```
(-1×10) + (-2×10) + (-1×10)
+(0×10) + (0×10) + (0×10)
+(1×200) + (2×200) + (1×200)
```

Calculation:

```
-10 -20 -10 + 0 + 0 + 0 + 200 + 400 + 200
= 760
```

The result **760 is a large value**, which means a **strong edge exists**.


### Prewitt Operator
- Another edge detection technique is the **Prewitt Operator**.
- It is similar to Sobel but uses simpler kernels.

Horizontal kernel:
```
-1   0   1
-1   0   1
-1   0   1
```

Vertical kernel:
```
-1  -1  -1
 0   0   0
 1   1   1
```

Prewitt also measures the **gradient of intensity** but gives equal weight to all rows, while Sobel gives more weight to the center.

#### Prewitt Example
Suppose the same image:

```
10   10   10
10   10   10
200  200  200
```

Using the vertical kernel:

```
(-1×10) + (-1×10) + (-1×10)
+(0×10) + (0×10) + (0×10)
+(1×200) + (1×200) + (1×200)
```

Calculation:

```
-10 -10 -10 + 0 + 0 + 0 + 200 + 200 + 200
= 570
```

The large value indicates an **edge**.



### Roberts Operator
The **Roberts Cross Operator** is one of the earliest edge detection methods.

It uses **2×2 kernels**, which makes it simple but sensitive to noise.

The kernels are:

```
1   0
0  -1
```

and

```
0   1
-1  0
```

These detect **diagonal edges**.


#### Roberts Example
Image:

```
10   10
10   200
```

Apply kernel:

```
(1×10) + (0×10) + (0×10) + (-1×200)
```

Result:

```
10 − 200 = -190
```

The large magnitude shows a **strong edge**.


### Laplacian Edge Detection
Another method uses the **second derivative**, called the **Laplacian Operator**.

Instead of detecting gradient direction, it detects **regions where intensity changes rapidly**.

Common kernel:

```
0  -1   0
-1  4  -1
0  -1   0
```

This operator highlights edges in **all directions**.


#### Laplacian Example
Image:

```
10   10   10
10   10   10
200  200  200
```

Apply kernel to center pixel:

```
(0×10) + (-1×10) + (0×10)
+(-1×10) + (4×10) + (-1×10)
+(0×200) + (-1×200) + (0×200)
```

Calculation:

```
0 -10 +0 -10 +40 -10 +0 -200 +0
= -190
```

A large magnitude again indicates **edge presence**.


### Canny Edge Detection
The most advanced method is the **Canny Edge Detector**.

It detects edges in multiple stages to produce cleaner results.

The process works as follows.
- First, the image is smoothed using a **Gaussian filter** to remove noise.
- Then the gradient of the image is calculated to detect intensity changes and check strength.
- Next, **non-maximum suppression** is applied so that only the strongest edges remain.
- After that, two thresholds are used to classify edges as strong or weak.
- Finally, weak edges connected to strong edges are kept, forming continuous object boundaries.

This method produces **thin and accurate edges**.


## How Edge Detection Separates Objects
Consider a simple object on a background.

```
Background pixels = 20
Object pixels = 200
```

Image matrix:

```
20   20   20   20
20  200  200   20
20  200  200   20
20   20   20   20
```

Edge detection highlights the **boundary between 20 and 200**, producing something like:

```
0   255   255   0
255  0     0   255
255  0     0   255
0   255   255   0
```

These highlighted pixels form the **outline of the object**.


## Why Edge Detection is Important
Edge detection simplifies images while preserving important structural information.

Instead of analyzing millions of pixels, algorithms can focus on **object boundaries**, which helps in tasks such as object recognition, medical diagnosis, and autonomous driving.





# Edge Dectection Pipeline
## 1. Step 1 — Image Acquisition (Getting the Image)
First, a camera captures a scene and converts it into a **digital image matrix**.

Example grayscale image:

```
20   20   20   20
20  200  200   20
20  200  200   20
20   20   20   20
```

Meaning:

* **20 → dark background**
* **200 → bright object**

So visually this image looks like:

```
Background
   ↓
□□□□
□■■□
□■■□
□□□□
      ↑
    Object
```

The object is brighter than the background.


## 2. Step 2 — Convert to Grayscale (if needed)
If the original image is **RGB color**, we convert it to grayscale first.

Example color pixel:

```
(120, 80, 60)
```

Converted grayscale intensity:

```
Gray ≈ 0.3R + 0.59G + 0.11B
```

After this step we have **one intensity value per pixel**, which simplifies edge detection.

Our example is already grayscale, so we skip this step.

## 3. Step 3 — Image Filtering (Noise Removal)
Before detecting edges we usually apply **smoothing filters** such as:

* Mean filter
* Gaussian filter

The purpose is **noise removal**.

Noise example:

```
20   21   19   20
20  200  198   21
19  201  200   20
21   20   22   19
```

These small random variations can create **false edges**.

A smoothing filter averages nearby pixels.

Example **3×3 mean filter**:

Kernel:

```
1/9 1/9 1/9
1/9 1/9 1/9
1/9 1/9 1/9
```

After smoothing the image becomes more uniform:

```
20   20   20   20
20  200  200   20
20  200  200   20
20   20   20   20
```

Now noise is reduced, making edge detection more accurate.


## 4. Step 4 — Gradient Calculation
Now we detect **intensity changes** using gradient operators like:

* **Sobel Operator**
* **Prewitt Operator**
* **Roberts Cross Operator**

These operators use **kernels** that slide over the image.

Example Sobel vertical kernel:

```
-1  -2  -1
 0   0   0
 1   2   1
```

This measures **vertical intensity change**.

### Example Gradient Calculation
Take the center region:

```
20  200  200
20  200  200
20  200  200
```
Apply Sobel kernel:

```
(-1×20) + (-2×200) + (-1×200)
+(0×20) + (0×200) + (0×200)
+(1×20) + (2×200) + (1×200)
```

Compute:

```
-20 -400 -200 + 0 + 0 + 0 + 20 + 400 + 200
= 0
```

But if the kernel is centered at the **boundary**, the change becomes large.

Large gradient values indicate **edges**.

## 5. Step 5 — Edge Strength Calculation
The gradient is calculated in two directions:

* Horizontal
* Vertical

Then we combine them:

[
G = \sqrt{G_x^2 + G_y^2}
]

Where:

* (G_x) = horizontal gradient
* (G_y) = vertical gradient

If **G is large**, that pixel is likely an edge.

## 6. Step 6 — Thresholding
After calculating gradient values, we decide **which pixels are edges**.

Example gradient matrix:

```
5   10   8   6
15  200 200  12
10  200 200  15
5   10   12   7
```

Choose threshold:

```
T = 100
```

Rule:

```
if value ≥ T → edge
if value < T → not edge
```

Result:

```
0   0   0   0
0 255 255  0
0 255 255  0
0   0   0   0
```

Here:

* **255 = edge pixel**
* **0 = background**


## 7. Step 7 — Final Edge Image
The final result shows **only the object boundary**.

```
0   255   255   0
255  0     0   255
255  0     0   255
0   255   255   0
```

This forms the **outline of the object**.

Visually:

```
□□□□
□■■□
□■■□
□□□□
```

The algorithm detected the **boundary between intensity 20 and 200**.


## Complete Edge Detection Pipeline
The full process looks like this:

```
Input Image
     ↓
Grayscale Conversion
     ↓
Noise Removal (Filtering)
     ↓
Gradient Calculation
     ↓
Edge Strength Measurement
     ↓
Thresholding
     ↓
Final Edge Image
```

### How Canny Edge Dectection Works
The **Canny Edge Detector** is considered the most reliable edge detection method in **Computer Vision** and **Digital Image Processing** because it detects edges **accurately while reducing noise and false edges**.

Unlike simple operators (Sobel or Prewitt), Canny follows a **multi-stage process**. I’ll explain the **entire working step-by-step with an example so you understand how the edge image is produced**.


#### Complete Working of the Canny Edge Detection Process
Suppose we start with a simple grayscale image matrix:

```
20   20   20   20
20  200  200   20
20  200  200   20
20   20   20   20
```

Here:

* 20 → background
* 200 → object

We want to detect the **boundary of the object**.


#### Step 1: Gaussian Smoothing (Noise Removal)
Real images often contain **noise** (random pixel variations). If we detect edges directly, noise can create **false edges**.

So the first step is smoothing using a **Gaussian filter**.

Example Gaussian kernel:

```
1 2 1
2 4 2
1 2 1
```

Normalize by dividing by 16.

This filter **averages nearby pixels but gives more weight to center pixels**, which preserves object shapes better than a mean filter.

After smoothing, the image becomes slightly blurred but **noise is reduced**.

Example smoothed values might look like:

```
22   25   25   22
25  180  180   25
25  180  180   25
22   25   25   22
```

Now the image is cleaner for edge detection.

#### Step 2: Gradient Calculation
Next we measure **how quickly pixel intensity changes**.

This is done using gradient operators such as **Sobel Operator**.

Two gradients are calculated:

* Horizontal gradient (G_x)
* Vertical gradient (G_y)

Example kernels:

Horizontal:

```
-1 0 1
-2 0 2
-1 0 1
```

Vertical:

```
-1 -2 -1
 0  0  0
 1  2  1
```

When these kernels slide across the image they produce **two gradient images**:

```
Gx → horizontal intensity change
Gy → vertical intensity change
```

#### Step 3: Gradient Magnitude (Edge Strength)
Now we calculate **edge strength** from the gradients.

Formula:

[
G = \sqrt{G_x^2 + G_y^2}
]

Example:

If

```
Gx = 120
Gy = 160
```

Then

```
G = √(120² + 160²)
G = √40000
G = 200
```

This value **200 represents the strength of the edge**.

Large value → strong edge
Small value → weak edge

This step produces a **gradient magnitude image**.

#### Step 4: Gradient Direction
Besides strength, we also calculate **edge direction**:
```
[
\theta = \tan^{-1}(G_y / G_x)
]
```
This tells us whether the edge is:

* horizontal
* vertical
* diagonal

The direction helps in the next step to **thin the edges**.

#### Step 5: Non-Maximum Suppression
After gradient calculation, edges appear **thick**.

Example:

```
0   100  120  100   0
0   150  200  150   0
0   120  180  120   0
```

But real edges should be **thin lines**.

Non-maximum suppression works like this:

1. Look at the gradient direction.
2. Compare the pixel with its neighbors in that direction.
3. Keep it **only if it is the maximum value**.

Example:

```
100   200   100
```

Here 200 is the maximum → keep it.

Result after suppression:

```
0   0   200   0   0
```

Now edges become **thin and precise**.

#### Step 6: Double Thresholding
Next we classify edges using **two thresholds**:

High threshold (T_h)

Low threshold (T_l)

Example:

```
Th = 150
Tl = 70
```

Rules:

If gradient ≥ 150 → **strong edge**

If 70 ≤ gradient < 150 → **weak edge**

If gradient < 70 → **not edge**

Example gradient values:

```
40   80   160
20  120   200
30   60   140
```

Classification:

```
0   weak   strong
0   weak   strong
0   0      weak
```

#### Step 7: Edge Tracking by Hysteresis
Now we connect weak edges to strong edges.

Rule:

* Weak edge **connected to strong edge → keep it**
* Weak edge **not connected → remove it**

Example:
```
Strong → Weak → Weak
```
These pixels remain as edges because they form a **continuous boundary**.

But isolated weak edges are removed.

Final result:

```
0   255   255   0
255  0     0   255
255  0     0   255
0   255   255   0
```
This represents the **outline of the object**.

## Final Pipeline of Canny Edge Detection
The complete process is:

```
Input Image
     ↓
Gaussian Smoothing
     ↓
Gradient Calculation
     ↓
Gradient Magnitude + Direction
     ↓
Non-Maximum Suppression
     ↓
Double Thresholding
     ↓
Edge Tracking by Hysteresis
     ↓
Final Edge Image
```

### Why Canny Edge Detection is Better
The **Canny Edge Detector** works better because:

* It removes noise first
* It calculates edge strength precisely
* It keeps edges thin
* It removes false edges
* It produces continuous object boundaries
