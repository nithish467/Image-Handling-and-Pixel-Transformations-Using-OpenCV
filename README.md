# Image-Handling-and-Pixel-Transformations-Using-OpenCV 
## NAME : NITHISHKUMAR S
## REG NO : 212223240109
## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

### Ex. No. 01

#### 1. Read the image ('nithish.jpg'') using OpenCV imread() as a grayscale image.
```
import cv2
import matplotlib.pyplot as plt
# Read the image using OpenCV
img = cv2.imread('nithish.jpg', cv2.IMREAD_COLOR)
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

```

#### 2. Print the image width, height & Channel.
```python
bgr_img.shape
```

#### 3. Display the image using matplotlib imshow().
```python
# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
# Load the image
image = cv2.imread('Qno. 1.jpg')
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2) # cv2.line(image, start_point, end_point, color, thickness)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()
```

#### 7. Crop the image to extract any specific object from the image.
```python
crop = rgb_color_img[20:430,200:550] 
plt.imshow(crop[:,:,::-1])
plt.title("Cropped Region")
plt.axis("off")
plt.show()
crop.shape
```

#### 8. Resize the image up by a factor of 2x.
```python
res= cv2.resize(crop,(200*2, 200*2))
```

#### 9. Flip the cropped/resized image horizontally.
```python
flip= cv2.flip(res,1)
plt.imshow(flip[:,:,::-1])
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
img=cv2.imread('Apollo-11-launch.jpg',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = cv2.putText(img_rgb, "Apollo 11 Saturn V Launch, July 16, 1969", (300, 700),cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)  
plt.imshow(text, cmap='gray')  
plt.title("New image")
plt.show()  
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)  
```

#### 13. Display the final annotated image.
```python
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```python
img =cv2.imread('boy.jpg',cv2.IMREAD_COLOR)
img_rgb= cv2.cvtColor(img, cv2.COLOR_BGR2RGB) 
```

#### 15. Adjust the brightness of the image.
```python
# Create a matrix of ones (with data type float64)
# matrix_ones = 
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
#img_brighter = cv2.add(img, matrix)
#img_darker = cv2.subtract(img, matrix)
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m)  
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```

#### 18. Modify the image contrast.
```python
# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```

## Output:
**i)** Read and Display an Image.

1.Read 'nithish.jpg' as grayscale and display:  
<img width="240" height="487" alt="image" src="https://github.com/user-attachments/assets/e4a8f27e-9257-49b0-a62f-8b61eba2af4f" />

2.Image with line, Circle and Rectangle:  

<img width="240" height="470" alt="image" src="https://github.com/user-attachments/assets/96a031f7-1fdc-4b16-9198-af4193f1d44c" />

<img width="240" height="475" alt="image" src="https://github.com/user-attachments/assets/9e06c3dd-a91b-4723-ab84-1ddeee80ea20" />

<img width="240" height="480" alt="image" src="https://github.com/user-attachments/assets/1d4039f0-c19e-43ee-8810-3a5242f827ec" />

3. Image with Text:

<img width="240" height="482" alt="image" src="https://github.com/user-attachments/assets/c478cf55-c017-4dcf-971d-c1827df95654" />

4. Original RGB Image:

<img width="240" height="375" alt="image" src="https://github.com/user-attachments/assets/27b9a802-ba8d-4cbb-8d5f-3aca87e29fa5" />

5. HSV Image,Grayscale Image and YCrCb Image:

<img width="240" height="372" alt="image" src="https://github.com/user-attachments/assets/ce514f98-51b7-4728-b821-ef6ee2d82e5f" />

<img width="262" height="377" alt="image" src="https://github.com/user-attachments/assets/d6be6af2-ef56-4c8d-b2de-a112f89dfa9b" />

<img width="251" height="376" alt="image" src="https://github.com/user-attachments/assets/0d029a5f-99cf-47c2-8ef0-a1091059d468" />

6. HSV to RGB Image:
 
<img width="237" height="383" alt="image" src="https://github.com/user-attachments/assets/9b08f95d-04d3-4af2-a1f3-5afc23187f04" />

7. Image With 300 x 300 White Box:

<img width="235" height="382" alt="image" src="https://github.com/user-attachments/assets/a77daf56-ae6d-46a6-8c15-ce30d98e2fa4" />

8. Resized Image:

<img width="362" height="373" alt="image" src="https://github.com/user-attachments/assets/ae5031d7-aa76-477a-b1b2-ba2e8814e627" />

9. Cropped Region Of Interest (ROI) :

<img width="242" height="371" alt="image" src="https://github.com/user-attachments/assets/48c83045-6b62-413b-a349-7d4803434bb1" />

10. Flipped Image:

<img width="248" height="378" alt="image" src="https://github.com/user-attachments/assets/a099e53d-b446-4e79-bab2-fa65dd7c688d" />

<img width="236" height="373" alt="image" src="https://github.com/user-attachments/assets/dfae5706-213c-473a-ade1-2b2bd54cd95f" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

