# Persian Emotion Detection using ArmanEmo Dataset


 <img width="40" height="40" src="https://img.icons8.com/?size=100&id=kOPTH4LnJoIU&format=png&color=000000" alt="homework"/> Sentiments and opinions in online texts are highly important, and accurately detecting sentiments in the Persian language is a challenging task. In this project, we aim to perform sentiment analysis on Persian texts using pre-trained deep learning models.


# Emotion Recognition
Emotion recognition plays a crucial role in social and professional life, closely linked to cognitive abilities and communication skills. Companies strive to align their behavior, services, and products with customer expectations to ensure business growth.

# ArmanEmo Dataset
With the rise of open text data on social media platforms, sentiment analysis has gained attention. This study introduces ArmanEmo, a dataset of over 7,000 Persian sentences labeled for seven categories. The data, collected from Twitter, Instagram, and Digikala, is labeled based on Ekman's six basic emotions (anger, fear, joy, hate, sadness, surprise) and an additional category (other).

️# Data Preprocessing
To improve data quality, emojis, IDs, and links were removed. Heuristic and manual methods were used for classification, resulting in 12,000 sentences. After normalization and annotation, 4,700 sentences were labeled and split into training (3,500+) and test (1,100+) sets. ParsBERT was fine-tuned for this task.

# Labeling Process
7,500 sentences were manually labeled into emotion classes or two other categories ("unknown" and "other"). 38% of these sentences remained unlabeled, highlighting the challenge of emotion classification even for human annotators. 25% of the final labeled sentences were classified as "other," and some were labeled as "unknown" and excluded from the dataset.

# Data Cleaning
Raw data often contains various inconsistencies that hinder accurate analysis and modeling. Preprocessing aims to address these challenges, ensuring data reliability, accuracy, and completeness, ultimately improving analysis and predictions.

# Preprocessing Methods
•  Noise Reduction: Removing or correcting noisy, erroneous, inconsistent, or incomplete data.

•  Data Transformation: Converting text, audio, or image data into numerical data, normalizing, standardizing, or encoding data for compatibility with deep learning models.

•  Feature Selection: Reducing dimensionality, clustering data, and converting categorical, textual, or sequential data into numerical data.

•  Data Augmentation: Generating new data to enhance the dataset.

# Implementation
Using the Hazm library for normalization and lemmatization, we clean texts by removing extra spaces, fixing attachments, replacing Arabic letters with Persian ones, and finding the base form of each word. A function processes the text and returns the cleaned version.

•  Step 1: Replace characters like # and _ with spaces to reduce noise.

•  Step 2: Normalize text using the Normalizer class to remove diacritics, fix spacing, and replace Persian digits and quotes.

•  Step 3: Tokenize text into words or punctuation marks using tokenize_word.

•  Step 4: Remove punctuation from tokens to simplify them for further processing.
Tokenization and Punctuation Removal
For each token, a loop removes all punctuation marks from the list puncs (e.g., commas, periods, colons, quotes). This simplifies tokens for further text processing like lemmatization, named entity recognition, and sentiment analysis.

## Example
Original text:

»من امروز به مدرسه رفتم و یک کتاب جدید خریدم.«

Tokenized:

['»', 'من', 'امروز', 'به', 'مدرسه', 'رفتم', 'و', 'یک', 'کتاب', 'جدید', 'خریدم', '.', '«']

After punctuation removal:

['', 'من', 'امروز', 'به', 'مدرسه', 'رفتم', 'و', 'یک', 'کتاب', 'جدید', 'خریدم', '', '']

Final tokens:

['من', 'امروز', 'به', 'مدرسه', 'رفتم', 'و', 'یک', 'کتاب', 'جدید', 'خریدم']

#Removing Short Tokens and Numbers
Tokens with length ≤ 1 or containing only digits are removed.

Example
Original text:

من 2 تا برادر و 3 تا خواهر دارم. اسم برادرهام علی و مهدی و اسم خواهرهام زهرا، فاطمه و مریم است.

Tokenized:

['من', '2', 'تا', 'برادر', 'و', '3', 'تا', 'خواهر', 'دارم', '.', 'اسم', 'برادرهام', 'علی', 'و', 'مهدی', 'و', 'اسم', 'خواهرهام', 'زهرا', '،', 'فاطمه', 'و', 'مریم', 'است', '.']

After removal:

['من', 'تا', 'برادر', 'تا', 'خواهر', 'دارم', 'اسم', 'برادرهام', 'علی', 'مهدی', 'اسم', 'خواهرهام', 'زهرا', '،', 'فاطمه', 'مریم', 'است']

# Lemmatization
If enabled, tokens are lemmatized using the Lemmatizer class, converting words to their base forms.

# Transfer Learning for Sentiment Classification
We use transfer learning models for sentiment classification on ArmanEmo, leveraging pre-trained language models like ParsBERT and RoBERTa-XLM.

# Model Comparison
ParsBERT, a monolingual model for Persian, outperforms multilingual BERT in various NLP tasks. We also compare RoBERTa-XLM and EMO-XLM for sentiment detection in Persian.

trophy Selected Model
The chosen model, large-roberta-xlm, achieved over 70% accuracy, outperforming BERT and ParsBERT.

️# Model Architecture
RoBERTa-XLM is a multilingual version of RoBERTa, pre-trained on 2.5TB of filtered CommonCrawl data in 100 languages. It uses a transformer encoder with self-attention mechanisms and feed-forward neural networks.

# Improvements Over XLM
•  Larger pre-training dataset

•  More training steps

•  Removed Next Sentence Prediction (NSP) task

# Performance
RoBERTa-XLM achieves state-of-the-art results in multilingual NLP tasks, leveraging shared information across languages for improved performance.

# Article Overview
This article discusses the importance of sentiment analysis, the available Persian datasets, and the concept of mixed sentiments in texts. It explains the use of multi-label classification to identify multiple sentiments in a sentence.

️# Approaches
Different sentiment detection approaches are covered, including:
•  Rule-based methods: Based on linguistic rules.

•  Machine Learning methods: Use trained labels to classify unlabeled text efficiently. Algorithms like SVM, LSTM, and GRU are highlighted for their advanced results.

# Hybrid Approaches
Combining rule-based and ML approaches to leverage the strengths of both while minimizing their weaknesses. The idea is to implement a set of classifiers and enrich them with linguistic knowledge from dictionaries for more accurate sentiment detection.

# Dataset and Preprocessing
Details on the collection, labeling, and preprocessing of Persian datasets are provided. The article reviews the statistics of the datasets and compares various models.

# ⚙️ Model Training
The process of fine-tuning models using transfer learning is described. The article explains the use of dropout layers and the tokenizer for the large-roberta-xlm model. The model is compiled and trained, with results stored for analysis.

# Evaluation
The article evaluates the model using precision, F1 score, and recall. It includes a manual analysis of misclassified texts to understand model errors. The performance of two datasets is compared, highlighting the superiority of the training data.

# Confusion Matrix
A confusion matrix is used to show the performance of the classification algorithm, indicating the number of correctly and incorrectly predicted samples.

# Loss and Accuracy Charts
Charts showing the loss and accuracy for training and testing data are presented. The model's performance is analyzed over multiple epochs, with suggestions for improving generalization.

# Manual Testing
Functions for manually testing sentences and texts are implemented. The article discusses the challenges of classifying texts with mixed sentiments and the use of multi-label classifiers to address this issue.

# Evaluation Metrics Comparison
The article compares evaluation metrics with the results from the paper, showing higher average scores for precision, recall, and F1 score.

# Confusion Matrix
The confusion matrix from the project is compared with the one from the paper, demonstrating the model's appropriate performance in classifying texts according to their sentiments.

