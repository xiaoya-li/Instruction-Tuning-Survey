# Instruction Tuning for Large Language Models: A Survey

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

### News 


* [21 Aug, 2023] 🥳 We release the first version of the paper. 


## Table of Contents 
* [Overview](#Overview)
* [Instruction Tuning](#Instruction-Tuning)
  * [Datasets](#Datasets)
  * [Models](#Models)
* [Multi-modality Instruction Tuning](#Multi-modality-Instruction-Tuning)
  * [Datasets](#Datasets)
  * [Models](#Models)
* [Domain-specific Instruction Tuning](#Domain-specific-Instruction-Tuning)
* [Efficient Tuning Techniques](#Efficient-Tuning-Techniques)
* [References](#References)
* [Contact](#Contact) 
  

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


## Instruction Tuning

### Datasets

<table border="1" style="text-align:center;">
<tr>
        <th style="width:12cm;">Type</th>
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
        <td align="center">UnifiedQA [<a href="#ref1">1</a>]</td> 
        <td align="center"><a href="https://arxiv.org/abs/2005.00700" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/allenai/unifiedqa" target="_blank">project</a></td>
        <td align="center">750K</td>
        <td align="center">46</td>
        <td align="center">En</td>
        <td align="center">human-crafted</td>
        <td align="center">Yes</td>
</tr>
<tr>
        <td align="center">OIG [<a href="#ref2">2</a>]</td> 
        <td align="center">-</td>
        <td align="center"><a href="https://github.com/LAION-AI/Open-Instruction-Generalist" target="_blank">project</a></td>
        <td align="center">43M</td>
        <td align="center">30</td>
        <td align="center">En</td>
        <td align="center">human-model-mixed</td>
        <td align="center">Yes</td>
</tr>
<tr>
		<td align="center">UnifiedSKG [<a href="#ref3">3</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2201.05966" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/hkunlp/unifiedskg" target="_blank">project</a></td>
		<td align="center">0.8M</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Natural Instructions [<a href="#ref4">4</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2104.08773" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/allenai/natural-instructions-v1" target="_blank">project</a></td>
		<td align="center">193K</td>
		<td align="center">61</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Super-Natural Instructions [<a href="#ref5">5</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2204.07705" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/allenai/natural-instructions" target="_blank">project</a></td>
		<td align="center">5M</td>
		<td align="center">76</td>
		<td align="center">55 Lang</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">P3 [<a href="#ref6">6</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2110.08207" target="_blank">paper</a></td>
        <td align="center"><a href="https://huggingface.co/datasets/bigscience/P3" target="_blank">project</a></td>
		<td align="center">12M</td>
		<td align="center">62</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">xP3 [<a href="#ref7">7</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2211.01786" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/bigscience-workshop/xmtf" target="_blank">project</a></td>
		<td align="center">81M</td>
		<td align="center">53</td>
		<td align="center">46 Lang</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Flan 2021 [<a href="#ref8">8</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2301.13688" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/google-research/FLAN" target="_blank">project</a></td>
		<td align="center">4.4M</td>
		<td align="center">62</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">COIG [<a href="#ref9">9</a>]</td>
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
		<td align="center">InstructGPT [<a href="#ref10">10</a>]</td>
        <td align="center">-</td>
        <td align="center">-</td>
		<td align="center">13K</td>
		<td align="center">-</td>
		<td align="center">Multi</td>
		<td align="center">human-crafted</td>
		<td align="center">No</td>
</tr>
<tr>
		<td align="center">Unnatural Instructions [<a href="#ref11">11</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2212.09689" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/orhonovich/unnatural-instructions" target="_blank">project</a></td>
		<td align="center">240K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">InstructGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Self-Instruct [<a href="#ref12">12</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2212.10560" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/yizhongw/self-instruct" target="_blank">project</a></td>
		<td align="center">52K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">InstructGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">InstructWild [<a href="#ref13">13</a>]</td>
        <td align="center">-</td>
        <td align="center"><a href="https://github.com/XueFuzhao/InstructionWild" target="_blank">project</a></td>
		<td align="center">104K</td>
		<td align="center">429</td>
		<td align="center">-</td>
		<td align="center">model-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Evol-Instruct [<a href="#ref14">14</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.12244" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/nlpxucan/evol-instruct" target="_blank">project</a></td>
		<td align="center">52K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">ChatGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Alpaca [<a href="#ref15">15</a>]</td>
        <td align="center">-</td>
        <td align="center"><a href="https://github.com/tatsu-lab/stanford_alpaca" target="_blank">project</a></td>
		<td align="center">52K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">InstructGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">LogiCoT [<a href="#ref16">16</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.12147" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/csitfun/LogiCoT" target="_blank">project</a></td>
		<td align="center">-</td>
		<td align="center">2</td>
		<td align="center">En</td>
		<td align="center">GPT-4-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Dolly [<a href="#ref17">17</a>]</td>
        <td align="center">-</td>
        <td align="center"><a href="https://huggingface.co/datasets/databricks/databricks-dolly-15k" target="_blank">project</a></td>
		<td align="center">15K</td>
		<td align="center">7</td>
		<td align="center">En</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">GPT-4-LLM [<a href="#ref18">18</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.03277" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM" target="_blank">project</a></td>
		<td align="center">52K</td>
		<td align="center">-</td>
		<td align="center">En&Zh</td>
		<td align="center">GPT-4-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">LIMA [<a href="#ref19">19</a>]</td>
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
		<td align="center">ChatGPT [<a href="#ref20">20</a>]</td>
        <td align="center">-</td>
        <td align="center">-</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">Multi</td>
		<td align="center">human-crafted</td>
		<td align="center">No</td>
</tr>
<tr>
		<td align="center">Vicuna [<a href="#ref21">21</a>]</td>
        <td align="center">-</td>
        <td align="center"><a href="https://lmsys.org/blog/2023-03-30-vicuna/" target="_blank">project</a></td>
		<td align="center">70K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">user-shared</td>
		<td align="center">No</td>
</tr>
<tr>
		<td align="center">Guanaco [<a href="#ref22">22</a>]</td>
        <td align="center">-</td>
        <td align="center"><a href="https://huggingface.co/datasets/JosephusCheung/GuanacoDataset" target="_blank">project</a></td>
		<td align="center">534,530</td>
		<td align="center">-</td>
		<td align="center">Multi</td>
		<td align="center">model-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">OpenAssistant [<a href="#ref23">23</a></a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.07327" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/LAION-AI/Open-Assistant" target="_blank">project</a></td>
		<td align="center">161,443</td>
		<td align="center">-</td>
		<td align="center">Multi</td>
		<td align="center">human-crafted</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">Baize v1 [<a href="#ref24">24</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.01196" target="_blank">paper</a></td>
        <td align="center"><a href="https://github.com/project-baize/baize-chatbot" target="_blank">project</a></td>
		<td align="center">111.5K</td>
		<td align="center">-</td>
		<td align="center">En</td>
		<td align="center">ChatGPT-generated</td>
		<td align="center">Yes</td>
</tr>
<tr>
		<td align="center">UltraChat [<a href="#ref25">25</a>]</td>
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

<table border="1" style="text-align:center;">
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

<table border="1" style="text-align:center;">
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

<table border="1" style="text-align:center;">
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

<table border="1" style="text-align:center;">
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
        <td align="center"><a href="https://arxiv.org/abs/2306.08666" target="_blank">paper</a></td>
		<td align="center"><a href="https://huggingface.co/spaces/allen-eric/radiology-gpt" target="_blank">project</a></td>
        <td align="center">Alpaca</td>
        <td align="center">122K</td>
</tr>
<tr>
        <td align="center">ChatDoctor</td>
        <td align="center">7B</td>
        <td align="center"><a href="https://arxiv.org/abs/2303.14070" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/Kent0n-Li/ChatDoctor" target="_blank">project</a></td>
        <td align="center">LLaMA</td>
        <td align="center">122K</td>
</tr>
<tr>
         <td align="center">ChatGLM-Med</td>
        <td align="center">6B</td>
        <td align="center">-</td>
		<td align="center"><a href="https://github.com/SCIR-HI/Med-ChatGLM" target="_blank">project</a></td>
        <td align="center">ChatGLM</td>
        <td align="center">-</td>
</tr>

<tr>
        <td rowspan="3" align="center">Writing</td>
         <td align="center">Writing-Alpaca</td>
        <td align="center">7B</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.13225" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/facebookresearch/EditEval" target="_blank">project</a></td>
        <td align="center">LLaMa </td>
        <td align="center">-</td>
</tr>
<tr>
         <td align="center">CoEdIT</td>
        <td align="center">11B</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.09857" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/vipulraheja/coedit" target="_blank">project</a></td>
        <td align="center">FlanT5</td>
        <td align="center">82K</td>
</tr>
<tr>
         <td align="center">CoPoet</td>
        <td align="center">11B</td>
        <td align="center"><a href="https://aclanthology.org/2022.emnlp-main.460/" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/vishakhpk/creative-instructions" target="_blank">project</a></td>
        <td align="center">T5</td>
        <td align="center">-</td>
</tr>
<tr>
        <td align="center">Code Generation</td>
         <td align="center">WizardCoder</td>
        <td align="center">15B</td>
        <td align="center"><a href="https://arxiv.org/abs/2306.08568" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/nlpxucan/WizardLM" target="_blank">project</a></td>
        <td align="center">StarCoder</td>
        <td align="center">78K</td>
</tr>
<tr>
        <td align="center">Sentiment Analysis</td>
         <td align="center">IT-MTL</td>
        <td align="center">220M</td>
        <td align="center"><a href="https://aclanthology.org/2023.wassa-1.3.pdf" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/amazon-science/instruction-tuning-for-absa" target="_blank">project</a></td>
        <td align="center">T5</td>
        <td align="center">-</td>
</tr>
<tr>
        <td align="center">Arithmetic</td>
         <td align="center">Goat</td>
        <td align="center">7B</td>
        <td align="center"><a href="https://aclanthology.org/2023.wassa-1.3.pdf" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/liutiedong/goat" target="_blank">project</a></td>
        <td align="center">LLaMA</td>
        <td align="center">1.0M</td>
</tr>
<tr>
        <td align="center">Information Extraction</td>
         <td align="center">InstructUIE</td>
        <td align="center">11B</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.08085" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/BeyonderXX/InstructUIE" target="_blank">project</a></td>
        <td align="center">FLANT5</td>
        <td align="center">1.0M</td>
</tr>
</table> 

## Efficient Tuning Techniques

<table border="1" style="text-align:center;">
<tr>
        <th style="width:8cm;">Name</th>
        <th>Paper</th>
        <th>Project</th>
</tr>
<tr>
        <td align="center">LoRA</td>
        <td align="center"><a href="https://arxiv.org/abs/2106.09685" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/microsoft/LoRA" target="_blank">project</a></td>
</tr>
<tr>
        <td align="center">HINT</td>
        <td align="center"><a href="https://arxiv.org/abs/2212.10315" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/allenai/hyper-task-descriptions" target="_blank">project</a></td>
</tr>

<tr>
        <td align="center">QLoRA</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.14314" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/artidoro/qlora" target="_blank">project</a></td>
</tr>

<tr>
        <td align="center">LOMO</td>
        <td align="center"><a href="https://arxiv.org/abs/2306.09782" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/OpenLMLab/LOMO" target="_blank">project</a></td>
</tr>

<tr>
        <td align="center">Delta-tuning</td>
        <td align="center"><a href="https://arxiv.org/abs/2203.06904" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/thunlp/OpenDelta" target="_blank">project</a></td>
</tr>


</table>

## References

<a id="ref1">[1]</a> Khashabi, Daniel, Sewon Min, Tushar Khot, Ashish Sabharwal, Oyvind Tafjord, Peter Clark, and Hannaneh Hajishirzi. Unifiedqa: Crossing format boundaries with a single qa system. arXiv preprint arXiv:2005.00700 (2020). [Paper](https://arxiv.org/abs/2005.00700) 

<a id="ref2">[2]</a> LAION.ai. Oig: the open instruction generalist dataset, 2023.

<a id="ref3">[3]</a> Tianbao Xie, Chen Henry Wu, Peng Shi, Ruiqi Zhong, Torsten Scholak, Michihiro Yasunaga, Chien-Sheng Wu, Ming Zhong, Pengcheng Yin, Sida I. Wang, Victor Zhong, Bailin Wang, Chengzu Li,
Connor Boyle, Ansong Ni, Ziyu Yao, Dragomir R.
Radev, Caiming Xiong, Lingpeng Kong, Rui Zhang,
Noah A. Smith, Luke Zettlemoyer, and Tao Yu.
Unifiedskg: Unifying and multi-tasking structured
knowledge grounding with text-to-text language
models. In Conference on Empirical Methods in
Natural Language Processing, 2022.


<a id="ref4">[4]</a> Or Honovich, Thomas Scialom, Omer Levy, and
Timo Schick. Unnatural instructions: Tuning
language models with (almost) no human labor.
arXiv preprint arXiv:2212.09689, 2022.

<a id="ref5">[5]</a> Yizhong Wang, Swaroop Mishra, Pegah
Alipoormolabashi, Yeganeh Kordi, Amirreza
Mirzaei, Anjana Arunkumar, Arjun Ashok,
Arut Selvan Dhanasekaran, Atharva Naik, David
Stap, et al. Super-naturalinstructions:generalization
via declarative instructions on 1600+ tasks. In
EMNLP, 2022.

<a id="ref6">[6]</a>  Victor Sanh, Albert Webson, Colin Raffel, Stephen H
Bach, Lintang Sutawika, Zaid Alyafeai, Antoine
Chaffin, Arnaud Stiegler, Teven Le Scao, Arun
Raja, et al. Multitask prompted training enables
zero-shot task generalization. arXiv preprint
arXiv:2110.08207, 2021.

<a id="ref7">[7]</a> Niklas Muennighoff, Thomas Wang, Lintang
Sutawika, Adam Roberts, Stella Biderman, Teven Le
Scao, M Saiful Bari, Sheng Shen, Zheng-Xin
Yong, Hailey Schoelkopf, et al. Crosslingual
generalization through multitask finetuning. arXiv
preprint arXiv:2211.01786, 2022.

<a id="ref8">[8]</a> Shayne Longpre, Le Hou, Tu Vu, Albert Webson,
Hyung Won Chung, Yi Tay, Denny Zhou, Quoc V Le,
Barret Zoph, Jason Wei, et al. The flan collection:
Designing data and methods for effective instruction
tuning. arXiv preprint arXiv:2301.13688, 2023.

<a id="ref9">[9]</a> Ge Zhang, Yemin Shi, Ruibo Liu, Ruibin Yuan, Yizhi
Li, Siwei Dong, Yu Shu, Zhaoqun Li, Zekun Wang,
Chenghua Lin, Wen-Fen Huang, and Jie Fu. Chinese
open instruction generalist: A preliminary release.
ArXiv, abs/2304.07987, 2023.

<a id="ref10">[10]</a> Long Ouyang, Jeffrey Wu, Xu Jiang, Diogo
Almeida, Carroll Wainwright, Pamela Mishkin,
Chong Zhang, Sandhini Agarwal, Katarina Slama,
Alex Ray, et al. Training language models to follow
instructions with human feedback. Advances in
Neural Information Processing Systems, 35:27730–
27744, 2022.


<a id="ref11">[11]</a> Honovich, Or, Thomas Scialom, Omer Levy, and Timo Schick. Unnatural instructions: Tuning language models with (almost) no human labor. arXiv preprint arXiv:2212.09689 (2022).

<a id="ref12">[12]</a> Yizhong Wang, Yeganeh Kordi, Swaroop Mishra,
Alisa Liu, Noah A Smith, Daniel Khashabi, and
Hannaneh Hajishirzi. Self-instruct: Aligning
language model with self generated instructions.
arXiv preprint arXiv:2212.10560, 2022.

<a id="ref13">[13]</a> Fuzhao Xue, Kabir Jain, Mahir Hitesh Shah,
Zangwei Zheng, and Yang You. Instruction
in the wild: A user-based instruction dataset.
`github.com/XueFuzhao/InstructionWild,2023`.


<a id="ref14">[14]</a> Can Xu, Qingfeng Sun, Kai Zheng, Xiubo Geng,
Pu Zhao, Jiazhan Feng, Chongyang Tao, and Daxin
Jiang. Wizardlm: Empowering large language
models to follow complex instructions, 2023.

<a id="ref15">[15]</a> Rohan Taori, Ishaan Gulrajani, Tianyi Zhang,
Yann Dubois, Xuechen Li, Carlos Guestrin, Percy
Liang, and Tatsunori B Hashimoto. Alpaca:
A strong, replicable instruction-following model.
Stanford Center for Research on Foundation Models.
`https://crfm.stanford.edu/2023/03/13/alpaca.html`,
3(6):7, 2023.


<a id="ref16">[16]</a> Hanmeng Liu, Zhiyang Teng, Leyang Cui, Chaoli
Zhang, Qiji Zhou, and Yue Zhang. Logicot: Logical
chain-of-thought instruction-tuning data collection
with gpt-4. ArXiv, abs/2305.12147, 2023.

<a id="ref17">[17]</a> Mike Conover, Matt Hayes, Ankit Mathur, Xiangrui
Meng, Jianwei Xie, Jun Wan, Sam Shah, Ali Ghodsi,
Patrick Wendell, Matei Zaharia, et al. Free dolly:
Introducing the world’s first truly open instruction-
tuned llm, 2023.

<a id="ref18">[18]</a> Baolin Peng, Chunyuan Li, Pengcheng He, Michel
Galley, and Jianfeng Gao. Instruction tuning with
gpt-4. arXiv preprint arXiv:2304.03277, 2023.

<a id="ref19">[19]</a> Chunting Zhou, Pengfei Liu, Puxin Xu, Srini Iyer,
Jiao Sun, Yuning Mao, Xuezhe Ma, Avia Efrat, Ping
Yu, L. Yu, Susan Zhang, Gargi Ghosh, Mike Lewis,
Luke Zettlemoyer, and Omer Levy. Lima: Less is
more for alignment. ArXiv, abs/2305.11206, 2023.

<a id="ref20">[20]</a> OpenAI. Introducing chatgpt. Blog post
openai.com/blog/chatgpt, 2022.

<a id="ref21">[21]</a> Wei-Lin Chiang, Zhuohan Li, Zi Lin, Ying Sheng,
Zhanghao Wu, Hao Zhang, Lianmin Zheng, Siyuan
Zhuang, Yonghao Zhuang, Joseph E Gonzalez, et al.
Vicuna: An open-source chatbot impressing gpt-4
with 90%* chatgpt quality. See `https://vicuna.lmsys.org` (accessed 14 April 2023), 2023.

<a id="ref22">[22]</a> JosephusCheung. Guanaco: Generative universal
assistant for natural-language adaptive context-aware
omnilingual outputs, 2021.


<a id="ref23">[23]</a> Andreas Köpf, Yannic Kilcher, Dimitri von Rütte,
Sotiris Anagnostidis, Zhi-Rui Tam, Keith Stevens,
Abdullah Barhoum, Nguyen Minh Duc, Oliver
Stanley, Richárd Nagyfi, et al. Openassistant
conversations–democratizing large language model
alignment. arXiv preprint arXiv:2304.07327, 2023.


<a id="ref24">[24]</a> Mike Conover, Matt Hayes, Ankit Mathur, Jianwei
Xie, Jun Wan, Sam Shah, Ali Ghodsi, Patrick
Wendell, Matei Zaharia, and Reynold Xin. Free
dolly: Introducing the world’s first truly open
instruction-tuned llm, 2023.

<a id="ref25">[25]</a> Ning Ding, Yulin Chen, Bokai Xu, Yujia Qin, Zhi
Zheng, Shengding Hu, Zhiyuan Liu, Maosong Sun,
and Bowen Zhou. Enhancing chat language models
by scaling high-quality instructional conversations.
arXiv preprint arXiv:2305.14233, 2023.


## Contact 

If you have any questions or suggestions, please feel free to create an issue or send an e-mail to `xiaoya_li@shannonai.com`.

