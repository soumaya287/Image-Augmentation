# Image-Augmentation
What is the concept behind Image Augmentation
There are many things to consider when creating a custom detector and one of them is the image dataset. For example, if we were to have this type of dog recognized:
![image](https://user-images.githubusercontent.com/81196476/178696274-fa458f0c-ec18-4a35-8482-a7826779ec4e.png)
we must have as many images as possible and as diverse as possible because having only front dogs in the dataset (in the same position), the algorithm will only recognize this. A dog slightly rotated or positioned in reverse would not be recognized.

For this reason, it is necessary to use a library or code for augmenting the image. With some modifications, we generate new images with light changes, cut a part of the image, enlargements, rotations, color changes, and much more. Generally, 5 or 6 types are generated.
How to implement from scratch Image augmentation with Imgaug
There are various methods to augment images but we will use a python library called imgaug. To install, open the terminal and run the command:

pip install imgaug
If you don’t get any errors, everything has been installed correctly.

import libraries
Let’s open up our python editor and import the libraries needed to get started.

import imgaug.augmenters as iaa
import cv2
import glob
Load the dataset
We open the folder in which the images are contained and add the extracted links into an array called images[]

# 1. Load Dataset
images = []
images_path = glob.glob("images/*.jpg")
for img_path in images_path:
    img = cv2.imread(img_path)
    images.append(img)
Image Augmentation
Let’s prepare the function to apply these filters almost randomly and to each photo:
Flip
Affine
Multiply
LinearContrast

# 2. Image Augmentation
augmentation = iaa.Sequential([
    # 1. Flip
    iaa.Fliplr(0.5),
    iaa.Flipud(0.5),
    # 2. Affine
    iaa.Affine(translate_percent={"x": (-0.2, 0.2), "y": (-0.2, 0.2)},
               rotate=(-30, 30),
               scale=(0.5, 1.5)),
    # 3. Multiply
    iaa.Multiply((0.8, 1.2)),
    # 4. Linearcontrast
    iaa.LinearContrast((0.6, 1.4)),
    # Perform methods below only sometimes
    iaa.Sometimes(0.5,
        # 5. GaussianBlur
        iaa.GaussianBlur((0.0, 3.0))
        )
])
Image Augmentation
Last step and also the simplest: we show the images.

# 3. Show Images
while True:
    augmented_images = augmentation(images=images)
    for img in augmented_images:
        cv2.imshow("Image", img)
        cv2.waitKey(0)
