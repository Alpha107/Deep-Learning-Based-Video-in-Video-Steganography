# Deep-Learning-Based-Video-in-Video-Steganography

## Introduction

Videosteganography, the art of concealing secret information within innocuous video files,has emerged as a promising technique for covert 
data transmission. However, traditional video steganography methods are often plagued by limitations, including lowpayload capacity,
noticeable visual distortions that could raise suspicion, and vulnerability to modern steganalysis techniques designed to detect the 
presence of hidden data. 

In today's digital age, keeping sensitive information secure is crucial, especially in fields like military operations, intelligence, and business transactions. Video steganography offers a way to hide secret data within ordinary video files, allowing for covert data transmission. However, traditional methods often have drawbacks such as low data capacity, visible distortions that could raise suspicions, and vulnerability to detection techniques.

Recent advances in deep learning, particularly with CNNs and RNNs, have revolutionized how we handle complex data like images, videos, and time-series data. These advanced neural networks can capture intricate patterns and representations, making them ideal for developing more effective video steganography techniques. By using these models, we can hide larger amounts of data while maintaining video quality and avoiding detection by steganalysis methods. This is particularly useful in situations requiring covert transmission of large amounts of sensitive information.

Moreover, videos add complexity due to their temporal nature, making it harder for detection algorithms to find and extract hidden data. Despite the effectiveness of current methods, there hasn't been much exploration into hiding one video inside another. Traditional approaches rely on techniques like modified LSB, DCT, and DWT transform. This gap motivates us to explore deep learning for video-in-video steganography, aiming to enhance security and data capacity in covert multimedia communication. This innovative approach offers a robust solution for secure data transmission and protection.
#
#
## Aim and Scope of the Project:

In the realm of digital concealment techniques, image and audio steganography face inherent limitations in terms of the amount of data they can hide without compromising quality. This restriction necessitates heavy compression of payloads, which often leads to noticeable distortions and loss of quality in the concealed content. Video steganography addresses this challenge by offering a higher payload capacity. It allows for embedding extensive data within a single cover video, leveraging higher bitrate compression to minimize distortion and preserve overall video quality.

The primary objective of this project is to develop a specialized convolutional autoencoder architecture designed specifically for embedding video frames and audio segments within other videos. This approach aims to conceal significant volumes of data covertly within videos, ensuring that the quality and size of the cover video remain perceptually unchanged.

The scope of the project encompasses the implementation of a deep learning-driven system tailored for video-in-video steganography. Key objectives include securely embedding one video within another to safeguard sensitive video data. This technique also supports the embedding of digital watermarks containing ownership information, thereby preventing unauthorized use or distribution of intellectual property. In sectors such as military and intelligence, video steganography plays a critical role in securely transmitting classified information, ensuring confidentiality while evading detection of sensitive data.
#
## Terms to be clear about:

• Video Steganography

• Auto Encoder

• Convolutional Neural Network

• Convolutional Auto Encoder

#
## Hardware Requirements:

• **GPU:** At least an NVIDIA RTX 3050 or higher, as deep learning algorithms benefit greatly from GPU acceleration.

• **CPU:** A powerful CPU such as Intel Core i5/Ryzen5 or above, will be required for tasks like the data preprocessing.

• **RAM:** At least 16GB of RAM to handle memory-intensive deep learning models,particularly when working with video data.

• **Storage:** High-speed storage such as a 512 GB SSD will be required to efficiently manage large video and audio datasets that can ensure fast loading and processing.

#
## Task Accomplished

• **Data Collection:** During the data collection phase of our video steganography project, we meticulously gathered and prepared a substantial dataset. We collected a total of 644 videos for both the cover and secret video categories, ensuring consistency by trimming each video to a uniform length of 15 seconds. To enhance playback smoothness, we set the frame rate of all videos to 30 frames per second. Additionally, we reduced the number of frames in each video folder from 450 to 300 to streamline the dataset. As a result, our efforts culminated in a robust dataset comprising 644×300×2 images, providing a solid foundation for further work on the project.

• **Data Preprocessing:** The data preprocessing phase was crucial for preparing the frames for analysis and model training. We implemented several steps to ensure the data was formatted appropriately. First, we rescaled the frame size to 224x224 pixels to meet our model’s requirements. Next, we normalized the frames to adjust the pixel values, which enhanced the effectiveness of the model training process. After processing, we denormalized the frames to revert them to a viewable state, enabling us to check and validate the processed data.

• **Model Architecture Building:** For the model training phase, a comprehensive neural network architecture tailored for video steganography is being developed. The model is composed of several key components, each designed to perform specific functions in the steganography process

![Screenshot 2024-10-19 202304](https://github.com/user-attachments/assets/631427d3-2b11-40f7-9e1d-9a9a1c020ab3)

**Secret Encoding Block**

The secret encoding begins by processing the secret image, which is input at a resolution of 224x224 pixels with 3 color channels. This network employs a series of convolutional layers that utilize various kernel sizes and filters to extract and refine features
from the secret image. Initially, convolutional layers with kernel sizes of 3x3, 4x4, and
5x5 have been used to perform feature extraction with ReLU activation functions. This
processing prepares the secret image for integration with the cover image in subsequent
stages of the network.

**Concealment Block**

In the concealment block, the cover image and the processed secret image are combined
to form a single input. The network processes this combined input through a series of
convolutional operations designed to embed the secret image into the cover image. The
convolutional layers applied here are configured with various kernel sizes and filters to
effectively perform this embedding. The final layer of the hiding network generates a
predicted cover image that contains the secret information by applying a convolutional
operation with a specific filter configuration.

**Decoding Block**

The decoding block takes the noisy predicted cover image as input to recover the secret
image. This network processes the image through a series of convolutional layers, designed to extract features and reconstruct the secret image. The final layer of the reveal
network produces the revealed secret image, utilizing a specific convolutional setup to
refine the output.

#
## Task Remaining

• Video Steganography Model Training

• Audio Data Collection

• Audio Preprocessing

• Audio Steganography Model Architecture Development

• Audio Steganography Model Training

• Model Analysis and Optimization

• GUI Design
