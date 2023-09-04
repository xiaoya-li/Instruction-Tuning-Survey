# Instruction-Tuning-Survey

This repository contains resources referenced in the paper [Instruction Tuning for Large Language Models: A Survey](https://arxiv.org/abs/2308.10792). 

If you find this repository helpful, please cite the following:
```latex
@article{zhang2023instruction,
  title={Instruction Tuning for Large Language Models: A Survey},
  author={Zhang, Shengyu and Dong, Linfeng and Li, Xiaoya and Zhang, Sen and Sun, Xiaofei and Wang, Shuhe and Li, Jiwei and Hu, Runyi and Zhang, Tianwei and Wu, Fei and others},
  journal={arXiv preprint arXiv:2308.10792},
  year={2023}
}
```

## Table of Contents 
* [Overview](#Overview)
* [Natural Language Instruction Tuning](Instruction-Tuned-LLMs)
  * [Datasets](#Datasets)
  * [Models](#Models)
* [Multi-modality Instruction Tuning](Multi-modality-Instruction-Tuning)
  * [Datasets](#Datasets)
  * [Models](#Models)
* [Domain-specific Instruction Tuning](Domain-specific-Instruction-Tuning)
  

## Overview

Instruction tuning (IT) refers to the process of further training large language models (LLMs) on a dataset consisting 
of `(instruction, output)` pairs
 in a supervised fashion, 
which bridges the gap between the next-word prediction objective of LLMs and the users' objective of having LLMs adhere 
to human instructions. The general pipeline of instruction tuning is shown in the following: 
![link](./assets/method_overview.png)

In the [paper](https://arxiv.org/abs/2308.10792), we make a systematic review of the literature, including the general methodology of IT, 
the construction of IT datasets, the training of IT models, 
and applications to different modalities, domains and application, along with analysis on aspects that influence the outcome of IT (e.g., generation of instruction outputs, size of the instruction dataset, etc). We also 
review the potential pitfalls of IT along with criticism against it, along with efforts
pointing out current deficiencies of existing strategies and suggest some avenues for fruitful research.
The typology of the paper is as follows: 



## Natural Language Instruction Tuning

### Datasets 


### Models

| Instruction tuned LLMs | Params | Github | Base Model ｜  Self-build Train | Trainset | Trainset Size |
| ------------------|-----------|-----|-----------|---------|-----------| --------|
| Instruct-GPT | 176B | -  | GPT-3    | Yes    | -   | - | 
| BLOOMZ | 176B     |    [link](https://huggingface.co/bigscience/bloomz)  | BLOOM      | No     | xP3       | -  | 
| FLAN-T5\tnotex{id:2} | 11B      |     [link](https://huggingface.co/google/flan-t5-xxl)    | T5         | No   | FLAN 2021 | - | 
| Alpaca\tnotex{id:3} | 7B       |    [link](https://github.com/tatsu-lab/stanford_alpaca)  | LLaMA           | Yes              | -         | 52K  | 
| Vicuna\tnotex{id:4} | 13B      |    [link](https://github.com/lm-sys/FastChat)   | LLaMA         | Yes              | -         | 70K  | 
| GPT-4-LLM\tnotex{id:5} | 7B       |     [link](https://github.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM)  | LLaMA           | Yes              | -         | 52K | 
| Claude~\citep{bai2022constitutional} | -       |     -     | -             | Yes              | -         | - | 
| WizardLM\tnotex{id:6} | 7B      |    [link](https://github.com/nlpxucan/WizardLM)   | LLaMA            | Yes              | Evol-Instruct | 70K  | 
| ChatGLM2\tnotex{id:7}| 6B      |    [link](https://github.com/THUDM/ChatGLM2-6B)   | GLM           | Yes              | -         | 1.1 Tokens | 
| LIMA | 65B   |    -  | LLaMA              | Yes              | -         | 1K  | 
| OPT-IML \tnotex{id:8}| 175B    |    [link](https://huggingface.co/facebook/opt-iml-30b)   | OPT           | No               | -         | - | 
| Dolly 2.0\tnotex{id:9} | 12B    |    [link](https://github.com/databrickslabs/dolly)    | Pythia         | No               | -         | 15K  | 
| Falcon-Instruct\tnotex{id:10}| 40B    |   [link](https://huggingface.co/tiiuae/falcon-40b-instruct)    | Falcon       | No               | -         | - | 
| Guanaco\tnotex{id:11} | 7B     |    [link](https://huggingface.co/JosephusCheung/Guanaco)    | LLaMA         | Yes              | -         | 586K | 
| Minotaur\tnotex{id:12}| 15B      |    [link](https://huggingface.co/openaccess-ai-collective/minotaur-15b)  | Starcoder Plus      | No               | -         | -  | 
| Nous-Hermes\tnotex{id:13}| 13B     |    [link](https://huggingface.co/NousResearch/Nous-Hermes-13b)   | LLaMA          | No               | -         | 300K+ | 
| TÜLU\tnotex{id:14} | 6.7B    |    [link](https://github.com/allenai/open-instruct)   | OPT          | No               | Mixed     | - | 
| YuLan-Chat\tnotex{id:15}| 13B    |    [link](https://github.com/RUC-GSAI/YuLan-Chat)    | LLaMA             | Yes              | -         | 250K  | 
| MOSS\tnotex{id:16} | 16B     |    [link](https://github.com/OpenLMLab/MOSS)   | -  | Yes              | -         | -  | 
| Airoboros\tnotex{id:17} | 13B    |    [link](https://github.com/jondurbin/airoboros)    | LLaMA        | Yes              | -         | -  | 
| UltraLM\tnotex{id:18}| 13B     |    [link](https://github.com/thunlp/UltraChat)   | LLaMA             | Yes              | -         | - | 

## Multi-modality Instruction Tuning

### Datasets

### Models

## Domain-specific Instruction Tuning


