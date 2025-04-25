## Comparative Analysis of the Three Models

### 1. SkipGram

| Embedding Dimension | Spearman Correlation |
|---------------------|---------------------|
| 64                 | 0.1900              |
| 128                | 0.3417              |
| 256                | 0.3512              |
| 512                | 0.3128              |

**Observations:**  
- SkipGram shows a strong improvement from **64 → 128** dimensions and peaks at **256** dimensions.  
- The slight drop at **512** dims suggests overfitting, optimization issues, or diminishing returns.  
- Overall, SkipGram consistently captures semantic similarity better than the other two methods at most dimensional settings.

---

### 2. CBOW

| Embedding Dimension | Spearman Correlation |
|---------------------|---------------------|
| 64                 | 0.1750              |
| 128                | 0.1872              |
| 256                | 0.2187              |
| 512                | 0.2623              |

**Observations:**  
- CBOW improves steadily with increasing dimensions.  
- While it starts lower than SkipGram, the gap narrows at higher dimensions (**512** dims).  
- CBOW benefits from additional dimensions by gradually capturing more semantic relationships.

---

### 3. SVD (Count-based Method)

| Embedding Dimension | Spearman Correlation |
|---------------------|---------------------|
| 64                 | 0.0349              |
| 128                | 0.0783              |
| 256                | 0.1048              |
| 512                | 0.1458              |

**Observations:**  
- SVD consistently yields the lowest Spearman correlations compared to the predictive models.  
- However, it does improve steadily with larger embedding dimensions.  
- Despite improvements, it remains less effective at capturing nuanced contextual relationships compared to neural approaches.

---

## Overall Trends

### **Impact of Dimensionality**
For all models, increasing the embedding dimension tends to improve performance. However, the magnitude of improvement varies:
- **SkipGram** benefits significantly from **64 → 128** dimensions, peaking at **256**.
- **CBOW** improves steadily and becomes more competitive at **512** dimensions.
- **SVD** shows improvement but still lags behind the predictive models at all dimensions.

### **Model Comparison**
| Model  | Best Performance (Spearman) | Best Dimension |
|--------|-----------------------------|---------------|
| SkipGram | 0.3512 | 256 |
| CBOW | 0.2623 | 512 |
| SVD | 0.1458 | 512 |

- **SkipGram** leads in capturing semantic similarity, especially at moderate dimensions (**128–256**).
- **CBOW** closes the gap at higher dimensions, suggesting it benefits more from increased capacity.
- **SVD**, while improving, remains behind the neural models in effectiveness.

---

## Conclusion
The results indicate that predictive models (**SkipGram** and **CBOW**) outperform the **SVD** approach in capturing word similarity, with **SkipGram** showing the best performance at moderate embedding sizes (**128–256**). **CBOW**, while initially trailing, improves with higher dimensions. **SVD**, despite its improvements, remains less effective in this metric.

**NOTE:** Observed that **Skip-Gram outperformed CBOW on a rarer corpus**, as its use of individual context words preserved the influence of rare words, unlike CBOW’s averaging of contextual embeddings which diluted their contribution.
