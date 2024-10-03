# VisionImages
Given images of an orange ball at random depths, and next to random objects, I identified only the ball in the result image. 

Initially used an RGB color space, but realized that the boundaries of "orange" color included objects other than the ball. Changed the color space to HSV, which allowed me to get the ball in different orange hues, saturations, and lightings. Iterated through every pixel in the image, and determined if it met the minimum threshold of orange, and only showed those pixles in the resulting image. 
