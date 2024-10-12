# Starbucks Reviews Analysis with NLP

This project aims to apply Natural Language Processing (NLP) techniques to a dataset of Starbucks reviews. By utilizing the [spaCy](https://spacy.io/) library, various analyses were conducted to extract valuable insights into customer experiences and brand perception.

## Project Objectives

- **Sentiment Analysis**: Classify reviews into categories such as positive, negative, or neutral.
- **Entity Extraction**: Identify entities mentioned in the reviews, such as products, locations, and specific aspects of service.
- **Automatic Summarization**: Create summaries of the reviews to facilitate the visualization of customer opinions.
- **Data Visualization**: Generate charts and visualizations to illustrate the results of the analyses.

## Technologies Used

- **Python**: The programming language used for the development of the project.
- **spaCy**: A powerful NLP library that provides efficient tools for text processing.
- **Pandas**: A library for data manipulation and analysis.
- **Matplotlib/Seaborn**: Libraries for data visualization.

## Implemented NLP Functions

In the project, two main functions were created for text preprocessing and analysis:

1. **`nlp_function(text)`**: This function performs text preprocessing, applying the following steps:
   - **Lowercasing**: Normalizes the text to facilitate analysis.
   - **Removing unwanted characters**: Uses regular expressions to remove URLs, HTML tags, punctuation, and numeric characters.
   - **Lemmatization**: Applies the trained spaCy model to convert words to their base forms (lemmas).
   - **Stop Words Removal**: Filters out common words that do not add significant meaning to the analysis.

   ```python
   def nlp_function(text):
       ## Apply lower case
       text = str(text).lower()

       ## Removing characters
       text = re.sub(r'\[.*?\]', '', text)
       text = re.sub(r'https?://\S+|www\.\S+', '', text)
       text = re.sub(r'<.*?>+', '', text)
       text = re.sub(r'[%s]' % re.escape(string.punctuation), '', text)
       text = re.sub(r'\n', '', text)
       text = re.sub(r'\w*\d\w*', '', text)

       ## Applying the trained model (spaCy)
       doc = nlp(text)

       ## Lemmatization
       text = " ".join([token.lemma_ for token in doc])

       ## Remove stop words
       filtered_tokens = [token.text for token in doc if not token.is_stop]
       text = " ".join(filtered_tokens)

       return text
    ```

2. **`preprocess_text(text)`**: This function is responsible for filtering and lemmatizing the text, removing stop words and punctuation.
```python

    def preprocess_text(text):
        doc = nlp(text)
        # Filter words (tokens) by removing stop words and punctuation
        words = [token.lemma_ for token in doc if not token.is_stop and not token.is_punct]
        return words
```

## Installation

To run the project locally, follow the instructions below:

1. Clone the repository: git https://github.com/clariceahm/nlp_starbucks.git
2. Navigate to the project directory: cd yourrepository
3. Install the dependencies: pip install -r requirements.txt

After installation, you can run the included scripts to perform analyses. The results will be saved in output files or displayed in charts, depending on the script used.
