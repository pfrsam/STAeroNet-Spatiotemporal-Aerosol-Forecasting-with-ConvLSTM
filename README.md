# STAeroNet: Spatiotemporal Aerosol Forecasting with ConvLSTM

## Overview

STAeroNet is a deep learning project focused on forecasting Aerosol Optical Depth (AOD) using satellite imagery and ConvLSTM architecture.

The project uses MODIS MAIAC AOD GeoTIFF data to model spatiotemporal air pollution patterns over Korea. By learning from historical sequential AOD maps, the model predicts future pollution distributions, helping support environmental monitoring and air quality analysis.

This repository includes:

- Data visualization of satellite AOD imagery
- Data mining using Google Earth Engine
- Data preprocessing and missing value handling
- Patch extraction and pollution labeling
- ConvLSTM model implementation from scratch
- Dataset sequence generation
- DataLoader creation
- Model training and validation
- Forecast visualization and performance analysis

---

## Project Structure

```bash
STAeroNet/
│
├── STAeroNet.ipynb          # Full project notebook
├── README.md                # Project documentation
````

---

## Problem Statement

Air pollution forecasting is a critical task for environmental science and public health.

Traditional statistical approaches often struggle to capture complex spatial and temporal dependencies in atmospheric data. This project applies deep learning, specifically ConvLSTM, to improve forecasting of Aerosol Optical Depth (AOD), which is a strong indicator of particulate air pollution.

The objective is to predict future AOD maps based on previous satellite observations.

---

## Dataset

The dataset consists of MODIS MAIAC AOD satellite imagery in GeoTIFF (`.tif`) format collected over Korea.

### Data Source

* MODIS/061/MCD19A2_GRANULES
* Retrieved using Google Earth Engine

### Data Features

* Daily AOD observations
* GeoTIFF raster format
* Spatial region: Korea
* Time period: Multiple years of observations
* Preprocessing includes:

  * scaling factor correction
  * negative value removal
  * missing value filling
  * normalization

### Dataset Access

The dataset is not publicly included in this repository due to size limitations.

If you would like access to the dataset, please contact:

**[sayfitdinovsarvar12@gmail.com](mailto:sayfitdinovsarvar12@gmail.com)**

---

## Model Architecture

The forecasting model is based on **ConvLSTM (Convolutional Long Short-Term Memory)**.

### Why ConvLSTM?

ConvLSTM is designed for spatiotemporal forecasting tasks where both:

* spatial relationships (image structure)
* temporal dependencies (time sequence)

are important.

This makes it highly suitable for satellite-based pollution forecasting.

### Model Details

* Input channels: 1
* Hidden dimensions: [16, 32]
* Number of ConvLSTM layers: 2
* Output channels: 1
* Loss function: MSE Loss
* Optimizer: Adam
* Learning rate: 1e-3

---

## Training Pipeline

### Sequence Creation

Input sequences are generated using:

* Sequence length: 5 historical frames
* Target: next future AOD frame

Example:

```text
Day 1 → Day 2 → Day 3 → Day 4 → Day 5 → Predict Day 6
```

### Dataset Split

* Train: 80%
* Validation: 20%

### Batch Size

```python
batch_size = 4
```

### Epochs

```python
num_epochs = 30
```

---

## Evaluation Metrics

The model is evaluated using:

* Mean Squared Error (MSE)
* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)

Additionally, pollution threshold analysis is performed using:

```python
THRESHOLD = 0.4
```

to classify polluted vs non-polluted regions.

---

## Result Visualization

The notebook includes:

* Ground truth vs prediction comparisons
* Pollution zone visualizations
* Validation set analysis
* Multi-sample forecast demonstrations

This helps visually assess forecasting quality beyond numerical metrics.

---

## Installation

### Clone Repository

```bash
git clone https://github.com/yourusername/STAeroNet.git
cd STAeroNet
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Main Libraries Used

```txt
torch
numpy
matplotlib
rasterio
google-earth-engine
glob
os
```

---

## Future Improvements

Possible future work includes:

* Attention-based ConvLSTM
* Transformer-based forecasting models
* Multi-channel meteorological feature integration
* PM2.5 prediction extension
* Real-time forecasting pipeline deployment

---

## Author

**Sarvarbek Sayfitdinov**

For collaboration, research discussions, or dataset access:

📧 **[sayfitdinovsarvar12@gmail.com](mailto:sayfitdinovsarvar12@gmail.com)**

---

## License

This project is intended for academic and research purposes.

```
```
