# CV
OpenCV Image Processing

This project demonstrates basic image processing operations using OpenCV (cv2) and Matplotlib in Python. It is suitable for beginners learning how to read, modify, transform, and display images.

📌 Features

The notebook covers:

Installing OpenCV
Importing OpenCV
Checking the OpenCV version
Reading and displaying images
Checking pixel values
Editing image colors
Resizing images
Rotating images
Flipping images
Cropping images
Saving processed images
🛠️ Technologies Used
Python
OpenCV (opencv-python)
Matplotlib
Jupyter Notebook / Google Colab
📦 Installation

Install OpenCV and Matplotlib using pip:

pip install opencv-python matplotlib
🚀 Usage

Import the required libraries:

import cv2
import matplotlib.pyplot as plt
1. Check OpenCV Version
print(cv2.__version__)
2. Read and Display an Image

OpenCV reads images in BGR format, while Matplotlib expects RGB. Therefore, the image is converted before displaying.

image = cv2.imread('/content/meow.png', cv2.IMREAD_COLOR)

if image is None:
    print('Image not found or unable to load')
else:
    print('Image Loaded Successfully!')

    image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

    plt.imshow(image_rgb)
    plt.axis('off')
    plt.show()
3. Check Pixel Values

You can access the BGR values of an individual pixel using its coordinates.

pixel = image[100, 50]
print("Pixel value at (100, 50):", pixel)

For a color image:

blue = image[100, 50, 0]
green = image[100, 50, 1]
red = image[100, 50, 2]

print(f"Blue: {blue}, Green: {green}, Red: {red}")

Note: OpenCV uses BGR, not RGB, by default.

4. Edit Image Colors

A rectangular region of an image can be modified using NumPy slicing.

image[50:100, 100:200] = [255, 255, 255]

cv2.imwrite("modified_image.jpg", image)

This example changes the selected region to white.

5. Resize an Image
resized_image = cv2.resize(image, (500, 300))

cv2.imwrite("resized_image.jpg", resized_image)

resized_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

plt.imshow(resized_rgb)
plt.axis("off")
plt.title("Resized Image")
plt.show()
6. Rotate an Image

The image can be rotated using a rotation matrix.

h, w = image.shape[:2]
angle = 45

center = (w // 2, h // 2)

rotation_matrix = cv2.getRotationMatrix2D(center, angle, 1.0)

rotated_image = cv2.warpAffine(
    image,
    rotation_matrix,
    (w, h)
)

cv2.imwrite("rotated_image.jpg", rotated_image)

The same approach can be used with different angles such as:

angle = 90
angle = 180
7. Flip an Image

OpenCV provides cv2.flip() for flipping images.

flipped_horizontally = cv2.flip(image, 1)
flipped_vertically = cv2.flip(image, 0)
flipped_both = cv2.flip(image, -1)

The flip codes are:

Code	Operation
1	Horizontal flip
0	Vertical flip
-1	Horizontal + Vertical flip
8. Crop an Image

Images can be cropped using NumPy slicing.

cropped_image = image[50:250, 100:400]

cv2.imwrite("cropped_image.jpg", cropped_image)

cropped_rgb = cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB)

plt.imshow(cropped_rgb)
plt.axis("off")
plt.title("Cropped Image")
plt.show()

The general format is:

image[y_start:y_end, x_start:x_end]
📁 Example Project Structure
OpenCV-Image-Processing/
│
├── meow.png
├── modified_image.jpg
├── resized_image.jpg
├── rotated_image.jpg
├── flipped_horizontal.jpg
├── flipped_vertical.jpg
├── flipped_both.jpg
├── cropped_image.jpg
├── image_processing.ipynb
└── README.md
🎯 Learning Outcomes

After completing this project, you will understand how to:

Load and save images using OpenCV
Work with BGR and RGB color formats
Access individual pixel values
Modify image regions
Resize images
Rotate images
Flip images
Crop images
Display images using Matplotlib
