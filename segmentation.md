Image segmentation is the task of partitioning an image into multiple segments. This makes it a whole lot easier to analyze the given image.
Semantic segmentation refers to the process of linking each pixel in an image to a class label. These labels could include a items in garage.

Constructing an architecture
A naive approach towards constructing a neural network architecture for this task is to simply stack a number of convolutional
layers (with same padding to preserve dimensions) and output a final segmentation map. This directly learns a mapping from the 
input image to its corresponding segmentation through the successive transformation of feature mappings; however, it's 
quite computationally expensive to preserve the full resolution throughout the network.


Semantic Segmentation is a technique that enables us to differentiate different objects in an image. It can be considered
an image classification task at a pixel level.

U-Net Image Segmentation in Keras
Image segmentation is a computer vision task that segments an image into multiple areas by assigning a label to every pixel of the image. 
It provides much more information about an image than object detection, which draws a bounding box around the detected object, or image classification,
which assigns a label to the object.

Segmentation is useful and can be used in real-world applications such as medical imaging, clothes segmentation, flooding maps, self-driving cars, etc.

There are two types of image segmentation:

Semantic segmentation: classify each pixel with a label.
Instance segmentation: classify each pixel and differentiate each object instance.
U-Net is a semantic segmentation technique originally proposed for medical imaging segmentation. It’s one of the earlier deep learning segmentation models,
and the U-Net architecture is also used in many GAN variants such as the Pix2Pix generator.

U-Net Architecture

U-Net Architecture
U-Net was introduced in the paper, U-Net: Convolutional Networks for Biomedical Image Segmentation.
The model architecture is fairly simple: an encoder (for downsampling) and a decoder (for upsampling) with skip connections. 
