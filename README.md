# stock-predictions-lstm

### LSTM Model
LSTM is a network model proposed by Schmidhuber et al. in 1997. It is a network model designed to solve the longstanding problems of gradient explosion and gradient disappearance in RNN. It has been widely used in speech recognition, emotional analysis and text analysis because this model has its own memory and can make relatively accurate forecasting. As we saw in the previous model, a traditional neural network also known as a feed-forward neural network, it has its input layer, the hidden layer and the output layer. An RNN has a looping mechanism that acts as a highway to allow information to flow from one step to the next. This information is the hidden state, which is a representation of previous inputs. The LSTM can solve the problem of short memory traditional RNN has.
More specifically, in our case in order to build our model, some modules from Keras were imported. Firstly the Sequential for initializing the neural network, Dense in order to add a densely connected neural network layer, LSTM for the Long Short-Term Memory layer and Dropout for adding dropout layers for preventing overfitting. 
Firstly, we add an LSTM layer. For the LSTM layer, we choose 50 units which is the dimensionality of the output, return_sequences = True which choose if the full sequence will be returned or the last output and finally we include the input_shape as the shape of our training set.
Then, for Dropout layers, we choose 0.2. This means that 20% of the layers will be dropped. Then we add the Dense layer. 
Our model is compiled with the adam optimizer and the loss is set as mean_squared_error. This function estimates the mean of the squared errors. The model runs for 100 epochs and the batch size is 32.

### Trained and test on the same stock
In the first case we choose the AAL stock from our dataset. There is the need for our model not to over-learn from training data and to be generalizing. For this reason, we split our dataset into training, validation and testing subsets. In the first experiment, we use only one stock (AAL), therefore these subsets are from the same dataset. We chose to make the separation as follow:
70% of the dataset is the training subset
10% of the dataset is the validation subset
20% of the dataset is the testing subset

The training and the validation subsets were used during the fit process of the model, while the testing subsets were during the prediction process.
We used the MeanSquaredError, MeanAbsoluteError, MeanAbsolutePercentageError from TensorFlow and we have the results as follow:
AAL MSE 3.6569757
AAL MAE 1.1791536
AAL MAPE 2.481861

       
### Test on unknown stock
In the second case, we use the AAL stock from our dataset in order to train our model and the GOOGL stock in order to make our predictions. We used again the MeanSquaredError, MeanAbsoluteError, MeanAbsolutePercentageError from TensorFlow and we have the results as follow:
GOOGL MSE 418.25244
GOOGL MAE 14.210677
GOOGL MAPE 2.38179


### Results
For both stocks AAL and GOOGL it is obvious that the predicted prices follow the trends of the actual prices of the stock. It is clear that there are small differences between the predicted and actual prices and the model takes a while to recognise the changes.

The mean squared error is higher when using stocks with higher prices (as expected). As we can see in the MAPE values, the GOOGL stock has a lower value even if it is an unknown stock for our model than the AAL stock.

