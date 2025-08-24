# Text_to_Math

## Overview
This project explores multiple neural architectures for converting **natural language text into mathematical formulas**.  
We experiment with traditional Seq2Seq models and modern Transformer-based models (BERT), comparing their performance in terms of **execution accuracy** and **exact match accuracy**.

---

## Implemented Architectures

### 1. Seq2Seq Model with GloVe Embeddings
- **Encoder–Decoder architecture** with GloVe embeddings.  
- Achieved **51.32% execution accuracy** and **47.06% exact match accuracy** on the test set:contentReference[oaicite:0]{index=0}.  
- **Limitation:** Struggles with complex relationships, making it a modest baseline.  
- _Loss Plot:_  
  ![Seq2Seq Loss](images/seq2seq_loss.png)

---

### 2. Seq2Seq + Attention (with GloVe)
- Introduced **attention mechanism** to improve context handling.  
- Performance highly dependent on teacher forcing ratio:  
  - At ratio **0.6**, achieved **58.12% execution accuracy** and **54.28% exact match accuracy** on test set:contentReference[oaicite:1]{index=1}.  
- **Insight:** Balanced teacher forcing (0.6) strikes the best trade-off, while higher values (0.9) lead to overfitting.  
- _Loss Plot Comparison:_  
  ![Seq2Seq + Attention Loss](images/seq2seq_attention_loss.png)

---

### 3. BERT Seq2Seq + Attention (Frozen Encoder)
- Encoder initialized with **frozen BERT-base-cased embeddings**.  
- Achieved **56.98% execution accuracy** and **53.61% exact match accuracy** on test set:contentReference[oaicite:2]{index=2}.  
- **Insight:** Shows strong generalization even without fine-tuning.  
- _Loss Plot:_  
  ![BERT Frozen Loss](images/bert_frozen_loss.png)

---

### 4. BERT Seq2Seq + Attention (Fine-tuned Encoder)
- Fine-tuned **BERT-base-cased encoder**, giving the best results.  
- Achieved **69.14% execution accuracy** and **66.54% exact match accuracy** on test set with beam width 10:contentReference[oaicite:3]{index=3}.  
- **Insight:** Fine-tuning significantly boosts performance, but introduces mild overfitting (validation loss diverges).  
- _Loss Plot:_  
  ![BERT Fine-tuned Loss](images/bert_finetuned_loss.png)

---

## Comparative Results

| Model                          | Test Exec. Acc. (%) | Test Exact Match (%) |
|--------------------------------|----------------------|-----------------------|
| Seq2Seq (GloVe)                | 51.32               | 47.06                |
| Seq2Seq + Attention (GloVe, 0.6 TF) | 58.12               | 54.28                |
| BERT + Attention (Frozen)      | 56.98               | 53.61                |
| BERT + Attention (Fine-tuned)  | **69.14**           | **66.54**            |

_Comparison Plot:_  
![Model Comparison](images/model_comparison.png)

---

## Insights
- **Attention improves context handling**, but the teacher forcing ratio must be carefully tuned.  
- **BERT embeddings** significantly improve performance even without fine-tuning.  
- **Fine-tuned BERT** is the best performer, but requires careful regularization to avoid overfitting.  
- **Future work:** explore data augmentation, early stopping, and task-specific fine-tuning:contentReference[oaicite:4]{index=4}.  

---

## Repository Contents
- `bert_finetuned.ipynb` → BERT-based seq2seq with fine-tuning  
- `bert_frozen.ipynb` → BERT-based seq2seq with frozen embeddings  
- `lstm-lstm.ipynb` → Seq2Seq baseline  
- `lstm_with_attention.ipynb` → Seq2Seq with attention  
- `final_report.pdf` → Full report with methodology, experiments, and plots  

---

## Usage
1. Clone the repo:
   ```bash
   git clone https://github.com/Infiski/Text_to_Math.git
   cd Text_to_Math
