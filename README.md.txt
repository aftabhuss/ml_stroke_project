Stroke Prediction using Neural Networks 
Name: Hussain Aftab 
Neptun: KPEEAT 
This project develops a binary classification model using a Neural Network (Keras/TensorFlow) to predict 
the likelihood of a patient experiencing a stroke based on various health and lifestyle factors. 
Project Goal 
The goal of this project is to build a predictive model for stroke, with a focus on maximizing the model's 
ability to correctly identify positive stroke cases. 
Dataset 
I downloaded the Stoke Prediction Dataset from Kaggle. The dataset contains various features, 
including: 
Gender, age, hypertension, heart_disease, ever_married, work_type, Residence_type, 
avg_glucose_level, bmi, smoking_status.   
The target is: Stroke (1=yes, 0= no) 
Methodology 
1. Data Preparation and Preprocessing 
1. Missing Values were replaced using the median value. 
2. Outlier Handling: Outliers in continuous features ( bmi , avg_glucose_level ) were identified and addressed 
using the median. 
3. First when I evaluated the model and its accuracy was 95.11%. I looked into the dataset and found out that 
it is imbalanced (only 4.87% stroke cases). The same accuracy could be get from a dumb model (which gives 
only no stroke output). 
Dumb model accuracy = 100% - 4.78% = 95.22% 
It means the model I developed was acting like a dumb model. 
To fix this, I applied SMOTE (Synthetic Minority Over-Sampling Technique) to the training data. 
This creates synthetic stroke cases in the training set, giving the model enough data to learn the patterns of 
the stroke class. 
4. Encoding: Categorical features (e.g., gender , work_type , smoking_status ) were converted into numerical 
format using one-hot encoding. 
5. Scaling: All numerical features ( age , bmi , avg_glucose_level ) were standardized using StandardScaler to ensure 
they contribute equally to the model training process. 
6. Train-Test Split: The complete dataset was split into 80% training data and 20% testing data for model 
development and final evaluation. 
2. Model Architecture and Training 
A sequential Artificial Neural Network (ANN) was constructed and trained: 
 Architecture: Multiple dense layers with ReLU activation were used to capture complex patterns in the data. 
A Dropout layer (0.2) was included for regularization to prevent overfitting. 
 Output Layer: A single neuron with a Sigmoid activation function was used for the final binary prediction. 
Compilation: The model was compiled using the Adam optimizer and binary cross-entropy loss. 
Metrics: Key performance metrics tracked during training included Accuracy, Recall, and Precision. 
 Early Stopping: An EarlyStopping callback was implemented to monitor validation loss and automatically halt 
training once performance stabilized. 
Result 
The model's performance was evaluated on the unseen test set, demonstrating its predictive capabilities across 
both classes: 
 
                                                           Test Accuracy: 80.63% 
 
Test Recall (stroke): 52.00%   The model successfully identified 52% of all actual stroke cases. 
No Stroke Recall: 97%    The model remains highly accurate in identifying healthy individuals. 