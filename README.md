# VisionImages
Given images of an orange ball at random depths, and next to random objects, I identified only the ball in the result image. 

Initially used an RGB color space, but realized that the boundaries of "orange" color included objects other than the ball. Changed the color space to HSV, which allowed me to get the ball in different orange hues, saturations, and lightings. Iterated through every pixel in the image, and determined if it met the minimum threshold of orange, and only showed those pixles in the resulting image. 

# Example image from tests:

![2](https://github.com/user-attachments/assets/14be0f71-3bb1-4d94-bda6-473913a35a81)
![image](https://github.com/user-attachments/assets/b69eb1c9-a693-4c97-b1e1-7f8a583dd430)

# Example image from training:
![image](https://github.com/user-attachments/assets/2faf94f3-f1a8-49f7-b3b1-655901e5cda7)
![image](https://github.com/user-attachments/assets/9b21f889-ad53-4218-80a6-2e97c93a454e)
