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
![project](./assets/method_overview.png)

In the [paper](https://arxiv.org/abs/2308.10792), we make a systematic review of the literature, including the general methodology of IT, 
the construction of IT datasets, the training of IT models, 
and applications to different modalities, domains and application, along with analysis on aspects that influence the outcome of IT (e.g., generation of instruction outputs, size of the instruction dataset, etc). We also 
review the potential pitfalls of IT along with criticism against it, along with efforts
pointing out current deficiencies of existing strategies and suggest some avenues for fruitful research.
The typology of the paper is as follows: 

<div align="center">
  <img src="assets/paper_typology_v2.png" width="800">
</div>


## Natural Language Instruction Tuning

### Datasets

<table border="1" align="center" style="text-align:center;">
<tr>
        <th style="width:8cm;">Type</th>
        <th>Dataset Name</th> 
        <th>Paper</th> 
        <th>Project</th> 
        <th># of Instructions</th>
        <th># of Tasks</th>
        <th># of Lang</th>
        <th>Construction</th>
        <th>Open Source</th>
</tr>
<tr>
        <td rowspan="9" align="center">Generalize to unseen tasks</td>
        <td align="center">UnifiedQA</td> 
        <td align="center"><a href="https://arxiv.org/abs/2005.00700" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/allenai/unifiedqa" target="_blank">project</a></td>
        <td align="center">750K</td>
        <td align="center">46</td>
        <td align="center">En</td>
        <td align="center">human-crafted</td>
        <td align="center">Yes</td>
</tr>
<tr>
        <td align="center">OIG</td> 
        <td align="center">-</td>
        <td align="center"><a href="https://github.com/LAION-AI/Open-Instruction-Generalist" target="_blank">project</a></td>
        <td align="center">43M</td>
        <td align="center">30</td>
        <td align="center">En</td>
        <td align="center">human-model-mixed</td>
        <td align="center">Yes</td>
</tr>
<tr>
		<td align="center">UnifiedSKG</td>
        <td align="center"><a href="https://arxiv.org/abs/2201.05966" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/hkunlp/unifiedskg" target="_blank">project</a></td>
		<td align="center">0.8M</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Natural Instructions</td>
        <td align="center"><a href="https://arxiv.org/abs/2104.08773" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/allenai/natural-instructions-v1" target="_blank">project</a></td>
		<td align="center">193K</td>
		<td align="center">61</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Super-Natural Instructions</td>
        <td align="center"><a href="https://arxiv.org/abs/2204.07705" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/allenai/natural-instructions" target="_blank">project</a></td>
		<td align="center">5M</td>
		<td align="center">76</td>
		<td align="center">55 Lang</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">P3</td>
        <td align="center"><a href="https://arxiv.org/abs/2110.08207" target="_blank">paper</a></td>
        <td align="center"><a href="https://huggingface.co/datasets/bigscience/P3" target="_blank">project</a></td>
		<td align="center">12M</td>
		<td align="center">62</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">xP3</td>
        <td align="center"><a href="https://arxiv.org/abs/2211.01786" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/bigscience-workshop/xmtf" target="_blank">project</a></td>
		<td align="center">81M</td>
		<td align="center">53</td>
		<td align="center">46 Lang</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Flan 2021</td>
        <td align="center"><a href="https://arxiv.org/abs/2301.13688" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/google-research/FLAN" target="_blank">project</a></td>
		<td align="center">4.4M</td>
		<td align="center">62</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">COIG</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.07987" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/BAAI-Zlab/COIG" target="_blank">project</a></td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">Yes</td>
</tr>
<tr>
        <td rowspan="10" align="center">Follow users' instructions in a single turn</td>
		<td align="center">InstructGPT</td>
        <td align="center">-</td>
        <td align="center">-</td>
		<td align="center">13K</td>
		<td align="center">-</td>
		<td align="center">Multi</td>
		<td align="center">human-crafted</td>
		<td align="center">No</td>
</tr>
<tr>
		<td align="center">Unnatural Instructions</td>
        <td align="center"><a href="https://arxiv.org/abs/2212.09689" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/orhonovich/unnatural-instructions" target="_blank">project</a></td>
		<td align="center">240K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">InstructGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Self-Instruct</td>
        <td align="center"><a href="https://arxiv.org/abs/2212.10560" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/yizhongw/self-instruct" target="_blank">project</a></td>
		<td align="center">52K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">InstructGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">InstructWild</td>
        <td align="center">-</td>
        <td align="center"><a href="https://github.com/XueFuzhao/InstructionWild" target="_blank">project</a></td>
		<td align="center">104K</td>
		<td align="center">429</td>
		<td align="center">-</td>
		<td align="center">model-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Evol-Instruct</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.12244" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/nlpxucan/evol-instruct" target="_blank">project</a></td>
		<td align="center">52K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">ChatGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Alpaca</td>
        <td align="center">-</td>
        <td align="center"><a href="https://github.com/tatsu-lab/stanford_alpaca" target="_blank">project</a></td>
		<td align="center">52K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">InstructGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">LogiCoT</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.12147" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/csitfun/LogiCoT" target="_blank">project</a></td>
		<td align="center">-</td>
		<td align="center">2</td>
		<td align="center">En</td>
		<td align="center">GPT-4-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Dolly</td>
        <td align="center">-</td>
        <td align="center"><a href="https://huggingface.co/datasets/databricks/databricks-dolly-15k" target="_blank">project</a></td>
		<td align="center">15K</td>
		<td align="center">7</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">GPT-4-LLM</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.03277" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM" target="_blank">project</a></td>
		<td align="center">52K</td>
		<td align="center">-</td>
		<td align="center">En&Zh</td>
		<td align="center">GPT-4-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">LIMA</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.11206" target="_blank">paper</a></td>
        <td align="center"><a href="https://huggingface.co/datasets/GAIR/lima" target="_blank">project</a></td>
		<td align="center">1K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
        <td rowspan="9" align="center">Offer assistance like humans across multiple turns</td>
		<td align="center">ChatGPT</td>
        <td align="center">-</td>
        <td align="center">-</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">Multi</td>
		<td align="center">human-crafted</td>
		<td align="center">No</td>
</tr>
<tr>
		<td align="center">Vicuna</td>
        <td align="center">-</td>
        <td align="center"><a href="https://lmsys.org/blog/2023-03-30-vicuna/" target="_blank">project</a></td>
		<td align="center">70K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">user-shared</td>
		<td align="center">No</td>
</tr>
<tr>
		<td align="center">Guanaco</td>
        <td align="center">-</td>
        <td align="center"><a href="https://huggingface.co/datasets/JosephusCheung/GuanacoDataset" target="_blank">project</a></td>
		<td align="center">534,530</td>
		<td align="center">-</td>
		<td align="center">Multi</td>
		<td align="center">model-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">OpenAssistant</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.07327" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/LAION-AI/Open-Assistant" target="_blank">project</a></td>
		<td align="center">161,443</td>
		<td align="center">-</td>
		<td align="center">Multi</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Baize v1</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.01196" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/project-baize/baize-chatbot" target="_blank">project</a></td>
		<td align="center">111.5K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">ChatGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">UltraChat</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.14233" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/thunlp/UltraChat" target="_blank">project</a></td>
		<td align="center">675K</td>
		<td align="center">-</td>
		<td align="center">En&Zh</td>
		<td align="center">model-generated</td>
		<td align="center">Yes</td>
</tr>
</table>

### Models

<table border="1" align="center" style="text-align:center;">
    <tr>
        <th>Model Name</th>
        <th># Params</th> 
        <th>Paper</th>
        <th>Project</th>
        <th>Base Model</th>
        <th colspan="3">Instruction Train Set</th>
    </tr>
    <tr>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th>Self-build</th>
        <th>Name</th>
        <th>Size</th>
    </tr>
    <tr>
        <td align="center">Instruct-GPT</td>
        <td align="center">176B</td>
        <td align="center"><a href="https://www.example.com/project1" target="_blank">paper</a></td>
        <td align="center">-</td>
        <td align="center">GPT-3</td>
        <td align="center">Yes</td>
        <td align="center">-</td>
        <td align="center">-</td>
    </tr>
    <tr>
        <td align="center">BLOOMZ</td>
        <td align="center">176B</td>
        <td align="center"><a href="https://www.example.com/project1" target="_blank">paper</a></td>
        <td align="center"><a href="https://huggingface.co/bigscience/bloomz" target="_blank">project</a></td>
        <td align="center">BLOOM</td>
        <td align="center">No</td>
        <td align="center">xP3</td>
        <td align="center">-</td>
    </tr>
    <tr>
        <td align="center"></td>
        <td align="center"></td>
        <td align="center"><a href="https://www.example.com/project1" target="_blank">paper</a></td>
        <td align="center"><a href="https://www.example.com/project1" target="_blank">project</a></td>
        <td align="center"></td>
        <td align="center"></td>
        <td align="center"></td>
        <td align="center"></td>
    </tr>
<tr>
		<td align="center">FLAN-T5</td>
		<td align="center">11B</td>
		<td align="center"><a href="https://arxiv.org/abs/2210.11416" target="_blank">paper</a></td>
		<td align="center"><a href="https://huggingface.co/google/flan-t5-xxl" target="_blank">project</a></td>
		<td align="center">T5</td>
		<td align="center">No</td>
		<td align="center">FLAN 2021</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Alpaca</td>
		<td align="center">7B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/tatsu-lab/stanford_alpaca" target="_blank">project</a></td>
		<td align="center">LLaMA</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">52K</td>
</tr>
<tr>
		<td align="center">Vicuna</td>
		<td align="center">13B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/lm-sys/FastChat" target="_blank">project</a></td>
		<td align="center">LLaMA</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">70K</td>
</tr>
<tr>
		<td align="center">GPT-4-LLM</td>
		<td align="center">7B</td>
		<td align="center"><a href="https://arxiv.org/abs/2304.03277" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM" target="_blank">project</a></td>
		<td align="center">LLaMA</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">52K</td>
</tr>
<tr>
		<td align="center">Claude</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">WizardLM</td>
		<td align="center">7B</td>
		<td align="center"><a href="https://arxiv.org/abs/2304.12244" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/nlpxucan/WizardLM" target="_blank">project</a></td>
		<td align="center">LLaMA</td>
		<td align="center">Yes</td>
		<td align="center">Evol-Instruct</td>
		<td align="center">70K</td>
</tr>
<tr>
		<td align="center">ChatGLM2</td>
		<td align="center">6B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/THUDM/ChatGLM2-6B" target="_blank">project</a></td>
		<td align="center">GLM</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">1.1 Tokens</td>
</tr>
<tr>
		<td align="center">LIMA</td>
		<td align="center">65B</td>
		<td align="center"><a href="https://arxiv.org/abs/2305.11206 ｜  -" target="_blank">paper</a></td>
		<td align="center"><a href="LLaMA" target="_blank">project</a></td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">1K</td>
</tr>
<tr>
		<td align="center">OPT-IML</td>
		<td align="center">175B</td>
		<td align="center"><a href="https://arxiv.org/abs/2212.12017" target="_blank">paper</a></td>
		<td align="center"><a href="https://huggingface.co/facebook/opt-iml-30b" target="_blank">project</a></td>
		<td align="center">OPT</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Dolly 2.0</td>
		<td align="center">12B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/databrickslabs/dolly" target="_blank">project</a></td>
		<td align="center">Pythia</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">15K</td>
</tr>
<tr>
		<td align="center">Falcon-Instruct</td>
		<td align="center">40B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://huggingface.co/tiiuae/falcon-40b-instruct" target="_blank">project</a></td>
		<td align="center">Falcon</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Guanaco</td>
		<td align="center">7B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://huggingface.co/JosephusCheung/Guanaco" target="_blank">project</a></td>
		<td align="center">LLaMA</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">586K</td>
</tr>
<tr>
		<td align="center">Minotaur</td>
		<td align="center">15B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://huggingface.co/openaccess-ai-collective/minotaur-15b" target="_blank">project</a></td>
		<td align="center">Starcoder Plus</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Nous-Hermes</td>
		<td align="center">13B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://huggingface.co/NousResearch/Nous-Hermes-13b" target="_blank">project</a></td>
		<td align="center">LLaMA</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">300K+</td>
</tr>
<tr>
		<td align="center">TÜLU</td>
		<td align="center">6.7B</td>
		<td align="center"><a href="https://arxiv.org/abs/2306.04751" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/allenai/open-instruct" target="_blank">project</a></td>
		<td align="center">OPT</td>
		<td align="center">No</td>
		<td align="center">Mixed</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">YuLan-Chat</td>
		<td align="center">13B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/RUC-GSAI/YuLan-Chat" target="_blank">project</a></td>
		<td align="center">LLaMA</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">250K</td>
</tr>
<tr>
		<td align="center">MOSS</td>
		<td align="center">16B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/OpenLMLab/MOSS" target="_blank">project</a></td>
		<td align="center">-</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Airoboros</td>
		<td align="center">13B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/jondurbin/airoboros" target="_blank">project</a></td>
		<td align="center">LLaMA</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">UltraLM</td>
		<td align="center">13B</td>
		<td align="center"><a href="https://arxiv.org/abs/2305.14233" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/thunlp/UltraChat" target="_blank">project</a></td>
		<td align="center">LLaMA</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>

</table>

## Multi-modality Instruction Tuning

### Datasets 

<table border="1" align="center" style="text-align:center;">
<tr>
        <th style="width:8cm;">Dataset Name</th>
        <th>Paper</th>
        <th>Project</th>
        <th colspan="2">Modalities</th>
        <th># Tasks</th>
</tr>
<tr>
        <th></th>
        <th></th>
        <th></th>
        <th>Modality Pair</th>
        <th># Instance</th>
        <th></th>
</tr>
<tr>
		<td align="center">MUL-TIINSTRUCT</td>
        <td align="center"><a href="https://arxiv.org/abs/2212.10773" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/VT-NLP/MultiInstruct" target="_blank">project</a></td>
		<td align="center">Image-Text</td>
		<td align="center">5K to 5M per task</td>
		<td align="center">62 </td>
</tr>
<tr>
		<td align="center">PMC-VQA</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.10415" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/xiaoman-zhang/PMC-VQA" target="_blank">project</a></td>
		<td align="center">Image-Text</td>
		<td align="center">227K</td>
		<td align="center">9</td>
</tr>
<tr>
        <td rowspan="2" align="center">LAMM</td>
        <td rowspan="2" align="center"><a href="https://arxiv.org/abs/2306.06687" target="_blank">paper</a></td>
		<td rowspan="2" align="center"><a href="https://github.com/OpenLAMM/LAMM" target="_blank">project</a></td>
		<td align="center">Image-Text</td>
		<td align="center">186K</td>
		<td align="center">9</td>
</tr>
<tr>
		<td align="center">Point Cloud-Text</td>
		<td align="center">10K</td>
		<td align="center">3</td>
</tr>
</table>

### Models

<table border="1" align="center" style="text-align:center;">
<tr>
        <th style="width:8cm;">Model Name</th>
        <th># Params</th>
        <th>Paper</th>
        <th>Project</th>
        <th>Modality</th>
        <th colspan="2">Base Model</th>
         <th colspan="2">Train set</th>
</tr>
<tr>
        <th style="width:8cm;"></th>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th>Model Name</th>
        <th># Params</th>
        <th>Self-build</th>
        <th>Size</th>
</tr>
<tr>
		<td align="center">InstructPix2Pix</td>
        <td align="center">983M</td>
        <td align="center"><a href="https://arxiv.org/abs/2211.09800" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/timothybrooks/instruct-pix2pix" target="_blank">project</a></td>
		<td align="center">Image-Text</td>
		<td align="center">Stable Diffusion</td>
        <td align="center">983M</td>
        <td align="center">Yes</td>
        <td align="center">450K</td>
</tr>
<tr>
        <td rowspan="3" align="center">LLaVA</td>
         <td rowspan="3" align="center">13B</td>
        <td rowspan="3" align="center"><a href="https://arxiv.org/abs/2304.08485" target="_blank">paper</a></td>
		<td rowspan="3" align="center"><a href="https://github.com/haotian-liu/LLaVA" target="_blank">project</a></td>
		 <td rowspan="3" align="center">Image-Text</td>
		<td align="center">CLIP</td>
        <td align="center">400M</td>
         <td rowspan="3" align="center">Yes</td>
         <td rowspan="3" align="center">158K</td>
</tr>
<tr>
		<td align="center">LLaMA</td>
        <td align="center">7B</td>
</tr>
<tr>
		<td align="center">LLaMA</td>
        <td align="center">7B</td>
</tr>
<tr>
        <td rowspan="3" align="center">Video-LLaMA</td>
         <td rowspan="3" align="center">-</td>
        <td rowspan="3" align="center"><a href="https://arxiv.org/abs/2306.02858" target="_blank">paper</a></td>
		<td rowspan="3" align="center"><a href="https://github.com/DAMO-NLP-SG/Video-LLaMA" target="_blank">project</a></td>
		 <td rowspan="3" align="center">Image-Text-Video-Audio</td>
		<td align="center">BLIP-2</td>
        <td align="center">-</td>
         <td rowspan="3" align="center">No</td>
         <td rowspan="3" align="center">-</td>
</tr>
<tr>
		<td align="center">ImageBind</td>
        <td align="center">-</td>
</tr>
<tr>
		<td align="center">Vicuna</td>
        <td align="center">7B/13B</td>
</tr>
<tr>
		<td align="center">InstructBLIP</td>
        <td align="center">12B</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.06500" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/salesforce/LAVIS/tree/main/projects/instructblip" target="_blank">project</a></td>
		<td align="center">Image-Text-Video</td>
		<td align="center">BLIP-2</td>
        <td align="center">-</td>
        <td align="center">No</td>
        <td align="center">-</td>
</tr>
<tr>
		<td align="center">Otter</td>
        <td align="center">-</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.03726" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/Luodian/Otter" target="_blank">project</a></td>
		<td align="center">Image-Text-Video</td>
		<td align="center">OpenFlamingo</td>
        <td align="center">9B</td>
        <td align="center">Yes</td>
        <td align="center">2.8M</td>
</tr>
<tr>
		<td align="center">MultiModal-GPT</td>
        <td align="center">-</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.04790" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/open-mmlab/Multimodal-GPT" target="_blank">project</a></td>
		<td align="center">Image-Text-Video</td>
		<td align="center">OpenFlamingo</td>
        <td align="center">9B</td>
        <td align="center">No</td>
        <td align="center">-</td>
</tr>
</table>

## Domain-specific Instruction Tuning

<table border="1" align="center" style="text-align:center;">
<tr>
        <th style="width:8cm;">Domain</th>
        <th>Model Name</th>
        <th># Params</th>
        <th>Paper</th>
        <th>Project</th>
        <th>Base Model</th>
        <th>Train Size</th>
</tr>
<tr>
        <td rowspan="3" align="center">Medical</td>
         <td align="center">Radiology-GPT</td>
        <td align="center">7B</td>
        <td align="center"><a href="" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">Alpaca</td>
        <td align="center">122K</td>
</tr>
<tr>
        <td align="center">ChatDoctor</td>
        <td align="center">7B</td>
        <td align="center"><a href="" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">LLaMA</td>
        <td align="center">122K</td>
</tr>
<tr>
         <td align="center">ChatGLM-Med</td>
        <td align="center">6B</td>
        <td align="center"><a href="" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">ChatGLM</td>
        <td align="center">-</td>
</tr>

<tr>
        <td rowspan="3" align="center">Writing</td>
         <td align="center">Writing-Alpaca</td>
        <td align="center">7B</td>
        <td align="center"><a href="" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">LLaMa </td>
        <td align="center">-</td>
</tr>
<tr>
         <td align="center">CoEdIT</td>
        <td align="center">11B</td>
        <td align="center"><a href="" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">FlanT5</td>
        <td align="center">82K</td>
</tr>
<tr>
         <td align="center">CoPoet</td>
        <td align="center">11B</td>
        <td align="center"><a href="" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">T5</td>
        <td align="center">-</td>
</tr>
<tr>
        <td align="center">Code Generation</td>
         <td align="center">WizardCoder</td>
        <td align="center">15B</td>
        <td align="center"><a href="" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">StarCoder</td>
        <td align="center">78K</td>
</tr>
<tr>
        <td align="center">Sentiment Analysis</td>
         <td align="center">IT-MTL</td>
        <td align="center">220M</td>
        <td align="center"><a href="https://aclanthology.org/2023.wassa-1.3.pdf" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">T5</td>
        <td align="center">-</td>
</tr>
<tr>
        <td align="center">Arithmetic</td>
         <td align="center">Goat</td>
        <td align="center">7B</td>
        <td align="center"><a href="https://aclanthology.org/2023.wassa-1.3.pdf" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">LLaMA</td>
        <td align="center">1.0M</td>
</tr>
<tr>
        <td align="center">Information Extraction</td>
         <td align="center">InstructUIE</td>
        <td align="center">11B</td>
        <td align="center"><a href="" target="_blank">paper</a></td>
		<td align="center"><a href="" target="_blank">project</a></td>
        <td align="center">FLANT5</td>
        <td align="center">1.0M</td>
</tr>
</table> 

