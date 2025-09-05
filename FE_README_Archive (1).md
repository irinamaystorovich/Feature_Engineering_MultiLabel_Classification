
#  Multi-Label Classification for Archive Text Using Advanced Feature Engineering

##  Overview
This project focuses on **automating archive cataloging** using **multi-label classification (MLC)** techniques and **transformer-based deep learning models**.  
Traditional archive metadata classification is slow, labor-intensive, and prone to inconsistencies. With the growing size of **digital archive collections**, manual methods are no longer efficient.  

Our solution leverages **feature engineering** and **fine-tuned BERT models** to automatically classify archive resources into multiple categories, significantly improving the **accuracy, speed, and scalability** of cataloging systems.  

---

## Key Features
- **Automated Multi-Label Classification** for complex archive metadata.
- **Advanced Feature Engineering Techniques:**
  - Text preprocessing and normalization  
  - Label binarization  
  - Top-K label filtering to handle class imbalance  
  - Grouping and hierarchical mapping of Archive of Congress Subject Headings (LCSH)
- **Deep Learning Model:**
  - Fine-tuned **BERT-based model** for contextual understanding of archive text.
- **Performance Optimization:**
  - Handles long-tail label distribution in archive data.
  - Achieved **F1-score of 0.8975** with Top-20 label filtering.
- **Scalable System Design** suitable for modern digital archive workflows.

---

##  Dataset
The dataset used in this project was provided by the **University of North Texas Archive** and contains **100,000 MARC records**.

### Extracted Fields:
- **Title** (MARC field 245)  
- **Abstract** (MARC field 530)  
- **Table of Contents (TOC)**  
- **Subject Headings (LCSH)** – MARC 650 subfield `$a`

### Challenges Addressed:
- **Hierarchical Metadata Structure:** LCSH with parent-child label relationships.  
- **Data Quality Issues:** Missing, outdated, or inconsistent records.  
- **Long-Tail Distribution:** Few common labels dominate, while many rare labels appear infrequently.

---

##  Tech Stack
- **Language:** Python  
- **Libraries & Tools:**
  - `PyTorch`
  - `Transformers` (Hugging Face)
  - `Pandas`, `NumPy`
  - `PyMARC` (for MARC file processing)
  - `tqdm` (progress visualization)
- **Hardware:**  
  - Linux server with **two NVIDIA A40 GPUs (48GB each)**

---

##  Methodology

### 1. Data Preprocessing
- Cleaned data by removing duplicates, errors, and handling missing values.
- Normalized text (lowercasing, removing non-ASCII characters).
- Tokenized text using BERT tokenizer.

### 2. Label Engineering
- **Multi-Label Binarization:** Created a binary matrix for classification.
- **Top-K Filtering:** Focused on the top 20/40/60 most frequent labels.
- **Hierarchical Grouping:** Grouped labels based on Archive of Congress Classification (LCC) hierarchy.

### 3. Model Training
- **Model:** BERT (bert-base-uncased)
- **Training Split:**
  - 70% training  
  - 15% validation  
  - 15% testing
- **Hyperparameters:**
  - Loss function: Binary Cross-Entropy (BCE)
  - Optimizer: AdamW
  - Batch size: 16
  - Epochs: 3, 5, 10

### 4. Evaluation
- **Metrics:**
  - Accuracy
  - Precision
  - Recall
  - F1-score (macro averaging to handle imbalance)
- **Visualization:** Frequency distributions, label charts, and performance graphs.

---

##  Results

| Label Set | Epochs | Accuracy | Precision | Recall | F1-score |
|-----------|--------|----------|-----------|--------|----------|
| **Top-20** | 10     | **85.34%** | **90.09%**  | **90.51%** | **89.75%** |
| **Top-40** | 10     | 79.07%    | 85.16%      | 84.41%     | 84.15% |
| **Top-60** | 10     | 70.45%    | 78.58%      | 76.39%     | 76.65% |


