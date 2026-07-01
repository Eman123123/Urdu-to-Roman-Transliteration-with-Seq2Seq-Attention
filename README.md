# 🔤 Urdu to Roman Transliteration using Seq2Seq with  Attention

An end-to-end **Urdu-to-Roman Urdu transliteration** system built using a **Sequence-to-Sequence (Seq2Seq)** architecture with **Luong Attention**. The model is trained on a large Urdu poetry dataset and uses **SentencePiece** tokenization for efficient subword modeling.

---

# 📋 Overview

This project implements a **Sequence-to-Sequence (Seq2Seq)** model with **Luong Attention** for transliterating **Urdu text** into **Romanized Urdu (Roman script)**. The model is trained on a corpus of Urdu poetry and leverages **SentencePiece** tokenization for both source and target languages.

The project includes:

- 🔤 Urdu-to-Roman transliteration
- 🧠 Bidirectional LSTM encoder
- 🎯 Luong attention-based decoder
- 📚 SentencePiece subword tokenization
- 📊 BLEU and Character Error Rate (CER) evaluation
- ⚡ Efficient inference with multi-line input support

---

# 🎯 Key Features

| Feature | Description |
| --- | --- |
| 🔤 **Urdu Transliteration** | Converts Urdu text into Romanized Urdu |
| 🧠 **Seq2Seq Architecture** | Bidirectional LSTM encoder with attention-based decoder |
| 🎯 **Luong Attention** | Dot-product attention for improved alignment |
| 📝 **SentencePiece Tokenization** | Efficient subword tokenization for both languages |
| 📚 **Poetry Dataset** | Trained on aligned Urdu and Roman Urdu poetry |
| 📊 **Evaluation Metrics** | Accuracy, BLEU-4, and Character Error Rate (CER) |
| ⚡ **Training Optimizations** | Teacher forcing, gradient clipping, and early stopping |
| 📄 **Multi-line Support** | Preserves paragraphs and line breaks during transliteration |

---

# 🏗️ Model Architecture

## Encoder

| Component | Configuration |
| --- | --- |
| **Type** | Bidirectional LSTM |
| **Embedding Size** | `512` |
| **Hidden Size** | `128` |
| **Number of Layers** | `2` |
| **Dropout** | `0.3` |
| **Output** | Encoder hidden states and final hidden/cell states |

---

## Decoder

| Component | Configuration |
| --- | --- |
| **Type** | LSTM with Luong Attention |
| **Embedding Size** | `512` |
| **Hidden Size** | `128` |
| **Number of Layers** | `2` |
| **Dropout** | `0.3` |
| **Attention** | Luong (Dot-Product) Attention |
| **Output** | Vocabulary probability distribution |

---

## 🎯 Attention Mechanism

| Step | Description |
| --- | --- |
| **1️⃣** | Compute attention weights between decoder hidden state and encoder outputs |
| **2️⃣** | Generate a context vector using weighted encoder outputs |
| **3️⃣** | Concatenate context vector with decoder hidden state |
| **4️⃣** | Pass through a linear layer to predict the next token |

---

# 📊 Dataset

The model is trained on an aligned **Urdu Poetry Dataset**, organized by poet.

## Dataset Structure

```text
dataset/
├── poet_name_1/
│   ├── ur/
│   └── en/
├── poet_name_2/
│   ├── ur/
│   └── en/
└── ...
```

## Dataset Statistics

| Metric | Value |
| --- | --- |
| **Total Urdu Lines** | `21,068` |
| **Total Roman Lines** | `21,068` *(aligned)* |
| **Vocabulary Size** | `6,000` tokens *(Urdu)* |
| **Vocabulary Size** | `6,000` tokens *(Roman Urdu)* |

---

# 📝 Text Preprocessing

| Language | Processing |
| --- | --- |
| **Urdu** | Unicode normalization, diacritic removal, punctuation standardization |
| **Roman Urdu** | Lowercasing, character deduplication, punctuation filtering |

---

# ⚙️ Training Configuration

| Parameter | Value |
| --- | --- |
| **Epochs** | `15` |
| **Batch Size** | `32` |
| **Learning Rate** | `0.001` |
| **Optimizer** | Adam |
| **Maximum Sequence Length** | `50` tokens |
| **Teacher Forcing Ratio** | `0.5` |
| **Gradient Clipping** | Max Norm = `1.0` |
| **Early Stopping** | Patience = `5` |

---

# 🚀 Training Features

| Feature | Description |
| --- | --- |
| 🎯 **Teacher Forcing** | Applied with probability `0.5` |
| ✂️ **Gradient Clipping** | Prevents exploding gradients |
| ⏹️ **Early Stopping** | Stops training after 5 epochs without improvement |
| 📊 **BLEU Evaluation** | Validation BLEU Score = `0.3918` |
| 🔤 **CER Metric** | Character Error Rate using Levenshtein Distance |

---

# 📈 Model Performance

| Metric | Score |
| --- | --- |
| **Training Accuracy** | `95.17%` |
| **Validation Accuracy** | `71.22%` |
| **Test Accuracy** | `71.22%` |
| **Validation BLEU** | `0.3918` |
| **Final Training Loss** | `0.2588` |

---

# 🔤 Sample Transliterations

| Urdu Input | Roman Output |
| --- | --- |
| **تجھ کو دیکھا ہے آج دیر کے بعد** | *tujh ko dekh hai aaj der ke baad* |
| **آج کا دن گزر نہ جائے کہیں** | *aaj k din guzar na jaa.e kah* |

---

# 📝 SentencePiece Tokenization

| Component | Configuration |
| --- | --- |
| **Vocabulary Size** | `6,000` tokens *(each language)* |
| **Model Type** | Unigram |
| **Special Tokens** | `<bos>`, `<eos>`, `<unk>`, `<pad>` |

---

# 📊 Evaluation Metrics

| Metric | Description |
| --- | --- |
| **Accuracy** | Token-level prediction accuracy |
| **BLEU-4** | BLEU score with smoothing |
| **CER** | Character Error Rate using Levenshtein Distance |
