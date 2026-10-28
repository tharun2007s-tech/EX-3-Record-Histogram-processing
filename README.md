# EX-3-Record-Histogram-processing

# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

---

## Program

Developed By:
Name: Tharun S

Register No:
212225240174

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Read the image in grayscale
```
gray = cv2.imread('Cattt.jpg', cv2.IMREAD_GRAYSCALE)

if gray is None:
    print("Error: Image not found. Check the file path.")
else:
```
# Step 2: Display grayscale image and histogram
```
    plt.figure(figsize=(10, 8))

    plt.subplot(2, 2, 1)
    plt.imshow(gray, cmap='gray')
    plt.title('Original Grayscale Image')
    plt.axis('off')

    plt.subplot(2, 2, 2)
    plt.hist(gray.ravel(), 256, [0, 256])
    plt.title('Original Histogram')
```
# Step 3: Apply histogram equalization
```
    equalized = cv2.equalizeHist(gray)

    plt.subplot(2, 2, 3)
    plt.imshow(equalized, cmap='gray')
    plt.title('Equalized Image')
    plt.axis('off')

    plt.subplot(2, 2, 4)
    plt.hist(equalized.ravel(), 256, [0, 256])
    plt.title('Equalized Histogram')

    plt.tight_layout()
    plt.show()
```
# Step 4: Read the image in color
```
    img = cv2.imread('Cattt.jpg', cv2.IMREAD_COLOR)

    if img is not None:
        # Step 5: Split B, G, R channels
        b, g, r = cv2.split(img)

        plt.figure(figsize=(12, 4))

        plt.subplot(1, 3, 1)
        plt.hist(b.ravel(), 256, [0, 256])
        plt.title('Blue Histogram')

        plt.subplot(1, 3, 2)
        plt.hist(g.ravel(), 256, [0, 256])
        plt.title('Green Histogram')

        plt.subplot(1, 3, 3)
        plt.hist(r.ravel(), 256, [0, 256])
        plt.title('Red Histogram')

        plt.tight_layout()
        plt.show()
```
# Step 6: Convert BGR to HSV
```
        hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```
# Step 7: Split HSV channels
```
        h, s, v = cv2.split(hsv)
```
# Step 8: Equalize the V channel
```
        v_eq = cv2.equalizeHist(v)
```
# Step 9: Merge channels and convert back to BGR
```
        hsv_eq = cv2.merge([h, s, v_eq])
        enhanced = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)
```
# Step 10: Display original and enhanced color images
```
        plt.figure(figsize=(10, 8))

        plt.subplot(2, 2, 1)
        plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
        plt.title('Original Color Image')
        plt.axis('off')

        plt.subplot(2, 2, 2)
        plt.hist(img.ravel(), 256, [0, 256])
        plt.title('Original Color Histogram')

        plt.subplot(2, 2, 3)
        plt.imshow(cv2.cvtColor(enhanced, cv2.COLOR_BGR2RGB))
        plt.title('Enhanced Color Image')
        plt.axis('off')

        plt.subplot(2, 2, 4)
        plt.hist(enhanced.ravel(), 256, [0, 256])
        plt.title('Enhanced Color Histogram')

        plt.tight_layout()
        plt.show()
```

##  Output

### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  

### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution

<img width="942" height="783" alt="Screenshot 2026-10-28 090757" src="https://github.com/user-attachments/assets/7764cd0b-3c0c-44a9-a6ab-7c26ae14fc32" />


---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
