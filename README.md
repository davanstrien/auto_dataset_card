auto_dataset_card
================

<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

This file will become your README and also the index of your
documentation.

## Install

``` sh
python -m pip install git+https://github.com/davanstrien/auto_dataset_card.git
```

## How to use

writing dataset cards is essential. it is also time-consuming. wouldn’t
it be nice to generate parts of our dataset card automagically?

``` python
from auto_dataset_card.core import generate_label_breakdown_tables, get_label_counts
from datasets import load_dataset
ds = load_dataset('imdb',streaming=True)
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
