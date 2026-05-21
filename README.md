# THRESHOLDING
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

### Step1:
<br>Import the required libraries (cv2, numpy, matplotlib) and read the input image in grayscale mode.

### Step2:
<br>Apply Global Thresholding techniques: Binary, Binary Inverse, To Zero, To Zero Inverse, and Truncate.

### Step3:
<br>Apply Otsu’s Thresholding method to automatically determine the optimal threshold value.

### Step4:
<br>Apply Adaptive Thresholding methods using Mean and Gaussian techniques.

### Step5:
<br>Store all processed images in a list and display the original image along with each thresholded result using Matplotlib.

## Program
```
#NAME :
#REF NO :

# Load the necessary packages
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the Image and convert to grayscale

# READ THE IMAGE USING IMREAD
# CONVERT THE COLOR FROM BGR TO RGB
image = cv2.imread("DUCK.jpg")
image_gray = cv2.imread("DUCK.jpg",0)

# Use Global thresholding to segment the image
ret, thresh_dipt1 = cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY)
ret, thresh_dipt2 = cv2.threshold(image_gray,86,255,cv2.THRESH_BINARY_INV)
ret, thresh_dipt3 = cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO)
ret, thresh_dipt4 = cv2.threshold(image_gray,86,255,cv2.THRESH_TOZERO_INV)
ret, thresh_dipt5 = cv2.threshold(image_gray,100,255,cv2.THRESH_TRUNC)

# Use Adaptive thresholding to segment the image
ret, thresh_dipt6 = cv2.threshold(image_gray,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# Use Otsu's method to segment the image
thresh_dipt7 = cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_MEAN_C,
                                     cv2.THRESH_BINARY,11,2)

thresh_dipt8 = cv2.adaptiveThreshold(image_gray,255,cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
                                     cv2.THRESH_BINARY,11,2)

# Display the results
titles = ["Gray Image",
          "Threshold Image (Binary)",
          "Threshold Image (Binary Inverse)",
          "Threshold Image (To Zero)",
          "Threshold Image (To Zero-Inverse)",
          "Threshold Image (Truncate)",
          "Otsu",
          "Adaptive Threshold (Mean)",
          "Adaptive Threshold (Gaussian)"]

images = [image_gray, thresh_dipt1, thresh_dipt2, thresh_dipt3,
          thresh_dipt4, thresh_dipt5, thresh_dipt6,
          thresh_dipt7, thresh_dipt8]

for i in range(0,9):
    plt.figure(figsize=(10,10))

    plt.subplot(1,2,1)
    plt.title("Original Image")
    plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
    plt.axis("off")

    plt.subplot(1,2,2)
    plt.title(titles[i])

    if len(images[i].shape) == 2:
        plt.imshow(images[i], cmap='gray')
    else:
        plt.imshow(cv2.cvtColor(images[i], cv2.COLOR_BGR2RGB))

    plt.axis("off")
    plt.show()

```
## Output

### Original Image

<img width="908" height="409" alt="image" src="https://github.com/user-attachments/assets/4e3318ad-6298-4b8e-b3c7-ded3511c258d" />


### Global Thresholding
<br>
<br><img width="794" height="353" alt="download" src="https://github.com/user-attachments/assets/a9a859bb-b873-4929-a46d-01429583896f" />
<img width="794" height="353" alt="download" src="https://github.com/user-attachments/assets/a8ea3d8f-8038-410c-8a18-f9284f7b1798" />
<img width="794" height="353" alt="download" src="https://github.com/user-attachments/assets/f96e84ad-3f9c-48ab-bb46-bccda47e15bb" />
<img width="794" height="353" alt="download" src="https://github.com/user-attachments/assets/660c0642-7ef1-4801-8e19-8501e3813ad8" />
<img width="448" height="414" alt="image" src="https://github.com/user-attachments/assets/a33c5921-c382-4f01-b19b-cbf5f3d7a780" />

<br>
<br>
<br>

### Adaptive Thresholding
<br><img width="909" height="409" alt="image" src="https://github.com/user-attachments/assets/454c19f3-e7c6-41b2-b596-ccc39f060d96" />

<br><img width="945" height="424" alt="image" src="https://github.com/user-attachments/assets/2b582984-da7c-4638-b838-e43b5652f92f" />

<br>
<br>
<br>

### Optimum Global Thesholding using Otsu's Method
<br>
<br><img width="950" height="421" alt="image" src="https://github.com/user-attachments/assets/33740602-4aba-4d9c-9cc6-544607d9b2d7" />

<br>
<br>
<br>


## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
