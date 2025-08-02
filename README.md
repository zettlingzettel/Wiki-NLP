# Wikipedia NLP Work-in-Progress
![IMG_0643](https://github.com/user-attachments/assets/7382e2a6-b5e1-4c16-96c0-09c320622881)
![IMG_0644](https://github.com/user-attachments/assets/9777bb79-30bb-43c8-b7a5-a503389c68c4)
![IMG_0645](https://github.com/user-attachments/assets/4dcb07fb-d498-4a80-95bc-b0ef3b85bd73)
![IMG_0646](https://github.com/user-attachments/assets/c10bbd9b-c8d6-4e50-a3e8-f3d3ef4fdb70)
![IMG_0647](https://github.com/user-attachments/assets/fed24aa7-c522-4f1a-8b1e-823de4465795)
![IMG_0648](https://github.com/user-attachments/assets/41be23bf-5341-422e-a37c-73ffd5b9efac)
![IMG_0649](https://github.com/user-attachments/assets/ea6549a9-8d6e-4590-b287-c9a85e149e0b)
![IMG_0650](https://github.com/user-attachments/assets/d471a917-5e68-4bab-90c9-d7649d5c9522)
![IMG_0651](https://github.com/user-attachments/assets/4e04b5b4-821d-43be-b9c5-92f6bba88f4d)
![IMG_0652](https://github.com/user-attachments/assets/6c9a5725-e4f4-4d7f-8d24-78ac82d5bd52)
![IMG_0653](https://github.com/user-attachments/assets/1b665d2f-ea5d-4534-bcb3-1e907d4def70)
![IMG_0654](https://github.com/user-attachments/assets/f784af4b-fefb-4aa9-a411-aa992d7d01ee)
![IMG_0655](https://github.com/user-attachments/assets/2727922e-f788-41f0-ab8e-662eb4497b73)
![IMG_0656](https://github.com/user-attachments/assets/4d0cdf03-49e9-4135-8615-d9e42a334248)
![IMG_0657](https://github.com/user-attachments/assets/486bfb03-872e-46c4-8d90-bd6f0bb61cac)
![IMG_0658](https://github.com/user-attachments/assets/90070967-4c13-48dd-97b9-9fa0f5154717)
![IMG_0659](https://github.com/user-attachments/assets/43ac9336-9135-4503-9f84-9ee957bfca1c)

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



