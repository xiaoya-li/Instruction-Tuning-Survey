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



## Natural Language Instruction Tuning

### Datasets

<table border="1" align="center" style="text-align:center;">
<tr>
        <th style="width:5cm;">Type</th>
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
		<td align="center">Super-Natural Instructions}</td>
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
		<td align="center">En</td>
		<td align="center">Zh</td>
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
		<td align="center">UltraChat~tnotex{id:22}</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.14233" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/thunlp/UltraChat" target="_blank">project</a></td>
		<td align="center">675K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">Zh</td>
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
</table>



| FLAN-T5 | 11B   |  [paper]()   |     [project](https://huggingface.co/google/flan-t5-xxl)    | T5      | No   | FLAN 2021 | - | 
| Alpaca | 7B     |  [paper]()  |    [project](https://github.com/tatsu-lab/stanford_alpaca)  | LLaMA   | Yes       | -  | 52K  | 
| Vicuna | 13B    |  [paper]()  |    [project](https://github.com/lm-sys/FastChat)   | LLaMA   | Yes       | -  | 70K  | 
| GPT-4-LLM | 7B    |  [paper]()   |     [project](https://github.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM)  | LLaMA   | Yes       | -  | 52K | 
| Claude | -     |  [paper]()  |     -     | -       | Yes       | -  | - | 
| WizardLM | 7B   |  [paper]()   |    [project](https://github.com/nlpxucan/WizardLM)   | LLaMA   | Yes       | Evol-Instruct | 70K  | 
| ChatGLM2 | 6B   |  [paper]()   |    [project](https://github.com/THUDM/ChatGLM2-6B)   | GLM     | Yes       | -  | 1.1 Tokens | 
| LIMA | 65B   | [paper]() ｜  -  | LLaMA   | Yes       | -  | 1K  | 
| OPT-IML | 175B |  [paper]()  |    [project](https://huggingface.co/facebook/opt-iml-30b)   | OPT     | No | -  | - | 
| Dolly 2.0 | 12B  |  [paper]()  |    [project](https://github.com/databrickslabs/dolly)    | Pythia  | No  | -  | 15K  | 
| Falcon-Instruct | 40B  |  [paper]()  |   [project](https://huggingface.co/tiiuae/falcon-40b-instruct)    | Falcon  | No  | -  | - | 
| Guanaco | 7B   |  [paper]()  |    [project](https://huggingface.co/JosephusCheung/Guanaco)    | LLaMA   | Yes       | -  | 586K | 
| Minotaur | 15B   |  [paper]()   |    [project](https://huggingface.co/openaccess-ai-collective/minotaur-15b)  | Starcoder Plus | No   | -  | -  | 
| Nous-Hermes | 13B  |  [paper]()   |    [project](https://huggingface.co/NousResearch/Nous-Hermes-13b)   | LLaMA   | No   | -  | 300K+ | 
| TÜLU  | 6.7B  |  [paper]()  |   [project](https://github.com/allenai/open-instruct)   | OPT     | No     | Mixed     | - | 
| YuLan-Chat | 13B  |  [paper]()  |    [project](https://github.com/RUC-GSAI/YuLan-Chat)    | LLaMA   | Yes     | -  | 250K  | 
| MOSS  | 16B   |  [paper]()  |    [project](https://github.com/OpenLMLab/MOSS)   | -  | Yes | -  | -  | 
| Airoboros  | 13B   |  [paper]() |    [project](https://github.com/jondurbin/airoboros)    | LLaMA   | Yes       | -  | -  | 
| UltraLM | 13B    |  [paper]() |    [project](https://github.com/thunlp/UltraChat)   | LLaMA   | Yes       | -  | - | 

## Multi-modality Instruction Tuning

### Datasets

### Models

## Domain-specific Instruction Tuning


