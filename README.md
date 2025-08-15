# AIML425-A2

## Model 1

### Purpose
- Convert 2D Gaussian Data into 2D Uniform data

### Parameters
- Inputs: Randomly generated 2D Gaussian Data
- Number of Epochs: 5000
- Batch Size: 256
- Optimizer: Adam (lambda = 0.001)
- Loss Function: Maximum Mean Discrepancy

### Model Configuration
- Input layer: 2 Neurons
- 2 Hidden layers: 20 Neurons
- Output layer: 2 Neurons
- Activation function after hidden layers: Leaky ReLU
- Activation function after output layer: Sigmoid

### Loss Function
- Maximum Mean Discrepancy using the Gaussian Kernal to calculate pairwise similarities
- Compares predicted distribution (output of model) to target distribution (2D uniform data)

### Training the model
- Generate random 2D Gaussian and 2D Uniform data of size batch_size (256)
- Input gaussian data into model to get predicted data
- Calculate MMD loss by comparing predicted distribution to uniform distribution
- Backpropogate using the optimizer to shift weights away from the higher gradient
- Repeat over 5000 epochs

### Plot
- Generate 1000 random 2D gaussian vectors
- Input them into the trained model to get predicted 2D uniform data
- Plot on a scatter plot the input and output data to show the product of the model

### Details

- The model used was more simple as adding added complexity didn't reduce the final loss so it was unnecessary
- It had sigmoid as an activation function after the output to ensure the predictions were in the range [0, 1]
- MMD was used as the loss as the target out put was a distribution, so MMD is perfect as it outputs the similarity between two distributions
- Therefore, it could be used to train the model by pushing outputs towards that desired distribution

## Model 2

### Purpose
- Convert 2D Uniform Data into 2D Gaussian data

### Parameters
- Inputs: Randomly generated 2D Uniform Data
- Number of Epochs: 5000
- Batch Size: 256
- Optimizer: Adam (lambda = 0.001)
- Loss Function: Mean squared error

### Model Configuration
- Input layer: 2 Neurons
- 3 Hidden layers: 50 Neurons
- Output layer: 2 Neurons
- Activation function after hidden layers: Leaky ReLU

### Loss Function
- Mean squared error comparing predicted values to target values

### Training the model
- Generate random 2D Gaussian data of size batch_size (256)
- Input gaussian data into first model to get paired 2D uniform data
- Input 2D Uniform data into second model to get predicted 2D gaussian data
- Calculate MSE loss by comparing predicted values to paired gaussian target values
- Backpropogate using the optimizer to shift weights away from the higher gradient
- Repeat over 5000 epochs

### Plot
- Generate 1000 random 2D uniform vectors
- Input them into the trained model to get predicted 2D gaussian data
- Plot on a scatter plot the input and output data to show the product of the model

### Details
- The model used was more complex and used supervised training
- Doing this caused the output to be more random and follow a gaussian distribution more closely
- Otherwise the predictions tended to follow a square shape around the origin

## Model 3

### Purpose
- Convert 1D Uniform data into 2D Gaussian Data

### Parameters
- Inputs: Randomly generated 1D Uniform Data
- Number of Epochs: 5000
- Batch Size: 256
- Optimizer: Adam (lambda = 0.001)
- Loss Function: Maximum Mean Discrepancy

### Model Configuration
- Input layer: 1 Neurons
- 2 Hidden layers: 50 Neurons
- Output layer: 2 Neurons
- Activation function after hidden layers: Leaky ReLU

### Loss Function
- Maximum Mean Discrepancy using the Gaussian Kernal to calculate pairwise similarities
- Compares predicted distribution (output of model) to target distribution (2D gaussian data)

### Training the model
- Generate random 1D uniform and 2D Gaussian data of size batch_size (256)
- Input uniform data into model to get predicted data
- Calculate MMD loss by comparing predicted distribution to gaussian distribution
- Backpropogate using the optimizer to shift weights away from the higher gradient
- Repeat over 5000 epochs

### Plot
- Generate 1000 random 1D uniform
- Input them into the trained model to get predicted 2D gaussian data
- Plot on a scatter plot the predicted gaussian data and the 1D inputs along the x-axis (i.e., y = 0) to show the product of the model

### The Output: What failed

- The model didn't work.
-  I tried using supervised learning, adding complexity, changing the activation function, the optimizer and the loss function, and adding noise to the model.
-  However, the output always remained the same, all values were printed on a single (sometimes curved) line in 2D space.
-  I assume this is because the model acts much in the same way as algorithm would - transforming data. However, it can't replicate the sense of randomness that is required to generate gaussian data.
-  In the end I decided to keep my original (simple) attempt even though it didn't work as this best portrayed the intent of my model

## Additional Features

### Changing Activation Functions
- Parameters were added to the method in the model class to allow the user to change the activation function used.

### Testing different regularisations on model one
- By adding either "l1" or "l2" to the loop of the first model you can train the model using l1 or l2 regularisation
- You can also print out the weight distributions of the regularisations used after if desired

## Using the Program

### Adjusting parameters

#### Activation functions
- Can be changed by passing a different activation function as the argument when initialising models
- This only changes activation functions after hidden layers as sigmoid is always required after the output layer in model 2

#### Learning rate, Number of epochs, Batch Size, and lambda
- All can be easily changed by changing their respective global variables

#### Optimizer
- Can be changed by adjusting the function called when the optimizer variable is initialised

### Execution

#### How to Execute
- The program should be run using a GPU
- This can be done using Colab, which the code is designed to work with
- Simply change the runtime type to GPU before running

#### Output of execution
- Each model will train for 5000 epochs, producing the loss every 500 epochs
- For each model a scatterplot should be produced comparing inputs to outputs for a random sample


  
