# Arabic Document Intelligence Platform

## Project Title
**Arabic Text Classification for News Articles using AraBERT with LoRA**

## Team Members
- شهد صالح حسين (20220237)
- جهاد عبد الغني دمرداش (20230161)
- حماس محمد محمود (20230180)
- رحمة حسان عبد القادر (20230201)
- سارة علي السيد (20230247)
- ملك رجب عشري (20230574)
- ملك هاني عيسى (20230582)

## Problem
Manual classification of Arabic news articles is slow, costly, and inefficient. Most NLP tools focus on English.

## Solution
We fine-tuned **AraBERT v2** with **LoRA** to classify Arabic news into 7 categories with **97.87% accuracy**.  
We also built:
- A **Gradio web interface** for real-time testing
- An **event-driven AWS pipeline** (S3 → SQS → Lambda → S3) for batch processing

## Dataset
- **SANAD** (45,500 articles)
- 7 classes: Sports, Finance, Medical, Politics, Religion, Culture, Tech
- Split: 80% train / 10% validation / 10% test

## Model & Training
- Base model: `aubmindlab/bert-base-arabertv02`
- Fine-tuning: LoRA (r=16, alpha=32, dropout=0.1)
- Trainable parameters: 0.44% of the model
- Training environment: Kaggle (GPU T4, ~4 hours)

## Results
| Model | Accuracy | F1 (weighted) |
|-------|----------|----------------|
| Base AraBERT (no fine‑tune) | 13.74% | 10.43% |
| **LoRA Fine‑tuned** | **97.87%** | **97.87%** |

- **5‑fold cross validation**: 97.11% ± 0.33%

## How to Run the Deployed Demo (AWS EC2)

1. **Download the key file** (`key.pem`) from your team member.
2. **Open a terminal** (Command Prompt / PowerShell) in the same folder as `key.pem`.
3. **Connect to the EC2 instance**:
   ```bash
   ssh -i "key.pem" ubuntu@13.49.75.27
4.Run the Gradio app:
   python3 ~/arabic_classifier/app.
5.Open your browser and go to:
   http://13.49.75.27:7860

You can now test the model with any Arabic sentence.

## How to Retrain (Optional – Kaggle Only)
Open the notebook on Kaggle with GPU enabled
Add the SANAD dataset
Run all cells (~4 hours of training)

## Repository Contents
projectcloud-966ca1 (1).ipynb – full training, evaluation, and Gradio
configuration.txt – setup details
requirements.txt – Python dependencies
README.md – this file
key.pem

## Links
GitHub repo: https://github.com/hamas22/Project.git
Live demo (AWS): http://13.49.75.27:7860
