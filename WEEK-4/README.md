# Week-4: Tokenizer Lab – Comparison of BPE, WordPiece and SentencePiece

## Project Description

This project focuses on understanding and comparing three popular subword tokenization techniques used in Natural Language Processing (NLP): **Byte Pair Encoding (BPE), WordPiece, and SentencePiece**.

The project uses Python and pretrained tokenizers to process text in three different languages: English, Telugu, and Hindi. It demonstrates how each tokenizer divides sentences into smaller units called tokens and converts them into numerical token IDs that can be understood by language models.

The main objective is to observe how different tokenization techniques split words, compare the number of tokens generated, and understand how tokenizer vocabulary and training data influence tokenization results.

## Technologies Used
- Python
- Hugging Face Transformers
- SentencePiece
- Visual Studio Code

## Tokenizers Compared
1. **BPE (Byte Pair Encoding):** Builds subword units by repeatedly merging frequently occurring adjacent symbol pairs. Model used: GPT-2.
2. **WordPiece:** Uses a learned vocabulary to divide words into smaller subword units. Model used: Multilingual BERT.
3. **SentencePiece:** Provides a language-independent framework for tokenization directly from raw text. Model used: XLM-RoBERTa.

## Languages Used
- English
- Telugu
- Hindi

## Key Features
- Implements three pretrained tokenization approaches.
- Compares tokenization results across three languages.
- Displays generated tokens and their numerical token IDs.
- Calculates the total token count for each tokenizer.
- Demonstrates multilingual text processing.
- Helps understand subword tokenization in NLP.

## Learning Outcomes
- Understand the importance of tokenization in language models.
- Differentiate between word-level and subword-level tokenization.
- Learn how BPE, WordPiece, and SentencePiece work.
- Compare token counts across different languages.
- Understand how tokenizers convert text into numerical IDs.

## Conclusion

This practical demonstrates how different tokenization techniques process multilingual text. By comparing BPE, WordPiece, and SentencePiece, we can understand how language models break sentences into smaller tokens and why token counts vary depending on vocabulary and training data.
