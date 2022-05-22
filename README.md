# Emotion Analysis of Writers and Readers of Japanese Tweets on Vaccinations

[[`paper`](https://aclanthology.org/2022.wassa-1.10/)] [[`HuggingFace model`](https://huggingface.co/patrickramosobf/bert-base-japanese-v2-wrime-fine-tune)]

This is the official repo for ["Emotion Analysis of Writers and Readers of Japanese Tweets on Vaccinations"](https://aclanthology.org/2022.wassa-1.10/), accepted at [WASSA 2022](https://wassa-workshop.github.io/), a workshop at [ACL 2022](https://www.2022.aclweb.org/).

We fine-tune a [Japanese Wikipedia-pretrained BERT](https://huggingface.co/cl-tohoku/bert-base-japanese-v2) on [WRIME](https://github.com/ids-cv/wrime), a dataset for predicting intensity levels for Plutchik's 8 emotions for writers and readers from Japanese Tweets. We use the fine-tuned BERT to infer emotional intensities from a dataset of Japanese Tweets containing COVID-19 vaccine-related keywords. We then compare the inferred emotions to a set of vaccination measures in Japan.

## Repo contents

| file | contents |
| --- | --- |
| `Emotion Analysis of Writers and Readers of Japanese Tweets on Vaccinations.ipynb`<br>[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/PatrickJohnRamos/BERT-Japan-vaccination/blob/main/Emotion%20Analysis%20of%20Writers%20and%20Readers%20of%20Japanese%20Tweets%20on%20Vaccinations.ipynb) | fine-tuning, inference, and visualization code|
| `vaccine_tweet_ids.csv` | Tweet IDs for vaccine-related Tweet dataset |
| `vaccine_tweets_emotions.csv` | emotion analysis results on vaccine-related Tweet dataset | 

## About the vaccine-related Tweet dataset

We provide the IDs for the Tweets in `vaccine_tweet_ids.csv`. Use your preferred Twitter scraping library to scrape the Tweets themselves into a CSV file. To use with the fine-tuning code, name the file `vaccine_tweets.csv` and place the Tweet texts in a column named `text`.

## Using the model

Our model is hosted on HuggingFace. You can find the model card [here](https://huggingface.co/patrickramosobf/bert-base-japanese-v2-wrime-fine-tune). The model can be loaded as follows:

```python
from transformers import BertJapaneseTokenizer, BertForSequenceClassification

# Note that we did not train a tokenizer. It should be the same as cl-tohoku/bert-base-japanese-v2.
tokenizer = BertJapaneseTokenizer.from_pretrained("patrickramosobf/bert-base-japanese-v2-wrime-fine-tune")

model = BertForSequenceClassification.from_pretrained("patrickramosobf/bert-base-japanese-v2-wrime-fine-tune")
```

## Citation

```bibtex
@inproceedings{ramos-etal-2022-emotion,
    title = "Emotion Analysis of Writers and Readers of {J}apanese Tweets on Vaccinations",
    author = "Ramos, Patrick John  and
      Ferawati, Kiki  and
      Liew, Kongmeng  and
      Aramaki, Eiji  and
      Wakamiya, Shoko",
    booktitle = "Proceedings of the 12th Workshop on Computational Approaches to Subjectivity, Sentiment {\&} Social Media Analysis",
    month = may,
    year = "2022",
    address = "Dublin, Ireland",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.wassa-1.10",
    pages = "95--103",
    abstract = "Public opinion in social media is increasingly becoming a critical factor in pandemic control. Understanding the emotions of a population towards vaccinations and COVID-19 may be valuable in convincing members to become vaccinated. We investigated the emotions of Japanese Twitter users towards Tweets related to COVID-19 vaccination. Using the WRIME dataset, which provides emotion ratings for Japanese Tweets sourced from writers (Tweet posters) and readers, we fine-tuned a BERT model to predict levels of emotional intensity. This model achieved a training accuracy of $MSE$ = 0.356. A separate dataset of 20,254 Japanese Tweets containing COVID-19 vaccine-related keywords was also collected, on which the fine-tuned BERT was used to perform emotion analysis. Afterwards, a correlation analysis between the extracted emotions and a set of vaccination measures in Japan was conducted.The results revealed that surprise and fear were the most intense emotions predicted by the model for writers and readers, respectively, on the vaccine-related Tweet dataset. The correlation analysis also showed that vaccinations were weakly positively correlated with predicted levels of writer joy, writer/reader anticipation, and writer/reader trust.",
}
```
