This repository contains a Jupyter Notebook (wiki-nlp-work-in-progress.ipynb) demonstrating Natural Language Processing (NLP) techniques on a subset of the Wikipedia structured contents dataset.

Dataset
The dataset used is the Wikipedia structured contents dataset, available on Kaggle: https://www.kaggle.com/datasets/wikimedia-foundation/wikipedia-structured-contents/data.

Notebook Contents
The notebook performs the following steps:

Download and Load Data: Downloads a portion of the Wikipedia structured contents dataset using kagglehub and loads it into a Pandas DataFrame.

Data Conversion and Saving: Converts the DataFrame to a Parquet file for efficient storage and then to a JSON string, which is saved as both a .json and a .csv file (the .csv file contains the JSON string).

Data Preparation for NLP:

Loads the JSON data into a Python dictionary and flattens it into a list of dictionaries with 'Source' and 'Target' keys.

Creates a DataFrame from the flattened data.

Splits the DataFrame into training data.

Filters for rows where 'Source' is 'sections' and extracts text from the nested 'has_parts' structure within the 'Target' column.

Saves the extracted text into an out.csv file.

Text Cleaning and Tokenization:

Defines a clean_text function to preprocess text by converting to lowercase, removing extra whitespace, special characters, and numbers.

Downloads NLTK 'punkt' and 'stopwords' and Spacy 'en_core_web_lg' for text processing.

Reads the out.csv file.

Combines all character columns into a single 'Extracted_Text' column.

Samples 10,000 rows from the dataset.

Applies the clean_text function to create a 'Cleaned_Extracted_Text' column.

Tokenizes the cleaned text and removes stopwords, storing the result in a 'Tokens' column.

N-gram Analysis:

Identifies and prints the top 10 and top 500 bigrams based on raw frequency.

Calculates and prints the most common 100 words.

Filters and prints bigrams where at least one word is among the 100 most common words.

Calculates and prints all bigrams scored by Pointwise Mutual Information (PMI) and Likelihood Ratio.

Dependencies
The notebook requires the following Python libraries:

kagglehub

tqdm

scikit-learn

pandas

json

csv

nltk

spacy
