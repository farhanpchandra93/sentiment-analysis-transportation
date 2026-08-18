# Sentiment Analysis of Transportation Infrastructure Comments
A Natural Language Processing (NLP) project that analyzes public sentiment from YouTube comments related to transportation and infrastructure topics.
The project covers the complete workflow from YouTube data collection and text preprocessing to sentiment classification using traditional machine learning and deep learning approaches.

## Project Overview
Public comments on transportation and infrastructure topics can provide useful insights into how people perceive infrastructure development and related issues.
This project explores sentiment analysis on YouTube comments by combining:

- YouTube comment scraping
- Text preprocessing
- Lexicon-based sentiment labeling
- TF-IDF feature extraction
- Traditional machine learning
- Deep learning with BiLSTM
- Model evaluation and comparison

## Objectives
- Collect comments from YouTube videos related to transportation and infrastructure.
- Prepare and preprocess Indonesian text data for NLP.
- Assign sentiment labels using a lexicon-based approach.
- Build sentiment classification models using machine learning and deep learning.
- Compare model performance based on classification metrics.
- Perform sentiment inference on new text.

## Dataset
The dataset was collected from YouTube comments related to transportation and infrastructure topics.
The final dataset contains approximately **32,004 comments**.

### Dataset Versions
The project contains three main dataset stages:

| Dataset | Description |
|---|---|
| `dataset_transportasi_raw.csv` | Raw comments collected from YouTube |
| `dataset_transportasi_processed.csv` | Dataset after text preprocessing |
| `dataset_transportasi_labeled.csv` | Dataset with sentiment labels |

The datasets are organized in the `data/` directory according to their processing stage.

## Data Collection
YouTube comments were collected using the **YouTube Data API v3**.
The scraping workflow includes:

1. Searching for relevant YouTube videos.
2. Collecting video IDs.
3. Retrieving comments from the selected videos.
4. Removing duplicate comments.
5. Filtering the collected comments.
6. Saving the resulting dataset for further processing.

The API credential is accessed through Google Colab Secrets and is not stored directly in the notebook.

## Sentiment Labeling
Sentiment labels were generated using a lexicon-based approach.
The labeling process was applied to the collected Indonesian comments before supervised sentiment classification.
The project also includes text normalization to better handle informal language and slang commonly found in Indonesian social media-style comments.

## Text Preprocessing
The NLP preprocessing workflow includes:

- Text cleaning
- Lowercasing
- Stopword removal
- Slang normalization
- Stemming
- Text normalization

The processed text was then used as input for feature extraction and model development.

## Feature Extraction
For the traditional machine learning models, text features were represented using **TF-IDF (Term Frequency–Inverse Document Frequency)**.
TF-IDF was used to transform the processed text into numerical feature vectors suitable for conventional machine learning algorithms.

## Modeling
The project compares traditional machine learning approaches with a deep learning model.

### Machine Learning
The following models were evaluated:
- Logistic Regression
- Linear Support Vector Machine (SVM)

### Deep Learning
A **Bidirectional Long Short-Term Memory (BiLSTM)** model was also developed to capture sequential patterns within the text.
This provides a comparison between conventional TF-IDF-based approaches and a neural network-based NLP approach.

## Model Results
The recorded test-set performance was:

| Model | Accuracy |
|---|---:|
| Logistic Regression | **86.29%** |
| Linear SVM | **86.66%** |
| BiLSTM | **88.29%** |

Among the evaluated models, **BiLSTM achieved the highest accuracy at 88.29%**.
The results demonstrate the progression from traditional NLP classification methods toward deep learning-based text classification.

## Inference
The project also includes an inference stage for testing sentiment classification on new text input.
This allows the trained model to be used to predict sentiment for previously unseen comments.

## Key Findings
- TF-IDF-based traditional machine learning models achieved strong baseline performance.
- Linear SVM slightly outperformed Logistic Regression in the recorded experiments.
- BiLSTM achieved the highest recorded accuracy among the evaluated models.
- Indonesian informal language and slang require dedicated normalization during preprocessing.
- The project demonstrates a complete NLP workflow from data collection to sentiment prediction.

## Project Workflow

```text
YouTube Videos
      │
      ▼
YouTube Data API
      │
      ▼
Comment Collection
      │
      ▼
Raw Dataset
      │
      ▼
Text Preprocessing
      │
      ├── Cleaning
      ├── Stopword Removal
      ├── Slang Normalization
      └── Stemming
      │
      ▼
Lexicon-Based Labeling
      │
      ▼
Sentiment Dataset
      │
      ├───────────────┐
      ▼               ▼
    TF-IDF          Tokenized Text
      │               │
      ▼               ▼
Logistic Regression  BiLSTM
Linear SVM             │
      │                │
      └───────┬────────┘
              ▼
       Model Evaluation
              │
              ▼
          Inference
