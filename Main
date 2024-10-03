import matplotlib.pyplot as plt
import matplotlib.image as mpimg
import numpy as np
from google.colab.patches import cv2_imshow
from scipy.stats import multivariate_normal
import numpy as np
import cv2
import os

# Check whether the training images were successfully imported
train_image = mpimg.imread('/content/train_images/106.jpg')
plt.imshow(train_image)
plt.axis("off")
plt.show()

# Read in training images
image_paths = ['/content/train_images/' + item for item in os.listdir('/content/train_images')]
all_orange_pixels = []
total_num_pixels = 0

# Iterate over training images to extract orange pixels using masks
for path in image_paths:
  train_image = cv2.imread(path)
  total_num_pixels += train_image.size
  hsv_train_image = cv2.cvtColor(train_image, cv2.COLOR_BGR2HSV)

  orange_lower_bound = np.array([5, 145, 145])
  orange_upper_bound = np.array([30, 255, 255])

  mask = cv2.inRange(hsv_train_image, orange_lower_bound,orange_upper_bound)
  result = cv2.bitwise_and(train_image,train_image,mask=mask)
  print(path)
  cv2_imshow(train_image)
  cv2_imshow(result)
  all_orange_pixels.append(train_image[mask > 0])

# Compute mean and covariance using MLE(Maximum Likelihood Estimation)
all_orange_pixels = np.vstack(all_orange_pixels)
mean = np.mean(all_orange_pixels, axis=0)
cov = np.cov(all_orange_pixels.T)

# Compute PDF(Probability Density Function) of single gaussian model
guassian = multivariate_normal(mean, cov)

# Set parameters (threshold, prior)
threshold = .000000000001
prior = all_orange_pixels.size/total_num_pixels

# Send test images into algorithm to detect orange ball
def find_mask(path):
  test_image = cv2.imread(path)
  rows, cols, _ = test_image.shape

  mask = np.zeros((rows, cols), dtype=np.uint8)

  for i,row in enumerate(test_image):
    for j,pixel in enumerate(row):
      probability = guassian.pdf(pixel) * prior

      if probability > threshold:
        mask[i][j] = 255
  return mask

# Result
image_paths = ['/content/test_images/' + item for item in os.listdir('/content/test_images')]
image_paths.sort()
for path in image_paths:
  print(path)
  cv2_imshow(find_mask(path))
