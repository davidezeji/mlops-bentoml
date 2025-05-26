# House Price Prediction with BentoML

This project demonstrates a practical implementation of machine learning model serving using BentoML. It showcases how to build, train, and deploy a house price prediction model with different levels of complexity and features.

## Project Overview

The project implements a house price prediction system with three progressively complex versions:

1. **Version 1**: Basic model predicting house prices based on square footage and number of rooms
2. **Version 2**: Enhanced model with additional features like bathrooms, house age, and location factors
3. **Version 3**: Multi-model service supporting both basic and enhanced predictions

## Repository Structure

```
.
├── model_train_v1.py      # Basic model training script
├── model_train_v2.py      # Enhanced model training script
├── model_service_v1.py    # Basic model serving implementation
├── model_service_v2.py    # Enhanced model serving implementation
├── model_service_v3.py    # Multi-model serving implementation
└── README.md             # Project documentation
```

## Key Features

- **Model Training**: Separate scripts for training different versions of the model
- **Model Serving**: REST API endpoints for making predictions
- **Version Control**: Support for multiple model versions
- **Input Validation**: Pydantic models for request validation
- **Async Support**: Asynchronous prediction handling

## Prerequisites

- Python 3.7+
- pip
- Git (optional)

## Setup

1. **Create and activate virtual environment**
   ```bash
   python3 -m venv bentoml-env
   source bentoml-env/bin/activate
   ```

2. **Install dependencies**
   ```bash
   pip3 install bentoml scikit-learn pandas
   ```

## Usage

### Training Models

1. **Basic Model (Version 1)**
   ```bash
   python3 model_train_v1.py
   ```

2. **Enhanced Model (Version 2)**
   ```bash
   python3 model_train_v2.py
   ```

### Serving Models

1. **Basic Service (Version 1)**
   ```bash
   bentoml serve model_service_v1.py --reload
   ```

2. **Enhanced Service (Version 2)**
   ```bash
   bentoml serve model_service_v2.py --reload
   ```

3. **Multi-Model Service (Version 3)**
   ```bash
   bentoml serve model_service_v3.py --reload
   ```

### Making Predictions

1. **Basic Prediction (Version 1)**
   ```bash
   curl -X POST "http://127.0.0.1:3000/predict_house_price" \
        -H "Content-Type: application/json" \
        -d '{"square_footage": 2500, "num_rooms": 5}'
   ```

2. **Enhanced Prediction (Version 2)**
   ```bash
   curl -X POST "http://127.0.0.1:3000/predict_house_price" \
        -H "Content-Type: application/json" \
        -d '{
             "square_footage": 2500,
             "num_rooms": 5,
             "num_bathrooms": 3,
             "house_age": 10,
             "distance_to_city_center": 8,
             "has_garage": 1,
             "has_garden": 1,
             "crime_rate": 0.2,
             "avg_school_rating": 8,
             "country": "Germany"
         }'
   ```

## Model Versions

### Version 1
- Simple linear regression model
- Features: square footage, number of rooms
- Basic prediction endpoint

### Version 2
- Enhanced model with more features
- Additional features: bathrooms, age, location factors
- Improved prediction accuracy

### Version 3
- Multi-model service
- Supports both basic and enhanced predictions
- Separate endpoints for different model versions

## Cleanup

To deactivate the virtual environment:
```bash
deactivate
```

## Project Photos
![alt text](photos/Screenshot%202025-05-26%20at%204.05.51 PM.png)

![alt text](photos/Screenshot%202025-05-26%20at%204.13.45 PM.png)

![alt text](photos/Screenshot%202025-05-26%20at%203.59.24 PM.png)

![alt text](photos/Screenshot%202025-05-26%20at%204.01.44 PM.png)