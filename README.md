# NER Model for Entity Recognition in Product Descriptions

## Overview

This project implements a Named Entity Recognition (NER) model using the `DeepPavlov/rubert-base-cased` transformer model to identify specific entities (like product codes/IDs) in product descriptions. The model is trained to recognize entities marked as "ENT" (Entity) in Russian text data.

## Features

- Custom NER model based on BERT architecture
- Handles Russian language text
- Identifies product codes/IDs in various formats
- Provides both raw predictions and processed entity outputs
- Evaluation metrics including precision, recall, F1-score and accuracy

## Requirements

To run this project, you'll need:

- Python 3.6+
- PyTorch
- Transformers library
- Pandas
- Seqeval
- Evaluate
- Datasets

Install requirements with:
```bash
pip install seqeval evaluate pandas transformers datasets
```

## Data Preparation

The model expects input data in Excel format with columns:
- `text`: The full product description
- `entity`: The specific entity to be recognized within the text

The preprocessing script (`split_text_by_entity` function) splits the text into tokens and assigns tags (0 for non-entity, 1 for entity).

## Training

The model is trained with:
- Learning rate: 2e-5
- Batch size: 8
- Epochs: 3
- Weight decay: 0.01

Training metrics are logged and the best model is saved after each epoch.

## Usage

### Inference

Use the `predict_NER` function to get predictions:

```python
examples = [
    'Тест-система для идентификации линий ГМО "Соя A2704-12 идентификация" (50 тестов) Артикул:Sintol-GM-202-50',
    'Кольцо № 76086022',
    'ТРУБА 12X2X1120 ИЗОГ. 475 9853',
    'Нипель МОМ 209-38-11270_Артикул: 209-38-11270'
]

predictions, ents = predict_NER(examples)
```

The function returns:
- `predictions`: Raw model predictions with token-level labels
- `ents`: Processed entity strings extracted from the text

### Saved Models

Trained models are saved in the `ner_model` directory, including:
- Model weights
- Tokenizer
- Configuration

## Performance

The model is evaluated using standard NER metrics:
- Precision
- Recall
- F1-score
- Accuracy

Metrics are computed using the `seqeval` library.

## Limitations

- Primarily designed for Russian language text
- Best performance on product descriptions similar to training data
- May require retraining for significantly different text formats

## License

[Specify your license here if applicable]
