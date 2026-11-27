# Week 6 – Golden Set Evaluation Using Llama 3.2

## Overview
This project focuses on evaluating the performance of a Large Language Model (LLM) using a Golden Question Set.

A collection of questions, expected answers, keywords, and reference sources is created. The Llama 3.2 model generates answers, which are compared with expected keywords to measure answer quality.

The first baseline evaluation is recorded as Release v0.1.

## Objectives
- Create a Golden Question Set with expected answers.
- Understand LLM evaluation and benchmarking.
- Run the Llama 3.2 model using Ollama.
- Compare generated answers with expected keywords.
- Calculate keyword matching scores.
- Identify passed, review, and failed responses.
- Save evaluation results in a CSV file.

## Technologies Used
- Python
- Ollama
- Llama 3.2
- Visual Studio Code
- JSON
- CSV
- Requests Library

## Project Structure
```text
Week-6/
│
├── golden_set.json
├── main.py
├── requirements.txt
└── baseline_results.csv
```

## Features
- Golden Question Set containing 30 questions.
- Automatic LLM answer generation.
- Keyword-based evaluation.
- Matched and missing keyword identification.
- Percentage-based scoring.
- PASS, REVIEW, and ERROR status identification.
- CSV report generation.
- Release v0.1 baseline evaluation.

## How to Run

1. Install Ollama on your system.
2. Download the Llama 3.2 model:

```bash
ollama pull llama3.2
```

3. Install Python dependencies:

```bash
pip install -r requirements.txt
```

4. Start Ollama and make sure the model is available.
5. Execute the Python program:

```bash
python3 main.py
```

## Output
The program generates `baseline_results.csv`, which contains:

- Question ID
- Question
- Expected Answer
- LLM Answer
- Matched Keywords
- Missing Keywords
- Evaluation Score
- Status
- Source
- Model
- Release Version

## Conclusion
This practical demonstrates how to evaluate LLM responses using a Golden Question Set and keyword-based scoring. It helps measure model performance, identify incorrect or incomplete answers, and establish a baseline evaluation for Release v0.1.
