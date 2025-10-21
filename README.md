# Implementation-of-filter
## Aim:
To implement filters for smoothing and sharpening the images in the spatial domain.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1
Import the required libraries.

### Step2
Convert the image from BGR to RGB.

### Step3
Apply the required filters for the image separately.

### Step4
Plot the original and filtered image by using matplotlib.pyplot.

### Step5
End the program. 

## Program:
### Developed By   : SOMALARAJU ROHINI
### Register Number: 212224240156


### 1. Smoothing Filters
```
import cv2
import numpy as np
from google.colab.patches import cv2_imshow  # For image display
# Load the image
image = cv2.imread("My pic.jpeg")
if image is None:
    raise ValueError("Image not found. Check the file path.")
# Resize to smaller dimensions
resized = cv2.resize(image, (400, 300))
# ------------------ Original Image ------------------
print("Displaying Original Image:")
cv2_imshow(resized)
```
i) Using Averaging Filter
```Python

# ------------------ 1. Averaging Filter ------------------
average_blur = cv2.blur(resized, (5, 5))
print("Displaying Average Filter Output:")
cv2_imshow(average_blur)


```
ii) Using Weighted Averaging Filter
```Python


# ------------------ 2. Weighted Averaging Filter ------------------
kernel = np.array([[1, 2, 1],
                   [2, 4, 2],
                   [1, 2, 1]], dtype=np.float32)
kernel /= np.sum(kernel)
weighted_blur = cv2.filter2D(resized, -1, kernel)
print("Displaying Weighted Average Filter Output:")
cv2_imshow(weighted_blur)


```
iii) Using Gaussian Filter
```Python

# ------------------ 3. Gaussian Filter ------------------
gaussian_blur = cv2.GaussianBlur(resized, (5, 5), 0)
print("Displaying Gaussian Filter Output:")
cv2_imshow(gaussian_blur)



```
iv)Using Median Filter
```Python

# ------------------ 4. Median Filter ------------------
median_blur = cv2.medianBlur(resized, 5)
print("Displaying Median Filter Output:")
cv2_imshow(median_blur)



```

### 2. Sharpening Filters
i) Using Laplacian Linear Kernal
```Python
gray = cv2.cvtColor(image_small, cv2.COLOR_BGR2GRAY)

# ------------------ 1. Sharpening with Laplacian Linear Kernel ------------------
laplacian_kernel = np.array([[0, -1, 0],
                             [-1, 5, -1],
                             [0, -1, 0]], dtype=np.float32)

sharpened_kernel = cv2.filter2D(image_small, -1, laplacian_kernel)
print("Displaying Sharpened Image using Laplacian Linear Kernel:")
cv2_imshow(sharpened_kernel)




```
ii) Using Laplacian Operator
```Python
laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = cv2.convertScaleAbs(laplacian)

# Convert grayscale Laplacian to 3-channel
laplacian_color = cv2.merge([laplacian] * 3)

# Add Laplacian details back to the original image
sharpened_operator = cv2.addWeighted(image_small, 1.0, laplacian_color, 1.0, 0)
print("Displaying Sharpened Image using Laplacian Operator:")
cv2_imshow(sharpened_operator)




```

## OUTPUT:
### 1. Smoothing Filters


<img width="503" height="403" alt="Screenshot 2025-10-21 143145" src="https://github.com/user-attachments/assets/509b5054-a3bf-48b2-a0f0-e743e50f3e75" />







i) Using Averaging Filter




<img width="505" height="410" alt="Screenshot 2025-10-21 143151" src="https://github.com/user-attachments/assets/da5f7e27-8a26-49ec-b5a1-3a40b3b9d183" />


ii)Using Weighted Averaging Filter




<img width="498" height="400" alt="Screenshot 2025-10-21 143156" src="https://github.com/user-attachments/assets/1bfea8be-346f-427f-8653-fb6fdb853e12" />


iii)Using Gaussian Filter




   <img width="495" height="403" alt="Screenshot 2025-10-21 143201" src="https://github.com/user-attachments/assets/fa70c494-163d-4775-848a-a42e9ab09c08" />


iv) Using Median Filter




<img width="502" height="405" alt="Screenshot 2025-10-21 143206" src="https://github.com/user-attachments/assets/e66f2850-b17e-4720-9f09-df45f0fc9bbb" />


### 2. Sharpening Filters
</br>

i) Using Laplacian Kernal





<img width="556" height="281" alt="Screenshot 2025-10-21 143733" src="https://github.com/user-attachments/assets/df45e736-a60a-4d29-a9bc-7637c7973cac" />


ii) Using Laplacian Operator




<img width="577" height="287" alt="Screenshot 2025-10-21 143740" src="https://github.com/user-attachments/assets/5451af80-1cca-4c07-85b9-f42bac0f6299" />


## Result:
Thus the filters are designed for smoothing and sharpening the images in the spatial domain.
