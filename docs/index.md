## Neonatal manipulations analysis pipeline to enable bed-side learning

Harpreet Singh
October 11, 2020

I have used the ‘Logitech C920’ USB camera installed on neonate bed in NICU at the same level as the top coils of radiant warmer. The camera was top facing the neonate using a custom-designed wall mount in order to observe the whole body of the infant. The videos had a resolution of 1280 x 720 pixels and were recorded at 30 frames per second. Three common neonatal care manipulations were selected for study analysis: (i) patting, (ii) diaper change, and (iii) tube feeding. Examples of video captured patting, diaper change and tube feeding manipulations are shown in Figure 1. Acquired video sequences were down sampled at 15 fps (frames per second) to reduce redundant computations and images were resized from the original 1280 x 720 pixels to a color image of 720 x 480 pixels.

### Methodology

We used combination of Inception-v3 convolutional neural network (CNN) followed by transfer learning layers of Long Short-Term Memory (LSTM) for automated tagging of data. The pooled output of the Time-distributed CNN model generates an output of the 2048-dimensional feature vector. While training the model, we had set the weights of InceptionV3’s layers as non-trainable and trained only the LSTM layers added for transfer learning. The 720 x 480 pixels input images were resized to 224x224 pixels as input to InceptionV3 keras implementation and default image augmentation technique with zoom range of 0.1, rotation range of 0.8, and width & height range shift of 0.2 was utilized. This technique was very slow for real time learning, as for all epoch, InceptionV3’s layers will run for all images to generate feature map and as it contains 21802784 parameters. The model training process was computationally too exhaustive and in-efficient. Moreover, user could not visualize the features used in this process such as the neonate, the clinical staff, diapers, syringe, plunger, and their spatial attributes and how they correlate during the manipulations. 

In this project instead of color image of 720 x 480 pixels, we aim to reduce the computational overload to set of derived features and build a custom matrix of features for manipulations which will be used to generate spatial signature of the respective manipulation. Possible options to reduce this analysis pipeline are
•	Fast R-CNN (Region based convolution network) and RPN (region proposed network) to perform object identification. Once objects are identified, then explore motion of these objects in sequence of frames. 
•	Based on movement of objects in video will be different in feeding, patting, and diaper-change, we can build different manipulations as activity amongst different objects. 
•	Analyzing each color channel of image (Red, Green, Blue) for its properties and identifying if one or more is sufficient for manipulation identification.
•	Use specific image analysis techniques (convolutions) to identify manipulation specific features which are performed in patting, diaper change, and feeding.
•	Explore possibility of using greyscale images instead of RGB images to reduce computation time


This will allow us to generalize analysis pipeline for different manipulations which can subsequently be used in combination of neural network or otherwise to detect a manipulation on the real time basis


# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/harpreet-chil/cs639_neonatal_video_manipulations/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
