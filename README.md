# obfuscated_novel_detection
Novel detection on obfuscated data

Dataset is from https://www.kaggle.com/alaeddineayadi/obfuscated-multiclassification

Solution Description:

The code is included in a Jupyter notebook for the ease of visualisation.

After reading and checking the data for any need for cleaning, I performed the following:

1- I first attempted to initialise the embeddings based on the character position in the alphabet and inserting these integers to a trainable embeddings layer then using models beginning with CNNs to GRUs to LSTMs and Bidirectional LSTMs. The models were converging but the convergence was very slow and needed more processing power that I couldn't access. For example: 500 epochs were not enough to converge to more than 50% accuracy.

2- I used the glove vectors to initialise the embedding layer and still fine-tune it as due to obfuscation the learned embeddings can differ highly, however, the the learned representations can be useful for faster convergence, not to mention that if the obfuscation is only interleaving characters then the glove vectors will be even more useful.

Indeed the convergence speed was much higher but the training speed was lower (epoch
=3 mins on my MacBook pro), after 250 epochs  using 1 layer of LSTM and 1 hidden dense layer, the model reached around 83.5% training accuracy and 71% validation accuracy. The model was still converging and needed more training time. So more training time is required.

A Bidirectional LSTM using the same setup was similar, except the convergence was slightly faster, but the training time reached 5 mins per epoch).


To do:

1- Do cross-validation

2- Go deeper as I only used shallow models when using LSTM with 1 LSTM and 1 Dense hidden layer.

3- Hyperparameter optimization, especially for hyperparamteres such as dropout probability

4- Perform early stopping and save the best model.

5- Choose a suitable metric for validation as accuracy is not suitable for such imbalanced dataset, I prefer F1 score.

6- Also related to the imbalanced data, use other techniques for producing less biased models to specific classes, such as oversampling and other methods.

7- Train the models without glove embeddings for a long time (> 1000 epochs)

8- I am curious about the performance of transformers on this task 


For the current model that was incompletely trained for 250 epochs, the expected testing accuracy would be around 71% given the same data distribution as training set. I have no doubt that it will be higher when using the above points

