---
layout: doc
title: Setting Up
subtitle: Loading the Dataset
post_image: assets/images/home_credit_dataset.png
tags: [Profile]
toc: false
custom_links:
- text: Dataset
  url: https://www.kaggle.com/competitions/home-credit-default-risk/data
---

### Downloading the Data

If you already have a Kaggle account and cli tool configured, just run

```bash
kaggle competitions download -c home-credit-default-risk
```

to download the dataset.

Otherwise you need to create a Kaggle account first to have access to the datasets. Afterwards you can download it [here](https://www.kaggle.com/competitions/home-credit-default-risk/data). Alternatively, install and use [Kaggle API](https://github.com/Kaggle/kaggle-api).

<br>


### Creating a Database

Although it is possible to load data from file (locally or from S3), I prefer to imitate the working conditions and injest it into a relational database. Here I show how to 