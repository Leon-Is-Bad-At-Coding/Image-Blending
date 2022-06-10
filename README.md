# Image-Blending

Image blending is the process of taking two images and combining them smoothly. It’s different than just combining images because in image blending, the output image should be seamless and have no sharp edges.

![image](https://user-images.githubusercontent.com/84482670/172959789-8e835903-7293-4642-97fd-14e68ccbf1d6.png)



The inputs of the algorithm are the two images being combined, and the mask (the layout of the output image). The output is a single blended image. 


The gaussian pyramid is an image consisting of multiple downsampled copies of the same image. To generate a gaussian pyramid, the image is smoothed and downsampled until the inputed level is reached.


This is an example of a gaussian pyramid:
![image](https://user-images.githubusercontent.com/84482670/172961251-b7611f0a-e6ce-4e69-8848-19bb8d53cc61.png)




Downsampling an image is when certain pixels are removed to make the image smaller, but still retaining the overall image.To smooth an image, every pixel becomes the average of the surrounding pixels. Smoothing takes away sharp edges and makes it better when downsampled. If you downsample an image without smoothing it first, the output image becomes aliased and looks very pixelated. The convolution operation is a function that smooths an image by taking the weighted average of surrounding pixels within the kernel size. The kernel is the size around the pixel that is being averaged and the weight of each pixel. Bigger kernels result in smoother images.

![image](https://user-images.githubusercontent.com/84482670/172961942-9e6c455f-05e3-49da-9542-715e0d3e695e.png)





The laplacian pyramid is the difference between a gaussian pyramid image and the upsampled version of the level before it.To generate a laplacian pyramid image, first a gaussian pyramid is created. Then, the gaussian pyramid one level before is upsampled and subtracted from the current gaussian image. 


Here is an example of a lapplacian pyramid
![image](https://user-images.githubusercontent.com/84482670/172961395-1939c239-15a4-4b4d-b862-21ec2f671ef0.png)



Upsampling an image is making an image bigger by adding more pixels. For every pixel, a new one is created by averaging the pixels around it. 


To combine two images, a black and white mask is used. The mask is the template for the blended image and can be any shape. To use a mask, you assign all the pixels of one image to the white portion of the mask, and the pixels of the other image to the black portion.

This is an example of a circular mask.
![image](https://user-images.githubusercontent.com/84482670/172963354-8c3adef9-b33a-46b7-88f7-f2698706fc62.png)




Here are the steps to the algorithm:
1. Make 2 lapplacian pyramids for both images
2. Make a gaussian pyramid for the mask
3. Combine the 2 lapplacian pyramids by using nodes of the gaussian pyramid as weights
4. Collapse the combined lapplacian pyramid to get the final output
