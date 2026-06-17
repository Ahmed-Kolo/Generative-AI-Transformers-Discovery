# Generative AI & Transformers Discovery Project

## Table of Contents

*   [Project Overview](#project-overview)
*   [Installation](#installation)
*   [Discovery Phase: Setup and Initialization](#discovery-phase-setup-and-initialization)
*   [Technical Phase: Implementation](#technical-phase-implementation)
    *   [Audit Task: Sentiment Analysis](#audit-task-sentiment-analysis)
    *   [Creator Task: Text Generation](#creator-task-text-generation)
    *   [Executive Summary Task: Summarization](#executive-summary-task-summarization)
*   [Action Phase](#action-phase)
    *   [Pre-training vs. Fine-tuning Explanation](#pre-training-vs.-fine-tuning-explanation)
    *   [Business Workflow Design (Upcoming)](#business-workflow-design-upcoming)
    *   [Hallucination & Bias Discussion (Upcoming)](#hallucination--bias-discussion-upcoming)
*   [Usage](#usage)
*   [Conclusion](#conclusion)

## Project Overview

This project serves as a hands-on discovery journey into Generative AI and Transformer models, primarily utilizing the Hugging Face `transformers` library. The goal is to set up and experiment with core Natural Language Processing (NLP) tasks like sentiment analysis, text generation, and text summarization. We will explore model capabilities, identify limitations (e.g., sarcasm detection), and understand practical considerations like output length control. Furthermore, the project delves into fundamental AI concepts such as pre-training vs. fine-tuning and considers the broader implications of deploying Generative AI, including potential biases and ethical considerations.

## Installation

To run this notebook, you need to install the `transformers` and `torch` libraries. The following command handles the installation:

```python
!pip install transformers torch
```

## Discovery Phase: Setup and Initialization

In this phase, we set up the environment and initialize the primary Hugging Face pipelines crucial for our exploration:

*   **Sentiment Analysis Pipeline:** Used for classifying text into positive or negative sentiments.
*   **Text Generation Pipeline:** Used for generating coherent and contextually relevant text based on a given prompt.
*   **Summarization Pipeline:** Used for creating concise summaries of longer texts.

These pipelines automatically download and load default pre-trained models (e.g., DistilBERT for sentiment, GPT-2 for text generation, BART-CNN for summarization) and their corresponding tokenizers. Initial `UserWarning` messages regarding `HF_TOKEN` are noted but do not impede the functionality for public models.

## Technical Phase: Implementation

### Audit Task: Sentiment Analysis

We audited the sentiment analysis pipeline with various test sentences, including a sarcastic one. The model successfully identified straightforward positive and negative sentiments. However, it demonstrated a key limitation: it **failed to correctly detect sarcasm**, misclassifying a sarcastic negative statement as positive. This highlights the challenge of nuanced language understanding for current models.

### Creator Task: Text Generation

The text generation pipeline was used to create domain-specific text based on a customer support prompt. We learned the importance of using `max_new_tokens` instead of `max_length` when attempting to control the length of the generated output, as `max_new_tokens` dictates the number of *new* tokens to generate beyond the prompt, ensuring the desired conciseness.

### Executive Summary Task: Summarization

The summarization task involved generating a short executive summary from a news article. Initial attempts faced a persistent `KeyError` with the `pipeline` function. This was ultimately resolved by bypassing the `pipeline`'s task recognition and directly loading the `AutoTokenizer` and `AutoModelForSeq2SeqLM` for the `sshleifer/distilbart-cnn-12-6` model. The model successfully generated a concise summary of the provided article, adhering to the specified word count constraints.

## Action Phase

### Pre-training vs. Fine-tuning Explanation

**Pre-training** is like a chef attending a general culinary school, learning broad cooking techniques and ingredient knowledge. In AI, this means training a model on vast, diverse text data to learn general language patterns, grammar, and facts.

**Fine-tuning** is like that chef specializing in an Italian restaurant after culinary school, applying their broad skills to master specific Italian dishes. In AI, this involves taking a pre-trained model and training it further on a smaller, specific dataset (e.g., customer support tickets) to make it highly proficient at a particular task (e.g., classifying support requests).

### Business Workflow Design (Upcoming)

*(This section will detail a business workflow for customer support using sentiment analysis, text generation, and summarization.)*

### Hallucination & Bias Discussion (Upcoming)

*(This section will identify instances of hallucination/bias observed or potential risks and discuss the risks of over-reliance on generative AI.)*

## Usage

To use the models, simply run the code cells in sequence. Ensure you have the necessary libraries installed. Each section demonstrates how to initialize and use the respective pipelines (sentiment analysis, text generation, summarization) with example inputs.

## Conclusion

This project provides a foundational understanding of Generative AI capabilities through Hugging Face Transformers. We've seen their power in various NLP tasks and encountered practical challenges, such as handling nuanced language (sarcasm) and troubleshooting library specific errors. Understanding the distinction between pre-training and fine-tuning is crucial for effective deployment, and the ongoing Action Phase will further explore real-world applications and ethical considerations.
