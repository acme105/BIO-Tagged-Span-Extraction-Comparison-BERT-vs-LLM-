****Skill Extraction from Job Descriptions (NER)****

This repository contains a progressive series of Jupyter Notebooks exploring different techniques for extracting skills from job descriptions. The core of this study focuses on two main objectives:

1. Ablation Study on SRICL with LLMs: Analyzing the performance improvements by iteratively applying different techniques (SFT, ICL, SRICL) on Large Language Models, particularly Qwen2.5-3B-Instruct.
2. SRICL LLM vs BERT models: Benchmarking the advanced SRICL LLM approach against various specialized and general-purpose BERT architectures.
Datasets
The models are trained and evaluated on several skill extraction datasets, including:

1. jjzha/sayfullina (Soft skills focused)
2. jjzha/skillspan
3. green
4. gnehm

**Explored Techniques (LLM Ablation Study)**
The project progresses through multiple phases of LLM adaptation, improving performance with advanced techniques:

Baselines: Few-shot prompting and Retrieval-Augmented Generation (RAG).
SFT (Supervised Fine-Tuning): Fine-tuning Qwen2.5-3B-Instruct using LoRA.
SFT + ICL (In-Context Learning): Enhancing SFT with dataset-specific in-context demonstrations.
SRICL (Self-Reflective In-Context Learning): Combining SFT with self-reflective reasoning and in-context examples for superior NER performance.
**BERT Baseline Comparisons**
To ground the performance of the LLMs, several BERT-based models were also trained and evaluated on the same datasets, acting as a comparison point against the SRICL LLM approach. The tested models include:

bert-base
spanbert
jobbert
jobspanbert
**Performance Results**
BERT Models Evaluation Summary
The following table summarizes the F1 scores, precision, and recall for the BERT-based models across the four datasets:

Model	Dataset	Precision	Recall	F1 Score
bert-base	sayfullina	0.8007	0.8568	0.8278
bert-base	skillspan	0.4894	0.5141	0.5014
bert-base	green	0.4991	0.4030	0.4459
bert-base	gnehm	0.8164	0.8359	0.8260
spanbert	sayfullina	0.7795	0.8223	0.8003
spanbert	skillspan	0.4761	0.4770	0.4765
spanbert	green	0.4566	0.3532	0.3983
spanbert	gnehm	0.7816	0.8012	0.7913
jobbert	sayfullina	0.7836	0.8363	0.8091
jobbert	skillspan	0.5194	0.5687	0.5429
jobbert	green	0.4542	0.3701	0.4079
jobbert	gnehm	0.7842	0.8311	0.8070
jobspanbert	sayfullina	0.7964	0.8465	0.8207
jobspanbert	skillspan	0.5135	0.5539	0.5329
jobspanbert	green	0.4490	0.3746	0.4085
jobspanbert	gnehm	0.7712	0.7948	0.7828
**Computational Efficiency**
Training and inference costs demonstrate a significant trade-off between the advanced SRICL LLMs and the smaller BERT models.

Metric	SRICL LLM	BERT Models
Training Time	~12 hours	~2 hours
Inference Time (All datasets)	~4 hours	30 - 45 minutes
**Notebooks Overview**
***Phase 1 to 3: Baselines & Exploration***
p-1-to-3-skill-extraction-from-job-descriptions.ipynb
Establishes performance baselines using few-shot prompting.
Explores early Phase 2 implementations including RAG modules to extract skills dynamically.
***Phase 4 & 5: Supervised Fine-Tuning & In-Context Learning***
p-4-sft-only-skill-extraction-from-job.ipynb
Implements standard Supervised Fine-Tuning (SFT) using LoRA on the Qwen2.5-3B model.
Targeted specifically at the Sayfullina dataset (soft skills extraction).
p-5-sft-icl.ipynb
Introduces dataset-specific In-Context Learning (ICL) prompts natively into the SFT process to improve token extraction alignment.
***Phase 6: Self-Reflective In-Context Learning (SRICL)***
p-6-sricl-one-data.ipynb
Implements the SRICL approach on a single dataset, baking the inference prompt into the SFT training phase.
p-6-sricl-all-data-evals.ipynb
Evaluation of the SRICL methodology across multiple English datasets.
***Combined Training & Evals Pipeline***
phaseA_combined_train.ipynb
Consolidates training pipelines and data normalisation (e.g., merging tags) into a unified process.
Incorporates the BERT baseline models (bert-base, spanbert, jobbert, jobspanbert) for comparison.
train-model-for-all-english-datasets-sricl.ipynb
Complete SRICL training script scaled to 4 different English skill extraction datasets.
run-evals-for-all-english-datasets.ipynb
Comprehensive evaluation script to measure precision, recall, and F1 scores of the trained model across all datasets.
