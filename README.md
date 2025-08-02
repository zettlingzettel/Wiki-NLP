# Wikipedia NLP Work-in-Progress

This repository contains a Jupyter Notebook, `wiki-nlp-work-in-progress.ipynb`, demonstrating Natural Language Processing (NLP) techniques applied to a subset of the Wikipedia Structured Contents Dataset.

---

## 📚 Dataset

The dataset used is the Wikipedia Structured Contents Dataset, available on Kaggle.

---

## 🧪 Notebook Overview

The notebook demonstrates a workflow involving data ingestion, cleaning, tokenization, and bigram analysis. The steps are as follows:

### 1. Download and Load Data
- Downloads a portion of the dataset using `kagglehub`.
- Loads the data into a Pandas DataFrame.

### 2. Data Conversion and Storage
- Converts the DataFrame into a `.parquet` file for efficient storage.
- Serializes the dataset to a JSON string.
- Saves the JSON string as both `.json` and `.csv` (the CSV contains the JSON string in a single column).

### 3. Data Preparation for NLP
- Loads the JSON into a Python dictionary.
- Flattens the structure into a list of dictionaries with `'Source'` and `'Target'` keys.
- Creates a DataFrame from this list.
- Filters rows where `'Source' == 'sections'`.
- Extracts section text from the nested `has_parts` structure in the `'Target'` column.
- Saves the extracted text to `out.csv`.

### 4. Text Cleaning and Tokenization
- Defines a `clean_text()` function that:
  - Converts text to lowercase.
  - Removes extra whitespace, special characters, and numbers.
- Downloads NLP resources:
  - NLTK: `punkt`, `stopwords`
  - spaCy: `en_core_web_lg`
- Reads `out.csv`.
- Merges all character columns into a single `Extracted_Text` column.
- Samples 10,000 rows.
- Applies `clean_text()` to generate a `Cleaned_Extracted_Text` column.
- Tokenizes and removes stopwords, storing the results in a `Tokens` column.

### 5. N-gram and Frequency Analysis
- Identifies and prints:
  - Top 10 and top 500 bigrams by raw frequency.
  - 100 most common individual words.
  - Bigrams where at least one word is in the top 100 words list.
- Calculates bigram scores using:
  - **Pointwise Mutual Information (PMI)**
  - **Likelihood Ratio**

---



