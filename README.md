# Distributed-Term-Project

## Members
* Utsav Basu - 20CS30057
* Anamitra Mukhopadhyay - 20CS30064
* Ritwik Ranjan Mallik - 20CS10049
* Gaurav Malakar - 20CS10029
* Bhanu Teja - 20CS10059

## Task Description

## How to Run

## Project Workflow
### 1. Model
The relevant files are contained inside `./model`. The usage of the important ones are given below:

1. `model.py`: Defines the model architecture.
2. `main.py`: Contains functions for training, testing and saving the best model.
3. `model.pth`: Contains the trained model weights from `pytorch`.
4. `weights.py`: Saves the model parameters inside `model_params.hpp` ready to be imported into a C++ source file.
5. `data.py`: Generates dummy data.
5. `eval.py`: Evaluates the model predictions.
5. `model_params.hpp`: Contains the saved parameters of the model ready to be imported into a C++ source file.
6. `model.hpp`: Defines the model architecture in C++. Uses the saved parameters from `model_params.hpp` to initialise the model's weights and biases.
7. `main.cpp`: Initialises the saved model in C++ and checks to see whether there are any bugs.
