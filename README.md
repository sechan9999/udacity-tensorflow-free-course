# Free Tensorflow Course from Udacity
These are the exercises and notes taken during Udacity's free Tensorflow Course.

# Preparation

## Install scripts

**Prerequisites**: Python3, pip3, virtualenv are already installed. Folder used: `MachineLearningVirtualEnv`.

1. `CreateMachineLearningVirtualEnv.sh`: create virtual environment in folder MachineLearningVirtualEnv
2. `InstallMachineLearningAppsInVirtualEnv.sh`: installed required pip packages. Must be run in the virtual environment
3. `StartMachineLearningVirtualEnv.sh`: start the virtual environment.

If `StartMachineLearningVirtualEnv.sh` does not start for some reason, use the following to start the virtual environment:

```Bash
source ./MachineLearningVirtualEnv/bin/activate
```

### Quit from virtual environment

```Bash
deactivate
```

### Start Jupyter

```Bash
jupyter notebook
```

## Install Tensorflow from scratch

I was using Ubuntu 18.04.

### Python3, pip3

```Bash
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
sudo apt-get install python3-dev python3-pip
sudo pip3 install -U virtualenv
```

### Create virtual environment in `./venv`

#### The --system-site-packages Option

If you build with `virtualenv --system-site-packages ENV`, **your virtual environment will inherit packages from /usr/lib/python2.7/site-packages (or wherever your global site-packages directory is).**

This can be used if you have control over the global site-packages directory, and you want to depend on the packages there. **If you want isolation from the global system, do not use this flag.**

If you need to change this option after creating a virtual environment, you can add (to turn off) or remove (to turn on) the file no-global-site-packages.txt from lib/python3.7/ or equivalent in the environments directory.

More: https://virtualenv.pypa.io/en/latest/userguide/#the-system-site-packages-option

#### The command

Create a new virtual environment by choosing a Python interpreter and making a ./venv directory to hold it:

##### With system-wide package usage

```Bash
virtualenv --system-site-packages -p python3 ./venv
```

##### Without system-wide package usage - better option in my opinion

```Bash
virtualenv -p python3 ./venv
```

### Activate virtual environment

```Bash
source ./venv/bin/activate
```

When virtualenv is active, your shell prompt is prefixed with (venv).

Install packages within a virtual environment without affecting the host system setup. Start by upgrading pip:

### Upgrade pip

```Bash
pip install --upgrade pip
```

### List packages installed within virtual environment

```Bash
pip list 
```

### Exit the virtual environment

```Bash
deactivate
```

## Install Tensorflow

```Bash
pip install --upgrade tensorflow
```

## Prepare Jupyter notebook in virtual environment

This assumes Jupyter notebook is already installed in the system.

### Create new virtual environment

#### Option 1: system-wide package usage

```Bash
virtualenv --system-site-packages -p python3 ./projectname
source projectname/bin/activate
```

#### Option 2: package usage only in the virtual environment

```Bash
virtualenv -p python3 ./projectname
source projectname/bin/activate
```

### Deactivate virtual environment

```Bash
deactivate
```

### Install Tensorflow, Tensorflow-datasets, matplotlib, Jupyter, jupyterthemes, ipykernel and numpy in virtual environment, and starting Jupyter notebook

Inside the virtual environment:

```Bash
pip install --upgrade tensorflow
pip install --upgrade matplotlib
pip install --upgrade tensorflow_datasets
pip install --upgrade ipykernel
pip install --upgrade numpy
pip install --upgrade jupyter
pip install --upgrade jupyterthemes
ipython kernel install --user --name=projectname
jupyter notebook
```

# Notes

## Useful Terms

* **Neural Networks**: A neural network is a network or circuit of neurons, or in a modern sense, an artificial neural network, composed of artificial neurons or nodes. Thus a neural network is either a biological neural network, made up of real biological neurons, or an artificial neural network, for solving artificial intelligence (AI) problems. The connections of the biological neuron are modeled as weights. A positive weight reflects an excitatory connection, while negative values mean inhibitory connections. All inputs are modified by a weight and summed. This activity is referred as a linear combination. Finally, an activation function controls the amplitude of the output. For example, an acceptable range of output is usually between 0 and 1, or it could be −1 and 1. Unlike von Neumann model computations, artificial neural networks do not separate memory and processing and operate via the flow of signals through the net connections, somewhat akin to biological networks. These artificial networks may be used for predictive modeling, adaptive control and applications where they can be trained via a dataset. Self-learning resulting from experience can occur within networks, which can derive conclusions from a complex and seemingly unrelated set of information.
* **Feature**: The input(s) to our model
* **Examples**: An input/output pair used for training
* **Labels**: The output of the model
* **Layer**: A collection of nodes connected together within a neural network.
* **Model**: The representation of your neural network
* **Dense and Fully Connected (FC)**: Each node in one layer is connected to each node in the previous layer.
* **Weights and biases**: The internal variables of model
* **Loss**: The discrepancy between the desired output and the actual output
* **MSE**: Mean squared error, a type of loss function that counts a small number of large discrepancies as worse than a large number of small ones.
* **Gradient Descent**: An algorithm the internal variables a bit at a time to gradually reduce the loss function.
* **Optimizer**: A specific implementation of the gradient descent algorithm. (There are many algorithms for this. In this course we will only use the “Adam” Optimizer, which stands for ADAptive with Momentum. It is considered the best-practice optimizer.)
* **Learning rate**: The “step size” for loss improvement during gradient descent.
* **Batch**: The set of examples used during training of the neural network
* **Epoch**: A full pass over the entire training dataset
* **Forward pass**: The computation of output values from input
* **Backward pass (backpropagation)**: The calculation of internal variable adjustments according to the optimizer algorithm, starting from the output layer and working back through each layer to the input.
* **Flattening**: The process of converting a 2d image into 1d vector
* **ReLU (Rectified Linear Unit)**: An activation function that allows a model to solve nonlinear problems. Typically f(x)=max(0,x)
  * **Noisy ReLUs**
  * **Leaky ReLUs**
  * **Parametric ReLUs**
  * **ELUs (Exponential Linear Units)**
* **Softmax**: A function that provides probabilities for each possible output class
* **Regression problem and model**: A model that outputs a single value. For example, an estimate of a house’s value
* **Classification problem and model**: A model that outputs a probability distribution across several categories. For example, in Fashion MNIST, the output was 10 probabilities, one for each of the different types of clothing. Remember, we use Softmax as the activation function in our last Dense layer to create this probability distribution
* **Training Set**: The data used for training the neural network.
* **Test set**: The data used for testing the final performance of our neural network.
* **Convolution**: The process of applying a filter (“kernel”) to an image. Max pooling is the process of reducing the size of the image through downsampling.
* **Convolutional Neural Networks**: A network which has at least one convolutional layer. A typical CNN also includes other types of layers, such as pooling layers and dense layers.
* **Kernel / filter**: A matrix which is smaller than the input, used to transform the input into chunks
* **Padding**: Adding pixels of some value, usually 0, around the input image
* **Pooling**: The process of reducing the size of an image through downsampling.There are several types of pooling layers. For example, average pooling converts many values into a single value by taking the average. However, maxpooling is the most common.
* **Max Pooling**: A pooling process in which many values are converted into a single value by taking the maximum value from among them.
* **Stride**: the number of pixels to slide the kernel (filter) across the image.
* **Downsampling**: The act of reducing the size of an image.
