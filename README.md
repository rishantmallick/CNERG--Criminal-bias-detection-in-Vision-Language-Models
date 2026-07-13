CNERG – Criminal Bias Detection in Vision-Language Models
Evaluated the multimodal reasoning capabilities of state-of-the-art Vision-Language Models (VLMs), including Qwen2.5-VL-7B-Instruct and its QLoRA fine-tuned variants, by implementing the MM-SHAP framework proposed in the research paper "MM-SHAP: A Performance-Agnostic Metric for Measuring Multimodal Contributions in Vision and Language Models Tasks." Developed a custom SHAP explainer to quantify the relative contributions of visual and textual modalities, achieving T-SHAP scores of 0.667 for the fine-tuned Qwen model and 0.669 for the base Qwen2.5-VL-7B-Instruct model.
Designed and implemented a Retrieval-Augmented Generation (RAG) pipeline for four Vision-Language Models—LLaVA-NeXT, Qwen2.5-VL-7B-Instruct, Idefics, and InternVL. Built a legal knowledge base using ChromaDB for document indexing and semantic retrieval, and evaluated the effect of retrieval augmentation on bail prediction using a dataset of 3,500 legal cases. Compared the performance of each VLM in both vanilla and RAG-enhanced settings to measure improvements in predictive accuracy and contextual reasoning.
Evaluated the semantic quality of automatically generated legal summaries by computing BERTScore between model-generated summaries and original case statements over 3,000 legal case records, providing a robust semantic similarity metric beyond traditional lexical overlap measures.
Conducted extensive ablation studies to analyze the dependence of Vision-Language Models on visual information. Evaluated Idefics and InternVL with and without RAG while intentionally removing image inputs, enabling a comparison of model performance across different caste groups and measuring the contribution of visual features to bail prediction.
Performed image clustering and feature analysis using CLIP embeddings and Qwen-3VL to identify visual characteristics that influence bail prediction. Investigated whether specific image attributes contributed to disparities in model decisions across different demographic groups.
Fine-tuned Qwen-3VL using QLoRA with the PEFT framework under multiple LoRA configurations. Compared configurations of r = 8, α = 16 and r = 64, α = 128, observing significant improvements in model performance. The former configuration achieved an accuracy of 56.3%, while the latter improved accuracy to 74.8%, demonstrating the impact of LoRA hyperparameters on multimodal fine-tuning.
Fine-tuned IndicBERT and MuRILBERT for caste prediction to accurately identify caste information from multilingual legal records containing both Hindi and English names and text. This preprocessing stage improved the reliability of downstream demographic analysis and bias evaluation.
Performed a comprehensive fairness evaluation of Vision-Language Models with and without Retrieval-Augmented Generation across multiple demographic attributes, including caste groups and age groups. Computed performance metrics such as Accuracy, Positive Predictive Value (PPV), Negative Predictive Value (NPV), Positive Likelihood Ratio (LR+), and Negative Likelihood Ratio (LR−) to compare predictive behavior across different population groups.
Investigated demographic bias in bail prediction by computing the Caste Conversion Ratio, measuring how frequently bail decisions changed across caste categories under different model configurations. Compared vanilla and RAG-enhanced Vision-Language Models to quantify the impact of retrieval augmentation on reducing or amplifying prediction bias.

This version is more suitable for a research internship or GitHub README because it clearly highlights the methodologies, datasets, evaluation metrics, and contributions while maintaining a professional tone.

for GITHUB readme

For a GitHub README, it is better to describe the project in a structured way with sections, bullet points, and concise explanations rather than writing it like a CV. Here's a polished version:

CNERG – Criminal Bias Detection in Vision-Language Models

This repository contains the implementation and experimental evaluation of Vision-Language Models (VLMs) for analyzing bias in judicial bail prediction. The project investigates how demographic attributes such as caste and age influence model predictions and evaluates whether Retrieval-Augmented Generation (RAG) can improve prediction accuracy while reducing bias.

Project Overview

The project focuses on:

Evaluating the performance of state-of-the-art Vision-Language Models on legal case understanding.
Investigating demographic bias in bail prediction.
Improving legal reasoning using Retrieval-Augmented Generation (RAG).
Explaining multimodal model decisions using SHAP-based attribution methods.
Fine-tuning Vision-Language Models for improved legal domain performance.
Vision-Language Models Evaluated

The following models were evaluated throughout the project:

Qwen2.5-VL-7B-Instruct
Qwen3-VL (QLoRA Fine-tuned)
LLaVA-NeXT
InternVL
Idefics

Each model was tested under both vanilla and Retrieval-Augmented Generation (RAG) settings.

Multimodal Explainability using MM-SHAP

To understand how Vision-Language Models utilize visual and textual information, we implemented the research paper:

MM-SHAP: A Performance-Agnostic Metric for Measuring Multimodal Contributions in Vision and Language Models Tasks

A custom SHAP explainer was developed to quantify modality contributions.

Results
Model	T-SHAP Score
Fine-tuned Qwen3-VL	0.667
Qwen2.5-VL-7B-Instruct	0.669
Retrieval-Augmented Generation (RAG)

A legal knowledge retrieval pipeline was developed using ChromaDB to provide additional context during inference.

Features
ChromaDB-based semantic indexing
Legal document retrieval
Context-aware prompting
Comparison between vanilla and RAG-based inference

The RAG framework was implemented for:

LLaVA-NeXT
Qwen2.5-VL-7B-Instruct
Idefics
InternVL

Experiments were conducted on a dataset containing 3,500 legal cases, comparing the bail prediction accuracy of RAG-enhanced models against their vanilla counterparts.

Summary Evaluation

Generated case summaries were evaluated using BERTScore on 3,000 legal cases to measure semantic similarity between generated summaries and the original case statements.

Ablation Studies

Multiple ablation experiments were performed to understand the importance of different modalities.

Experiments included:

VLM with images
VLM without images
VLM + RAG
VLM + RAG without images

These experiments helped analyze the influence of visual information on bail prediction across different caste groups.

Image Feature Analysis

Image representations were extracted using:

CLIP
Qwen3-VL

Feature embeddings were clustered to investigate whether specific visual characteristics contributed to differences in bail prediction across demographic groups.

Fine-Tuning Qwen3-VL

Qwen3-VL was fine-tuned using QLoRA through the PEFT framework.

Configuration Comparison
LoRA Rank	Alpha	Accuracy
8	16	56.3%
64	128	74.8%

The experiments demonstrate the impact of LoRA hyperparameters on legal-domain adaptation.

Caste Prediction Model

To accurately identify caste information from multilingual legal records, IndicBERT and MuRIL were fine-tuned on Hindi and English text.

This preprocessing stage improved the quality of downstream demographic analysis.

Bias Evaluation

The project evaluates model fairness across multiple demographic attributes, including:

Caste groups
Age groups

The following evaluation metrics were computed:

Accuracy
Positive Predictive Value (PPV)
Negative Predictive Value (NPV)
Positive Likelihood Ratio (LR+)
Negative Likelihood Ratio (LR−)

Additionally, Caste Conversion Ratio was introduced to quantify how frequently bail predictions changed across caste groups under different experimental settings.

Technologies Used
Python
PyTorch
Hugging Face Transformers
PEFT (QLoRA)
ChromaDB
CLIP
Qwen-VL
InternVL
Idefics
LLaVA-NeXT
SHAP
BERTScore
Pandas
NumPy
Scikit-learn

