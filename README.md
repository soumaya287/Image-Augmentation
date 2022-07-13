# Image-Augmentation
What is the concept behind Image Augmentation
There are many things to consider when creating a custom detector and one of them is the image dataset. For example, if we were to have this type of dog recognized:
![image](https://user-images.githubusercontent.com/81196476/178696274-fa458f0c-ec18-4a35-8482-a7826779ec4e.png)
we must have as many images as possible and as diverse as possible because having only front dogs in the dataset (in the same position), the algorithm will only recognize this. A dog slightly rotated or positioned in reverse would not be recognized.

For this reason, it is necessary to use a library or code for augmenting the image. With some modifications, we generate new images with light changes, cut a part of the image, enlargements, rotations, color changes, and much more. Generally, 5 or 6 types are generated.
# How to implement from scratch Image augmentation with Imgaug
There are various methods to augment images but we will use a python library called imgaug. To install, open the terminal and run the command:

pip install imgaug
If you don’t get any errors, everything has been installed correctly.
