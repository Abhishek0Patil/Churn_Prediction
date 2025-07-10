# Customer Churn Prediction Web App

This project is an interactive web application built with Streamlit that predicts whether a bank customer is likely to churn (leave the bank). It uses a pre-trained deep learning model (built with TensorFlow/Keras) to provide real-time predictions based on user-provided customer data.

  <!-- You can replace this with a real screenshot of your app -->

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [File Structure](#file-structure)
- [Setup and Installation](#setup-and-installation)
- [How to Run](#how-to-run)
- [How It Works](#how-it-works)
- [Model and Data](#model-and-data)

## Features

-   **Interactive UI**: A user-friendly web interface for entering customer details.
-   **Real-time Predictions**: Instantly get a churn probability score.
-   **Simple Interpretation**: Clear output indicating if a customer is likely to churn or not.
-   **Powered by Deep Learning**: Utilizes a trained neural network for accurate predictions.

## Tech Stack

-   **Backend & ML**: Python
-   **Web Framework**: Streamlit
-   **Machine Learning**: TensorFlow (Keras)
-   **Data Manipulation**: Pandas, NumPy
-   **Model Preprocessing**: Scikit-learn
-   **Model/Encoder Persistence**: Pickle

## File Structure

The repository should be structured as follows for the application to work correctly:

```
.
├── app.py                   # The main Streamlit application script
├── model.h5                 # The pre-trained Keras model file
├── scaler.pkl               # The pre-fitted StandardScaler object
├── label_encoder_gender.pkl # The pre-fitted LabelEncoder for the 'Gender' feature
├── onehot_encoder_geo.pkl   # The pre-fitted OneHotEncoder for the 'Geography' feature
├── requirements.txt         # A file listing the project's dependencies
└── README.md                # This README file
```

## Setup and Installation

Follow these steps to set up the project on your local machine.

**1. Clone the repository:**
```bash
git clone https://github.com/your-username/customer-churn-prediction.git
cd customer-churn-prediction
```

**2. Create a virtual environment (recommended):**
This keeps the project's dependencies isolated from your global Python environment.
```bash
# For Windows
python -m venv venv
venv\Scripts\activate

# For macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

**3. Install the required dependencies:**
Create a `requirements.txt` file with the following content:

**`requirements.txt`**
```
streamlit
numpy
pandas
tensorflow
scikit-learn
```

Then, run the following command to install them:
```bash
pip install -r requirements.txt
```

## How to Run

Once the setup is complete, you can run the Streamlit application with a single command:

```bash
streamlit run app.py
```

Your web browser should automatically open a new tab with the running application. If not, open your browser and go to the local URL displayed in your terminal (usually `http://localhost:8501`).

## How It Works

The application follows a simple yet effective pipeline to make predictions:

1.  **User Input**: The user enters customer data through the Streamlit interface (e.g., Credit Score, Age, Balance).
2.  **Data Preprocessing**:
    -   The input data is collected into a Pandas DataFrame.
    -   Categorical features (`Gender`, `Geography`) are transformed into a numerical format using pre-fitted encoders (`LabelEncoder` and `OneHotEncoder`) that were saved during the model training phase.
    -   The complete feature set is then scaled using a pre-fitted `StandardScaler`. This is a critical step, as the model was trained on scaled data, and providing it with unscaled data would lead to incorrect predictions.
3.  **Prediction**:
    -   The processed and scaled input data is passed to the pre-trained Keras model (`model.h5`).
    -   The model outputs a prediction, which is the probability of the customer churning.
4.  **Display Results**:
    -   The application displays the raw churn probability (e.g., `0.75`).
    -   Based on a threshold of 0.5, it provides a clear, human-readable message: "The customer is likely to churn" or "The customer is not likely to churn."

## Model and Data

-   **Model**: The prediction model is a sequential neural network built with TensorFlow/Keras and saved as `model.h5`.
-   **Preprocessing Objects**: The `scaler.pkl`, `label_encoder_gender.pkl`, and `onehot_encoder_geo.pkl` files are essential. They store the "state" of the preprocessing steps applied to the original training data. Using them ensures that the live data entered by the user is transformed in the exact same way as the data the model was trained on.


