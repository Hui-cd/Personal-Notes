# GPT-4 Technical Report

## Metadata
- **CiteKey**: {{citekey}}
 - **Type**: Preprint
 - **Title**: GPT-4 Technical Report, 
 - **Author**: OpenAI,, 
 - **Year**: 2023 ;
- **Journal**: {{publicationTitle}}, 
- **Pages**: {{pages}}
- **Publisher**: {{publisher}},
- **Location**: {{place}},
- **DOI**: {{DOI}}
------


## Files and Links
- **Url**: [Open online](http://arxiv.org/abs/2303.08774)
- **zotero entry**: [Zotero](zotero://select/library/items/HBXY5IN2)
- **open pdf**: [OpenAI - 2023 - GPT-4 Technical Report.pdf](zotero://open-pdf/library/items/TJ3Z5A7Y)

- **Keywords**: Computer Science - Artificial Intelligence; Computer Science - Computation and Language; ObsCite

## Abstract
We report the development of GPT-4, a large-scale, multimodal model which can accept image and text inputs and produce text outputs. While less capable than humans in many real-world scenarios, GPT-4 exhibits human-level performance on various professional and academic benchmarks, including passing a simulated bar exam with a score around the top 10% of test takers. GPT-4 is a Transformerbased model pre-trained to predict the next token in a document. The post-training alignment process results in improved performance on measures of factuality and adherence to desired behavior. A core component of this project was developing infrastructure and optimization methods that behave predictably across a wide range of scales. This allowed us to accurately predict some aspects of GPT-4’s performance based on models trained with no more than 1/1,000th the compute of GPT-4.

----

## Comments
Comment: 100 pages


----

## Extracted Annotations

注释(2023/9/30 下午3:51:27)

注释(2023/9/30 下午3:49:03)

- *“limitations, and safety properties of GPT-4”* [(OpenAI, 2023, p. 2)](zotero://open-pdf/library/items/TJ3Z5A7Y?page=2&annotation=J2JSFQXZ) 

- *“cape and the safety implications of large-scale models like GPT-4, this report contains no further details about the architecture (including model size), hardware, training compute, dataset construction, training method, or”* [(OpenAI, 2023, p. 2)](zotero://open-pdf/library/items/TJ3Z5A7Y?page=2&annotation=EYN6RWT5) 

- *“The final loss of properly-trained large language models is thought to be well approximated by power laws in the amount of compute used to train the model [41, 42, 2, 14, 15]. To verify the scalability of our optimization i”* [(OpenAI, 2023, p. 2)](zotero://open-pdf/library/items/TJ3Z5A7Y?page=2&annotation=8UZZ6LAP) 

注释(2023/9/30 下午3:54:57)

- *“re k and α are positive constants, and P is a subset of problems in the dataset. We hypothesize that this relationship holds for all problems in this dataset. In practice, very low pass rates are difficult or impossible to estimate, so we restrict to problems P and models M such that”* [(OpenAI, 2023, p. 4)](zotero://open-pdf/library/items/TJ3Z5A7Y?page=4&annotation=WTN9NDMM) 

- *“stered predictions for GPT-4’s performance on HumanEval before training completed, using only information available prior to training. All but the 15 hardest HumanEval problems were split into 6 difficulty buckets based on the performance of smaller models. The results on the 3rd easiest bucket are shown in Figure 2, showing that the resulting predictions were very accurate for this subset of HumanEval problems where we can accurately estimate log(pass_rate) for several smaller models. Predictions on the other five buckets performed almost as well, the main exception being GPT-4 underperforming our predictions on the easiest bucket. Certain capabilities remain hard to predict. For example, the Inverse Scalin”* [(OpenAI, 2023, p. 4)](zotero://open-pdf/library/items/TJ3Z5A7Y?page=4&annotation=ZQW9AVF9) 



****



## Summary
****
  
## Research Objective(s)


## Background / Problem Statement


## Method(s)


## Evaluation


## Conclusion


## Notes
