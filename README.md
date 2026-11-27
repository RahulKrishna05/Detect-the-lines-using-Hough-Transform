## EX:07-Record-HOUGH TRANSFORM
## NAME: Rahul Krishna S
## REG.NO: 212223040162
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('R.jpg')  # Replace 'image.jpg' with your image path

# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')

<img width="431" height="410" alt="881ff0f7-a3a1-473e-a222-2fb0d960afed" src="https://github.com/user-attachments/assets/49c7ea48-d5e8-4c8f-8e87-c7c47ebc2ecb" />

plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')

<img width="431" height="410" alt="3dd26d95-d9d6-4c57-8b92-cbff67af5ac1" src="https://github.com/user-attachments/assets/793cf777-080f-4dcb-a5c3-e73e22d7cdd2" />

# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150

# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')

<img width="431" height="410" alt="493175fe-5437-4c6b-8539-414b8037c7ac" src="https://github.com/user-attachments/assets/eaba0954-bc80-41e1-ad89-c3fe5e25f81b" />


# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 100, minLineLength=50, maxLineGap=10)

# Step 6: Using a for loop, draw the lines on the original image using the detected coordinates
# The lines variable contains the endpoints of the detected lines
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line.flatten()  # Unpacking the line coordinates
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)  # Draw green lines with thickness of 2

# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Image with lines drawn
plt.title("Result of Hough Transform")
plt.axis('off')

<img width="431" height="410" alt="174902ae-c511-41ae-b799-3a268c718cf0" src="https://github.com/user-attachments/assets/5a8df1ff-fc99-47ba-93f3-a66eca6a127c" />
