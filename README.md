# AstroSpect-Photometric-Redshift-Estimation-for-Celestial-Bodies
AstroSpect is a deep learning project for estimating celestial redshifts from photometric data using a custom CNN. It automates distance prediction, improving accuracy and scalability over traditional spectral methods. Trained on SDSS data, it enables efficient, real-time analysis of large astronomical datasets.
AstroSpect: Photometric Redshift Estimation for Celestial Bodies
AstroSpect is an AI-powered system designed to predict the redshift of celestial bodies using multi-band photometric data. By leveraging a Convolutional Neural Network (CNN), the project enables efficient and scalable distance estimation for large astronomical datasets, addressing the limitations of traditional spectral analysis.

Key Features
CNN-based Redshift Estimation: Optimized convolutional model tailored for processing 64x64 pixel images across 5 spectral bands (u, g, r, i, z).
Photometric Data Analysis: Utilizes data from the Sloan Digital Sky Survey (SDSS) to predict redshifts with high accuracy.
Robust Architecture: Incorporates convolutional, max-pooling, and dropout layers to enhance performance and prevent overfitting.
Scalability: Designed to handle large datasets, enabling real-time analysis and reducing human intervention in redshift estimation.
Model Performance
Mean Squared Error (MSE): 0.0297
Bias: -0.0022
Variance: 0.0133
Technology Stack
Programming Language: Python
Frameworks/Libraries: TensorFlow, Keras, NumPy, Pandas
Dataset: Sloan Digital Sky Survey (SDSS)
Future Enhancements
Hyperparameter Tuning: Optimize learning rates, batch sizes, and other parameters.
Dataset Expansion: Incorporate additional datasets from surveys like DESI and Euclid.
Transfer Learning: Adapt the model to new datasets using pretrained architectures.
