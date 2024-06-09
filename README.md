
# Subtheme Sentiment Analysis
    By Raj Narayanan

In this problem statement, we have multiple sentiments for a single review/entry. We are required to create a model that analyses the entries or reviews and generates sentiments accordingly.


## Approach

Since there are multiple sentiments associated with the reviews, we can consider this as a multi-label classification.

The entire approach has been incorporated into a single ipynb file instead of a modular approach for assignment submission purpose.

### Steps Followed:

1) The dataset was analysed initially. The prepocessing steps followed are:
    - It was found that there are 14 target labels.
    - Out of these 14 target labels, labels from 10 - 14 have only one label each, the rest are all missing values.
    - Upon further analysing these labels, it was found that entry 384 was causing the single label in these target labels.
    - Therefore, we are removing the entry 384 and the columns 10 to 14. We are also resetting the index
    - The label count gets reduced to 9 and we are combining these labels into a single target label.
    - Then it was found that there are empty labels for some entries. We are removing those entries.
    - We are then correcting the labels that don't have special charecters such as: /. This ensures that the similar labels are combined.

2) Encoding of target labels
    - We are using multi-label binarizer to encode the target labels.

3) Tokenize the reviews
    - We are using the Bert model tokenizer to tokenize the reviews

4) Convert labels into tensor

5) Creating the tensorflow dataset and separate into train and validation steps

6) Creating Distilbert model
    - We are creating a custom class with Distilbert model, a dropout layer and a final classification layer with sigmoid activation layer
    - we are then using the call function to initiate the forward pass of the model
    - We are creating the model using strategy.scope() since it is an LLM and requires GPU for faster training periods.

7) We compile the model using Adam optimizer, BinaryCrossEntropy() & BinaryAccuracy & train the model using model.

8) We fit the model using model.fit() with the training and validation datasets.

We observe that the validation loss is very low and the validation accuracy is very high.

## Observation, shortcomings and improvements

1) It is observed that despite adding dropout layers, the model tends to overfit as the validation accuracy is near 98%

2) Hyper-parameter tuning can be implemented to tune the performance of the model 

3) We are dropping the entries that had no labels at all. Instead what we can do is, we can consider these entries as test_data and use them for prediction.

4) As the model is overfitting and is biased towards the highly frequent labels, we can undersample those labels to regulate the bias of th model.

5) Another improvement is that, we can use other models to test and compare their performances, charts and visualization of their performance metrices can be made
## 🔗 Links
### Github
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://github.com/Raj-Narayanan-B)

### LinkedIn
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/raj-narayanan-balaji/)
