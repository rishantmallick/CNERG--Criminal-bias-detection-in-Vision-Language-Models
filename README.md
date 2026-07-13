# CNERG – Criminal Bias Detection in Vision-Language Models

This repository presents a comprehensive study on **bias detection in Vision-Language Models (VLMs)** for judicial bail prediction. The project investigates how demographic attributes such as **caste** and **age** influence model decisions and evaluates whether **Retrieval-Augmented Generation (RAG)** can improve both prediction performance and fairness.

---

# Project Overview

The primary objectives of this project are:

- Evaluate the performance of state-of-the-art Vision-Language Models on judicial bail prediction.
- Analyze demographic bias across different caste and age groups.
- Improve legal reasoning using Retrieval-Augmented Generation (RAG).
- Interpret multimodal model decisions using SHAP-based explainability.
- Fine-tune Vision-Language Models for improved performance on legal datasets.
- Perform extensive fairness and ablation studies.

---

# Vision-Language Models Evaluated

The following Vision-Language Models were evaluated throughout this project:

- Qwen2.5-VL-7B-Instruct
- Qwen3-VL (QLoRA Fine-tuned)
- LLaVA-NeXT
- InternVL
- Idefics

Each model was evaluated under both **Vanilla** and **Retrieval-Augmented Generation (RAG)** settings.

---

# Multimodal Explainability using MM-SHAP

To quantify the contribution of visual and textual modalities, we implemented the research paper:

> **MM-SHAP: A Performance-Agnostic Metric for Measuring Multimodal Contributions in Vision and Language Models Tasks**

A custom SHAP-based explainer was developed to evaluate modality contributions for different Vision-Language Models.

### Results

| Model | T-SHAP Score |
|--------|--------------|
| Fine-tuned Qwen3-VL | **0.667** |
| Qwen2.5-VL-7B-Instruct | **0.669** |

---

# Retrieval-Augmented Generation (RAG)

A Retrieval-Augmented Generation framework was developed using **ChromaDB** for semantic indexing and retrieval of legal documents.

### Features

- Semantic indexing using ChromaDB
- Retrieval of relevant legal cases
- Context-aware prompting
- Comparison between Vanilla and RAG inference

The RAG pipeline was implemented for:

- Qwen2.5-VL-7B-Instruct
- LLaVA-NeXT
- InternVL
- Idefics

Experiments were conducted on a dataset containing **3,500 legal cases**, comparing the performance of vanilla VLMs with their RAG-enhanced counterparts for bail prediction.

---

# Summary Evaluation

To evaluate the semantic quality of generated legal summaries, **BERTScore** was computed between generated summaries and the corresponding case statements for **3,000 legal cases**.

---

# Ablation Studies

Several ablation experiments were conducted to understand the contribution of visual information and retrieval augmentation.

The following settings were evaluated:

- Vanilla VLM
- Vanilla VLM without image input
- RAG-enhanced VLM
- RAG-enhanced VLM without image input

These experiments helped analyze the dependence of Vision-Language Models on visual inputs while studying prediction behavior across different demographic groups.

---

# Image Feature Analysis

To investigate whether visual characteristics influence bail prediction, image embeddings were extracted using:

- CLIP
- Qwen3-VL

The extracted representations were clustered and analyzed to determine whether specific visual features contributed to different bail decisions across demographic groups.

---

# Fine-Tuning Qwen3-VL

Qwen3-VL was fine-tuned using **QLoRA** through the **PEFT** framework.

### Hyperparameter Comparison

| LoRA Rank | LoRA Alpha | Accuracy |
|-----------|------------|----------|
| 8 | 16 | **56.3%** |
| 64 | 128 | **74.8%** |

The experiments demonstrate the influence of LoRA hyperparameters on adapting Vision-Language Models to legal-domain tasks.

---

# Caste Prediction

To accurately identify caste information from multilingual legal records, **IndicBERT** and **MuRIL** were fine-tuned on Hindi and English text.

This preprocessing stage improved the reliability of downstream demographic analysis and bias evaluation.

---

# Bias Analysis

To understand demographic fairness, multiple bias metrics were computed across different **caste** and **age** groups for both vanilla and RAG-enhanced Vision-Language Models.

### Evaluation Metrics

- Accuracy
- Positive Predictive Value (PPV)
- Negative Predictive Value (NPV)
- Positive Likelihood Ratio (LR+)
- Negative Likelihood Ratio (LR−)

### Bias Metrics

- **Yes → No Conversion Rate:** Measures the percentage of cases where a prediction changes from **Grant Bail** to **Reject Bail** after modifying a demographic attribute.

- **No → Yes Conversion Rate:** Measures the percentage of cases where a prediction changes from **Reject Bail** to **Grant Bail** after demographic modification.

- **Net Bias:** Represents the overall directional bias of the model and is computed as:

  ```text
  Net Bias = (Yes → No Conversion Rate) − (No → Yes Conversion Rate)
  ```

  - Positive Net Bias indicates a tendency toward denying bail.
  - Negative Net Bias indicates a tendency toward granting bail.
  - A value close to zero indicates balanced model behavior.

These metrics were used to compare demographic fairness between vanilla and RAG-based Vision-Language Models.

---

# Technologies Used

- Python
- PyTorch
- Hugging Face Transformers
- PEFT (QLoRA)
- ChromaDB
- CLIP
- Qwen-VL
- InternVL
- Idefics
- LLaVA-NeXT
- SHAP
- BERTScore
- Pandas
- NumPy
- Scikit-learn

---

# Dataset

- **3,500** legal cases for bail prediction experiments.
- **3,000** legal case summaries for semantic similarity evaluation using BERTScore.
- Multimodal inputs consisting of legal case statements and associated images.

---


