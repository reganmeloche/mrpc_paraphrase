# Paraphrase Detection

The paraphrase task involves checking if two sentences are paraphrases of each other. This repo shows 3 approaches to the paraphrase task: 
- A baseline approach that makes use of TFIDF vectors and uses cosine similarity to measure the distance between these vectors. If the distance passes a certain threshold, then the sentence pair is marked as a paraphrase.
- The second approach uses a much more sophisticated scoring mechanism that combines different evaluation metrics, including one that accounts for word order. Like the baseline approach, we apply the scoring to the training set to learn a threshold, which is used to make predictions on our test set. This is based on a strategy defined in (this paper.)[https://ieeexplore.ieee.org/document/8639211]
- Finally we use a BERT-based approach, using DistilBERT. There is very little feature engineering or linguistic preprocessing involved here, as we are able to leverage the power of BERT using transfer learning. This approach borrows heavily from [this article](https://medium.com/mlearning-ai/nlp-day-26-semantic-similarity-with-bert-and-huggingface-transformers-ce76011d5a51). 

Begin by downloading the [dataset](https://www.microsoft.com/en-us/download/details.aspx?id=52398) and creating a folder in Google Drive where you can store it. Next run the data_cleaning notebook, which will format the data in a way that is easy to use for our 3 approaches. Now you can use any of the other three notebooks to explore approaches to the paraphrase task. More specific details for each approach are provided in the notebook.

The dataset used in this task is the Microsoft Research Paraphrase Corpus. It contains 5801 sentence pairs, each hand-labeled with a binary judgment as to whether the pair constitutes a paraphrase. More information about the dataset can be found [here.](https://www.microsoft.com/en-us/research/publication/automatically-constructing-a-corpus-of-sentential-paraphrases/)


## Results

Note that accuracy is not as valuable of a metric for this task since the dataset is unbalanced. We are more interested in the precision/recall/f-score. In the following table, these three metrics all represent weighted averages.

|              | Accuracy | Precision  | Recall | F-score |
|--------------|----------|------------|--------|---------|
| Baseline     | 0.63     | 0.70       | 0.63   | 0.64    |
| Semantic Sim | 0.63     | 0.74       | 0.63   | 0.64    |
| DistilBERT   | 0.82     | 0.82       | 0.82   | 0.81    |

