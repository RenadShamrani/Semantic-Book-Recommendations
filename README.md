# Semantic Book Recommendations

This repository contains a semantic book recommendation system implemented in a Jupyter notebook. The goal is to recommend books based on the meaning of a user’s query (topic, mood, short description, or quote) instead of simple keyword matching.

## How it works

- Preprocesses book metadata (title, author, description, etc.) from a dataset.
- Converts text into vector embeddings using an NLP model.
- Uses similarity search (e.g., cosine similarity) to find books that are semantically close to the user query.
- Returns the top matching books with their main information.

## Files

- `AISD_Poject-5.ipynb`: Main notebook that loads the data, builds embeddings, and generates recommendations.

## Requirements

- Python 3.x
- Jupyter Notebook
- pandas, numpy, scikit-learn (or any libraries you used for embeddings and similarity search)

## Usage

1. Open the notebook `AISD_Poject-5.ipynb` in Jupyter or Google Colab.
2. Install the required libraries if needed.
3. Run all cells.
4. Provide a query (description of the type of book you want), and view the recommended books.
