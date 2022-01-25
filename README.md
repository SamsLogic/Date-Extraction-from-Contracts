# Date-Extraction-from-Contracts
This is a NLP based project to extract effective date of the contract from their text files.

## Problem statement

This is a NLP based project where effective dates needs to be identified from the contracts as per the given text data of the contracts. The dates could be in any format for eg - 01/01/2022, 1st Jan, 2022, 1st January, 2022, 01 Jan 2022, etc.

## Libraries Used

1. Numpy
2. Tensorflow
3. keras
4. nltk
5. Sklearn
6. matplotlib
7. pandas

## Approach

### Data prerprocessing

To preprocess the text data the custom function was developed to preprocess the data as the convential libraires out there are not focused on preprocessing dates in a text corpus. To perform the requried tokenization and vectorization of the text nltk was used instaed of tensorflow or keras based text preprocessors. The preprocessing includes data cleaning (remvoing improper data lbaleing or file namings), stopwords removal, puncation removal but keeping in mind the punctutaions within a date like '/', spacing and seperating dates with words as there were cases where the numbers in the dates are conjoined with the preceding word, tokenization and vectorization of word. For vectorization of the word a normal word based vectorization was used as usig TF-IDF would not have made much difference in terms of date extraction.

Preprocessed data before vectorization:
![image](https://user-images.githubusercontent.com/41964069/150976544-18cb78f1-e6ad-4730-a0f0-cd9d05649fd3.png)

### Model Building

The model for this problem was a RNN based model with a bidirectional LSTM layer. the inputs of the model include the preprocessed data with 3 output values each predicting the values of a day, month and year respectively. 

The model was trained a decayed learning rate starting from a learning rate of 0.001 and trained for 80 epochs with a batch size of 8.

Model Architecture:
![image](https://user-images.githubusercontent.com/41964069/150977300-2db5590d-bbdc-470e-b877-5a4c7b85f97b.png)

## Results 

The model performed quite well being a baseline model to extract date using just a single Bidirectional LSTM layer. The prediction file is atatched to refer the results.
