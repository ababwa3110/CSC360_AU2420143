Session 24 - Project Kickoff - Grayscale Contrast Enhancement Filter
Session Date: 05/11/26
Session Content
Session 24 was another project session, similar to Sessions 12 to 14. There was no lecture or presentation. The entire class was dedicated to work on our group projects, and the professor visited each group individually to discuss our progress, clear doubts, and guide us on how to approach the assigned topic.

Unlike our earlier project, where we were developing an application, this project focuses more on understanding and demonstrating a specific image-processing concept. My project is titled Grayscale Contrast Enhancement Filter. It involves developing a Java program that improves the contrast of a grayscale image using three different methods: contrast stretching, histogram equalization, and gamma correction.

The program first converts a colour image into 8-bit grayscale if required. It then builds a 256-entry lookup table based on the selected enhancement method and replaces each pixel with its corresponding value from the table. Finally, the processed image is saved as a PNG file. Each method works differently: contrast stretching expands the used range of gray levels to cover 0 to 255, histogram equalization redistributes gray levels using the image histogram, and gamma correction brightens or darkens the image using a power curve.

During the professor's visit, we discussed the project requirements and how to approach the implementation. After the discussion, I started looking into the concepts and the working of the different contrast enhancement techniques so that I could understand the logic before working further on the code.

What Else I Remember
The professor's individual check-ins were useful because they gave each group an opportunity to discuss its project and get guidance. It also reminded me that understanding the assigned topic is important before starting the implementation.

One thing I found interesting about my project is that all three methods aim to improve an image, but they do it in different ways. Contrast stretching focuses on expanding the intensity range, histogram equalization uses the distribution of pixel intensities, and gamma correction changes brightness through a mathematical curve. The project also connects with the earlier image-processing topics we studied, especially histograms, grayscale images, and image enhancement.

What I Understood Well
I understood the overall workflow of my project. Since a grayscale image has 256 possible intensity values, ranging from 0 (black) to 255 (white), a lookup table can be created with 256 entries. Each entry represents the new intensity value that should replace an existing pixel value.

I also understood why converting a colour image into grayscale is the first step. The three enhancement methods are designed to work on grayscale intensity values, so converting the image first ensures that the same processing can be applied to every pixel.

The three methods also have different purposes. Contrast stretching is useful when an image uses only a small portion of the available intensity range. Histogram equalization uses the histogram to improve the distribution of intensity values, while gamma correction can be used to make an image brighter or darker depending on the selected gamma value. Understanding these differences will help me explain why the program supports three separate methods instead of just one.

Connections to Prior Sessions
This project connects directly to Session 22, where we studied image contrast, histograms, histogram equalization, convolution, and edge detection. Histogram equalization was already introduced in that session, and now I get to explore it through an actual Java implementation. The idea of improving contrast also builds on what we learned about how pixel intensity values affect the appearance of an image.

It also connects to Session 23, where we discussed how pixels are represented in memory using RGB and RGBA values. My project takes this further by converting colour images into grayscale and working with 8-bit intensity values instead of separate colour channels. Each grayscale pixel has a value between 0 and 255, which makes it possible to process the image using a lookup table.

Session 2 also connects to this project because we discussed raster graphics and how images are made up of pixels. Since my project processes the intensity value of each pixel, understanding how raster images are represented is important.

The way this session was conducted also reminded me of Sessions 12 to 14, where the professor visited each group during project time. However, this time the focus is on implementing and demonstrating image-processing techniques rather than developing a complete application.

Real-World Applications Explored
Contrast enhancement is useful in many areas where images need to be clearer and easier to analyse. For example, in medical imaging, improving contrast can help make certain details in X-rays or other grayscale images more visible. It can also be useful in satellite images, old photographs, document scanning, and low-light photography.

The three techniques have different practical uses. Contrast stretching can improve images where most pixel values are concentrated within a narrow range. Histogram equalization can help reveal details in images with poor contrast by redistributing intensity levels. Gamma correction is useful when an image appears too dark or too bright and needs adjustment.

Working on this project will help me understand how these techniques are used in actual image-processing applications rather than only studying their theory.

Insights
What I found interesting about this session is that a relatively small program can make a noticeable difference in how an image looks. Before studying image processing, I mostly thought of contrast enhancement as simply making an image brighter or darker. Now I understand that different mathematical techniques can be used to change pixel intensity values in different ways.

I also realised that implementing a concept is a good way to understand it properly. Reading about histogram equalization or gamma correction gives a basic idea, but actually applying these methods to an image and comparing the results makes the concepts easier to understand. I think this project will help me connect the theory from earlier sessions with practical coding.

Key Takeaways
Session 24 was a project session where the professor met each group individually to discuss progress and guide us on the assigned topics.
My project, Grayscale Contrast Enhancement Filter, is a Java program that improves grayscale images using contrast stretching, histogram equalization, and gamma correction.
The program converts colour images into grayscale, creates a 256-entry lookup table, updates the pixel values, and saves the final image as a PNG.
Each enhancement method works differently, so comparing their results will help demonstrate their individual purposes and effects.
The project connects directly to earlier sessions on grayscale images, pixel representation, histograms, and image enhancement. It will help me understand these concepts better by applying them through code.
