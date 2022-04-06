# Emotion Analysis of Writers and Readers of Japanese Tweets on Vaccinations

This is the official repo for "Emotion Analysis of Writers and Readers of Japanese Tweets on Vaccinations", accepted at [WASSA 2022](https://wassa-workshop.github.io/), a workshop at [ACL 2022](https://www.2022.aclweb.org/).

We fine-tune a [Japanese Wikipedia-pretrained BERT](https://huggingface.co/cl-tohoku/bert-base-japanese-v2) on [WRIME](https://github.com/ids-cv/wrime), a dataset for predicting intensity levels for Plutchik's 8 emotions for writers and readers from Japanese Tweets. We use the fine-tuned BERT to infer emotional intensities from a dataset of Japanese Tweets containing COVID-19 vaccine-related keywords. We then compare the inferred emotions to a set of vaccination measures in Japan.

## Repo contents

| file | contents |
| --- | --- |
| `Emotion Analysis of Writers and Readers of Japanese Tweets on Vaccinations.ipynb`<br>[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/PatrickJohnRamos/BERT-Japan-vaccination/blob/main/Emotion%20Analysis%20of%20Writers%20and%20Readers%20of%20Japanese%20Tweets%20on%20Vaccinations.ipynb) | fine-tuning, inference, and visualization code|
| `vaccine_tweet_ids.csv` | Tweet IDs for vaccine-related Tweet dataset |
| `vaccine_tweets_emotions.csv` | emotion analysis results on vaccine-related Tweet dataset | 

## About the vaccine-related Tweet dataset

We provide the IDs for the Tweets in `vaccine_tweet_ids.csv`. Use your preferred Twitter scraping library to scrape the Tweets themselves into a CSV file. To use with the fine-tuning code, name the file `vaccine_tweets.csv` and place the Tweet texts in a column named `text`.
