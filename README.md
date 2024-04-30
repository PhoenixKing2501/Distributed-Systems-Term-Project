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
### 1. Model Setup
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

### 2. Model at Work
The relevant file `ds_proj.ino` is present in `./ds_proj`. The live system is managed by four threads. They are as follows:
1. `inference_task`

This thread essentially simulates an ESP. It performs the model inference from the ESP readings. Every `5` second(s), it generates some random inputs, uses the trained model for inference and creates the following json file:
```
{
    id: <id of the ESP>
    state: <fire / not fire>
    time: <the logical clock value>
}
```

The json data is sent over an UDP port.

2. `udp_server`

This thread receives data from the `inference_task` threads over the UDP port. Every `1` second(s), it checks to see whether there is any data avaible over the UDP port. It saves the information from the `inference_task` threads in a log file. This log file is stored inside a little filesystem of the ESP itself. In case of failures, the log file persists. When the failed ESP again comes online, this thread ensures that the ESP starts from the last checkpoint itself. This is done using the logical timestamp.

3. `print_info`



