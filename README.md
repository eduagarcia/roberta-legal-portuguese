<br />
<div align="center">
    <h1 align="center">Roberta Legal Portuguese</h1>
    <img src="https://images.emojiterra.com/google/android-11/512px/2696.png" alt="https://emojiterra.com/balance-scale" width="300">
  <br />
</div>

This repository provides the related resources to the paper [RoBERTaLexPT: A Legal RoBERTa Model pretrained with deduplication for Portuguese]().

> [!TIP]
> Check out [Roberta Legal Portuguese](https://huggingface.co/collections/eduagarcia/roberta-legal-portuguese-65c3f7247d10ab35a75de3e9) in 🤗 Collection! 

## Corpora
We compile two main corpora for pre-training: 
- [LegalPT](https://huggingface.co/datasets/eduagarcia/LegalPT), a Portuguese legal corpus
- [CrawlPT](https://huggingface.co/datasets/eduagarcia/CrawlPT), a Portuguese general corpus used for comparison.

| Corpus          |  Domain | Tokens (B) | Size (GiB) |
|-----------------|:-------:|:----------:|:----------:|
| LegalPT         |  Legal  |    22.5    |    125.1   |
|  CrawlPT        |          |            |       |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;brWaC          | General |     2.7    |    16.3    |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CC100 (PT)  | General |     8.4    |    49.1    |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OSCAR-2301 (PT) | General |    18.1    |    97.8    |

Deduplication was done by using [MinHash algorithm](https://dl.acm.org/doi/abs/10.5555/647819.736184) and [Locality Sensitive Hashing](https://dspace.mit.edu/bitstream/handle/1721.1/134231/v008a014.pdf?sequence=2&isAllowed=y), following the approach of [Lee et al. (2022)](http://arxiv.org/abs/2107.06499). We used 5-grams and a signature of size 256, considering two documents to be identical if their Jaccard Similarity exceeded 0.7.

- [LegalPT (deduplicated)](https://huggingface.co/datasets/eduagarcia/LegalPT_dedup)
- [CrawlPT (deduplicated)](https://huggingface.co/datasets/eduagarcia/CrawlPT_dedup)

## Datasets

[PortuLex benchmark](https://huggingface.co/datasets/eduagarcia/PortuLex_benchmark) is a four-task benchmark designed to evaluate the quality and performance of language models in the Portuguese legal context.

| Dataset       | Task | Train | Dev   | Test  |
|---------------|------|-------|-------|-------|
| RRI           | CLS  | 8.26k | 1.05k | 1.47k |
| LeNER-Br      | NER  | 7.83k | 1.18k | 1,39k |
| UlyssesNER-Br | NER  | 3.28k | 489   | 524   |
| FGV-STF       | NER  | 415   | 60    | 119   |


## Models
Our model was pretrained in four different configurations:
- Solely on BrWaC (RoBERTaTimbau_base).
- Solely on the LegalPT corpus (RoBERTaLegalPT-base)
- Solely on the CrawlPT corpus ([RoBERTaCrawlPT-base](https://huggingface.co/eduagarcia/RoBERTaCrawlPT-base))
- Combining both corpora ([RoBERTaLexPT-base](https://huggingface.co/eduagarcia/RoBERTaLexPT-base))

Macro F1-Score (\%) for multiple models evaluated on PortuLex benchmark test splits:

| **Model**                                                                  | **LeNER** | **UlyNER-PL**   | **FGV-STF** |  **RRIP** | **Average (%)** |
|----------------------------------------------------------------------------|-----------|-----------------|-------------|:---------:|-----------------|
|                                                                            |           | Coarse/Fine     | Coarse      |           |                 |
| BERTimbau-based  | 88.34     | 86.39/83.83     | 79.34       |   82.34   | 83.78           |
| BERTimbau-large | 88.64     | 87.77/84.74     | 79.71       | **83.79** | 84.60           |
| Albertina-PT-BR-base               | 89.26     | 86.35/84.63     | 79.30       |   81.16   | 83.80           |
| Albertina-PT-BR-xlarge                | 90.09     | 88.36/**86.62** | 79.94       |   82.79   | 85.08           |
| BERTikal-base                      | 83.68     | 79.21/75.70     | 77.73       |   81.11   | 79.99           |
| JurisBERT-base      | 81.74     | 81.67/77.97     | 76.04       |   80.85   | 79.61           |
| BERTimbauLAW-base    | 84.90     | 87.11/84.42     | 79.78       |   82.35   | 83.20           |
| Legal-XLM-R-base                      | 87.48     | 83.49/83.16     | 79.79       |   82.35   | 83.24           |
| Legal-XLM-R-large                | 88.39     | 84.65/84.55     | 79.36       |   81.66   | 83.50           |
| Legal-RoBERTa-PT-large              | 87.96     | 88.32/84.83     | 79.57       |   81.98   | 84.02           |
| **Ours**                                                                   |           |                 |             |           |                 |
| RoBERTaTimbau-base (Reproduction of BERTimbau)                             | 89.68     | 87.53/85.74     | 78.82       |   82.03   | 84.29           |
| RoBERTaLegalPT-base (Trained on LegalPT)                                   | 90.59     | 85.45/84.40     | 79.92       |   82.84   | 84.57           |
| [RoBERTaCrawlPT-base](https://huggingface.co/eduagarcia/RoBERTaCrawlPT-base)  (Trained on CrawlPT)   | 89.24     | 88.22/86.58     | 79.88       |   82.80   | 84.83           |
| [RoBERTaLexPT-base](https://huggingface.co/eduagarcia/RoBERTaLexPT-base) (Trained on CrawlPT + LegalPT)                       | **90.73** | **88.56**/86.03 | **80.40**   |   83.22   | **85.41**       |

In summary, RoBERTaLexPT consistently achieves top legal NLP effectiveness despite its base size. 
With sufficient pre-training data, it can surpass larger models. The results highlight the importance of domain-diverse training data over sheer model scale.


## Citation

```bibtex
@inproceedings{garcia-etal-2024-robertalexpt,
    title = "{R}o{BERT}a{L}ex{PT}: A Legal {R}o{BERT}a Model pretrained with deduplication for {P}ortuguese",
    author = "Garcia, Eduardo A. S.  and
      Silva, Nadia F. F.  and
      Siqueira, Felipe  and
      Albuquerque, Hidelberg O.  and
      Gomes, Juliana R. S.  and
      Souza, Ellen  and
      Lima, Eliomar A.",
    editor = "Gamallo, Pablo  and
      Claro, Daniela  and
      Teixeira, Ant{\'o}nio  and
      Real, Livy  and
      Garcia, Marcos  and
      Oliveira, Hugo Gon{\c{c}}alo  and
      Amaro, Raquel",
    booktitle = "Proceedings of the 16th International Conference on Computational Processing of Portuguese",
    month = mar,
    year = "2024",
    address = "Santiago de Compostela, Galicia/Spain",
    publisher = "Association for Computational Lingustics",
    url = "https://aclanthology.org/2024.propor-1.38",
    pages = "374--383",
}
```

## Acknowledgment

This work has been supported by the AI Center of Excellence (Centro de Excelência em Inteligência Artificial – CEIA) of the Institute of Informatics at the Federal University of Goiás (INF-UFG).
