# Whisper Phoneme-Level Fine-Tuning

This repository contains code and scripts for fine-tuning [OpenAI's Whisper](https://github.com/openai/whisper) model for phoneme-level generation using a custom dataset.

## Overview

The goal of this project is to adapt Whisper for phoneme transcription instead of standard text transcription. This involves:

- Adding a dedicated `<|pad|>` token to resolve EOS conflicts
- Fine-tuning the decoder with a frozen encoder
- Using a phoneme-level tokenizer
- Evaluating performance using Character Error Rate (CER)

## Features

- Data preprocessing pipeline for phoneme-aligned datasets
- Custom tokenizer setup for phoneme sequences
- Layer-freezing strategy to reduce overfitting
- CER evaluation across training checkpoints
- Decoding pipeline for inference

## Dataset

The model was fine-tuned on a phoneme-labeled version of the [Svarah dataset from AI4Bharat](https://huggingface.co/datasets/ai4bharat/Svarah), with phoneme sequences generated using eSpeakNG.

## Training

The training script supports:

- Partial decoder training (top 30% layers unfrozen)
- Custom tokenizer integration
- Evaluation and logging of loss and CER per checkpoint

## Checkpoint Selection

After evaluation, the checkpoint at step 500 was selected as the final model due to its optimal trade-off between validation loss and CER.

## Inference

The decoding script takes raw audio and generates phoneme sequences using the fine-tuned model and phoneme tokenizer.

---
