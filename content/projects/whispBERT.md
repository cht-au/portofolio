---
date: '2026-05-21T18:08:17-06:00'
draft: false
tags: ["Data Science", "Machine Learning", "NLP", "BERT"]
title: 'WhispBERT'
summary: "A BERT-based multilabel classifier trained on anonymous social media posts to flag sensitive and high-risk mental health content."
featured_image: "/images/bert.png"
---

## 📌 Project Overview
Our goal was to build an automated multilabel classifier to detect harmful and mental health-related content. Trained on anonymous social media posts from the Whisper app, this model classifies text across 5 distinct harm categories. The ultimate objective is to flag high-risk content for human review and provide necessary mental health resources to users in need.  

To achieve this, we leveraged **MentalBERT**, a specialized BERT-based model that was pre-fine-tuned on mental health discussions from Reddit.

---

## ⚙️ The Machine Learning Pipeline 

We structured our development process into a six-step pipeline:

1. **Data Cleaning:** Processed the raw text to remove empty, short, non-English, and duplicate posts.
2. **Ground Truth Creation:** Manually labeled a subset of posts to establish a high-quality dataset.
3. **Few-Shot Learning:** Trained a few-shot **SetFit** model on our labeled data, allowing the system to learn strong semantic representations with limited initial training data.
4. **Pseudo-Labeling:** Deployed the trained SetFit model to label the remaining posts across the entire dataset.
5. **BERT Fine-Tuning:** Trained our fine-tuned iteration of MentalBERT on this larger, auto-labeled dataset to maximize classification accuracy and model robustness.
6. **API Deployment:** Saved and packaged the finalized model as a production-ready API.

---

## 🚀 Results & Performance Insights

Our model achieved a **Macro F1 score of 82%** and a **Micro F1 score of 86%**, demonstrating that it can reliably and correctly classify roughly 4 out of 5 social media posts. 

During our analysis, we noted a few key behavioral insights:
* **Class Frequency Correlation:** We observed that our F1, Precision, and Recall scores correlate linearly with the frequency of specific labeled posts in the dataset.
* **The Data Sparsity Challenge:** The model recorded its lowest performance scores when classifying self-harm posts. This directly aligns with our frequency observation, as self-harm posts appeared far less frequently in the training data compared to highly frequent categories like sexually suggestive content.