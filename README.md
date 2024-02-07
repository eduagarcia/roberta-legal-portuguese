<br />
<div align="center">
    <h1 align="center">Roberta Legal Portuguese3</h1>
    <img src="https://images.emojiterra.com/google/android-11/512px/2696.png" alt="https://emojiterra.com/balance-scale" width="300">
  <br />
</div>

This repository provides the related resources to the paper [RoBERTaLexPT: A Legal RoBERTa Model pretrained with deduplication for Portuguese]().
## Corpora
### Deduplicated
- [LegalPT (deduplicated)](https://huggingface.co/datasets/eduagarcia/LegalPT_dedup) aggregates the maximum amount of publicly available legal data in Portuguese, drawing from varied sources including legislation, jurisprudence, legal articles, and government documents. Deduplicated version.

- [CrawlPT (deduplicated)](https://huggingface.co/datasets/eduagarcia/CrawlPT_dedup) corpus provides a large sample of general Portuguese text from the internet. Deduplicated version. Some subsets are also available separatedly: 
	- [OSCAR-2301-pt (deduplicated)](https://huggingface.co/datasets/eduagarcia/OSCAR-2301-pt_dedup) is a curation from Portuguese subset of [OSCAR-2301](https://huggingface.co/datasets/oscar-corpus/OSCAR-2301). 
	- [brWaC (deduplicated)](https://huggingface.co/datasets/eduagarcia/brwac_dedup)  is deduplication of [brWaC](https://aclanthology.org/L18-1686/), a web corpus for Brazilian Portuguese from 120,000 different websites.
	
### Raw
- [LegalPT](https://huggingface.co/datasets/eduagarcia/LegalPT) aggregates the maximum amount of publicly available legal data in Portuguese, drawing from varied sources including legislation, jurisprudence, legal articles, and government documents. Raw version.

- [CrawlPT](https://huggingface.co/datasets/eduagarcia/CrawlPT_dedup) corpus provides a large sample of general Portuguese text from the internet. Raw version. Some subsets are also available separatedly: 
	- [C100-PT](https://huggingface.co/datasets/eduagarcia/cc100-pt) is a curation of news articles from CC100 in the Portuguese language. This version of the dataset is the portuguese subset from C100. Raw version.

## Models
- [RoBERTaLexPT-base](https://huggingface.co/eduagarcia/RoBERTaLexPT-base) is a Portuguese Masked Language Model pretrained from scratch from the LegalPT and CrawlPT corpora, using the same architecture as RoBERTa-base, introduced by [Liu et al. (2019)](https://arxiv.org/abs/1907.11692).

- [RoBERTaCrawlPT-base](https://huggingface.co/eduagarcia/RoBERTaCrawlPT-base) is a generic Portuguese Masked Language Model pretrained from scratch from the CrawlPT corpora, using the same architecture as [RoBERTa-base](https://arxiv.org/abs/1907.11692). 

## Datasets
- [PortuLex benchmark](https://huggingface.co/datasets/eduagarcia/PortuLex_benchmark) is a four-task benchmark designed to evaluate the quality and performance of language models in the Portuguese legal

## Citation

```bibtex
@InProceedings{garcia2024_roberlexpt,
    author="Garcia, Eduardo A. S.
    and Silva, N{\'a}dia F. F.
    and Siqueira, Felipe
    and Gomes, Juliana R. S.
    and Albuqueruqe, Hidelberg O.
    and Souza, Ellen
    and Lima, Eliomar
    and De Carvalho, André",
    title="RoBERTaLexPT: A Legal RoBERTa Model pretrained with deduplication for Portuguese",
    booktitle="Computational Processing of the Portuguese Language",
    year="2024",
    publisher="Association for Computational Linguistics"
}
```

## Acknowledgment

This work has been supported by the AI Center of Excellence (Centro de Excelência em Inteligência Artificial – CEIA) of the Institute of Informatics at the Federal University of Goiás (INF-UFG).
