# Detecting Algorithmic Bias in Large Language Models’ Interpretation of Yoruba Proverbs

## Overview

This project investigates how Large Language Models (LLMs) interpret culturally rich, low-resource language content, with a focus on Yoruba proverbs. It evaluates whether modern AI systems preserve cultural meaning or introduce distortions due to biases in their training data.

The work contributes to ethical AI by highlighting how underrepresented languages are affected by algorithmic bias and proposes a structured evaluation framework to assess this.

---

## Problem Statement

LLMs are predominantly trained on English-centric datasets, which leads to reduced performance in low-resource languages.

Yoruba, despite being widely spoken, is significantly underrepresented in AI training data. This results in:

- Loss of cultural nuance in translation  
- Misinterpretation of metaphorical expressions  
- Bias towards dominant cultural perspectives  

This project addresses this gap by evaluating how LLMs translate and interpret Yoruba proverbs.

---

## Objectives

- Develop a dataset of Yoruba proverbs with validated translations and interpretations  
- Evaluate LLM performance on translation and interpretation tasks  
- Detect and quantify algorithmic bias  
- Assess cultural alignment using structured frameworks  
- Propose improvements for AI systems handling low-resource languages  

---

## Dataset

The dataset consists of **2,948 Yoruba proverbs**.

Each entry contains:

- Original Yoruba proverb  
- Literal translation  
- Human interpretation  
- Thematic category  

---

## Methodology

### 1. Data Preparation
- Web scraping and dataset creation  
- Data cleaning and preprocessing  
- Handling missing values  

### 2. Model Evaluation

The following LLMs were evaluated:

- DeepSeek  
- Claude  
- Gemini  
- LLaMA  
- Mistral  

Each model was tasked with:
- Translating Yoruba proverbs  
- Providing interpretations  

### 3. Evaluation Metrics

#### Translation Metrics
- BLEU Score  
- BERTScore  

#### Semantic Evaluation
- Sentiment analysis comparison  
- Detection of polarity shifts  

#### Cultural Alignment
- Evaluation based on Hofstede’s cultural dimensions  
- Measurement of alignment with cultural values  

---

## Key Findings

- LLMs perform better in literal translation than interpretation  
- Cultural nuances are often lost or simplified  
- Significant variation exists across models  
- Outputs reflect biases from dominant training data  
- Low-resource languages are disproportionately affected  

---

## Contributions

- A structured framework for evaluating bias in cultural interpretation  
- A Yoruba proverb dataset for NLP research  
- Cross-model evaluation of LLM performance  
- Integration of cultural alignment into bias detection  
- Insights into building more inclusive AI systems  

---

## Technologies Used

- Python  
- Pandas, NumPy  
- Hugging Face Transformers  
- Sentence-BERT  
- BLEU, BERTScore  
- Matplotlib / Seaborn  

---

## Project Structure
├── data/
│ ├── raw_dataset.csv
│ ├── cleaned_dataset.csv
│
├── notebooks/
│ ├── data_cleaning.ipynb
│ ├── eda.ipynb
│ ├── evaluation.ipynb
│
├── models/
│ ├── prompts/
│ ├── outputs/
│
├── results/
│ ├── bleu_scores.csv
│ ├── bert_scores.csv
│ ├── sentiment_analysis.csv
│ ├── cultural_alignment.csv
│
├── src/
│ ├── preprocessing.py
│ ├── evaluation.py
│ ├── metrics.py
│
├── README.md
└── requirements.txt


---

## Ethical Considerations

- Reducing bias in AI systems  
- Preserving cultural integrity  
- Ensuring responsible AI usage  
- Promoting inclusivity in NLP  

---

## Future Work

- Extend to other African languages  
- Improve cultural evaluation metrics  
- Fine-tune models on culturally enriched datasets  
- Incorporate human evaluation  

---

## Conclusion

This project highlights the limitations of current AI systems in capturing cultural meaning in low-resource languages. It proposes a structured approach to evaluating and improving fairness in language models.

---

## Author

**Temisola Olajide**  
BSc (Hons) Computer Science & Artificial Intelligence  
Heriot-Watt University Dubai
