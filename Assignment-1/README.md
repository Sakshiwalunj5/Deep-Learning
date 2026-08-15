# Practice Lab Assignment 1 - Neural Network Implementation from Scratch

## Objective

The objective of this practical is to implement a simple feedforward neural network from scratch using Python and NumPy.

The main steps of the neural network, such as forward propagation, backpropagation, loss calculation, and gradient descent, are implemented manually without using deep learning libraries such as TensorFlow, Keras, or PyTorch.

---

## Dataset

The MNIST handwritten digit dataset is used for this practical.

MNIST contains images of handwritten digits from 0 to 9. Each image has a size of 28 × 28 pixels, giving 784 input features after flattening the image.

The pixel values are normalized from 0–255 to 0–1 before they are given to the neural network.

A stratified subset of 12,000 images is used for this practical.

### Dataset Split

| Dataset | Number of Images | Purpose |
|---|---:|---|
| Training | 8,000 | Used to train the neural network |
| Validation | 2,000 | Used to monitor the model during training |
| Testing | 2,000 | Used only for final evaluation |

The test data is kept separate from training so that the final accuracy gives a better estimate of how the model performs on unseen images.

---

## Neural Network Architecture

The neural network used in this practical has the following architecture:

```text
Input Layer
784 neurons
    ↓
Hidden Layer
64 neurons
    ↓
ReLU Activation
    ↓
Output Layer
10 neurons
    ↓
Softmax

Input Layer

The input layer contains 784 values because each MNIST image has 28 × 28 = 784 pixels.

Hidden Layer

The hidden layer contains 64 neurons and uses the ReLU activation function.

ReLU helps the network learn nonlinear patterns from the input images.

Output Layer

The output layer contains 10 neurons, representing the ten possible digits from 0 to 9.

Softmax is used to convert the output values into probabilities.

Activation Functions
ReLU

ReLU is used in the hidden layer.

ReLU(x) = max(0, x)

It keeps positive values and changes negative values to zero.

The derivative of ReLU is used during backpropagation to calculate the gradients.

Softmax

Softmax is used in the output layer.

It converts the output values into probabilities for the ten digit classes. The probabilities add up to 1, and the class with the highest probability is selected as the prediction.

Loss Function

Cross-Entropy Loss is used to measure the difference between the actual digit and the predicted probabilities.

A lower loss means that the predicted probability for the correct class is generally becoming higher.

Weight Initialization

He initialization is used to initialize the weights of the network.

It is suitable for the ReLU activation function and starts the weights with small random values.

The biases are initially set to zero.

Backpropagation

Backpropagation is used to calculate how much each weight and bias contributed to the prediction error.

The error is first calculated at the output layer and then passed backward through the network.

The gradients of the weights and biases are calculated and then used by gradient descent to update the network parameters.

Mini-Batch Gradient Descent

Mini-batch gradient descent is used for training.

The training data is divided into batches of 64 images.

For each batch:

The network performs a forward pass.
The predictions are calculated.
The cross-entropy loss is calculated.
Backpropagation calculates the gradients.
The weights and biases are updated using gradient descent.

This process is repeated for multiple epochs.

The model is trained for 15 epochs.

Training and Validation

The training set is used to update the weights and biases of the network.

The validation set is only used to check how the model is performing during training. It is not used to update the weights.

The test set is kept untouched until training is completed.

This gives the following flow:

Training Data
8,000 images
      ↓
Update weights
      ↓
Validation Data
2,000 images
      ↓
Monitor performance
      ↓
Training completed
      ↓
Test Data
2,000 images
      ↓
Final Evaluation
Results

The final results obtained from the implementation are:

Metric	Result
Training Accuracy	97.01%
Validation Accuracy	94.40%
Final Test Accuracy	94.50%
Logistic Regression Accuracy	90.15%

The training loss decreased from 0.4330 in the first epoch to 0.1149 in the last epoch.

This shows that the network was learning and reducing its prediction error during training.

Model Evaluation

The neural network is evaluated using the following measures:

Accuracy
Precision
Recall
F1-score
Confusion Matrix
Sample Predictions
Accuracy

Accuracy shows the overall percentage of test images classified correctly.

The final test accuracy of the neural network was:

94.50%

Classification Report

Precision, recall, and F1-score are calculated separately for each digit from 0 to 9.

This helps to see how well the model performs for individual classes instead of only looking at the overall accuracy.

Confusion Matrix

The confusion matrix shows the actual labels against the predicted labels.

Most of the predictions are concentrated along the diagonal, which means that most handwritten digits were classified correctly.

Some mistakes occur between digits that have similar handwritten shapes.

Sample Predictions

The notebook displays a few test images along with their actual and predicted labels.

For example:

Actual: 8 | Pred: 8
Actual: 7 | Pred: 7
Actual: 4 | Pred: 4
Actual: 8 | Pred: 8
Actual: 9 | Pred: 9

These examples show how the trained network performs on individual unseen images.

Comparison with Logistic Regression

Logistic Regression is used as a simple model for comparison.

It is a linear model, while the neural network has a hidden layer with ReLU activation.

Both models are trained using the same 8,000 training images and evaluated on the same 2,000 test images.

Model	Test Accuracy
Neural Network from Scratch	94.50%
Logistic Regression	90.15%

The neural network performed better by 4.35 percentage points.

The hidden ReLU layer allows the neural network to learn more complex patterns from the handwritten digit images.

Analysis

The training loss decreased from 0.4330 to 0.1149 over the 15 epochs, showing that the network was learning from the training data.

The training accuracy reached 97.01%, while the validation accuracy reached 94.40%. The difference between the two shows that the model performs slightly better on the training data than on unseen validation data.

The final test accuracy was 94.50%. The confusion matrix shows that most of the predictions were correct, although some errors occurred between visually similar handwritten digits.

The neural network achieved 94.50% accuracy compared with 90.15% for Logistic Regression. This shows that the neural network was able to learn more complex patterns than the simpler linear model.

Technologies Used
Python
NumPy
Matplotlib
Scikit-learn
Jupyter Notebook
Use of Scikit-learn

Scikit-learn is used only for:

Loading the MNIST dataset
Splitting the data
Calculating evaluation metrics
Creating the Logistic Regression baseline

The neural network itself is implemented manually using NumPy.

No TensorFlow, Keras, PyTorch, or other deep learning framework is used for the neural network implementation.

Project Structure
Deep-Learning-1/
│
├── Assignment-1/
│   ├── Practice_Lab_1_MNIST_From_Scratch.ipynb
│   └── README.md
│
└── README.md
How to Run
1. Clone the Repository
git clone https://github.com/Sakshiwalunj5/Deep-Learning-1.git
2. Open the Assignment Folder
cd Deep-Learning-1/Assignment-1
3. Install Required Libraries
pip install numpy matplotlib scikit-learn jupyter
4. Open Jupyter Notebook
jupyter notebook

Open the .ipynb file from the Assignment-1 folder.

5. Run the Notebook

Run the cells in order from the beginning.

The MNIST dataset is downloaded automatically when the dataset-loading cell is executed.

Conclusion

A feedforward neural network was successfully implemented from scratch using NumPy for handwritten digit classification.

The implementation includes forward propagation, activation functions, cross-entropy loss, backpropagation, mini-batch gradient descent, and model evaluation.

The model achieved a final test accuracy of 94.50%. It also performed better than the Logistic Regression baseline, which achieved 90.15% accuracy.

This practical helped in understanding how the main steps of a neural network work internally instead of relying on an in-built deep learning library.

Files
File	Description
Practice_Lab_1_MNIST_From_Scratch.ipynb	Complete implementation, training, evaluation, graphs, and results
README.md	Description and documentation of the practical
Student Details

Name: Sakshi Walunj
PRN No: 202201040092
Branch: CSE(AIML)
Batch: A3 
Declaration

This practical was completed as part of the Deep Learning laboratory assignment.

The neural network implementation was developed using NumPy to understand the working of forward propagation, backpropagation, and gradient descent.
