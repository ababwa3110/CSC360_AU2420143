# Session 22 Reflection: Digital Image Processing, Spatial Filtering, Convolution, Edge Detection
**Date:** 29 October 2026

### 1. Digital Image Processing & Contrast
Image processing focuses on how computers analyze images to either improve visual quality or extract structural details for further analysis. A foundational property in this process is **contrast**—the difference between the lighter and darker regions of an image (where 8-bit grayscale pixel intensities range from $0$ for black to $255$ for white).
- **High contrast:** Objects stand out clearly and are easy to distinguish from the background.
- **Low contrast:** The image looks flat or dull, making it difficult to separate objects or identify clear boundaries.

**Connection to Java 2D:** In earlier `Graphics2D` sessions, RGB and color values were used only to set the appearance of individual shapes we drew. Image processing flips that around by analyzing and manipulating pixel intensity values numerically across an entire existing image.

### 2. Spatial Filtering & Convolution
Spatial filtering modifies an image by calculating a new value for each pixel based on the values of its surrounding neighbors. In convolution, a small matrix—called a **kernel**—slides across every pixel in the image to perform these calculations.

**Connection to Matrix Math:** Previously, we used matrices for mathematical and geometric transformations. Filtering shows how a small matrix can also be applied directly over pixel neighborhoods to change an image's appearance or highlight structural features.

Different filtering operations and kernel values produce completely different results:

| Filter Type | Purpose / Output Effect |
| :--- | :--- |
| **Median Filter** | Removes unwanted isolated noise while preserving edges |
| **Gaussian Filter** | Blurs the image and reduces general noise |
| **Sharpening Filter** | Accentuates fine details and makes boundaries more noticeable |
| **Sobel / Laplacian** | Highlights sudden intensity changes for edge detection |

### 3. Project Connection: Image Filtering with the Median Filter
This session connected directly to our own project on **image filtering**, where we used the **median filter**.
- **How it fits in:** Instead of just treating an image as a static picture, our project worked with pixel neighborhoods to clean up image quality.
- **Why the Median Filter:** While standard blurring filters (like Gaussian) smooth out noise by averaging pixels, the median filter looks at the surrounding pixel intensities in a neighborhood and replaces the center pixel with the median value. This makes it particularly effective at removing unwanted noise without overly blurring the sharp boundaries of objects.
- Seeing spatial filtering covered in class helped formalize the theory behind the exact noise-removal logic we implemented in our project.

### 4. Edge Detection & Segmentation
Edges occur where there is a sharp, sudden change in pixel intensity, which typically marks the boundary of an object. Common edge detection operators include **Sobel**, **Prewitt**, and **Canny**.

Unlike single-step filters, the **Canny edge detector** runs as a multi-stage pipeline where each step handles a specific problem to produce cleaner, more accurate boundaries:

```text
Noise Reduction  ->  Finding Gradients  ->  Thinning Edges  ->  Selecting Strong Edges
```

In addition to edge detection, **thresholding (such as Otsu's method)** helps segment an image by automatically selecting an optimal cutoff value to separate different regions (e.g., foreground objects vs. background).

### 5. End-to-End Workflow & Real-World Applications
All of the topics from this session form a connected computer vision pipeline:
```text
Analyze Contrast  ->  Clean & Enhance (Median / Spatial Filtering)  ->  Extract Boundaries (Edge Detection & Segmentation)
```

These techniques go beyond making photos look better—they allow computers to interpret what is present inside an image:
- **Noise Removal & Restoration (Our Project Focus):** Using filters like the median filter to clean up corrupted or noisy images before further viewing or analysis.
- **Medical Imaging:** Filtering and edge detection make tissue boundaries and subtle details in medical scans easier to identify.
- **Autonomous Vehicles:** Computer vision systems rely on filtering and edge detection to identify lane markings, road boundaries, and nearby obstacles.
- **Document Scanning:** Thresholding algorithms cleanly separate dark text from the paper background to make scanned documents clearer.

### Summary of Technical Points
- **Contrast** measures the difference between light and dark regions ($0$ to $255$ in 8-bit grayscale); good contrast is required to distinguish objects from their backgrounds.
- **Spatial filtering and convolution** move a small matrix (kernel) across pixel neighborhoods; changing the operation switches the output between noise removal (Median), blurring (Gaussian), sharpening, or edge detection (Sobel/Laplacian).
- **Project application:** Our project focused on **image filtering** using the **median filter** to eliminate unwanted noise by evaluating neighboring pixel intensities.
- **Edge detection** locates sudden pixel intensity shifts that mark object boundaries using operators like **Sobel**, **Prewitt**, and the multi-step **Canny** pipeline (noise reduction, gradient calculation, edge thinning, strong-edge selection).
- **Segmentation via Otsu's method** automates threshold selection to separate distinct regions in an image.
- **Core pipeline connection:** Combines earlier `Graphics2D` pixel/color concepts and matrix operations into practical computer vision workflows (image denoising, medical scans, self-driving lane detection, and document thresholding).
