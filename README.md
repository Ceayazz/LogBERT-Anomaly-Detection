# HDFS LogBERT Anomaly Detection

BERT-based log anomaly detection system for HDFS (Hadoop Distributed File System) data. Developed during a Cyber Security internship at ISTEC, comparing supervised and unsupervised approaches for log analysis.

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red.svg)](https://pytorch.org)
[![BERT](https://img.shields.io/badge/BERT-base--uncased-green.svg)](https://huggingface.co/bert-base-uncased)

---

## Overview

This project applies BERT's natural language processing capabilities to HDFS log anomaly detection. It implements and compares two approaches:

- **Supervised**: Fine-tuned BERT classifier trained on 62,600 labeled log entries, achieving 94.97% accuracy across 11 anomaly categories
- **Unsupervised**: Clustering-based detection using MiniBatchKMeans + IsolationForest, requiring no labeled data

Developed as a research and portfolio project. Not intended for production deployment in its current form.

---

## Project Structure

```
LogBERT/
├── mega_logbert_analyzer.py          # Unsupervised anomaly detection
├── supervised_logbert_classifier.py  # Supervised BERT classifier
├── supervised_predictor_test.py      # Real-time prediction testing
├── comparison_analysis.py            # Supervised vs unsupervised comparison
├── FINAL_RAPOR.md                    # Detailed project report (Turkish)
├── requirements.txt                  # Dependencies
├── data/                             # HDFS dataset (place downloaded files here)
├── models/                           # Trained model weights
└── results/                          # Output visualizations and reports
```

---

## Dataset

This project uses the **LogHub HDFS Dataset** from Kaggle.

- **Source**: [LogHub HDFS (Hadoop Distributed File System) Data](https://www.kaggle.com/datasets/ayenuryrr/loghub-hdfs-hadoop-distributed-file-system-data)
- **Size**: ~590MB
- **Place downloaded files in**: `data/` directory

> Dataset is not included in this repository due to file size. Download from Kaggle before running.

---

## Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Unsupervised detection (no labels needed, ~30 min)
python mega_logbert_analyzer.py

# 3. Train supervised classifier (~21 hours, GPU recommended)
python supervised_logbert_classifier.py

# 4. Test predictions on sample logs
python supervised_predictor_test.py

# 5. Compare both approaches
python comparison_analysis.py
```

---

## Results

| Approach | Accuracy | Training Time | Labels Required |
|---|---|---|---|
| Supervised (BERT) | 94.97% | ~21 hours | Yes (62,600 samples) |
| Unsupervised | Silhouette: 0.880 | ~30 min | No |

### Anomaly Categories
Normal, Data_corrupt, Data_cut, Data_loss, Net_disconnect, Net_slow, Proc_kill, Proc_suspend, Sys_dead, Sys_panic, Complex

---

## Technical Details

- **Model**: BERT-base-uncased (HuggingFace Transformers)
- **Framework**: PyTorch
- **Clustering**: MiniBatchKMeans + IsolationForest
- **Visualization**: PCA + Matplotlib
- **Dataset**: LogHub HDFS (590MB, public)

---

## Example Output

### Supervised Model — Confusion Matrix
![Confusion Matrix](results/supervised_confusion_matrix.png)

### Unsupervised — Anomaly Distribution
![Anomaly Distribution](results/mega_data_analysis.png)

### Supervised vs Unsupervised Comparison
![Comparison](results/supervised_vs_unsupervised_comparison.png)

---

## Limitations

- Training requires ~21 hours and significant GPU resources
- Dataset is HDFS-specific; performance on other log formats not tested
- No production deployment infrastructure included
- Real-time latency figures are experimental, not benchmarked in production

---

## Author

**Celal Enes Ayaz**  
Cyber Security & Network Engineer | Python | OSINT | SOC

- LinkedIn: [linkedin.com/in/celalenesayaz](https://linkedin.com/in/celalenesayaz)
- GitHub: [github.com/Ceayazz](https://github.com/Ceayazz)

*Developed during Cyber Security Internship at ISTEC, August–September 2025*
