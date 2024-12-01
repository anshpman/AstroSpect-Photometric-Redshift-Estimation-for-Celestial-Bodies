# AstroSpect: Photometric Redshift Estimation for Celestial Bodies
AstroSpect is a deep learning project designed to estimate the redshift of celestial bodies using multi-band photometric data. By leveraging a custom Convolutional Neural Network (CNN), it automates distance prediction, improving accuracy and scalability over traditional spectral methods. Trained on Sloan Digital Sky Survey (SDSS) data, AstroSpect enables efficient, real-time analysis of large astronomical datasets.


## Features

- CNN-Based Redshift Estimation: Optimized convolutional model for processing 64x64 pixel images across 5 spectral bands (u, g, r, i, z).
- Photometric Data Analysis: Utilizes SDSS photometric data to predict redshifts with high accuracy
- Robust Architecture: Incorporates convolutional, max-pooling, and dropout layers to enhance performance and prevent overfitting.
- Scalability: Handles large datasets efficiently, reducing human intervention and enabling real-time analysis.


## Technology Stack

- Programming Language: Python
- Frameworks/Libraries: TensorFlow, Keras, NumPy, Pandas
- Dataset: Sloan Digital Sky Survey (SDSS)

## Future Enhancements
- Hyperparameter Tuning: Optimize learning rates, batch sizes, and other parameters.
- Dataset Expansion: Integrate additional datasets from surveys like DESI and Euclid.
- Transfer Learning: Adapt the model to new datasets using pretrained architectures.


