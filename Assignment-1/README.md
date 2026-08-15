# Practice Lab Assignment 1 - Neural Network Implementation from Scratch

## Objective

The aim of this practical is to understand how a basic neural network works by implementing it from scratch using Python and NumPy.

The forward pass, backpropagation, loss calculation and gradient descent are written manually instead of using TensorFlow, Keras or PyTorch.

## Dataset

The MNIST dataset is used for handwritten digit classification. It contains images of digits from 0 to 9, where each image is 28 × 28 pixels.

After flattening an image, it gives 784 input values. The pixel values are divided by 255 so that they are in the range 0 to 1.

For this practical, 12,000 images are used:

| Data | Images | Use |
|---|---:|---|
| Training | 8,000 | Used to train the model |
| Validation | 2,000 | Used to check the model during training |
| Testing | 2,000 | Used for the final evaluation |

The test data is kept separate and is not used while training the network.

## Neural Network Architecture

The network used in this practical is:

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
```

The input layer has 784 values because a 28 × 28 image contains 784 pixels.

The hidden layer has 64 neurons and uses ReLU activation. The output layer has 10 neurons, one for each digit from 0 to 9.

Softmax is used at the output to convert the values into probabilities.

## Activation Functions

### ReLU

ReLU is used in the hidden layer.

```text
ReLU(x) = max(0, x)
```

It keeps positive values and changes negative values to zero. Its derivative is used during backpropagation.

### Softmax

Softmax is used in the output layer. It converts the output values into probabilities for the ten digit classes.

The class with the highest probability is taken as the predicted digit.

## Loss Function

Cross-Entropy Loss is used to measure the difference between the actual digit and the predicted probabilities.

When the model gives a higher probability to the correct digit, the loss becomes smaller.

## Weight Initialization

He initialization is used for the weights because the hidden layer uses ReLU.

The biases are initialized to zero.

## Backpropagation

Backpropagation is used to find how the error should be passed back through the network.

First, the error is calculated at the output layer. The gradients are then calculated for the output and hidden layers, and these gradients are used to update the weights and biases.

## Mini-Batch Gradient Descent

The model is trained using mini-batch gradient descent with a batch size of 64.

For each batch, the network:

1. Performs a forward pass.
2. Calculates the predictions.
3. Calculates the loss.
4. Performs backpropagation.
5. Updates the weights and biases.

This is repeated for 15 epochs.

The validation set is checked after each epoch, while the test set is kept aside for the final evaluation.

## Results

The results obtained after training were:

| Metric | Result |
|---|---:|
| Training Accuracy | 97.01% |
| Validation Accuracy | 94.40% |
| Final Test Accuracy | 94.50% |
| Logistic Regression | 90.15% |

The training loss decreased from **0.4330** in the first epoch to **0.1149** in the last epoch.

This shows that the model was learning and reducing its error during training.

## Model Evaluation

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- Sample predictions

The confusion matrix shows that most predictions are on the diagonal, which means most of the digits were classified correctly.

Some mistakes still occur between handwritten digits that have similar shapes.

## Sample Predictions

The notebook also displays some test images along with their actual and predicted labels.

For example:

```text
Actual: 8 | Pred: 8
Actual: 7 | Pred: 7
Actual: 4 | Pred: 4
Actual: 8 | Pred: 8
Actual: 9 | Pred: 9
```

These are examples of predictions made on images from the test set.

## Comparison with Logistic Regression

Logistic Regression is used as a simple baseline model.

It is a linear model, while the neural network has a hidden layer with ReLU activation.

Both models are trained using the same 8,000 training images and evaluated on the same 2,000 test images.

| Model | Test Accuracy |
|---|---:|
| Neural Network from Scratch | **94.50%** |
| Logistic Regression | **90.15%** |

The neural network performed better by **4.35 percentage points**.

The hidden layer helps the neural network learn more complex patterns from the handwritten digit images.

## Analysis

The training loss decreased from 0.4330 to 0.1149 over the 15 epochs. At the end of training, the model reached 97.01% training accuracy and 94.40% validation accuracy.

The final test accuracy was 94.50%. The confusion matrix shows that most of the digits were classified correctly, although some mistakes were made between similar-looking handwritten digits.

Compared with Logistic Regression, the neural network performed better. Logistic Regression achieved 90.15%, while the neural network achieved 94.50%.

## Technologies Used

- Python
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

Scikit-learn is used for loading the MNIST dataset, splitting the data, calculating evaluation metrics and creating the Logistic Regression comparison model.

The neural network itself is implemented using NumPy.

## Project Structure

```text
Deep-Learning/
│
├── Assignment-1/
│   ├── Practice_Lab_1_MNIST_From_Scratch.ipynb
│   └── README.md
│
└── README.md
```

## How to Run

### Install the required libraries

```bash
pip install numpy matplotlib scikit-learn jupyter
```

### Open Jupyter Notebook

```bash
jupyter notebook
```

Open the notebook from the `Assignment-1` folder and run the cells from the beginning in order.

The MNIST dataset will be downloaded when the dataset-loading cell is executed.

## Conclusion

In this practical, a feedforward neural network was implemented from scratch using NumPy for handwritten digit classification.

The model achieved **94.50% test accuracy**. It also performed better than the Logistic Regression model, which achieved **90.15%**.

The practical helped in understanding the main steps involved in training a neural network, especially forward propagation, backpropagation and gradient descent.

## Files

| File | Description |
|---|---|
| `Practice_Lab_1_MNIST_From_Scratch.ipynb` | Neural network implementation, training, graphs and evaluation |
| `README.md` | Documentation for Assignment 1 |

## Student Details

**Name:** Sakshi Walunj  
**PRN No:** 202201040092  
**Branch:** CSE (AI & ML)  
**Batch:** A3

## Declaration

This practical was completed as part of the Deep Learning laboratory assignment.

The neural network was implemented using NumPy to understand the working of forward propagation, backpropagation and gradient descent.
