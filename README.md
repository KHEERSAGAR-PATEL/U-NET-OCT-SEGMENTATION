# U-NET-OCT-SEGMENTATION
This project uses a deep learning approach to automatically segment retinal layers in OCT images. The goal is to streamline the process of identifying and delineating retinal layers, leveraging neural networks to assist in diagnostic imaging.
To adapt your project documentation and avoid plagiarism, I'll rephrase and reorganize the text while preserving the content's structure and meaning. Below is the revised version:

---

# OCT - Retinal Layer Segmentation
A deep learning model for performing multiclass semantic segmentation on retinal layers in Optical Coherence Tomography (OCT) images.

## Table of Contents
* [Overview]
* [Retinal Layers]
* [Dataset Information]
* [Technologies Used]
* [Model Architecture]
* [How to Use]
* [Pre-trained Checkpoints]
* [Acknowledgments])

## Overview
This project uses a deep learning approach to automatically segment retinal layers in OCT images. The goal is to streamline the process of identifying and delineating retinal layers, leveraging neural networks to assist in diagnostic imaging.



## Dataset Information
The dataset used for this project, [OCT Image Database (OCTID)](https://dataverse.scholarsportal.info/dataset.xhtml?persistentId=doi:10.5683/SP/WLW4ZT), is publicly available and was developed by the University of Waterloo in 2018. It includes fovea-centered OCT images from 25 healthy individuals. Each image has a resolution of 750x500 pixels and is grayscale. Images were manually annotated to create ground truth segmentations using [makesense.ai](https://www.makesense.ai/).

## Retinal Layers
Segmenting retinal layers in OCT images is crucial in diagnosing various eye conditions. Each retinal layer can indicate early signs of diseases, which could allow for timely intervention. OCT segmentation helps analyze the layer thickness and structural changes associated with conditions such as diabetic macular edema, age-related macular degeneration, and diabetic retinopathy. Changes in the retinal layers often precede visible symptoms, making this segmentation process an essential diagnostic tool.

The algorithm in this project segments the following 8 retinal layers:
- NFL: Nerve Fiber Layer
- GCL+IPL: Ganglion Cell Layer and Inner Plexiform Layer
- INL: Inner Nuclear Layer
- OPL: Outer Plexiform Layer
- ONL: Outer Nuclear Layer
- Ellipsoid Zone
- RPE: Retinal Pigment Epithelium
- Choroid

## Model Architecture
The model architecture is based on the U-Net, a popular design in biomedical image segmentation. The U-Net architecture is a convolutional encoder-decoder network that performs downsampling, capturing high-level features, followed by upsampling to construct a detailed segmentation map. Skip connections link corresponding encoder and decoder layers to maintain spatial information across scales, creating a U-shaped structure.

The input is a grayscale image (640x640x1), and the model generates a segmented output (640x640x9), with each output channel corresponding to a specific retinal layer.

The model achieves a mean Intersection over Union (IoU) of 75.4% and a validation accuracy of 96.45%, with a final loss value of 0.1016 (decreasing from an initial loss of 2.01). 

### `simple_unet.py`
This file contains the U-Net model as a class definition. It’s used as the backbone model for the segmentation process. No variable adjustments are needed here.

### `multiclass_segmentation.ipynb`
The main notebook for the segmentation task. Variables to adjust:
- `TRAIN_PATH_X`: Local path to the original OCT images
- `TRAIN_PATH_Y`: Local path to the segmented OCT masks
- `n_classes`: Number of segmentation classes
- `SIZE_X`, `SIZE_Y`: Image dimensions (default is 640x640 pixels)
