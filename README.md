# whatSymbol

# EMNIST Letter and Digit Recognition Project

This project focuses on training machine learning models to recognize handwritten letters and digits from the EMNIST Balanced dataset. The project explores different algorithms, data preprocessing techniques, regularization and uses a web interface via Gradio.

## Dataset
   - The [EMNIST](https://www.nist.gov/itl/products-and-services/emnist-dataset) dataset is used for training and testing the model.
   - EMNIST balanced consists of handwritten letters and digits.
   - The `emnist-balanced-train.csv` and `emnist-balanced-test.csv` files contain the pixel data for the images, and the `emnist-balanced-mapping.txt` file provides mapping between the labels to their actual value.

## Usage

1.  **Run the main script:**

    ```bash
    python letteranddigitrecognition.py
    ```

    This script will:
    *   Load the data.
    *   Preprocess the data (reshape, rotate, flip and normalize the images).
    *   Train various machine learning models (KNN, SVM, Random Forest, MLP).
    *   Evaluate model performance.
    *   Save trained models.
    *   Launch a Gradio interface for web testing.

## Models Implemented

The following models are implemented in this project:

*   **K-Nearest Neighbors (KNN):** A simple instance-based learning algorithm.
*   **Support Vector Machine (SVM):** A powerful classifier that finds an optimal hyperplane for data separation.
*   **Random Forest:** An ensemble learning method that combines multiple decision trees for robust predictions.
*   **Multi-Layer Perceptron (MLP):** A neural network architecture for complex classification tasks.

### Model Training Details

*   Each model is trained, saved and then reloaded to perform further analysis.
*   Cross-validation is performed to assess each model's performance.
*   GridSearchCV is used to regularize and improve the performance of each model.
*   The Keras and Tensorflow libraries are used to construct the MLP model.
*   Each model has implemented early stopping when the val_accuracy and val_loss are no longer improving.
*   Data augmentation is used to try to improve the overall performance of the model.

## Web Interface (Gradio)

The project includes a Gradio interface, allowing you to interact with the trained model through a web browser:

*   **Image Upload:** Upload an image of a handwritten letter or digit, and the model will predict the corresponding character.
*   **Sketchpad:** Draw a symbol directly on the interface, and the model will predict the drawn character.

After running the `letteranddigitrecognition.py` script, a Gradio link will be provided. Copy and paste it into your browser to launch the interface.

## Code Description

*   **Data Loading and Exploration:** The code starts by loading the training data and the mapping file. Basic information about the dataset is printed to understand the data.
*   **Data Preprocessing:**
    *   Handles missing data and duplicates, also verifies if the data is in the expected range.
    *   Data is reshaped, flipped, rotated and normalized.
    *   Visualizes images before and after transformations to see how the data is being processed.
*   **Model Creation and Training:**
    *   Each model is created and trained.
    *   Hyperparameter tuning and regularization is performed using `GridSearchCV`.
    *   Evaluation of the model using various performance metrics.
    *   Cross-validation is used to assess the model's generalization performance.
*   **MLP model:**
    *   The MLP model is trained using the Keras library, with the help of `EarlyStopping`, `ModelCheckPoint` and `ReduceLROnPlateau` callbacks.
    *   A grid search is used to determine the optimal parameters for the model.
*   **UI:** The Gradio interface makes the final model accessible to the user.

## Results
 - By using an MLP model, an accuracy of 86% was reached, making it the best model of the project.
 - The SVM model had the second best performance, with an accuracy of 84%.
 - Both the Random Forest and KNN models performed similarly, reaching an accuracy around 80%.
