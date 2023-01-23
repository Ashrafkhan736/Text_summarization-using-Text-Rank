The following is a readme file for a text summarization project that utilizes the TextRank algorithm.

# Data Cleaning

In this project, the data is cleaned using the re module for string manipulation. The prepocessing function takes in a pandas Series of articles as input and performs several preprocessing steps to clean and prepare the articles for further analysis. The steps include:

    Converting all the articles to lowercase.
    Removing URLs from the articles using regular expression.
    Saving a copy of the original articles for sentence tokenization.
    Removing trailing whitespaces from the articles.
    Removing punctuations from the articles.
    Removing stopwords from the articles.

# Text Summarization

The TextRank algorithm is used for text summarization. The sentence_score function takes in a list of normalized word frequencies, where each list element corresponds to an article. The function then tokenizes the sentences of the original articles, and scores each sentence based on the frequency of the words in it. The summary function takes in the scored sentences and generates a summary by selecting the top 25% of sentences with the highest scores, and joining them together with a white space. The final summary of each article is added to a summary list and returned by the function.

# Additional functions

    `normalize_frequency(article_li: List[Dict[str, float]]) -> List[Dict[str, float]])`
     This function takes in a list of dictionaries where each dictionary contains a word and its corresponding frequency in an article. The function finds the maximum frequency and normalizes all other frequencies by dividing them by the maximum frequency.

    `word_frequency(articles: pd.Series) -> List[Dict[str, float]]`
    This function takes in a pandas Series of articles, tokenizes the words, and calculates the frequency of each word in the article. The function returns a list of dictionaries where each dictionary contains a word and its corresponding frequency in the article.

    `summary(score_li: List[Dict[str, int]]) -> List[str]`
    This function takes in a list of dictionaries, where each dictionary contains a sentence and its corresponding score. The function then iterates over each dictionary, calculates the summary length (25% of the total sentences), finds the top sentences (based on their scores) using the nlargest() function, and joins them together using a white space. The final summary of each article is added to the summary_li list and the function returns this list.

    summarize(articles: pd.Series) -> List[str]
    This function takes in a pandas Series of articles as input, it first calls the prepocessing() function to clean and preprocess the articles. Then it creates a normalized word frequency using word_frequency() function and calculates the score for each sentence using sentence_score() function. Finally, it creates the summary of each article by calling summary() function and returns the list of summaries.

    sent_remove() -> List[str]
    This function takes the original article and the summary, tokenize the sentences of both and converts them into sets. It then removes the sentences present in summary from the set of sentences of original article and join the remaining sentences with white space. It returns the list of removed sentences.

    metric(row: pd.Series) -> float
    This function takes a row of pandas DataFrame and uses ROUGE-1 metric to calculate the similarity score between the original article and the summary. It returns the ROUGE-1 F1 score.

[Text](./result.csv)
