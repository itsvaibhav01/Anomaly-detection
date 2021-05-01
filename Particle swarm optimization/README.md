# README.md
---
## Data and task 
- The csv file contains 31 columns including the class column which tells us if this perticular column is fraud or not 
- This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions
- Because we have such an imballanced distrubtion of classes we can not directly train our classifier otherwise it will quickly learn to predict everything as not fraud and will have very good acuracy
- So to deal with this skwed dataset we use only the 492 non fraud rows data along with 492 fraud data to make our classifer learn from features
- The non-fraud 492 rows of data are choosen randomly and total we get 492+492 = 984 rows of data to train our model.
- **More advance model will take the random non-fraud rows randomly from all data in every epoch**
- Then we split these 984 rows into train and testing data, taking 75% in training and 25% in testing. And they are choosen randomly from these 984 rows.
- Then we use standard scalling to scale down our data for better gradient descent optimization.
&nbsp;

- ![image.png](https://i.stack.imgur.com/obywE.png)
&nbsp;

- Then we reshape our data as 3d Data to make it process in convolutional neural network

&nbsp;
## The Model
---
- ![image.png](https://d2l.ai/_images/conv1d-channel.svg)
&nbsp;
- In model we first have 32 conv layers followed by 64 layers in second layer then we flatten the data to send it inside the NN
- the NN have 2 layers and a final softmax layer with 2 nurons to predict our classes (fraud or not)
- Inside the NN the no of Nuron for each layer is decided via the optimizer
- **In advance model we can also try changing the CNN kernal size and layers based on optimizer only**

- With in the search dict we give the our optimizer a range of values to try upon to get to global minima of opotimization

## particle swarm optimization
---
- we define a searh dict along with all the ranges optimizer can try upon
- then we define `performance` which takes `@optunity` as decorator and with in this we call our model and return the score(eg: accuracy) for the model 
- then we use `optunity.maximize` function and give it the `performance` function to give us the configuration to acchive the best hyper parameters.
- finally we train our new model on given hyper parameters and plot the confusion matrix 
&nbsp;
- ![image.png](https://glassboxmedicine.files.wordpress.com/2019/02/confusion-matrix.png)
&nbsp;
- Then we can get these values from confussion matrix.
![image.png](https://i.stack.imgur.com/U0hjG.png)