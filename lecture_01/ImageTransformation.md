## Image Transformation

Image transformation is about **changing the way an image is represented or projected**. It is a crucial concept in **computer vision**.

### Why We Use Image Transformation
* To **align images** (e.g., stitching panoramas)
* To **resize, rotate, or scale** images
* To **map images from one coordinate system to another**
* To **enhance features** for further processing



### Types of Image Transformation

#### 1. Geometric Transformation
Changes the **position or shape of the image**.

* **Translation** → move the image in x or y direction
* **Scaling** → increase or decrease size
* **Rotation** → rotate by an angle
* **Affine Transformation** → combines translation, scaling, rotation, and shearing
* **Homography / Perspective Transformation** → maps one plane to another (used in panorama stitching)

**Example:**
If you have a photo and rotate it 90°, all pixel positions change. The pixel intensities remain the same, but the coordinates change.

Mathematically:

[
\begin{bmatrix} x' \ y' \end{bmatrix} =
\begin{bmatrix} a & b \ c & d \end{bmatrix}
\begin{bmatrix} x \ y \end{bmatrix} +
\begin{bmatrix} t_x \ t_y \end{bmatrix}
]

Where (x, y) are original coordinates, (x', y') are transformed, (a,b,c,d) control rotation/scaling, (t_x, t_y) control translation.



#### 2. Intensity Transformation
Changes **pixel values** rather than coordinates.

* **Contrast adjustment** → make darks darker, brights brighter
* **Log transformation** → enhance darker regions
* **Power-law (Gamma) transformation** → correct brightness perception
* **Thresholding** → also an intensity transformation

**Example:**
If you apply a gamma correction with γ=2:

```text
New Pixel = (Old Pixel)^2
```

This brightens or darkens the image depending on γ.

#### 3. Frequency Domain Transformation
Transforms the image from **spatial domain (pixels)** to **frequency domain**.

* Example: Fourier Transform, DCT, Wavelets
* Useful for **compression**, **filtering**, or **noise reduction** in frequency space

**Example:**
JPEG uses DCT (Discrete Cosine Transform) to remove high-frequency details that humans don’t notice.

---

## 1️⃣ Image Restoration

Image restoration is about **improving the quality of an image that has been degraded**. In real life, images can be corrupted by **noise, blur, or distortions**, and restoration tries to fix these issues.

### a) Denoising

* **What it is:** Removing unwanted random variations in pixel values called **noise**.
* **Why it happens:** Noise can come from low-light conditions, sensors, transmission errors, or compression artifacts.
* **Example:** Imagine you take a photo in a dark room. The image looks grainy.

**How it works:**

* Linear filters like **Gaussian smoothing** can reduce noise by averaging neighboring pixel values.
* Nonlinear filters like **Median filter** replace each pixel with the median of its neighbors, which is very effective for **salt-and-pepper noise**.

**Step-by-step example:**

Original pixel values in a 3×3 patch:

```
10 12 11
250 10 12   ← “250” is noise
11 12 10
```

* Apply **median filter** → replace the center pixel (250) with the median of neighbors → result 11 or 12
* The image looks smoother, noise removed.

---

### b) Deblurring

* **What it is:** Restoring sharpness to a blurry image.
* **Why it happens:** Motion blur (camera shake), out-of-focus lens, or long exposure.
* **Example:** A moving car captured at night may appear blurry.

**How it works:**

* Deblurring often uses **inverse filtering** or **Wiener filtering**, which mathematically estimate the **original sharp image** from the blurred one.
* It uses **knowledge about the blur** (motion direction, lens properties) to reverse it.

---

## 2️⃣ Image Compression

Image compression is about **reducing the size of an image file** while keeping it visually acceptable.

* **Why:** To save storage space and transmit images faster.
* **Example formats:** JPEG, HEIF, MPEG (video)

**How it works:**

1. Transform the image into **frequency domain** using **DCT (Discrete Cosine Transform)** or other transforms.
2. Reduce or remove high-frequency components that are **less noticeable to the human eye**.
3. Quantize the remaining values and encode efficiently.

**Example:**

* Original image size: 5 MB
* After JPEG compression: 500 KB
* Visually almost identical, but file is much smaller.

Compression can be **lossy** (some data lost, e.g., JPEG) or **lossless** (no data lost, e.g., PNG).

---

## 3️⃣ Locating Structural Features

This is about **finding important points or structures in the image**, which is essential for tasks like **recognition, tracking, or 3D reconstruction**.

### a) Corners

* **What it is:** Points where **two edges meet** or where intensity changes in multiple directions.
* **Why important:** Corners are very **distinctive**, easy for a computer to detect, and stable across images.
* **Example:** The corners of a window or roof in a building.
* **How it works:** Algorithms like **Harris Corner Detector** or **Shi–Tomasi** detect corners by looking for **large intensity changes in multiple directions**.

### b) Edges

* **What it is:** Boundaries of objects where **pixel intensity changes sharply**.
* **Why important:** Edges define **shapes** and are crucial for **object recognition**.
* **Example:** The outline of a coin, the border of a car, or a road in satellite imagery.
* **How it works:** Operators like **Sobel, Prewitt, or Canny** calculate the **gradient of brightness** and detect pixels with high gradient values as edges.



## Image Synthesis
**Image synthesis** refers to the process of **generating new images using computational models based on learned data or scene information**. Instead of only analyzing images (which is the traditional task of computer vision), the system can also **create or reconstruct images**.

In simple words, image synthesis means that a computer **produces new images by learning patterns from existing images or by using mathematical models**. The system studies visual features such as shapes, textures, colors, lighting, and object structures, and then generates a new image that follows similar patterns.

**Traditionally,** computer vision focused mainly on **image understanding**, such as recognizing objects, detecting faces, or identifying scenes. However, modern computer vision systems can also **generate images**, reconstruct scenes, or simulate visual environments. This ability is what we call image synthesis.

**For example,** if a model is trained on thousands of images of human faces, it can learn the visual patterns that define a face. After training, the system can generate **completely new faces that look realistic but do not belong to real people**. This is a common example of image synthesis.

**Image synthesis is used in several important computer vision tasks:** 
- **Image reconstruction**, where the system generates a complete image from incomplete data.
- **3D Scene Generation**, where the system creates images of a scene from different viewpoints.
- **data augmentation**, where artificial images are created to increase training data for machine learning models.

Modern image synthesis systems usually rely on Deep Learning models such as generative neural networks. These networks learn the structure of images from large datasets and then produce new images with similar characteristics.


### Models Used in Image Synthesis
#### **Generative Adversarial Networks**
GANs work using two neural networks that compete with each other during training. One network, called the generator, tries to create fake images that look real. The second network, called the discriminator, tries to distinguish between real images and the generated ones. During training, the generator gradually improves because it tries to fool the discriminator. After many training iterations, the generator becomes very good at creating realistic images.

#### **Variational Autoencoders**  
This model learns a compressed representation of images called a latent space. During training, the encoder converts an image into this latent representation, and the decoder reconstructs the image from it. After learning the distribution of images in the latent space, the model can generate new images by sampling new points from this space and decoding them.

#### **Diffusion Models**
More recently, very powerful image synthesis systems use Diffusion Model. Diffusion models generate images by starting with random noise and gradually removing the noise step by step until a clear image appears. During training, the model learns how noise is added to images and how to reverse that process. When generating a new image, the model begins with pure noise and slowly transforms it into a meaningful image.

### How it works
Now consider how the generation process works in general. During training, the model is given a large dataset of images. The model analyzes patterns such as *object shapes, colors, textures, and spatial relationships.* These patterns are stored in the learned parameters of the neural network. When a new image needs to be generated, the model samples a random input (such as a noise vector or latent vector) and then transforms this input into an image using the patterns it learned during training.   

In many modern systems, text prompts can also guide the generation process, allowing the system to generate images that match a textual description.

### Metrics used in Image Synthesis
To evaluate the quality of synthesized images, researchers use several metrics. 
1) **Fréchet Inception Distance**, which measures how similar the generated images are to real images in terms of feature distributions. A lower score means the generated images are more realistic. 
     
2) **Inception Score**, which evaluates both the quality and diversity of generated images. High scores indicate that the images look realistic and represent different categories clearly.   
   
3) **Structural Similarity Index (SSIM)**, which measures similarity between generated and real images based on luminance, contrast, and structure. If two images same SSIM equal to 1 otherwise 0.

These metrics help researchers determine whether the generated images are realistic, diverse, and visually consistent.

