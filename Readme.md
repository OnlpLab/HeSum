# HeSum: A Novel Dataset for Abstractive Text Summarization in Hebrew

## Paper

The paper can be found [here]().

## Data

The data is composed of pairs of sub-heading + article scrapped from  [Shkuf](https://shakuf.co.il/), [ha-makom](https://www.ha-makom.co.il/), [the7eye](https://www.the7eye.org.il/)


The data can be found [here](https://huggingface.co/datasets/biunlp/HeSum).
You can also used the csv attached under the data folder.


The data can be downloaded directly from hugginface using datasets library in python.
```python
pip3 intall datasets
from datasets import load_dataset

hesum = load_dataset('biunlp/HeSum')
```
The data contains three data splits - train (8000 examples), validation (1000 examples) and test (1000 examples)

Each sample contains the following:

- `summary`: Sub-heading of an article
- `article`: The article.

## Models

There are two models fine-tuned on the HeSum dataset.
1. mT5LongHeSum-base (2.3 GB), [Download](https://huggingface.co/biunlp/mLongT5HeSum-base).
2. mT5LongHeSum-large (4.6 GB) [Download](https://huggingface.co/biunlp/mT5LongHeSum-large).

For running the model

```python

from datasets import load_dataset
from transformers import pipeline


dataset = load_dataset("biunlp/HeSum")['test']
hub_model_id = "biunlp/mT5LongHeSum-large"
summarizer = pipeline("summarization", model=hub_model_id)

article = "<Enter you text here>"
summarizer(article, max_length=250)
```
