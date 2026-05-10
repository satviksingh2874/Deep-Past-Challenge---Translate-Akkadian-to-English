# Deep Past Initiative: Machine Translation

This repository contains our submission for the **[Deep Past Initiative Machine Translation](https://www.kaggle.com/competitions/deep-past-initiative-machine-translation)** competition on Kaggle. The goal of this competition was to develop advanced machine translation models to translate historical texts from ancient languages (e.g., Akkadian, Sumerian) into modern English, preserving linguistic nuances and contextual accuracy.

---

## 📌 Competition Overview
The **Deep Past Initiative** focuses on bridging the gap between ancient and modern languages using AI. Participants were tasked with:
- Translating cuneiform inscriptions and other historical texts.
- Handling low-resource languages with limited parallel data.
- Ensuring translations are both **accurate** and **contextually relevant**.

---

## 🔧 Our Approach
We employed a **hybrid approach** combining **fine-tuning** and **Retrieval-Augmented Generation (RAG)** to tackle the challenges of ancient language translation:

### 1. **Fine-Tuning with Unsloth**
   - Used **[Unsloth](https://github.com/unslothai/unsloth)** to efficiently fine-tune a **Mistral-7B** model on the provided dataset.
   - Optimized for **low-resource scenarios** with techniques like:
     - **LoRA (Low-Rank Adaptation)** for parameter-efficient fine-tuning.
     - **Gradient Checkpointing** to reduce memory usage.
     - **Mixed-Precision Training** (FP16/bfloat16) for faster convergence.

### 2. **RAG-Based System**
   - Integrated a **Retrieval-Augmented Generation (RAG)** pipeline to enhance translations using the **dictionary provided by the competition organizers**.
   - Steps:
     1. **Preprocessing**: Cleaned and tokenized the input text (see [`preprocessing.ipynb`](preprocessing.ipynb)).
     2. **Dictionary Lookup**: Used the provided dictionary to retrieve relevant translations for rare or ambiguous terms (see [`Dictionary_transcription_translation_extraction.ipynb`](Dictionary_transcription_translation_extraction.ipynb)).
     3. **Contextual Augmentation**: Combined retrieved dictionary entries with the input text to provide **context-aware prompts** to the fine-tuned model.
     4. **Post-Processing**: Applied spell-checking and grammar correction (see [`translation_spelling_correction.ipynb`](translation_spelling_correction.ipynb)).

### 3. **Pipeline Workflow**
   - **Data Scraping**: Extracted and organized raw data (see [`scraping_data.ipynb`](scraping_data.ipynb) and [`AICC_Scraping.ipynb`](AICC_Scraping.ipynb)).
   - **POS Tagging**: Part-of-speech tagging for better tokenization (see [`POS_Tagging.ipynb`](POS_Tagging.ipynb)).
   - **Model Training**: Fine-tuned the model with custom scripts (see [`rag_inference_plus_training_pipeline.ipynb`](rag_inference_plus_training_pipeline.ipynb)).
   - **Evaluation**: Validated translations using BLEU, TER, and human evaluation (see [`Research_pipeline_gemini.ipynb`](Research_pipeline_gemini.ipynb)).

---

## 📂 Notebooks
   Notebook | Description |
 |----------|-------------|
 | [`AICC_Scraping.ipynb`](AICC_Scraping.ipynb) | Scraping and organizing raw cuneiform data. |
 | [`Dictionary_transcription_translation_extraction.ipynb`](Dictionary_transcription_translation_extraction.ipynb) | Extracting and processing the provided dictionary for RAG. |
 | [`EBL_Dictionary_Processing.ipynb`](EBL_Dictionary_Processing.ipynb) | Additional dictionary preprocessing. |
 | [`Gensim_Akkadian.ipynb`](Gensim_Akkadian.ipynb) | Topic modeling for Akkadian texts. |
 | [`POS_Tagging.ipynb`](POS_Tagging.ipynb) | Part-of-speech tagging for tokenization. |
 | [`Pre_processing_validation.ipynb`](Pre_processing_validation.ipynb) | Data cleaning and validation. |
 | [`Research_pipeline_gemini.ipynb`](Research_pipeline_gemini.ipynb) | Experimental pipeline for translation evaluation. |
 | [`by5_updated(dict and pos).ipynb`](by5_updated(dict and pos).ipynb) | Updated dictionary and POS integration. |
 | [`preprocessing.ipynb`](preprocessing.ipynb) | General preprocessing steps. |
 | [`rag_inference_plus_training_pipeline.ipynb`](rag_inference_plus_training_pipeline.ipynb) | RAG + fine-tuning pipeline. |
 | [`scraping_data.ipynb`](scraping_data.ipynb) | Additional data scraping. |
 | [`sentence_processing.ipynb`](sentence_processing.ipynb) | Sentence-level processing. |
 | [`translation_spelling_correction.ipynb`](translation_spelling_correction.ipynb) | Post-processing for spelling/grammar. |

---
