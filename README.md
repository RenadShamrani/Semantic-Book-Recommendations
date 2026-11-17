# Semantic Book Recommendations

> Academic prototype. Additional setup, a suitable dataset, and model downloads are required to run locally. This repository is not a production deployment.

### Find books by meaning, not just keywords

A notebook-based NLP project that turns a natural-language reading request into book recommendations. It combines sentence embeddings with vector search and includes an interactive Gradio interface.

[Explore the notebook](./semantic-book-recommendations.ipynb)

## How it works

```text
Book metadata -> cleaning -> sentence embeddings -> ChromaDB collection
User query    -> sentence embedding -> vector search -> ranked recommendations
```

- **Data preparation:** drops missing descriptions, keeps descriptions with at least 25 words, and combines book titles and descriptions for embedding.
- **Embeddings:** uses `sentence-transformers/all-MiniLM-L6-v2` through Sentence Transformers.
- **Retrieval:** searches a ChromaDB collection and ranks returned books by distance.
- **Interface:** a Gradio textbox accepts a reading request; a slider controls the number of recommendations.

Example query: `A story about friendship and rebuilding your life after a loss.`

## Technology

Python, Pandas, NumPy, Sentence Transformers, ChromaDB, Hugging Face Transformers, PyTorch, Jupyter Notebook, and Gradio.

## Running the notebook

1. Open `semantic-book-recommendations.ipynb` in Jupyter or Google Colab.
2. Supply a book metadata CSV. The notebook currently expects `books.csv.csv`; change `DATA_PATH` if your filename differs. The dataset is not bundled in this repository, and its provenance and redistribution license still need to be documented.
3. Ensure the CSV contains `title` and `description`. Optional fields used by the workflow include `subtitle`, `authors`, `categories`, `average_rating`, `ratings_count`, and `published_year`.
4. Run the installation cells, then the preparation, model-loading, and indexing cells. Initial model loading requires network access and may take time.
5. Enter a query in the notebook prompt or launch the Gradio interface in the final cells.

The notebook uses package upgrades without a pinned environment, so this is a source-based workflow guide rather than a clean-environment reproducibility guarantee. Review versions before running it in an existing environment.

## Evaluation and current scope

The notebook contains category-based Precision@k and self-retrieval Hit@k/nDCG@k experiments. Self-retrieval checks whether an indexed book can retrieve itself; it does not establish recommendation quality for unseen user queries. Category-based evaluation also queries the indexed corpus and is not a held-out benchmark.

Emotion and zero-shot category classifiers are exploratory components. Their current filtering branches do not exclude recommendations, and the Gradio path disables those filters. The implemented core is semantic vector retrieval, not validated emotion-aware personalization.

No production deployment or independently validated recommendation-quality score is claimed. The notebook initializes its collection by deleting any existing collection with the same name, so run it in a disposable project environment rather than against a shared database.
