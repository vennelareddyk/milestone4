                                                         SEMANTIC SEGMENTATION:


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

For building the U-Net architecture, we will utilize the TensorFlow deep learning framework, as discussed already.
Hence, we will import the TensorFlow library for this purpose as well as the Keras framework, which is now an integral part of TensorFlow model structures. 
From our previous understanding of the U-Net architecture, we know that some of the essential imports include the convolutional layer, the max-pooling layer,
an input layer, and the activation function ReLU for the basic modeling structure. We will then use some additional layers like the Conv2DTranspose layer, 
which will perform an upsampling for our desired decoder blocks. We will also make use of the Batch Normalization layers for stabilizing the training process 
and use the Concatenate layers for combining the necessary skip connections.

After importing the required libraries, we can continue to build the U-Net architecture. You can either do this in one complete class by defining
all the parameters and values accordingly in order and continuing the process until you reach the very end or you a few iterative blocks.
I will be using the latter method as it is more convenient for most users to understand the model architecture of U-Net with the help of few blocks.
We will utilize three iterative blocks as shown in the architecture representation, namely the convolution operation block, the encoder block,
and the decoder block. With the help of these three blocks, we can build the U-Net architecture with ease. Let us now process and understand each of these function code blocks one by one.

Our Next step will be to build the encoder and decoder blocks. These two functions are quite simple to construct. 
The encoder architecture will use consecutive inputs starting from the first layer all the way to the bottom. 
The encoder function as we have defined will have the convolutional block, i.e., two convolutional layers followed by their respective batch normalization and
ReLU layers. Once we pass them through the convolution blocks, we will quickly downsample these elements, as mentioned in the research paper. We will use a max-pooling layer and stick to the parameters mentioned in the paper as the strides = 2. We will then return both the initial output and the max-pooled output,
as we need the former for performing the skip connections.

The decoder block will include three arguments, namely the receiving inputs, the input of the skip connection, and the number of filters in
the particular building block. We will upsample the entered input with the help of the Conv2DTranspose layers in our model.
We will then concatenate both the receiving input and the newly upsampled layers to receive the final value of the skip connections.
We will then use this combined function and perform our convolutional block operation to proceed to the next layer and return this output value.

After this step, we will collect all the primary outputs and the skip outputs to pass them on to further blocks.
We will create the next block and construct the entire decoder architecture until we reach the output. 
The output will have the required dimensions according to our desired output. In this case,
I have one output node with the sigmoid activation function. 
We will call the functional API modeling system to create our final model and return this model to the user for performing any task with the U-Net architecture.

Ensure that your image shapes are divisible by at least 16 or multiples of 16. Since we are using four max-pooling layers 
during the down-sampling procedure, we don't want to encounter the divisibility of any odd number shapes. Hence, 
it would be best to ensure that the sizes of your architecture are equivalent to sizes like (48, 48), (80,80), (160, 160), (256, 256), (512, 512), 
and other similar shapes. Let us try our model structure for an input shape of (160, 160, 3) and test the results. 
A summary of the model and its respective plot is obtained. You can see both these structures from the attached Jupyter Notebook. 
I will also include the model.png to show the particular plot of the entire architectural build.

Train the model

In the next step, we will compile and train the model to see its performance on the data. We are also using a 
checkpoint to save the model so that we can make predictions in the future. I interrupted the training procedure after 
1epochs as I was quite satisfied with the result obtained.

Conclusion:
The U-Net architecture is one of the most significant and revolutionary landmarks in the field of deep learning. 


ACCURACY : 81%
