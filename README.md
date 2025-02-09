# Balloon-Trajectory-Prediction-And-Analysis
Balloon Trajectory Prediction with Weather Data and Elevation

This Python-based project predicts the trajectory of weather balloons using position data from WindBorne's API, elevation data from OpenTopoData, and weather conditions. The project trains a Random Forest model to predict balloon positions (latitude, longitude, and elevation) based on past data, weather conditions, and elevation information. The predicted results are then plotted for analysis, and abnormalities in the predicted trajectory are analyzed.
Table of Contents

    Overview
    Data Fetching and Preprocessing
    Model Training
    Model Evaluation and Prediction
    How to Run
    Abnormality Detection
    Caveats and Limitations
    Results

Overview

This project aims to predict weather balloon trajectories by integrating data from the WindBorne API and OpenTopoData to create a robust model. The project includes:

    Fetching balloon position data from the WindBorne API.
    Fetching elevation data from OpenTopoData.
    Interpolating missing data and creating a structured dataset.
    Training a Random Forest Regressor to predict balloon positions.
    Evaluating the model's performance and plotting predicted vs actual balloon trajectories.
    Analyzing abnormalities in predicted trajectories.

Data Fetching and Preprocessing
1. Balloon Data Fetching

    The WindBorne API provides live data on balloon positions, which includes latitude, longitude, elevation, and pressure values at different hourly intervals.

2. Elevation Data Fetching

    Elevation data is fetched using OpenTopoData's API, which provides elevation information at specific geographic coordinates.

3. Data Interpolation

    Missing data points are interpolated using linear interpolation to fill in gaps in the dataset. This ensures that we have continuous data to train the model.

4. Feature Engineering

    Features are created by calculating the differences in latitude, longitude, elevation, and pressure between consecutive hours to represent the motion and change in the balloon's trajectory.

Model Training

A Random Forest Regressor model is used to predict the balloon’s future position (latitude, longitude, and elevation). The process includes:

    Preprocessing the balloon position and weather data.
    Scaling the input and output data using StandardScaler.
    Splitting the data into training and testing sets using train_test_split.
    Training a Random Forest Regressor model on the processed data.
    Saving the trained model and the scalers for future use.


Model Evaluation and Prediction

Once the model is trained, it is evaluated using the test data. The performance is assessed using Mean Squared Error (MSE).

For prediction, the trained model is used to predict future balloon positions (latitude, longitude, and elevation) based on the input data.


Results:

    Predicted vs Actual Balloon Trajectories: Visualize the balloon's predicted trajectory against the actual path. The model's predictions should closely match the actual path in most cases.

How to Run
First Run:

    Clone this repository.
    Run the Windata.ipynb file sequentially to fetch data from the WindBorne and OpenTopoData APIs and start training the model. This may take some time, especially due to API calls and model training time.


Abnormality Detection

Once the model has made predictions, we perform a basic anomaly detection to check if there are large deviations in the predicted balloon trajectories. We identify abnormalities by looking for large deviations in predicted positions from the actual positions.
Example Analysis:



Caveats and Limitations

    Data Limitations:
        Elevation data from OpenTopoData may not be available for all coordinates.

    Prediction Accuracy:
        While Random Forest is effective, the model's performance may vary depending on the complexity of balloon movement and environmental conditions.

    Weather Data:
        Weather data integration might be limited in resolution and accuracy due to API throttling or data unavailability.

Results

Visualizations generated after the prediction process allow you to see how well the model predicts the balloon's trajectory. Example plots compare the actual and predicted paths, showing how close the predictions are to the actual balloon movement over time.

Feel free to adjust the hyperparameters and experiment with different models (e.g., Gradient Boosting, Neural Networks) for improved accuracy in your predictions.
