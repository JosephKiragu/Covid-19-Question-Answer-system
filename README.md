# Covid-19 Question Answer System

This Question Answer System (QAS) is designed to answer questions based on a knowledge base generated from scientific articles. It utilizes BERT model for natural language processing and information retrieval techniques to find relevant articles and generate answers to user queries.

## Overview
The QAS is divided into two main components:

* Knowledge Retriever: A class responsible for building a knowledge base from scientific articles and finding the most relevant articles based on a user query.
* Answer Generator: A class that utilizes the pre-trained BERT model to generate natural language answers from the context provided by the Knowledge Retriever.

## Knowledge Base Creation

The knowledge base is generated using various natural language processing techniques, including keyword extraction, entity recognition, and phrase detection. The following code snippet shows how the knowledge base is created:

```from rake_nltk import Rake
import yake
import pandas as pd

# Initialize DataFrame structure for the knowledge base
triples_df = pd.DataFrame(columns=['paper_id', 'entity', 'relation'])

# Process each scientific article and extract relevant information
for item in files:
    # ...

# Save the triples_df to a CSV file
triples_df.to_csv('triples.csv', index=False)
```

## Usage
To use the QAS, first, create instances of KnowledgeRetriever and AnswerGenerator. Then, for each user question, preprocess the question, retrieve the top relevant articles, and get the text of the most relevant article. Finally, use the AnswerGenerator instance to generate a natural language answer using the BERT model.

```
knowledge_retrieval = KnowledgeRetriever('triples.csv')
answer_generator = AnswerGenerator()

# Main loop
while True:
    question = input("Please enter your question or type 'quit' to exit: ")
    # ...

    # Preprocess the question
    question = preprocess_text(question)

    # Retrieve the top relevant articles
    top_articles = knowledge_retrieval.get_matching_articles(question, top_n=3)

    # Retrieve the text of the most relevant article
    most_relevant_article_id, _ = top_articles[0]
    most_relevant_text = knowledge_retrieval.get_article_text(most_relevant_article_id)

    # Generate a natural language answer based on BERT
    answer = answer_generator.generate_answer(question, most_relevant_text)

    print("Answer: {}".format(answer))

# End of the main loop

```
## Dependencies
* transformers
* torch
* pandas
* scikit-learn
*nltk
* yake
* spacy
* pke

## Installation

you need to download the necessary language models for
1. Spacy :
```
python -m spacy download en_core_web_sm

```
2. SciSpacy
```
pip install https://s3-us-west-2.amazonaws.com/ai2-s2-scispacy/releases/v0.5.1/en_core_sci_sm-0.5.1.tar.gz
```

## Contributing
Feel free to fork this repository, make changes, and submit pull requests. We appreciate your contributions to improve the QAS!






