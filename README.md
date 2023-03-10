auto_dataset_card
================

<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

## Install

``` sh
python -m pip install git+https://github.com/davanstrien/auto_dataset_card.git
```

## What is this?

This repo currently contains a proof-of-concept, but the idea is that
this library will allow you to:

- pass in a 🤗 `datasets` dataset and get back helpful information for
  your dataset card, i.e. label frequencies
- optionally format this information in a friendly Markdown format,
  i.e. a Markdown table

Please see
[davanstrien/autogenerated-dataset-card](https://huggingface.co/datasets/davanstrien/autogenerated-dataset-card/blob/main/README.md)
for an example of a dataset card using this library for generating
information for a dataset card.

## How to use

``` python
from auto_dataset_card.core import generate_label_breakdown_tables, get_label_counts
from datasets import load_dataset

ds = load_dataset("imdb", streaming=True)
label_counts = get_label_counts(ds)
print(label_counts)
```

    {'train': {'neg': 12500, 'pos': 12500}, 'test': {'neg': 12500, 'pos': 12500}, 'unsupervised': {'no label': 50000}}

``` python
tables = generate_label_breakdown_tables(label_counts)
print(tables[0][1])
```

    | Label   |   Count | Percentage   |
    |---------|---------|--------------|
    | neg     |   12500 | 50.0%        |
    | pos     |   12500 | 50.0%        |
