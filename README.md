# Taxi Fare Data Analysis

## Overview
This project analyzes taxi fare data to understand factors influencing the fare and develop machine learning models to predict taxi fares. The dataset is preprocessed to remove outliers and normalize values, and several regression models are explored to predict the taxi fare accurately.

## Dataset Description
The dataset contains the following columns:
- `amount`: The fare amount in dollars.
- `date_time_of_pickup`: The timestamp of the pickup.
- `longitude_of_pickup`: Longitude of the pickup location.
- `latitude_of_pickup`: Latitude of the pickup location.
- `longitude_of_dropoff`: Longitude of the dropoff location.
- `latitude_of_dropoff`: Latitude of the dropoff location.
- `no_of_passenger`: Number of passengers.

### Key Statistics Before Preprocessing
- The dataset contains 50,000 rows and no null values.
- Extreme outliers are present in latitude, longitude, and fare amount.
- Minimum fare is $3.00, and there must be at least one passenger.

### Preprocessing Steps
1. **Removing Outliers:**
   - Removed rows where fare is less than $3.00 or `no_of_passenger` is less than 1.
   - Filtered latitude and longitude to be within realistic ranges for New York City.
   - Excluded fares above $50 to handle outliers.
   - Calculated distance using the Haversine formula and removed rows with distances less than 0.1 km.

2. **Feature Engineering:**
   - Extracted `hour`, `month`, and `weekday` from the `date_time_of_pickup` column.
   - Calculated the distance between pickup and dropoff points using the Haversine formula.

3. **Scaling:**
   - Used MinMaxScaler to normalize features.

### Final Dataset Statistics
- Total Rows: 47,234
- Key Features:
  - `amount` range: $3.00 - $49.83
  - `distance_km` range: 0.1 km - 101.1 km

## Data Visualization
1. **Histograms:**
   - Visualized distributions for `amount`, `longitude_of_pickup`, `latitude_of_pickup`, `longitude_of_dropoff`, `latitude_of_dropoff`, and `distance_km`.
2. **Scatter Plots:**
   - Analyzed relationships between `distance_km` and `amount` before and after filtering outliers.

## Model Building
### Linear Regression
- Training Score: 0.805
- Test Score: 0.805

### K-Nearest Neighbors (KNN)
- Training Score: 0.841
- Test Score: 0.765

### Decision Tree Regressor
- Training Score: 0.845
- Test Score: 0.822

### Support Vector Regressor (SVR)
- Training Score: 0.798
- Test Score: 0.797

### After Removing Coordinates Columns
- Linear Regression Training Score: 0.803
- Linear Regression Test Score: 0.802

## Conclusions
- The Decision Tree Regressor achieved the highest test score (0.822), indicating it is the most effective model for this dataset.
- Removing coordinates columns slightly decreased the model performance, suggesting latitude and longitude provide valuable information.

## Future Work
- Experiment with additional feature engineering techniques.
- Optimize hyperparameters for the Decision Tree and KNN models.
- Explore ensemble methods such as Random Forest or Gradient Boosting.

## Requirements
### Libraries
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

### Usage
1. Install the required libraries using pip:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```
2. Load the dataset and run the preprocessing and model training scripts provided in the notebook.

---
**Author:** John Smith

