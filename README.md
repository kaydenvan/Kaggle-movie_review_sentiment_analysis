# Kaggle Competition
This repository contains the code for a Kaggle competition, [Sentiment Analysis on Movie Reviews](https://www.kaggle.com/c/sentiment-analysis-on-movie-reviews/overview)

### First Submission
With a quick start, LSTM is used without any word cleansing for the dataset. The score is 0.63621, which is a very competitive score. However, since the competition is ended, ranking could be only found manually. Hence, it is 208 out of 860 (top 25%).


### Second Submission
This submission focuses on the comparison between LSTM and GRU, two similar neural networks where GRU has a less gate, forget gate.
**Learning**: <br>
1. GRU controls the flow of information with a full hidden content but not memory unit, therefore, the accuracy could be slightly lower than LSTM. In this case, the score of using GRU is 0.64129, which is higher than 0.63621 using LSTM. Hence, it changes my impression at all.
2. GRU is comparatively faster as GRU has two gates (Reset and update gates) and LSTM has three gates (Input, output and forget gates). In this case, the training time of using GRU is 12mins where 17mins for LSTM. Hence, GRU is almost 30% quicker than LSTM.

### Third Submission
In old neutral language process, it is very common to have word pre-processing including, <br>
1. lower case of all characters
2. remove punctuation words
3. remove stop word
4. stemming word
These methods work good in a small dataset since there are limited characteristics within the words and speed up the training. However, after word preprocessing, features are reduced significantly. In this case. although the data size in this competition is not large, 156k, there are still sufficient features within the word. The score of this submission drops to 0.61526. By reading on the score and validation loss, it is not good to keep all word pre-processing.

### Fourth Submission
In this submission, couple things have been merged in this model. <br>
1. Manual created 7 extra features based on the sentences. 
2. Created a merged model (i.e. Combining GRU NLP model result and Dense feature model result and further predict the sentiment)
3. Find optimal learning rate
Result: The score goes down to 0.63733
**Learning**: Manual decay learning rate has been created. This is in fact better than not to use any decay functions. Although Adam is expected to be auto-adjust the learning rate. The decay controls the upper limit of the learning rate could be. From the first three submission, I can see an obvious overfit since the validation loss goes up after few rounds of training.<br>
**Learning**: Manual extracted features do not provide any good improvement to the result. It may happen because of the features are coming from the text directly instead of extra metadata provided. The weighting of the model may also lower the NLP result accuracy.<br>

### Fifth Submission
This is the final submission to find the optimal model with limited computational power.<br>
1. Upsampling has been tried and see the result<br>
2. Word preprocessing has been done<br>
3. Extra CCN (Conv1D) has been added<br>
4. Added a exponential learning rate decay scheduler<br>
Result: The score goes back to 0.64173<br>
**Learning**: Upsampling does not give an improvement to the model. It is because the ratio of "very position" and "very negative" are relatively low. To upsampling the dataset is changing the dataset behavior. <br>
**Learning**: The accuracy could be improved by fixing typo from the dataset. However, this will result in huge computational demand. In such case, only very basic word cleansing have been done. But it will be good to fix typo issue, which will reduce noise from the dataset.<br>
**Learning**: Conv1D creates a convolution kernel that is convolved with the layer input over a single spatial (or temporal) dimension to produce a tensor of outputs. It works good on a sequence model and will reduce the computational demand. [More](https://stats.stackexchange.com/questions/295397/what-is-the-difference-between-conv1d-and-conv2d) However, this does not provide a big improvement to the model. <br>
**Learning** While the first four submissions show an importance on the impact of learning rate. 1e-3 has been used as the starting learning rate with an aggressive exponential decay (i.e. 0.75 decay rate on every 1000 steps). This significant reduce the training time and retain the performance. <br>

### Overall
In order to further improve the model accuracy, multiple GRUs / Conv1D + Batchnormalization could be helpful. Learning rate, batch size and epochs are key parameters to train the model.<br>
