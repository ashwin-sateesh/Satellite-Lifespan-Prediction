# Satellite Lifespan Prediction

## Project Overview
This project aims to predict the expected lifespan of a satellite using various machine learning and deep learning models. Given the increasing number of satellites orbiting the Earth, predicting their lifespan is crucial to avoid collisions and manage space traffic effectively.

## Dataset
### Data Source
- [Kaggle: Active Satellites Dataset](https://www.kaggle.com/ucsusa/active-satellites)
- [EU Space Imaging: Lifespan of Orbiting Satellites](https://www.euspaceimaging.com/the-lifespan-of-orbiting-satellites/)

### Data Description
The dataset contains approximately 1500 records with 25 variables. The notable variables include:
- **Official Name of Satellite**: Name given to the satellite at launch
- **Country of UN Registry**: Country sending the satellite
- **Users**: Military, Civil, Government, Commercial
- **Purpose**: Reason for the launch of the satellite
- **Launch Mass (kg)**: Mass of the satellite during launch
- **Inclination (deg)**: Tilt of a satellite orbit around Earth
- **Power (watts)**: Initial power of a satellite
- **Apogee (km)**: Farthest point of the satellite from Earth
- **Perigee (km)**: Closest point of the satellite from Earth
- **Eccentricity**: Amount by which the satellite orbit deviates from a perfect circle
- **Period (minutes)**: Time taken by the satellite to complete one orbit
- **Launch Date**: Date of launch of the satellite
- **Expected Lifespan (years)**: Expected lifespan of the satellite

## Data Exploration
### Univariate Analysis
- **Launch Mass**: Most satellites have a launch mass ranging from 250 to 3750 kg with an average mass of 1950 kg.
- **Orbit Class**: More than 50% of satellites fall in the low Earth orbit category.
- **Country**: USA has the highest number of satellites, with India and China also in the top 10.
- **Purpose**: Communications and Earth observatory satellites are the most common.
- **Launch Years**: Satellite launches increased significantly starting from 1995 with a peak in 1998. Most satellites have an expected lifespan of 5-15 years.

### Bivariate Analysis
- **Users vs. Lifespan**: Commercial satellites generally have a higher expected lifespan compared to other users.
- **Correlation**: Significant correlations were found between:
  - Apogee and Perigee (0.91)
  - Apogee and Period (0.96)
  - Apogee and Inclination (-0.83)

## Feature Selection
Exhaustive Search was used for feature selection, with `f_regression` as the scoring function

## Model Building
### Models and Evaluation
The dataset was split into 80% training and 20% testing sets. The following regression models were used:

## Performance Evaluation
The performance of each model was evaluated, and the results are summarized as follows:

| Model                    | R2 Score | RMSE |
|--------------------------|----------|------|
| Linear Regression        | 0.70     | 4.24 | 
| AdaBoost Regression      | 0.84     | 3.01 | 
| KNN Regression           | 0.52     | 3.88 | 
| Random Forest Regression | 0.99     | 0.71 | 
| XGBoost Regression       | 0.99     | 0.65 | 
| XGBoost (Tuned)          | 0.99     | 0.57 | 
| Deep Neural Network      | 0.91     | 1.57 | 

### Hyperparameter Tuning
Hyperparameter tuning for XGBoost using Grid Search CV improved RMSE from 0.65 to 0.57 (nearly 20% improvement)

## Challenges
- Cleaning categorical variables and removing variants
- Deciding the amount of missing data to drop
- Selecting appropriate variables based on domain knowledge
- Hyperparameter tuning for the deep neural network

## Conclusion
Random Forest, XGBoost, and Deep Neural Network models provided excellent performance for predicting satellite lifespan. The choice of the model depends on the specific application and consistency of results, which was ensured using stratified k-fold cross-validation.
