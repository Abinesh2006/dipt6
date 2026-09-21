# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** Abinesh M
- **Register No:** 212224040009

---

## Output
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('nature.jpeg') 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
<img width="949" height="619" alt="image" src="https://github.com/user-attachments/assets/d5ad45c9-07c9-4c60-9be9-fe3c55bfd87b" />

###  Sobel Edge Detector
```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
<img width="897" height="629" alt="image" src="https://github.com/user-attachments/assets/d4888430-4a68-44b1-876c-03fe17158dcf" />
```
<img width="896" height="620" alt="image" src="https://github.com/user-attachments/assets/5066bb06-a8cb-4c5b-a2dd-44444a023e04" />


###  Prewitt Edge Detector
```
image = cv2.imread("nature.jpeg")

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

prewitt_x = np.array([[-1, 0, -1],
                      [ 1, 0, -1],
                      [ 1, 0, -1]])

prewitt_y = np.array([[ 1,  1,  1],
                      [ 0,  0,  0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)

prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))

plt.imshow(prewitt, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')
plt.show()
```
<img width="964" height="574" alt="image" src="https://github.com/user-attachments/assets/7afebd58-87ea-4958-8a9d-e466653918b1" />

###  Roberts Edge Detector
```
roberts_x = np.array([[1, 0],
                      [0, -1]])

roberts_y = np.array([[0, 1],
                      [-1, 0]])

roberts_x_edge = cv2.filter2D(gray, -1, roberts_x)
roberts_y_edge = cv2.filter2D(gray, -1, roberts_y)

roberts = cv2.magnitude(
    roberts_x_edge.astype(np.float32),
    roberts_y_edge.astype(np.float32)
)

plt.imshow(roberts, cmap='gray')
plt.title('Roberts Edge Detection')
plt.axis('off')
plt.show()
```
<img width="989" height="594" alt="image" src="https://github.com/user-attachments/assets/2cd6b0d7-dc1c-4750-82cd-71abf74528a0" />


###  Laplacian Edge Detector
```
Laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)

plt.imshow(Laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```
<img width="974" height="567" alt="image" src="https://github.com/user-attachments/assets/86fc4828-e62b-4df6-af7d-ac5e20ab5ea9" />

###  Canny Edge Detector
```
Canny_edges = cv2.Canny(gray_image, 50, 150)

plt.imshow(Canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```
<img width="1011" height="574" alt="image" src="https://github.com/user-attachments/assets/fb65cfdc-122f-4b82-9ba5-884918676937" />

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
