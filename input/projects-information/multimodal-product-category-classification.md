# Product Category Classification

## Project context

Individual Kaggle-style product-category classification project using an approximately 20K-row training set and a 5K-row test set.

## Technical evidence

- Built a PyTorch text-classification workflow with `vinai/phobert-large`.
- Tokenized product names and extended the sequence-classification model with fully connected, ReLU, and dropout layers.
- Used AdamW, cross-entropy loss, StepLR scheduling, validation, early stopping, and CUDA training.

## Result boundaries

Project-owner records show a private leaderboard score improvement from 0.77895 to 0.92219 after model fine-tuning, hyperparameter tuning, and prediction refinement. State this as a private leaderboard score, not validation accuracy or an official competition ranking.

## Relevance tags

NLP, Vietnamese NLP, PyTorch, PhoBERT, text classification, machine learning, Jupyter, Kaggle.
