# CHALLENGE-2---Ibuprofen

Possibili cose su cui lavorare.
______________________________________

NORMALIZATION
If /255 doesn't work well, try:



1. Per-Image Normalization (Z-score) if images look very different from each other

CODE:   pythonnormalized_image = (image - image.mean()) / image.std()

Pros:

Each image gets its own contrast enhancement

Robust to different lighting/exposure conditions between images

Works well when images have very different intensity distributions

Cons:

Loses absolute intensity information (a bright image and dark image could look similar after normalization)

Can amplify noise in low-contrast regions

Each image normalized independently, so the network can't learn absolute intensity patterns

Best for: Medical images from different machines/settings, varying exposure conditions



2. Dataset-Level Normalization if images look similar in brightness/contrast
__________________CODE:

python# Calculate once on training set

train_mean = np.mean(all_training_images)

train_std = np.std(all_training_images)

COMMENT: Apply to each image

normalized_image = (image - train_mean) / train_std

_______________________
Pros:

Preserves relative intensity differences between images

Network can learn absolute intensity features

Standard practice in computer vision (e.g., ImageNet normalization)

More stable across train/test split

Cons:

Requires computing statistics over entire dataset first

Less robust if train/test images come from different sources

Best for: Consistent imaging conditions, large datasets, when absolute intensity matters

________________________________________________________________________
RECEPTIVE FIELD dimension

Because different tasks need neurons to capture different types of information:

Small RF → useful for detecting fine details (edges, textures).

Large RF → needed for detecting large patterns (shapes, objects, context).

Whole-image RF → needed for tasks like classification or segmentation.
___________________________________________________________________________

Activation function
___________________________________________________________________________

Pooling layer and stride dimension
___________________________________________________________________________

Data augmentation
