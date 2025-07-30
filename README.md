# Extractive_Summarization_for_Airline_Review

This project uses zero-shot classification, rule-based logic, and sentiment scoring to extract meaningful summaries from real-world airline reviews. The goal is to identify key topics, classify emotional tone, and highlight the most expressive sentence for each review.

---

## Dataset

- **Source**: [Kaggle – Airline Reviews](https://www.kaggle.com/datasets/chaudharyanshul/airline-reviews)  
- The dataset contains over 3700 airline passenger reviews from multiple carriers
- Each review is stored in the `ReviewBody` column

---

## Core Techniques

| Task | Method |
|------|--------|
| **Topic Labeling** | Zero-shot classification using `facebook/bart-large-mnli` |
| **Fallback Logic** | Regex-based keyword rules for low-confidence predictions |
| **Sentence Splitting** | `spaCy` with `sentencizer` for accurate segmentation |
| **Sentiment Analysis** | `cardiffnlp/twitter-roberta-base-sentiment` |
| **Summary Selection** | Chooses sentence with strongest polarity for each labeled topic |

---

## Technologies Used

- Python 3.12
- Hugging Face Transformers
- spaCy
- pandas / NumPy / regex
- PyTorch (via Transformers)

---

## Features Highlights

- Assigns **thematic labels** to each sentence (e.g., "Baggage", "Customer Service Response")
- Identifies **dominant sentiment** (positive / neutral / negative)
- Extracts the **most emotional sentence** related to each key topic
- Uses a **fallback rule system** to ensure robustness on low-confidence predictions

---

## Sample Output Format (Multi-topic Summary)

| ReviewID | OriginalReview                          | Topic1                  | Summary1                                   | Topic2            | Summary2                                 | MostEmotionalSentence                         | EmotionTopic         | EmotionScore |
|----------|------------------------------------------|--------------------------|---------------------------------------------|-------------------|-------------------------------------------|------------------------------------------------|----------------------|---------------|
| 102      | The flight was delayed and staff was rude. | Flight Delay            | The flight was delayed                      | Staff & Service Attitude | The staff was rude                         | The staff was rude                              | Staff & Service Attitude | -0.92         |
| 203      | I loved the meal, but the boarding was chaotic. | In-flight Food and Drinks | I loved the meal                            | Boarding Process   | The boarding was chaotic                   | The boarding was chaotic                        | Boarding Process     | -0.65         |

---

## Files Overview

| File                                   | Description                                           |
|----------------------------------------|-------------------------------------------------------|
| `code/review_summary_and_dmodel.ipynb` | Data cleaning, feature engineering, model training    |
| `docs/final-report.pdf`                | Detailed written report                               |
| `docs/presentation-slides.pdf`         | Summary slide deck                                    |

