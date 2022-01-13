# Fake or Real? News Classifier for Misinformations

The goal of this project is to create a model that can classify fake and real news to tackle the issue of misinformation.

---

# Data Cleaning
I will be using the Kaggle Fake or Real News Dataset as linked: https://www.kaggle.com/clmentbisaillon/fake-and-real-news-dataset

Note that our dataset consist of 2 csv files, one being true, the other being false. We need to work with a single dataset to train our model, thus let's start concatenating our 2 csv files.

Dataset for both True and Fake csv are then binary encoded and concatenated with a set limit to manage the amount of memory our NLP process will use.

Unwanted latters, characters and numbers were subsequently removed.

`title`, `text` and `subject` were merged into a single column and  all other rows except `true_news` are removed.

# EDA
N-Gram Count Vectorization is used to process our data into a sparse matrix of words, in particular (1,1) and (2,2) count vectorization were used. Other values may be used, subject to computing capabilities

TF-IDF Count Vectorization is also performed for comparison.

# Modelling

Naive Bayes Models were used (Bernoulli, Multinomial and Gaussian), however, it is clear the Multinomial Naive Bayes model is going to perform better than the other 2 as it is more suitable for text based classification problems of this nature. Logistics Regression and K-Nearest Neighbour Classifier algorithms were also used.

All models were ran on each vectorized data ((1,1) N-Gram, (2,2) N-Gram and TF-IDF)

Results were generally positive with a high recall, precision and accuracy on both Test and Train dataset that was train-test splitted into an 80/20 ratio.

# Future Improvement

### Fake news vs Real news
Currently, we are using Kaggle Real or Fake news dataset, which has it's data manually flagged. This means that our data could potentially have human error or imputed bias in our dataset. Thus, the agency that provided the data is important to maintain the integrity of the model.

### Mislabel of Propaganda News as Real News
Remember that ultimately, the agency is the ones who determine which data is real or fake. They may introduce propaganda by deliberately labelling news that otherwise is false or over-inflated as real news. Remember that history is written by victors and one should always read the provenance.

### Further Classification of different news category
Our data is currently merged together with the topic. We may be able to train individual models for each category to tailor to audience and search engine providers even better.

# Conclusion
Our model is able to attain above 95% threshold classification of real and fake news within the given input dataset.

---"# fakenews_classifier_1" 
