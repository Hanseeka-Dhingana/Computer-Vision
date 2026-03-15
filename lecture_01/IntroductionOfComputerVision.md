
# Introduction to Computer Science
## What is the Computer Vision?
Computer Vision is a field of computer science and artificial intelligence that focuses on enabling computers to see, understand, and interpret visual information from the world, such as images and videos. 

The main goal of computer vision is to make machines capable of performing tasks that normally require human vision, like recognizing objects, understanding scenes, detecting motion, and identifying patterns in images.

In simple words, computer vision allows a computer to look at an image or video and understand what is inside it.  

**For example** When a human sees a photo of a dog, the brain quickly recognizes the shape, color, and features and identifies it as a dog. Computer vision tries to teach computers to perform a similar process.

A computer does not see an image the way humans do. Instead, it sees an image as numbers representing pixel values. Each pixel has intensity or color values. Computer vision algorithms analyze these values to detect patterns such as edges, textures, shapes, and objects. By processing this information, the system can recognize what the image contains.

**For example** If a computer vision system is given an image of a car, it analyzes the pixels, finds edges and shapes, and compares them with patterns it has learned during training. After this analysis, the system can recognize that the object in the image is a car.

Because of this ability to analyze visual information, computer vision is widely used in many modern technologies such as facial recognition systems, medical image analysis, and autonomous vehicles.  

Humans understand the world not only by seeing objects but also by interpreting their meaning and context. Cognitive computing tries to give machines similar capabilities. When computer vision provides visual information from images or videos, cognitive computing systems analyze that information and combine it with reasoning and knowledge to make intelligent decisions.

**For example** a computer vision system might detect that a person is holding an umbrella and the sky is cloudy. A cognitive computing system can analyze this information and infer that it might be raining or about to rain. This shows how visual perception and intelligent reasoning work together.

## Why We Study Computer Vision
We study computer vision because a large amount of information in the world is **visual**, and we wants computers have ability to understand that information automatically. Images and videos contain valuable data, but without computer vision, computers cannot interpret them in a meaningful way.

**1) Automation** 
Many tasks that require human observation can be automated using computer vision systems. For example, in manufacturing industries, cameras can inspect products and detect defects automatically. This improves speed, accuracy, and efficiency compared to manual inspection.

**2) Decision-Macking Systems**
Computer vision allows machines to analyze visual data and provide useful insights. For example, in medical imaging, computer vision helps doctors analyze X-rays, CT scans, and MRI images to detect diseases more accurately.

**3) Intelligent Systems that Interact with Real world**
Computer vision is also important because it helps build intelligent systems that interact with the real world. Technologies such as self-driving cars, security surveillance systems, and augmented reality rely on computer vision to understand their surroundings.

In computer vision, the input is usually an image or a video, and the system processes this visual data using mathematical models and algorithms. The goal is not only to capture images but also to extract meaningful information from them. This means the computer should be able to detect objects, recognize people, understand shapes, analyze movements, and sometimes even reconstruct the 3-dimensional structure of a scene. 


## Applications of Computer Vision
Computer vision is used in many real-world applications across different industries.

### Autonomous Vehicles
Self-driving cars use computer vision to detect roads, traffic signs, pedestrians (people), and other vehicles. The system processes images from cameras and makes decisions about steering, braking, and navigation. Companies such as **Tesla** use computer vision technology in their autonomous driving systems. Others examples, smart car, safety features in many cars, self driving cars.

### Face Detection
Face detection is a computer vision technique that focuses on identifying the presence and location of human faces in an image or video. The system scans the entire image and determines whether a face exists and where it is located. The purpose of face detection is not to identify who the person is, but simply to detect that a face is present. Once the face is detected, it is usually marked with a bounding box around the face region.

### Face Recognition And Security Systems
Face analysis and recognition go a step further than face detection. Computer vision systems can detect and recognize human faces from images or videos. This technology is used in smartphones for unlocking devices and in security systems for identifying people.

### Health Care
Doctors use computer vision techniques to analyze medical images like X-rays and MRI scans to detect diseases such as tumors, fractures, or infections. These systems assist doctors in diagnosing medical conditions more quickly and accurately.

### Retail and E-Commerce
Computer vision helps with tasks like product recognition, automated checkout systems, and inventory management. Cameras can track products on shelves and analyze customer behavior inside stores.

### Surveillance and Security Monitoring
Computer vision systems analyze video footage to detect suspicious activities, track people, and monitor public areas for safety.

### Image Search and Social Media Platforms
Platforms such as Google use computer vision to allow users to search for images and automatically organize photos. 




## Vision-Based Biometrics
Vision-based biometrics refers to identifying or verifying individuals using biological features that are captured through images or cameras. Biometric systems use unique physical characteristics of a person to recognize them.

**Examples of vision-based biometric features include:**
- Face recognition
- Iris recognition
- Retina scanning
- Fingerprint recognition

These systems are widely used in security, authentication, and access control systems. Since biometric features are unique to each individual, they provide a reliable method of identification.  



## Special Effects: Shape Capture & Motion Caption
Shape capture is a computer vision technique used to **capture and reconstruct the shape of objects or people from images or video data**. The system analyzes visual information from cameras and calculates the geometric structure of the object.

In the film and gaming industries, shape capture is used to create **realistic digital models** of objects or human bodies. This allows developers to build detailed 3D models that can be used in animations, video games, and visual effects.

**For example** when a movie creates a digital character that moves exactly like a real actor, computer vision techniques such as shape capture are used to record the actor’s body shape and motion.


## 3D Face Tracking with Consumer Cameras
3D face tracking is a technique where computer vision systems **track the position, movement, and orientation of a person's face in three-dimensional space** using regular cameras.

Unlike simple face detection, 3D face tracking can understand how the face moves in different directions such as turning, tilting, or moving forward and backward. The system continuously analyzes frames from the camera to track the face over time.

This technology is widely used in:

* Augmented reality filters
* Animation and gaming
* Virtual reality systems
* Facial motion capture for movies

Even consumer devices such as smartphones and webcams can perform basic 3D face tracking using advanced computer vision algorithms.


## Virtual Reality and Augmented Reality
Computer vision also plays an important role in immersive technologies such as Virtual Reality and Augmented Reality.

**Virtual reality** creates a completely digital environment where users can interact with simulated objects and scenes. Computer vision helps track the user’s head and body movements so the virtual environment changes accordingly.

**Augmented reality** combines real-world images with digital information. For example, when using an AR mobile application, the camera captures the real-world scene, and computer vision identifies surfaces or objects. The system then overlays virtual elements on top of the real environment.

A common example is the game Pokémon GO, where virtual characters appear in real-world locations through a smartphone camera.


## Challenges in Computer Vision
In Computer Vision, understanding images is difficult because the real world is very complex. Humans can easily recognize objects in different situations, but for a computer this is challenging because the appearance of objects can change in many ways. 

### Viewpoint Variation
Viewpoint variation means that an object can look very different when it is seen from different angles.

**For example,** imagine a car. If you look at the car from the front, you will see headlights and the grille. If you look at it from the side, you will see the doors and wheels. If you see it from above, it will look completely different.

Humans can easily understand that all these views represent the same object, but for a computer vision system it is difficult because the **shape and appearance of the object change depending on the viewing angle**.

### Scale Variation
Scale variation means that the **size of an object in an image can change depending on the distance from the camera**.

**For example,** if a person is standing very close to the camera, the person will appear very large in the image. If the same person is far away, the person will appear very small.

Even though it is the same person, the computer vision system must recognize the object at both large and small sizes, which makes the task difficult.

### Illumination Variation
Illumination means the **lighting condition of the scene**. Lighting can change the appearance of objects in an image.

**For example,** a white car may look bright during the daytime but may appear darker at night or in shadow. Similarly, indoor lighting, sunlight, or street lights can all change the color and brightness of objects.

Because of these lighting changes, the same object can look very different in different images.

### Intra-Class Variation
Intra-class variation means that **objects belonging to the same category can look very different from each other**.

**For example,** consider the category "dog". There are many different types of dogs. Some are large, some are small, some have long hair, and some have short hair. Their colors and shapes can also be different.

Even though they all belong to the same class (dog), their appearances vary a lot. This makes it difficult for a computer vision system to correctly identify them.

### Motion
Motion refers to movement of objects or the camera during image capture.

**For example,** if a car is moving very fast while a camera takes a picture, the image may become blurred. This is called motion blur.

Because the image is blurred, it becomes harder for the computer vision system to clearly detect and recognize the object.

### Occlusion
Occlusion happens when **part of an object is hidden by another object**.

**For example,** if a person is standing behind a tree, only part of the person may be visible in the image. The computer vision system must still recognize the person even though some parts are hidden.

Another example is a crowd of people where one person may partially block another person.

### Background Clutter
Background clutter means the **background contains many objects or patterns that make it difficult to detect the main object**.

**For example,** if you try to detect a red apple placed on a plain white table, it is very easy. But if the apple is placed in a fruit market with many fruits of similar colors, it becomes harder to identify the apple.

The computer vision system may confuse the object with the background because there are many similar visual patterns.

### Local Ambiguity
Local ambiguity occurs when **a small part of an image looks similar to something else**, making it difficult to identify the object correctly.

**For example,** a close-up image of a small circular object could be a coin, a button, or a bottle cap. If the system only sees that small region, it may not know what the object really is.

To understand the object correctly, the system needs more context from the surrounding image.  

### Noise and Image Quality
Sometimes images captured by cameras are blurry, grainy, or low resolution. For example, a security camera at night may produce a noisy image where objects are not clearly visible. This makes it difficult for the system to correctly detect or recognize objects.

### Deformation
Some objects change their shape depending on movement or position. For example, a human body can appear very different when standing, sitting, running, or bending. Even though it is the same person, the visual appearance changes significantly, which makes recognition harder for a computer vision system.

### Real-Time Processing
Many applications such as self-driving cars or robots must analyze images very quickly. The system needs to process thousands of pixels and detect objects in milliseconds. Handling large amounts of visual data while maintaining accuracy is a major technical challenge.

### Context Understanding
Humans naturally understand the meaning of a scene. For example, if we see a person holding an umbrella, we may assume it is raining. However, a computer vision system might detect the person and the umbrella separately but may not easily understand the relationship between them.

### Dataset Bias*
If a model is trained on images from limited environments, it may not perform well in new conditions. 
**For example,** a system trained mostly on daytime images may struggle to detect objects at night.

