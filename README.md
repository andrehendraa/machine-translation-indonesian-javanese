# Indonesian → Javanese Machine Translation: Model Comparison

Comparing pretrained translation models on Indonesian-to-Javanese, a low-resource language pair, using the NusaX-MT dataset.

**Tools:** Python, Hugging Face Transformers, deep_translator, Weights & Biases, BLEU / METEOR / BERTScore

**Data:** 
- [NusaX-MT](https://huggingface.co/datasets/indonlp/NusaX-MT) (ind–jav), 1,000 sentence pairs re-split into 800 / 100 / 100 (train / validation / test).
- **Stopwords:** Javanese and Sundanese stopword lists from [bimarakajati/Javanese-and-Sundanese-Stopwords](https://github.com/bimarakajati/Javanese-and-Sundanese-Stopwords).

**Models:** IndoT5 (`LazarusNLP/indo-t5-base-nusax`), NLLB-200 distilled 600M, mBART-50 many-to-many (labelled "XLMR" in the report), and Google Translate as a non-fine-tuned baseline.

**Environment:** Google Colab. Dependencies are listed in `requirements.txt` (each notebook also installs them in its first cell).

## Result
| Model | BLEU | METEOR | BERTScore F1 |
|---|---|---|---|
| NLLB-200 | **14.81** | 0.392 | **0.809** |
| mBART-50 | 13.54 | **0.397** | 0.800 |
| IndoT5* | 4.47 | 0.207 | 0.748 |
| Google Translate | 3.17 | 0.272 | – |

NLLB-200 gave the best overall translation quality; mBART-50 was a close second.

\*The IndoT5 run produced NaN validation loss and its metrics did not change across epochs, so this score does not reflect a working fine-tune.

**Note:** Stopwords and punctuation were removed during preprocessing, so the scores are not comparable with published NusaX-MT benchmarks.

## Report
[docs/report.pdf](docs/report.pdf)

---
Course project — Natural Language Processing, Semester 5. Team of 5.
**My contribution:** 
- Designed and built all four model notebooks.
- Ran the training and evaluation.
- Co-wrote the report.