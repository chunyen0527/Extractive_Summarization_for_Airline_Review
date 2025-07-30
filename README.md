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

| ReviewID | OriginalReview                     | Summary1               | Topic1 | Summary2               | Topic2 | MostEmotionalSentence               | EmotionTopic | EmotionScore |
|----------|------------------------------------|------------------------|--------|------------------------|--------|-------------------------------------|--------------|--------------|
| 79      | An excellent flight in Club World on British Airways. The welcome aboard was warm and that continued throughout the flight. The crew were attentive, friendly and very professional. On board food for dinner and breakfast was good and there was a well chosen selection of wines. In flight entertainment offered a great selection of films and audio. The seat/flat bed was very comfortable - British Airways have done an excellent job in the design and comfort of the suites on board the A350. I liked the sleek, minimalist design. This flight showed that BA can be among the world? best airlines. | In flight entertainment offered a great selection of films and audio. | In-flight Entertainment | On board food for dinner and breakfast was good and there was a well chosen selection of wines. | In-flight Food and Drinks | This flight showed that BA can be among the world? best airlines. | Overall Airline Experience | 0.97 |

---

## Files Overview

| File                                   | Description                                           |
|----------------------------------------|-------------------------------------------------------|
| `code/review_summary_and_dmodel.ipynb` | Data cleaning, feature engineering, model training    |
| `docs/final-report.pdf`                | Detailed written report                               |
| `docs/presentation-slides.pdf`         | Summary slide deck                                    |

