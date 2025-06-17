# Task-Specific Small Language Model for Legal Text Generation

This repository contains the code and results of a research assignment focused on **building a task-specific small language model (SLM) from scratch**, tailored for **legal document generation** using the EUR-Lex dataset from the LexGLUE benchmark.

## Project Overview

This project explores the training of a small transformer-based language model specialized in legal text processing. We designed and evaluated **four different training configurations**, analyzing the impact of training iterations, architecture scaling, and hyperparameters on model performance and text generation quality.

---

##  Dataset

- **Source**: [EUR-Lex from LexGLUE](https://huggingface.co/datasets/coastalcph/lex_glue#eurlex)
- **Domain**: European Union legal documents
- **Language**: Primarily English
- **Size**:
  - Training: ~81 million tokens
  - Validation: ~8.7 million tokens
- **Preprocessing**: 
  - HTML tag removal
  - Unicode normalization
  - Byte Pair Encoding (BPE) with 32k vocabulary
  - Filtering short/noisy documents

---

## Experimental Configurations

### 🧪 Case 1: Baseline Model (5000 Iterations)
- **Batch Size**: 16  
- **Block Size**: 64  
- **Learning Rate**: 1e-4  
- **Results**: 
  - Final Train Loss: 4.44  
  - Final Val Loss: 4.66  
  - Partial success in legal tone but low coherence  

---

### 🧪 Case 2: Extended Training (20,000 Iterations)
- Same architecture as Case 1
- **Learning Rate**: Cyclic schedule (0.0001 to 0.0005)
- **Results**:
  - Final Val Loss: 4.63  
  - Slight improvement, but diminishing returns after 10k iterations  

---

### 🧪 Case 3: Larger Model (5000 Iterations)
- **Batch Size**: 32  
- **Block Size**: 128  
- **Embedding Dim**: 512  
- **Layers**: 8  
- **Heads**: 8  
- **Results**:
  - Final Val Loss: 4.43  
  - Better fluency and structure in legal generation  

---

### 🧪 Case 4: Larger Model + Extended Training (19,500 Iterations)
- Same model as Case 3, extended training
- **Embedding Dim**: 256  
- **Layers**: 6  
- **Results**:
  - Final Train Loss: 3.57  
  - Final Val Loss: 3.78  
  - Best performing configuration, significantly more coherent output  

---

## Key Takeaways

- Larger models with longer training significantly improve legal text generation quality.
- Cyclic learning rate schedules proved stable for extended runs.
- Even small models can capture legal structure and terminology with correct configuration.
- Limitations observed in coherence and grammar can be improved with deeper architectures and more training data.

---

## 🧠 Challenges Faced

- Complex formatting and structure in legal texts required careful preprocessing.
- Difficulty in balancing model size with memory constraints.
- Managing learning rate schedules to avoid instability in early training.

---

## Future Work

- Scale up model depth and width
- Use gradient checkpointing for longer contexts
- Incorporate structured awareness of legal document format
- Explore multi-GPU training and legal-specific data augmentation

---

## Report

You can read the full research report [here](./SLM_Report.pdf) for an in-depth discussion on methodology, experiments, and results.

---

## Authors

- **Mansi Borle** – 2023301002 – [mansi.borle23@spit.ac.in](mailto:mansi.borle23@spit.ac.in)  
- **Manjiri Chavande** – 2023301003 – [manjiri.chavande23@spit.ac.in](mailto:manjiri.chavande23@spit.ac.in)

---

