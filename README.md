# Sentiment Analysis for Yelp Dataset Challenge 2018

This is a sentiment analysis of Yelp reviews dataset motivated by the Yelp dataset challenge that has been going on for some time now.

The link to the challenge can be found [here.](https://www.yelp.com/dataset/challenge)
The link to the relevant datasets can be found [here.](https://www.yelp.com/dataset/download)

For this analysis, the reviews dataset was primarily relevant to restaurants (Chinese, Italian, Mexican, etc.). For generalization to other datasets, the datasets for other types of services were used, including hair salons, home and garden, and bank & credit unions.

## Preprocessing

1. Removed reviews with 3 stars as they are neutral and doing this has improved accuracy across all of our analysis.
Clean and tokenize the reviews into list of words.
2. Removed common words from the reviews.
3. Added the sentiment column to classify a review as positive (4 or 5 stars) or negative (1 or 2 stars).
4. All lowercase, remove punctuations in the text column.

Only 3 variables were kept for this analysis: 
  1. Stars (number of stars/ratings)
  2. Text
  3. Sentiment (Pos or Neg)

## Long short-term memory (LSTM) 

Keras has been used for this analysis, as it is more user-friendly and easy to use than Tensorflow.
I closely followed the tutorial on implementing LSTMs in Keras [here.](https://towardsdatascience.com/understanding-lstm-and-its-quick-implementation-in-keras-for-sentiment-analysis-af410fd85b47)

```python
from sklearn.feature_extraction.text import CountVectorizer
from keras.preprocessing.text import Tokenizer
from keras.preprocessing.sequence import pad_sequences
from keras.models import Sequential
from keras.layers import Dense, Embedding, LSTM, SpatialDropout1D, CuDNNLSTM, Bidirectional
from keras.metrics import categorical_accuracy
from sklearn.model_selection import train_test_split
from keras.utils.np_utils import to_categorical

tokenizer = Tokenizer(num_words=2000, filters='!"#$%&()*+,-./:;<=>?@[\\]^_`{|}~\t\n',                                  
                      lower=True,split=' ')
tokenizer.fit_on_texts(review3['text'].values)
```
Note, my dataset is named "review3".
