# Deep-Learning-Based-Video-in-Video-Steganography (In Progress)

## Introduction  

In the digital era, safeguarding sensitive information is a pressing concern, particularly in critical areas such as military operations, intelligence, journalism, and corporate communication. Steganography, the practice of hiding secret data within ordinary files, has emerged as a promising solution for covert data transmission. Among its forms, video steganography stands out due to the high capacity and redundancy of video data. However, traditional techniques often grapple with limitations like low data-hiding capacity, visible distortions, and susceptibility to advanced detection methods.  

To address these challenges, advancements in deep learning have opened new possibilities. Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs) have revolutionized data representation by extracting complex patterns from images, videos, and audio signals. These capabilities enable the embedding of larger payloads with minimal distortion, ensuring imperceptibility and reduced vulnerability to detection.  

This project leverages deep learning to integrate video and audio steganography, harnessing the temporal dynamics of videos and the frequency characteristics of audio signals to create a robust, multidimensional steganographic system. By exploring this underutilized combination, the approach enhances security and enables the covert transmission of significant data volumes, offering a modern solution for secure communication in diverse applications.  

#
## Aim and Scope of the Project:

In the realm of digital concealment techniques, image and audio steganography face inherent limitations in terms of the amount of data they can hide without compromising quality. This restriction necessitates heavy compression of payloads, which often leads to noticeable distortions and loss of quality in the concealed content. Video steganography addresses this challenge by offering a higher payload capacity. It allows for embedding extensive data within a single cover video, leveraging higher bitrate compression to minimize distortion and preserve overall video quality.

The primary objective of this project is to develop a specialized convolutional autoencoder architecture designed specifically for embedding video frames and audio segments within other videos. This approach aims to conceal significant volumes of data covertly within videos, ensuring that the quality and size of the cover video remain perceptually unchanged.

The scope of the project encompasses the implementation of a deep learning-driven system tailored for video-in-video steganography. Key objectives include securely embedding one video within another to safeguard sensitive video data. This technique also supports the embedding of digital watermarks containing ownership information, thereby preventing unauthorized use or distribution of intellectual property. In sectors such as military and intelligence, video steganography plays a critical role in securely transmitting classified information, ensuring confidentiality while evading detection of sensitive data.
#
## Terms to be clear about:

• Video Steganography

• Encoding / Decoding

• Auto Encoder

• Convolutional Neural Network (CNN)

• Convolutional Auto Encoder (CAE)

#
## Hardware Requirements:

• **GPU:** At least an NVIDIA RTX 3050 or higher, as deep learning algorithms benefit greatly from GPU acceleration.

• **CPU:** A powerful CPU such as Intel Core i5/Ryzen5 or above, will be required for tasks like the data preprocessing.

• **RAM:** At least 16GB of RAM to handle memory-intensive deep learning models,particularly when working with video data.

• **Storage:** High-speed storage such as a 512 GB SSD will be required to efficiently manage large video and audio datasets that can ensure fast loading and processing.

#
# Task Accomplished

## Video Segment:

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

### System Flowchart

**Encoder:**


**Decoder:** 

### Video Steganography Model Training

The training phase for the *Video-in-Video Steganography* project aimed to optimize the embedding (hiding) and extraction (reveal) of hidden videos within cover videos using a deep learning-based approach. The model was trained for **90 epochs**, focusing on minimizing both the hiding and reveal losses while improving the respective accuracies.

### Training Overview  

The training process monitored four key metrics:  
1. **Loss**: Overall loss, hiding loss, and reveal loss during training.  
2. **Accuracy**: Training accuracy for hiding and reveal tasks.  
3. **Validation Loss**: Losses for hiding and reveal tasks on the validation set.  
4. **Validation Accuracy**: Validation accuracy for both tasks.  

### Key Epoch Snapshots  

| **Epoch** | **Loss** | **Hiding Loss** | **Reveal Loss** | **Hiding Accuracy** | **Reveal Accuracy** | **Validation Loss** | **Validation Hiding Loss** | **Validation Reveal Loss** | **Validation Hiding Accuracy** | **Validation Reveal Accuracy** |
|-----------|----------|-----------------|-----------------|----------------------|---------------------|----------------------|----------------------------|----------------------------|--------------------------------|--------------------------------|
| 1         | 1.178    | 0.218           | 1.281           | 57.82%              | 35.64%             | 0.971                | 0.291                      | 0.907                      | 52.04%                        | 22.26%                        |
| 45        | 0.084    | 0.043           | 0.054           | 63.11%              | 81.39%             | 0.070                | 0.043                      | 0.033                      | 62.31%                        | 85.17%                        |
| 90        | 0.076    | 0.040           | 0.048           | 64.92%              | 83.51%             | 0.064                | 0.042                      | 0.029                      | 62.82%                        | 85.51%                        |

### Observations  

1. **Steady Improvement in Loss and Accuracy**:  
   - Loss values (both hiding and reveal) showed consistent reduction across epochs, indicating effective learning.  
   - The reveal accuracy improved significantly, reaching over **85%** on the validation set by the final epoch.  

2. **Balanced Performance on Training and Validation**:  
   - While validation losses fluctuated slightly, they remained close to training losses, showing that the model generalized well.  

3. **Plateau in Performance**:  
   - After epoch 75, improvements in both loss and accuracy began to plateau, suggesting convergence.  

4. **Challenges in Hiding Task**:  
   - The hiding task showed a slower improvement compared to the reveal task, which could suggest a higher complexity in encoding features invisibly within the cover video.  

### Graphs and Plots

![download](https://github.com/user-attachments/assets/0e480dd8-25d1-4cfa-a868-27dee7469c4c)


### Conclusion  

The training process successfully prepared the model for embedding and extracting video content in a steganographic manner. With hiding accuracy stabilizing at over **62%** and reveal accuracy surpassing **85%**, the model demonstrates a promising capability for real-world application. Future work could focus on further optimizing the hiding task and exploring techniques to reduce training duration without compromising accuracy.  

#
## Audio Segment:

• **Data Collection and Preprocessing:** For the Audio Steganography project, we manually collected and prepared a diverse dataset of audio files to train, validate, and test our model effectively. The audio files were recorded from various sources, with recordings varying in length. To ensure uniformity, each recording was clipped into 10-second segments. After processing, we obtained a total of 8,000 audio files, each exactly 10 seconds long.

The original audio recordings were in stereo format, which is not supported by our model. To address this, we converted all stereo audio files into mono format, making them compatible with the model's requirements.

The dataset is structured within a main folder containing three subfolders: train, test, and val. We divided the total dataset into these folders using an 80:10:10 ratio. This split ensures the model has sufficient data for training while also providing balanced datasets for validation and testing.

In summary, the dataset consists of 10-second mono audio clips, organized and preprocessed to suit the requirements of the project, enabling efficient model training and evaluation.


### Audio Steganography Model Architecture Development

#
## Task Remaining
• Audio Steganography Model Training

• Model Analysis and Optimization

• GUI Design
