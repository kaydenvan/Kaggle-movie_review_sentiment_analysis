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
