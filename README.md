
# AstroSpect: Photometric Redshift Estimation using CNNs
A lightweight Convolutional Neural Network (CNN) to estimate photometric redshifts (photo-z) directly from multi-band galaxy images, trained on SDSS DR12 data.

![Example Input Galaxy Bands](https://github.com/anshpman/AstroSpect-Photometric-Redshift-Estimation-for-Celestial-Bodies/blob/a03dcfcb53c804b491b46d2acbefb5a0ddd30fa8/Galaxy%20bands.png)
## About The Project

Understanding galaxy redshift is crucial in astrophysics, but traditional spectroscopic methods are slow and resource-intensive for large surveys. Photometric redshift (photo-z) estimation using multi-band imaging offers a scalable alternative.

This project, **AstroSpect**, develops a specialized, lightweight Convolutional Neural Network (CNN) to estimate photo-z directly from raw 32x32x5 multi-band galaxy image cubes. The goal is to provide an accurate, scalable, and efficient solution for processing the vast datasets from modern astronomical surveys like SDSS, LSST, and Euclid.

Our approach avoids manual feature engineering by letting the CNN learn spatial and spectral features directly from the images. We also investigated the impact of dataset preprocessing, finding that training on the full, natural redshift distribution (including outliers) yields significantly better and more robust results compared to using a clipped dataset.
## Architecture

![Architecture](https://github.com/anshpman/AstroSpect-Photometric-Redshift-Estimation-for-Celestial-Bodies/blob/a03dcfcb53c804b491b46d2acbefb5a0ddd30fa8/Architecture.png)


The model is a sequential CNN designed for regression, utilizing approximately 421,525 trainable parameters. It processes compact 32x32x5 image cubes (where the 5 channels correspond to the u, g, r, i, z photometric bands) to predict a single normalized redshift value.

### **Layer Breakdown:**

1.  **Input:** 32x32x5 image cube
2.  **Conv2D_1:** 32 filters (5x5), ReLU activation
3.  **MaxPooling2D_1:** (2x2) pool size
4.  **Conv2D_2:** 64 filters (5x5), ReLU activation
5.  **MaxPooling2D_2:** (2x2) pool size
6.  **Flatten**
7.  **Dense_1:** 220 neurons, ReLU activation
8.  **Dropout_1:** 0.5 rate
9.  **Dense_2:** 64 neurons, ReLU activation
10. **Dropout_2:** 0.5 rate
11. **Dense_Output:** 1 neuron, Sigmoid activation

### **Data Pipeline:**

The pipeline begins with the input layer receiving the 32x32x5 data cube.
- The first convolutional layer (Conv2D_1) applies 32 filters to detect basic features, resulting in a (28, 28, 32) feature map.
- A max pooling layer (MaxPooling2D_1) downsamples this to (14, 14, 32).
- The second convolutional layer (Conv2D_2) learns more abstract features, producing a (10, 10, 64) feature map.
- A second max pooling operation (MaxPooling2D_2) reduces this to (5, 5, 64).
- The resulting tensor is then flattened into a 1D vector of size 1600.
- This vector passes through a dense layer (Dense_1) of 220 neurons with ReLU activation.
- A dropout layer (Dropout_1) with a 0.5 rate is applied to prevent overfitting.
- This is followed by a second dense layer (Dense_2) of 64 neurons and another 0.5 dropout layer (Dropout_2).
- Finally, the network ends with a single-neuron output layer using sigmoid activation to produce the normalized redshift prediction between [0, 1].
## Results

The model's performance was evaluated on the SDSS DR12 test set. Key findings show that training on the **full, unclipped dataset** significantly outperforms training on a dataset where redshift outliers were removed ("clipped dataset").

**Performance on Full Dataset:**

- **Mean Absolute Error (MAE):** 0.0304
- **R-squared Score:** 0.9041
- **Precision:** 0.0269
- **Catastrophic Outlier Rate (|Delta z| > 0.15):** 0.12%

This demonstrates the model's ability to generalize well and handle the natural diversity in astronomical data. Preserving the full data distribution, including outliers, proved critical for robustness.

![Predicted vs Actual Redshift (Clipped Data And Unclipped Data)](https://github.com/anshpman/AstroSpect-Photometric-Redshift-Estimation-for-Celestial-Bodies/blob/d0949a57fa7441ccfbec61dc015f59bc7aff5f93/ClippedAndUnclipped.png)


**Performance Comparison: Full vs. Clipped Dataset**

| Metric                          | Full Dataset | Clipped Dataset |
| :------------------------------ | :----------- | :-------------- |
| MAE                             | 0.0304       | 0.0556          |
| MSE                             | 0.0017       | 0.0056          |
| Bias                            | 0.00029      | -0.00067        |
| R-squared Score                 | 0.9041       | 0.8826          |
| Adjusted R-squared              | 0.9041       | 0.8825          |
| Precision                       | 0.0269       | 0.0427          |
| Cat. Outliers (&vert;Delta z&vert; > 0.05) | 10.86%       | 27.32%          |
| Cat. Outliers (&vert;Delta z&vert; > 0.10) | 0.91%        | 5.90%           |
| Cat. Outliers (&vert;Delta z&vert; > 0.15) | 0.12%        | 1.28%           |

## Acknowledgements

* Sloan Digital Sky Survey (SDSS) for providing the observational data.
* NERSC for hosting the processed dataset used in this study.
