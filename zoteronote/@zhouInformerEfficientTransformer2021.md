# Informer: Beyond Efficient Transformer for Long Sequence Time-Series Forecasting

## Metadata
- **CiteKey**: {{citekey}}
 - **Type**: Journal Article
 - **Title**: Informer: Beyond Efficient Transformer for Long Sequence Time-Series Forecasting, 
 - **Author**: Zhou, Haoyi; Zhang, Shanghang; Peng, Jieqi; Zhang, Shuai; Li, Jianxin; Xiong, Hui; Zhang, Wancai, 
 - **Year**: 2021 ;
- **Journal**: Proceedings of the AAAI Conference on Artificial Intelligence, 
- **Pages**: 11106-11115
- **Publisher**: {{publisher}},
- **Location**: {{place}},
- **DOI**: 10.1609/aaai.v35i12.17325
------


## Files and Links
- **Url**: [Open online](https://ojs.aaai.org/index.php/AAAI/article/view/17325)
- **zotero entry**: [Zotero](zotero://select/library/items/2BE3HB69)
- **open pdf**: [Zhou 等 - 2021 - Informer Beyond Efficient Transformer for Long Se.pdf](zotero://open-pdf/library/items/ZVVAF6CE)

- **Keywords**: {{keywordsAll}}

## Abstract
Many real-world applications require the prediction of long sequence time-series, such as electricity consumption planning. Long sequence time-series forecasting (LSTF) demands a high prediction capacity of the model, which is the ability to capture precise long-range dependency coupling between output and input efﬁciently. Recent studies have shown the potential of Transformer to increase the prediction capacity. However, there are several severe issues with Transformer that prevent it from being directly applicable to LSTF, including quadratic time complexity, high memory usage, and inherent limitation of the encoder-decoder architecture. To address these issues, we design an efﬁcient transformer-based model for LSTF, named Informer, with three distinctive characteristics: (i) a ProbSparse self-attention mechanism, which achieves O(L log L) in time complexity and memory usage, and has comparable performance on sequences’ dependency alignment. (ii) the self-attention distilling highlights dominating attention by halving cascading layer input, and efﬁciently handles extreme long input sequences. (iii) the generative style decoder, while conceptually simple, predicts the long time-series sequences at one forward operation rather than a step-by-step way, which drastically improves the inference speed of long-sequence predictions. Extensive experiments on four large-scale datasets demonstrate that Informer signiﬁcantly outperforms existing methods and provides a new solution to the LSTF problem.

----

## Comments



----

## Extracted Annotations

****



## Summary

  
## Research Objective(s)


## Background / Problem Statement


## Method(s)


## Evaluation


## Conclusion


## Notes
