# Sequential Learning: Recurrent Neural Networks (RNNs) and Long short-term memory (LSTM)
RNNs are heavily reliant on recent inputs and tend to forget long-term dependencies, known as the vanishing gradient problem. LSTM is a type of RNN which aimed to solve the vanishing gradient problem by introducing a cell state during training. 

LSTMs have great improvements over RNNs in regard to capturing both short-term and long-term dependencies. 

Both models are trained and evaluated using a dataset of 40,000 Tweets from social media where each model must accurately predict whether a tweet is labelled in one of the following 3 categories: sadness, neutral, happiness.

The database was imbalanced: sadness: 5165 tweets (27.2%)
neutral: 8638 tweets (45.4%)
happiness: 5209 tweets (27.4%). Data Augmentation was considered, but the dataset had enough data from
each sentiment. Instead, random oversampling was used to increase the data from underrepresented classes to help balance the
sentiment classes without modifying the original Tweets.
200-dimensional GloVe embeddings are used to initialise the word representations.

The architecture was kept the same for a fair comparison. The only change was to the RNN or LSTM layer in the network. The training protocol uses sparse-categorical-cross-entropy with the Adam
optimiser, and I have introduced
early stopping protocols as well as model checkpointing and
ReduceLROnPlateau to minimise time-loss during experimentation.

# Results
The LSTM outperformed the RNN by 17% with a substantially lower crossentropy loss. This is because of LSTM’s gating mechanisms which mitigate
the vanishing-gradient issues in RNNs.
![Screenshot 2025-05-09 141127](https://github.com/user-attachments/assets/88651731-32ed-48de-ac13-510a36293384)

![image](https://github.com/user-attachments/assets/91d27fc8-c01f-4898-9122-01498c0ee7a2)
The testing results also show the higher accuracy from the LSTM.
The simple RNN struggles with long-range dependencies which leads to
underfitting, and this is clear from the results. The advantages of LSTM with
its input, output, and forget gates help it to regulate the information and
effectively categorise the tweets into the give sentiments.

The empirical results favour the LSTM architecture. The LSTMs ability to manage long-term dependencies and mitigate the vanishing gradient problem have resulted in a higher test accuracy (84.6% vs. 68.6% for RNN), proving its superiority over RNN in sequence learning tasks.

Tweets dataset from: https://www.kaggle.com/datasets/yessicatuteja/sentiment-analysis-of-tweets
