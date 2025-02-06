# gi-tract-image-segmentation

## Overview
This project involves the implementation of a model able to segment healthy gastrointestinal tract organs (large bowel, small bowel and stomach) in MRI scans in order to mask them during the administration of radiotherapy.


## Data
The training annotations are provided as RLE-encoded masks, and the images are in 16-bit grayscale PNG format.

Each case in this competition is represented by multiple sets of scan slices (each set is identified by the day the scan took place). Some cases are split by time (early days are in train, later days are in test) while some cases are split by case - the entirety of the case is in train or test. The goal of this competition is to be able to generalize to both partially and wholly unseen cases.

Note that, in this case, the test set is entirely unseen. It is roughly 50 cases, with a varying number of days and slices, as seen in the training set.

### RLE
Run Length Encoding (RLE) is a lossless data compression (refers to compressing the data in such a way that the original form of the data can then be derived from it) algorithm.
It compresses data by reducing repetitive, and consecutive data called runs. It does so by storing the number of these runs followed by the data.
When a character occurs a large number of times consecutively in a sequence, then we can represent the same consecutive subsequence using only a single occurrence of that character and its count.
Using run length encoding, we can save memory space while transmitting data and preserving its original form. It is useful when we want to store or transmit large sequences of data.


## Model
The segmentation is performed by a custom U-Net architecture with the following specifications:

Input shape: 256x256x1
Filters: 32
Dropout rate: 0.3
Batch normalization: True
Layers: 4
Loss function: Binary cross-entropy
Adam optimizer


## Project Structure
- Image preprocessing and normalization
  - Creazione immagini png delle maschere
  - Caricamento delle immagini in memoria
  - Normalizzazione delle immagini
- Dataset splitting
- Data augmentation
- Model definition
- Training
- Mask prediction and visualization
- Results submission generation
