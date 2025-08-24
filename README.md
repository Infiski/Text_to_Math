# Text_to_Math

A set of Jupyter Notebook experiments exploring text-to-mathematical transformation techniques—including fine-tuning/freeze strategies with BERT, LSTM-based architectures, and attention mechanisms.

---

##  Contents

- **`bert_finetuned.ipynb`**: Experiments applying fine-tuning techniques to BERT for translating text input into math expressions.
- **`bert_frozen.ipynb`**: Experiments freezing BERT’s parameters and training only a top classifier/regressor head for transformation.
- **`lstm-lstm.ipynb`**: A baseline sequence-to-sequence model built with LSTM encoder-decoder layers for text-to-expression mapping.
- **`lstm_wtih_attention.ipynb`**: Enhanced LSTM model which incorporates an attention mechanism to better capture alignment between input text and output math tokens.
- **`final_report.pdf`**: A comprehensive summary document detailing dataset, model comparisons, training methodology, key results, and conclusions.

---

##  Objective

The main goal is to investigate different neural architectures and training paradigms for converting natural language descriptions into formal mathematical expressions. These experiments compare:

- **Pretrained Transformer (BERT)** — full fine-tuning vs. frozen embeddings + custom head
- **Seq2Seq LSTM models** — with and without attention—for sequence generation
- Performance metrics such as accuracy, convergence speed, and generalization capabilities

---

##  Usage Instructions

To run and view results:

1. Clone this repository:

   ```bash
   git clone https://github.com/Infiski/Text_to_Math.git
   cd Text_to_Math
