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

## 🥳 News 

* Stay tuned! More related work will be updated!
* [7 Sep, 2023] Create the repository. 
* [21 Aug, 2023] Release the first version of the paper. 


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
        <td align="center">InstructGPT [<a href="#ref10">10</a>]</td>
        <td align="center">176B</td>
        <td align="center"><a href="https://www.example.com/project1" target="_blank">paper</a></td>
        <td align="center">-</td>
        <td align="center">GPT-3 [<a href="#ref26">26</a>]</td>
        <td align="center">Yes</td>
        <td align="center">-</td>
        <td align="center">-</td>
    </tr>
    <tr>
        <td align="center">BLOOMZ [<a href="#ref7">7</a>]</td>
        <td align="center">176B</td>
        <td align="center"><a href="https://www.example.com/project1" target="_blank">paper</a></td>
        <td align="center"><a href="https://huggingface.co/bigscience/bloomz" target="_blank">project</a></td>
        <td align="center">BLOOM [<a href="#ref27">27</a>]</td>
        <td align="center">No</td>
        <td align="center">xP3</td>
        <td align="center">-</td>
    </tr>
<tr>
		<td align="center">FLAN-T5 [<a href="#ref28">28</a>]</td>
		<td align="center">11B</td>
		<td align="center"><a href="https://arxiv.org/abs/2210.11416" target="_blank">paper</a></td>
		<td align="center"><a href="https://huggingface.co/google/flan-t5-xxl" target="_blank">project</a></td>
		<td align="center">T5 [<a href="#ref29">29</a>]</td>
		<td align="center">No</td>
		<td align="center">FLAN 2021</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Alpaca [<a href="#ref15">15</a>]</td>
		<td align="center">7B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/tatsu-lab/stanford_alpaca" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">52K</td>
</tr>
<tr>
		<td align="center">Vicuna [<a href="#ref21">21</a>]</td>
		<td align="center">13B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/lm-sys/FastChat" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">70K</td>
</tr>
<tr>
		<td align="center">GPT-4-LLM [<a href="#ref18">18</a>]</td>
		<td align="center">7B</td>
		<td align="center"><a href="https://arxiv.org/abs/2304.03277" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">52K</td>
</tr>
<tr>
		<td align="center">Claude [<a href="#ref31">31</a>]</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">-</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">WizardLM [<a href="#ref14">14</a>]</td>
		<td align="center">7B</td>
		<td align="center"><a href="https://arxiv.org/abs/2304.12244" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/nlpxucan/WizardLM" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
		<td align="center">Yes</td>
		<td align="center">Evol-Instruct</td>
		<td align="center">70K</td>
</tr>
<tr>
		<td align="center">ChatGLM2 [<a href="#ref32">32</a>]</td>
		<td align="center">6B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/THUDM/ChatGLM2-6B" target="_blank">project</a></td>
		<td align="center">GLM[<a href="#ref32">32</a>]</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">1.1 Tokens</td>
</tr>
<tr>
		<td align="center">LIMA [<a href="#ref19">19</a>]</td>
		<td align="center">65B</td>
		<td align="center"><a href="https://arxiv.org/abs/2305.11206 ｜  -" target="_blank">paper</a></td>
		<td align="center"><a href="LLaMA" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
		<td align="center">Yes</td>
		<td align="center">1K</td>
</tr>
<tr>
		<td align="center">OPT-IML [<a href="#ref33">33</a>]</td>
		<td align="center">175B</td>
		<td align="center"><a href="https://arxiv.org/abs/2212.12017" target="_blank">paper</a></td>
		<td align="center"><a href="https://huggingface.co/facebook/opt-iml-30b" target="_blank">project</a></td>
		<td align="center">OPT [<a href="#ref34">34</a>]</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Dolly 2.0 [<a href="#ref17">17</a>]</td>
		<td align="center">12B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/databrickslabs/dolly" target="_blank">project</a></td>
		<td align="center">Pythia [<a href="#ref35">35</a>]</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">15K</td>
</tr>
<tr>
		<td align="center">Falcon-Instruct [<a href="#ref36">36</a>]</td>
		<td align="center">40B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://huggingface.co/tiiuae/falcon-40b-instruct" target="_blank">project</a></td>
		<td align="center">Falcon [<a href="#ref37">37</a>]</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Guanaco [<a href="#ref22">22</a>]</td>
		<td align="center">7B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://huggingface.co/JosephusCheung/Guanaco" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">586K</td>
</tr>
<tr>
		<td align="center">Minotaur [<a href="#ref38">38</a>]</td>
		<td align="center">15B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://huggingface.co/openaccess-ai-collective/minotaur-15b" target="_blank">project</a></td>
		<td align="center">Starcoder Plus [<a href="#ref39">39</a>]</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Nous-Hermes [<a href="#ref40">40</a>]</td>
		<td align="center">13B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://huggingface.co/NousResearch/Nous-Hermes-13b" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
		<td align="center">No</td>
		<td align="center">-</td>
		<td align="center">300K+</td>
</tr>
<tr>
		<td align="center">TÜLU [<a href="#ref41">41</a>]</td>
		<td align="center">6.7B</td>
		<td align="center"><a href="https://arxiv.org/abs/2306.04751" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/allenai/open-instruct" target="_blank">project</a></td>
		<td align="center">OPT [<a href="#ref34">34</a>]</td>
		<td align="center">No</td>
		<td align="center">Mixed</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">YuLan-Chat [<a href="#ref42">42</a>]</td>
		<td align="center">13B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/RUC-GSAI/YuLan-Chat" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">250K</td>
</tr>
<tr>
		<td align="center">MOSS [<a href="#ref43">43</a>]</td>
		<td align="center">16B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/OpenLMLab/MOSS" target="_blank">project</a></td>
		<td align="center">-</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">Airoboros [<a href="#ref44">44</a>]</td>
		<td align="center">13B</td>
		<td align="center">-</td>
		<td align="center"><a href="https://github.com/jondurbin/airoboros" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
		<td align="center">Yes</td>
		<td align="center">-</td>
		<td align="center">-</td>
</tr>
<tr>
		<td align="center">UltraLM [<a href="#ref25">25</a>]</td>
		<td align="center">13B</td>
		<td align="center"><a href="https://arxiv.org/abs/2305.14233" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/thunlp/UltraChat" target="_blank">project</a></td>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
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
		<td align="center">MUL-TIINSTRUCT [<a href="#ref45">45</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2212.10773" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/VT-NLP/MultiInstruct" target="_blank">project</a></td>
		<td align="center">Image-Text</td>
		<td align="center">5K to 5M per task</td>
		<td align="center">62 </td>
</tr>
<tr>
		<td align="center">PMC-VQA [<a href="#ref46">46</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.10415" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/xiaoman-zhang/PMC-VQA" target="_blank">project</a></td>
		<td align="center">Image-Text</td>
		<td align="center">227K</td>
		<td align="center">9</td>
</tr>
<tr>
        <td rowspan="2" align="center">LAMM [<a href="#ref47">47</a>]</td>
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
		<td align="center">InstructPix2Pix [<a href="#ref48">48</a>]</td>
        <td align="center">983M</td>
        <td align="center"><a href="https://arxiv.org/abs/2211.09800" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/timothybrooks/instruct-pix2pix" target="_blank">project</a></td>
		<td align="center">Image-Text</td>
		<td align="center">Stable Diffusion [<a href="#ref63">63</a>]</td>
        <td align="center">983M</td>
        <td align="center">Yes</td>
        <td align="center">450K</td>
</tr>
<tr>
        <td rowspan="3" align="center">LLaVA [<a href="#ref49">49</a>]</td>
         <td rowspan="3" align="center">13B</td>
        <td rowspan="3" align="center"><a href="https://arxiv.org/abs/2304.08485" target="_blank">paper</a></td>
		<td rowspan="3" align="center"><a href="https://github.com/haotian-liu/LLaVA" target="_blank">project</a></td>
		 <td rowspan="3" align="center">Image-Text</td>
		<td align="center">CLIP [<a href="#ref50">50</a>]</td>
        <td align="center">400M</td>
         <td rowspan="3" align="center">Yes</td>
         <td rowspan="3" align="center">158K</td>
</tr>
<tr>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
        <td align="center">7B</td>
</tr>
<tr>
		<td align="center">LLaMA [<a href="#ref30">30</a>]</td>
        <td align="center">7B</td>
</tr>
<tr>
        <td rowspan="3" align="center">Video-LLaMA [<a href="#ref51">51</a>]</td>
         <td rowspan="3" align="center">-</td>
        <td rowspan="3" align="center"><a href="https://arxiv.org/abs/2306.02858" target="_blank">paper</a></td>
		<td rowspan="3" align="center"><a href="https://github.com/DAMO-NLP-SG/Video-LLaMA" target="_blank">project</a></td>
		 <td rowspan="3" align="center">Image-Text-Video-Audio</td>
		<td align="center">BLIP-2 [<a href="#ref52">52</a>]</td>
        <td align="center">-</td>
         <td rowspan="3" align="center">No</td>
         <td rowspan="3" align="center">-</td>
</tr>
<tr>
		<td align="center">ImageBind [<a href="#ref53">53</a>]</td>
        <td align="center">-</td>
</tr>
<tr>
		<td align="center">Vicuna[<a href="#ref21">21</a>]</td>
        <td align="center">7B/13B</td>
</tr>
<tr>
		<td align="center">InstructBLIP [<a href="#ref54">54</a>]</td>
        <td align="center">12B</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.06500" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/salesforce/LAVIS/tree/main/projects/instructblip" target="_blank">project</a></td>
		<td align="center">Image-Text-Video</td>
		<td align="center">BLIP-2 [<a href="#ref52">52</a>]</td>
        <td align="center">-</td>
        <td align="center">No</td>
        <td align="center">-</td>
</tr>
<tr>
		<td align="center">Otter [<a href="#ref55">55</a>]</td>
        <td align="center">-</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.03726" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/Luodian/Otter" target="_blank">project</a></td>
		<td align="center">Image-Text-Video</td>
		<td align="center">OpenFlamingo [<a href="#ref57">57</a>]</td>
        <td align="center">9B</td>
        <td align="center">Yes</td>
        <td align="center">2.8M</td>
</tr>
<tr>
		<td align="center">MultiModal-GPT [<a href="#ref57">57</a>]</td>
        <td align="center">-</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.04790" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/open-mmlab/Multimodal-GPT" target="_blank">project</a></td>
		<td align="center">Image-Text-Video</td>
		<td align="center">OpenFlamingo [<a href="#ref57">57</a>]</td>
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
         <td align="center">Radiology-GPT [<a href="#ref64">64</a>]</td>
        <td align="center">7B</td>
        <td align="center"><a href="https://arxiv.org/abs/2306.08666" target="_blank">paper</a></td>
		<td align="center"><a href="https://huggingface.co/spaces/allen-eric/radiology-gpt" target="_blank">project</a></td>
        <td align="center">Alpaca[<a href="#ref15">15</a>]</td>
        <td align="center">122K</td>
</tr>
<tr>
        <td align="center">ChatDoctor [<a href="#ref65">65</a>]</td>
        <td align="center">7B</td>
        <td align="center"><a href="https://arxiv.org/abs/2303.14070" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/Kent0n-Li/ChatDoctor" target="_blank">project</a></td>
        <td align="center">LLaMA [<a href="#ref30">30</a>]</td>
        <td align="center">122K</td>
</tr>
<tr>
         <td align="center">ChatGLM-Med [<a href="#ref66">66</a>]</td>
        <td align="center">6B</td>
        <td align="center">-</td>
		<td align="center"><a href="https://github.com/SCIR-HI/Med-ChatGLM" target="_blank">project</a></td>
        <td align="center">ChatGLM [<a href="#ref32">32</a>]</td>
        <td align="center">-</td>
</tr>

<tr>
        <td rowspan="3" align="center">Writing</td>
         <td align="center">Writing-Alpaca [<a href="#ref61">61</a>]</td>
        <td align="center">7B</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.13225" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/facebookresearch/EditEval" target="_blank">project</a></td>
        <td align="center">LLaMA [<a href="#ref30">30</a>]</td>
        <td align="center">-</td>
</tr>
<tr>
         <td align="center">CoEdIT [<a href="#ref62">62</a>]</td>
        <td align="center">11B</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.09857" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/vipulraheja/coedit" target="_blank">project</a></td>
        <td align="center">FLAN-T5 [<a href="#ref28">28</a>]</td>
        <td align="center">82K</td>
</tr>
<tr>
         <td align="center">CoPoet [<a href="#ref63">63</a>]</td>
        <td align="center">11B</td>
        <td align="center"><a href="https://aclanthology.org/2022.emnlp-main.460/" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/vishakhpk/creative-instructions" target="_blank">project</a></td>
        <td align="center">T5[<a href="#ref29">29</a>]</td>
        <td align="center">-</td>
</tr>
<tr>
        <td align="center">Code Generation</td>
         <td align="center">WizardCoder [<a href="#ref68">68</a>]</td>
        <td align="center">15B</td>
        <td align="center"><a href="https://arxiv.org/abs/2306.08568" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/nlpxucan/WizardLM" target="_blank">project</a></td>
        <td align="center">StarCoder [<a href="#ref39">39</a>]</td>
        <td align="center">78K</td>
</tr>
<tr>
        <td align="center">Sentiment Analysis</td>
         <td align="center">IT-MTL [<a href="#ref60">60</a>]</td>
        <td align="center">220M</td>
        <td align="center"><a href="https://aclanthology.org/2023.wassa-1.3.pdf" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/amazon-science/instruction-tuning-for-absa" target="_blank">project</a></td>
        <td align="center">T5[<a href="#ref29">29</a>]</td>
        <td align="center">-</td>
</tr>
<tr>
        <td align="center">Arithmetic</td>
         <td align="center">Goat [<a href="#ref67">67</a>]</td>
        <td align="center">7B</td>
        <td align="center"><a href="https://aclanthology.org/2023.wassa-1.3.pdf" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/liutiedong/goat" target="_blank">project</a></td>
        <td align="center">LLaMA [<a href="#ref30">30</a>]</td>
        <td align="center">1.0M</td>
</tr>
<tr>
        <td align="center">Information Extraction</td>
         <td align="center">InstructUIE [<a href="#ref59">59</a>]</td>
        <td align="center">11B</td>
        <td align="center"><a href="https://arxiv.org/abs/2304.08085" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/BeyonderXX/InstructUIE" target="_blank">project</a></td>
        <td align="center">FLAN-T5 [<a href="#ref28">28</a>]</td>
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
        <td align="center">LoRA [<a href="#ref69">69</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2106.09685" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/microsoft/LoRA" target="_blank">project</a></td>
</tr>
<tr>
        <td align="center">HINT [<a href="#ref70">70</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2212.10315" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/allenai/hyper-task-descriptions" target="_blank">project</a></td>
</tr>

<tr>
        <td align="center">QLoRA [<a href="#ref71">71</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2305.14314" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/artidoro/qlora" target="_blank">project</a></td>
</tr>

<tr>
        <td align="center">LOMO [<a href="#ref72">72</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2306.09782" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/OpenLMLab/LOMO" target="_blank">project</a></td>
</tr>

<tr>
        <td align="center">Delta-tuning [<a href="#ref73">73</a>]</td>
        <td align="center"><a href="https://arxiv.org/abs/2203.06904" target="_blank">paper</a></td>
		<td align="center"><a href="https://github.com/thunlp/OpenDelta" target="_blank">project</a></td>
</tr>


</table>

## References

### Instruction Datasets

<a id="ref1">[1]</a> Khashabi, Daniel, Sewon Min, Tushar Khot, Ashish Sabharwal, Oyvind Tafjord, Peter Clark, and Hannaneh Hajishirzi. **Unifiedqa: Crossing format boundaries with a single qa system**. arXiv preprint arXiv:2005.00700 (2020). [Paper](https://arxiv.org/abs/2005.00700) 

<a id="ref2">[2]</a> LAION.ai. **Oig: the open instruction generalist dataset**, 2023. 

<a id="ref3">[3]</a> Tianbao Xie, Chen Henry Wu, Peng Shi, Ruiqi Zhong, Torsten Scholak, Michihiro Yasunaga, Chien-Sheng Wu, Ming Zhong, Pengcheng Yin, Sida I. Wang, Victor Zhong, Bailin Wang, Chengzu Li,
Connor Boyle, Ansong Ni, Ziyu Yao, Dragomir R.
Radev, Caiming Xiong, Lingpeng Kong, Rui Zhang,
Noah A. Smith, Luke Zettlemoyer, and Tao Yu.
**Unifiedskg: Unifying and multi-tasking structured
knowledge grounding with text-to-text language
models**. In Conference on Empirical Methods in
Natural Language Processing, 2022. [Paper](https://arxiv.org/abs/) 


<a id="ref4">[4]</a> Or Honovich, Thomas Scialom, Omer Levy, and
Timo Schick. **Unnatural instructions: Tuning
language models with (almost) no human labor**.
arXiv preprint arXiv:2212.09689, 2022. [Paper](https://arxiv.org/abs/2212.09689) 

<a id="ref5">[5]</a> Yizhong Wang, Swaroop Mishra, Pegah
Alipoormolabashi, Yeganeh Kordi, Amirreza
Mirzaei, Anjana Arunkumar, Arjun Ashok,
Arut Selvan Dhanasekaran, Atharva Naik, David
Stap, et al. **Super-naturalinstructions:generalization
via declarative instructions on 1600+ tasks**. In
EMNLP, 2022. [Paper](https://arxiv.org/abs/) 

<a id="ref6">[6]</a>  Victor Sanh, Albert Webson, Colin Raffel, Stephen H
Bach, Lintang Sutawika, Zaid Alyafeai, Antoine
Chaffin, Arnaud Stiegler, Teven Le Scao, Arun
Raja, et al. **Multitask prompted training enables
zero-shot task generalization**. arXiv preprint
arXiv:2110.08207, 2021. [Paper](https://arxiv.org/abs/2110.08207) 

<a id="ref7">[7]</a> Niklas Muennighoff, Thomas Wang, Lintang
Sutawika, Adam Roberts, Stella Biderman, Teven Le
Scao, M Saiful Bari, Sheng Shen, Zheng-Xin
Yong, Hailey Schoelkopf, et al. **Crosslingual
generalization through multitask finetuning**. arXiv
preprint arXiv:2211.01786, 2022. [Paper](https://arxiv.org/abs/2211.01786) 

<a id="ref8">[8]</a> Shayne Longpre, Le Hou, Tu Vu, Albert Webson,
Hyung Won Chung, Yi Tay, Denny Zhou, Quoc V Le,
Barret Zoph, Jason Wei, et al. **The flan collection:
Designing data and methods for effective instruction
tuning**. arXiv preprint arXiv:2301.13688, 2023. [Paper](https://arxiv.org/abs/2301.13688) 

<a id="ref9">[9]</a> Ge Zhang, Yemin Shi, Ruibo Liu, Ruibin Yuan, Yizhi
Li, Siwei Dong, Yu Shu, Zhaoqun Li, Zekun Wang,
Chenghua Lin, Wen-Fen Huang, and Jie Fu. **Chinese
open instruction generalist: A preliminary release**.
ArXiv, abs/2304.07987, 2023. [Paper](https://arxiv.org/abs/2304.07987) 

<a id="ref10">[10]</a> Long Ouyang, Jeffrey Wu, Xu Jiang, Diogo
Almeida, Carroll Wainwright, Pamela Mishkin,
Chong Zhang, Sandhini Agarwal, Katarina Slama,
Alex Ray, et al. **Training language models to follow
instructions with human feedback**. Advances in
Neural Information Processing Systems, 35:27730–
27744, 2022. [Paper](https://arxiv.org/abs/) 

<a id="ref11">[11]</a> Honovich, Or, Thomas Scialom, Omer Levy, and Timo Schick. 
**Unnatural instructions: Tuning language models with (almost) no human labor**. arXiv preprint arXiv:2212.09689 (2022).
[Paper](https://arxiv.org/abs/2212.09689) 

<a id="ref12">[12]</a> Yizhong Wang, Yeganeh Kordi, Swaroop Mishra,
Alisa Liu, Noah A Smith, Daniel Khashabi, and
Hannaneh Hajishirzi. **Self-instruct: Aligning
language model with self generated instructions**.
arXiv preprint arXiv:2212.10560, 2022. [Paper](https://arxiv.org/abs/2212.10560) 

<a id="ref13">[13]</a> Fuzhao Xue, Kabir Jain, Mahir Hitesh Shah,
Zangwei Zheng, and Yang You. **Instruction
in the wild: A user-based instruction dataset**.
`github.com/XueFuzhao/InstructionWild,2023`. 


<a id="ref14">[14]</a> Can Xu, Qingfeng Sun, Kai Zheng, Xiubo Geng,
Pu Zhao, Jiazhan Feng, Chongyang Tao, and Daxin
Jiang. **Wizardlm: Empowering large language
models to follow complex instructions**, 2023. [Paper](https://arxiv.org/abs/) 

<a id="ref15">[15]</a> Rohan Taori, Ishaan Gulrajani, Tianyi Zhang,
Yann Dubois, Xuechen Li, Carlos Guestrin, Percy
Liang, and Tatsunori B Hashimoto. **Alpaca:
A strong, replicable instruction-following model.
Stanford Center for Research on Foundation Models**.
`https://crfm.stanford.edu/2023/03/13/alpaca.html`,
3(6):7, 2023.


<a id="ref16">[16]</a> Hanmeng Liu, Zhiyang Teng, Leyang Cui, Chaoli
Zhang, Qiji Zhou, and Yue Zhang. **Logicot: Logical
chain-of-thought instruction-tuning data collection
with gpt-4**. ArXiv, abs/2305.12147, 2023. [Paper](https://arxiv.org/abs/2305.12147) 

<a id="ref17">[17]</a> Mike Conover, Matt Hayes, Ankit Mathur, Xiangrui
Meng, Jianwei Xie, Jun Wan, Sam Shah, Ali Ghodsi,
Patrick Wendell, Matei Zaharia, et al. **Free dolly:
Introducing the world’s first truly open instruction-
tuned llm**, 2023. [Paper](https://arxiv.org/abs/) 

<a id="ref18">[18]</a> Baolin Peng, Chunyuan Li, Pengcheng He, Michel
Galley, and Jianfeng Gao. **Instruction tuning with
gpt-4**. arXiv preprint arXiv:2304.03277, 2023. [Paper](https://arxiv.org/abs/2304.03277) 

<a id="ref19">[19]</a> Chunting Zhou, Pengfei Liu, Puxin Xu, Srini Iyer,
Jiao Sun, Yuning Mao, Xuezhe Ma, Avia Efrat, Ping
Yu, L. Yu, Susan Zhang, Gargi Ghosh, Mike Lewis,
Luke Zettlemoyer, and Omer Levy. **Lima: Less is
more for alignment**. ArXiv, abs/2305.11206, 2023. [Paper](https://arxiv.org/abs/2305.11206) 

<a id="ref20">[20]</a> OpenAI. **Introducing chatgpt**. Blog post
openai.com/blog/chatgpt, 2022. 

<a id="ref21">[21]</a> Wei-Lin Chiang, Zhuohan Li, Zi Lin, Ying Sheng,
Zhanghao Wu, Hao Zhang, Lianmin Zheng, Siyuan
Zhuang, Yonghao Zhuang, Joseph E Gonzalez, et al.
**Vicuna: An open-source chatbot impressing gpt-4
with 90% chatgpt quality**. See `https://vicuna.lmsys.org` (accessed 14 April 2023), 2023.

<a id="ref22">[22]</a> JosephusCheung. **Guanaco: Generative universal
assistant for natural-language adaptive context-aware
omnilingual outputs**, 2021. 


<a id="ref23">[23]</a> Andreas Köpf, Yannic Kilcher, Dimitri von Rütte,
Sotiris Anagnostidis, Zhi-Rui Tam, Keith Stevens,
Abdullah Barhoum, Nguyen Minh Duc, Oliver
Stanley, Richárd Nagyfi, et al. **Openassistant
conversations–democratizing large language model
alignment**. arXiv preprint arXiv:2304.07327, 2023. [Paper](https://arxiv.org/abs/2304.07327) 

<a id="ref24">[24]</a> Mike Conover, Matt Hayes, Ankit Mathur, Jianwei
Xie, Jun Wan, Sam Shah, Ali Ghodsi, Patrick
Wendell, Matei Zaharia, and Reynold Xin. **Free
dolly: Introducing the world’s first truly open
instruction-tuned llm**, 2023. [Paper](https://arxiv.org/abs/) 

<a id="ref25">[25]</a> Ning Ding, Yulin Chen, Bokai Xu, Yujia Qin, Zhi
Zheng, Shengding Hu, Zhiyuan Liu, Maosong Sun,
and Bowen Zhou. **Enhancing chat language models
by scaling high-quality instructional conversations**.
arXiv preprint arXiv:2305.14233, 2023. [Paper](https://arxiv.org/abs/2305.14233) 

### Instruction Tuned LLMs

<a id="ref26">[26]</a> Tom B. Brown, Benjamin Mann, Nick Ryder,
Melanie Subbiah, Jared Kaplan, Prafulla Dhariwal,
Arvind Neelakantan, Pranav Shyam, Girish Sastry,
Amanda Askell, Sandhini Agarwal, Ariel Herbert-
Voss, Gretchen Krueger, T. J. Henighan, Rewon
Child, Aditya Ramesh, Daniel M. Ziegler, Jeff Wu,
Clemens Winter, Christopher Hesse, Mark Chen, Eric
Sigler, Mateusz Litwin, Scott Gray, Benjamin Chess,
Jack Clark, Christopher Berner, Sam McCandlish,
Alec Radford, Ilya Sutskever, and Dario Amodei.
**Language models are few-shot learners**. ArXiv,
abs/2005.14165, 2020. [Paper](https://arxiv.org/abs/2005.14165) 


<a id="ref27">[27]</a> Scao, Teven Le, Angela Fan, Christopher Akiki, Ellie Pavlick, Suzana Ilić, Daniel Hesslow, Roman Castagné et al. 
**Bloom: A 176b-parameter open-access multilingual language model**. arXiv preprint arXiv:2211.05100 (2022). 
[Paper](https://arxiv.org/abs/2211.05100) 

<a id="ref28">[28]</a> Hyung Won Chung, Le Hou, S. Longpre, Barret
Zoph, Yi Tay, William Fedus, Eric Li, Xuezhi
Wang, Mostafa Dehghani, Siddhartha Brahma, Albert
Webson, Shixiang Shane Gu, Zhuyun Dai, Mirac
Suzgun, Xinyun Chen, Aakanksha Chowdhery,
Dasha Valter, Sharan Narang, Gaurav Mishra,
Adams Wei Yu, Vincent Zhao, Yanping Huang,
Andrew M. Dai, Hongkun Yu, Slav Petrov, Ed Huai
hsin Chi, Jeff Dean, Jacob Devlin, Adam Roberts,
Denny Zhou, Quoc V. Le, and Jason Wei. **Scaling
instruction-finetuned language models**. ArXiv,
abs/2210.11416, 2022.
[Paper](https://arxiv.org/abs/2210.11416) 

<a id="ref29">[29]</a> Colin Raffel, Noam M. Shazeer, Adam Roberts,
Katherine Lee, Sharan Narang, Michael Matena,
Yanqi Zhou, Wei Li, and Peter J. Liu. **Exploring the
limits of transfer learning with a unified text-to-text
transformer**. ArXiv, abs/1910.10683, 2019.
[Paper](https://arxiv.org/abs/1910.10683) 


<a id="ref30">[30]</a> Hugo Touvron, Thibaut Lavril, Gautier Izacard,
Xavier Martinet, Marie-Anne Lachaux, Timothée
Lacroix, Baptiste Rozière, Naman Goyal, Eric
Hambro, Faisal Azhar, Aur’elien Rodriguez, Armand
Joulin, Edouard Grave, and Guillaume Lample.
**Llama: Open and efficient foundation language
models**. ArXiv, abs/2302.13971, 2023.
[Paper](https://arxiv.org/abs/2302.13971) 


<a id="ref31">[31]</a> Yuntao Bai, Saurav Kadavath, Sandipan Kundu,
Amanda Askell, Jackson Kernion, Andy Jones, Anna
Chen, Anna Goldie, Azalia Mirhoseini, Cameron
McKinnon, et al. **Constitutional ai: Harmlessness
from ai feedback**. arXiv preprint arXiv:2212.08073, 2022.
[Paper](https://arxiv.org/abs/2212.08073) 


<a id="ref32">[32]</a> Zhengxiao Du, Yujie Qian, Xiao Liu, Ming
Ding, Jiezhong Qiu, Zhilin Yang, and Jie Tang.
**Glm: General language model pretraining with
autoregressive blank infilling**. In Proceedings of
the 60th Annual Meeting of the Association for
Computational Linguistics (Volume 1: Long Papers),
pages 320–335, 2022.
[Paper](https://arxiv.org/abs/) 

<a id="ref33">[33]</a> Srinivas Iyer, Xiaojuan Lin, Ramakanth Pasunuru,
Todor Mihaylov, Daniel Simig, Ping Yu, Kurt
Shuster, Tianlu Wang, Qing Liu, Punit Singh
Koura, Xian Li, Brian O’Horo, Gabriel Pereyra, Jeff
Wang, Christopher Dewan, Asli Celikyilmaz, Luke
Zettlemoyer, and Veselin Stoyanov. **Opt-iml: Scaling
language model instruction meta learning through the
lens of generalization**. ArXiv, abs/2212.12017, 2022.
[Paper](https://arxiv.org/abs/2212.12017) 


<a id="ref34">[34]</a> Stella Rose Biderman, Hailey Schoelkopf,
Quentin G. Anthony, Herbie Bradley, Kyle O’Brien,
Eric Hallahan, Mohammad Aflah Khan, Shivanshu
Purohit, USVSN Sai Prashanth, Edward Raff, Aviya
Skowron, Lintang Sutawika, and Oskar van der Wal.
**Pythia: A suite for analyzing large language models
across training and scaling**. ArXiv, abs/2304.01373, 2023.
[Paper](https://arxiv.org/abs/2304.01373) 


<a id="ref35">[35]</a> Ebtesam Almazrouei, Hamza Alobeidli, Abdulaziz
Alshamsi, Alessandro Cappelli, Ruxandra Cojocaru,
Merouane Debbah, Etienne Goffinet, Daniel Heslow,
Julien Launay, Quentin Malartic, Badreddine Noune,
Baptiste Pannier, and Guilherme Penedo. **Falcon-
40B: an open large language model with state-of-the-
art performance**. 2023.
[Paper](https://arxiv.org/abs/) 

<a id="ref36">[36]</a> Ebtesam Almazrouei, Hamza Alobeidli, Abdulaziz
Alshamsi, Alessandro Cappelli, Ruxandra Cojocaru,
Merouane Debbah, Etienne Goffinet, Daniel Heslow,
Julien Launay, Quentin Malartic, et al. **Falcon-40b:
an open large language model with state-of-the-art
performance**, 2023.
[Paper](https://arxiv.org/abs/) 


<a id="ref37">[37]</a> **OpenAccess AI Collective**. software:
huggingface.co/openaccess-ai-collective/minotaur-
15b, 2023.


<a id="ref38">[38]</a> Raymond Li, Loubna Ben Allal, Yangtian Zi, Niklas
Muennighoff, Denis Kocetkov, Chenghao Mou, Marc
Marone, Christopher Akiki, Jia Li, Jenny Chim, et al.
**Starcoder: may the source be with you**! arXiv
preprint arXiv:2305.06161, 2023.
[Paper](https://arxiv.org/abs/2305.06161) 

<a id="ref39">[39]</a> **NousResearch**. software:
huggingface.co/NousResearch/Nous-Hermes-13b, 2023.


<a id="ref40">[40]</a> Yizhong Wang, Hamish Ivison, Pradeep Dasigi,
Jack Hessel, Tushar Khot, Khyathi Raghavi Chandu,
David Wadden, Kelsey MacMillan, Noah A. Smith,
Iz Beltagy, and Hanna Hajishirzi. **How far can
camels go? exploring the state of instruction tuning
on open resources**. ArXiv, abs/2306.04751, 2023.
[Paper](https://arxiv.org/abs/2306.04751) 

<a id="ref41">[41]</a> YuLan-Chat-Team. **Yulan-chat: An open-
source bilingual chatbot**. github.com/RUC-GSAI/YuLan-Chat, 2023.

<a id="ref42">[42]</a> Sun Tianxiang and Qiu Xipeng. **Moss**. Blog post
txsun1997.github.io/blogs/moss.html, 2023.

<a id="ref43">[43]</a> Jon Durbin. **Airoboros**. software:
github.com/jondurbin/airoboros, 2023.

<a id="ref44">[44]</a> Ning Ding, Yulin Chen, Bokai Xu, Yujia Qin, Zhi
Zheng, Shengding Hu, Zhiyuan Liu, Maosong Sun,
and Bowen Zhou. **Enhancing chat language models
by scaling high-quality instructional conversations**.
arXiv preprint arXiv:2305.14233, 2023.
[Paper](https://arxiv.org/abs/2305.14233) 

### Multimodal Instruction Datasets

<a id="ref45">[45]</a> Zhiyang Xu, Ying Shen, and Lifu Huang.
**Multiinstruct: Improving multi-modal zero-
shot learning via instruction tuning**. ArXiv,
abs/2212.10773, 2022.
[Paper](https://arxiv.org/abs/2212.10773) 

<a id="ref46">[46]</a> Xiaoman Zhang, Chaoyi Wu, Ziheng Zhao,
Weixiong Lin, Ya Zhang, Yanfeng Wang, and Weidi
Xie. **Pmc-vqa: Visual instruction tuning for medical
visual question answering**. ArXiv, abs/2305.10415. 2023.
[Paper](https://arxiv.org/abs/2305.10415) 

<a id="ref47">[47]</a> Zhenfei Yin, Jiong Wang, Jianjian Cao, Zhelun Shi,
Dingning Liu, Mukai Li, Lu Sheng, Lei Bai, Xiaoshui
Huang, Zhiyong Wang, Wanli Ouyang, and Jing Shao.
**Lamm: Language-assisted multi-modal instruction-
tuning dataset, framework, and benchmark**. ArXiv,
abs/2306.06687, 2023. [Paper](https://arxiv.org/abs/2306.06687) 

### Multimodal Instruction Tuned Models

<a id="ref48">[48]</a> Tim Brooks, Aleksander Holynski, and Alexei A.
Efros. **Instructpix2pix: Learning to follow image
editing instructions**. ArXiv, abs/2211.09800, 2022. [Paper](https://arxiv.org/abs/2211.09800) 

<a id="ref49">[49]</a> Haotian Liu, Chunyuan Li, Qingyang Wu, and
Yong Jae Lee. **Visual instruction tuning**. ArXiv,
abs/2304.08485, 2023. [Paper](https://arxiv.org/abs/2304.08485) 

<a id="ref50">[50]</a> Alec Radford, Jong Wook Kim, Chris Hallacy,
Aditya Ramesh, Gabriel Goh, Sandhini Agarwal,
Girish Sastry, Amanda Askell, Pamela Mishkin,
Jack Clark, Gretchen Krueger, and Ilya Sutskever.
**Learning transferable visual models from natural
language supervision**. In International Conference
on Machine Learning, 2021. [Paper](https://arxiv.org/abs/) 

<a id="ref51">[51]</a> Hang Zhang, Xin Li, and Lidong Bing. **Video-
llama: An instruction-tuned audio-visual language
model for video understanding**. arXiv preprint
arXiv:2306.02858, 2023. [Paper](https://arxiv.org/abs/2306.02858) 

<a id="ref52">[52]</a> Junnan Li, Dongxu Li, Silvio Savarese, and Steven
Hoi. **BLIP-2: bootstrapping language-image pre-
training with frozen image encoders and large
language models**. In ICML, 2023. [Paper](https://arxiv.org/abs/) 


<a id="ref53">[53]</a> Rohit Girdhar, Alaaeldin El-Nouby, Zhuang Liu,
Mannat Singh, Kalyan Vasudev Alwala, Armand
Joulin, and Ishan Misra. **Imagebind: One embedding
space to bind them all**. In CVPR, 2023. [Paper](https://arxiv.org/abs/) 

<a id="ref54">[54]</a> Wenliang Dai, Junnan Li, Dongxu Li, Anthony
Meng Huat Tiong, Junqi Zhao, Weisheng Wang,
Boyang Li, Pascale Fung, and Steven Hoi.
**Instructblip: Towards general-purpose vision-
language models with instruction tuning**. ArXiv,
abs/2305.06500, 2023. [Paper](https://arxiv.org/abs/2305.06500) 

<a id="ref55">[55]</a> Bo Li, Yuanhan Zhang, Liangyu Chen, Jinghao
Wang, Jingkang Yang, and Ziwei Liu. **Otter: A
multi-modal model with in-context instruction tuning**.
ArXiv, abs/2305.03726, 2023. [Paper](https://arxiv.org/abs/2305.03726) 

<a id="ref56">[56]</a> Anas Awadalla, Irena Gao, Joshua Gardner, Jack
Hessel, Yusuf Hanafy, Wanrong Zhu, Kalyani
Marathe, Yonatan Bitton, Samir Gadre, Jenia Jitsev,
et al. **Openflamingo**, 2023. [Paper](https://arxiv.org/abs/) 

<a id="ref57">[57]</a> Tao Gong, Chengqi Lyu, Shilong Zhang, Yudong
Wang, Miao Zheng, Qianmengke Zhao, Kuikun
Liu, Wenwei Zhang, Ping Luo, and Kai Chen.
**Multimodal-gpt: A vision and language model for
dialogue with humans**. ArXiv, abs/2305.04790, 2023. [Paper](https://arxiv.org/abs/2305.04790) 

<a id="ref58">[58]</a> Prakhar Gupta, Cathy Jiao, Yi-Ting Yeh,
Shikib Mehri, Maxine Eskénazi, and Jeffrey P.
Bigham. **Instructdial: Improving zero and few-shot
generalization in dialogue through instruction tuning**.
In Conference on Empirical Methods in Natural
Language Processing, 2022. [Paper](https://arxiv.org/abs/) 

<a id="ref59">[59]</a> Bill Yuchen Lin, Kangmin Tan, Chris Miller,
Beiwen Tian, and Xiang Ren. **Unsupervised cross-
task generalization via retrieval augmentation**. ArXiv,
abs/2204.07937, 2022. [Paper](https://arxiv.org/abs/2204.07937) 

<a id="ref60">[60]</a> Andrew Rosenbaum, Saleh Soltan, Wael Hamza,
Yannick Versley, and Markus Boese. **Linguist:
Language model instruction tuning to generate
annotated utterances for intent classification and
slot tagging**. In International Conference on
Computational Linguistics, 2022. [Paper](https://arxiv.org/abs/) 

<a id="ref61">[61]</a> Saleh Soltan, Shankar Ananthakrishnan, Jack
FitzGerald, Rahul Gupta, Wael Hamza, Haidar Khan,
Charith Peris, Stephen Rawls, Andy Rosenbaum,
Anna Rumshisky, et al. **Alexatm 20b: Few-shot
learning using a large-scale multilingual seq2seq
model**. arXiv preprint arXiv:2208.01448, 2022. [Paper](https://arxiv.org/abs/2208.01448) 

<a id="ref62">[62]</a> Xiao Wang, Wei Zhou, Can Zu, Han Xia, Tianze
Chen, Yuan Zhang, Rui Zheng, Junjie Ye, Qi Zhang,
Tao Gui, Jihua Kang, J. Yang, Siyuan Li, and
Chunsai Du. **Instructuie: Multi-task instruction
tuning for unified information extraction**. ArXiv,
abs/2304.08085, 2023. [Paper](https://arxiv.org/abs/2304.08085) 

<a id="ref63">[63]</a> Robin Rombach, Andreas Blattmann, Dominik
Lorenz, Patrick Esser, and Björn Ommer. **High-
resolution image synthesis with latent diffusion
models**. In Proceedings of the IEEE/CVF conference
on computer vision and pattern recognition, pages
10684–10695, 2022. [Paper](https://arxiv.org/abs/) 

### Domain-specific Instruction Tuned LLMs

<a id="ref64">[64]</a> Zheng Liu, Aoxiao Zhong, Yiwei Li, Longtao Yang,
Chao Ju, Zihao Wu, Chong Ma, Peng Shu, Cheng
Chen, Sekeun Kim, Haixing Dai, Lin Zhao, Dajiang
Zhu, Jun Liu, Wei Liu, Dinggang Shen, Xiang Li,
Quanzheng Li, and Tianming Liu. **Radiology-gpt: A
large language model for radiology**. 2023. [Paper](https://arxiv.org/abs/) 


<a id="ref65">[65]</a> Yunxiang Li, Zihan Li, Kai Zhang, Ruilong Dan,
and You Zhang. **Chatdoctor: A medical chat model
fine-tuned on llama model using medical domain
knowledge**. ArXiv, abs/2303.14070, 2023. [Paper](https://arxiv.org/abs/2303.14070) 

<a id="ref66">[66]</a> Sendong Zhao Bing Qin Ting Liu Haochun Wang,
Chi Liu. **Chatglm-med. github.com/SCIR-
HI/Med-ChatGLM**, 2023.

<a id="ref67">[67]</a> Tiedong Liu and Bryan Kian Hsiang Low. **Goat:
Fine-tuned llama outperforms gpt-4 on arithmetic
tasks**. arXiv preprint arXiv:2305.14201, 2023. [Paper](https://arxiv.org/abs/2305.14201, 2023) 

<a id="ref68">[68]</a> Ziyang Luo, Can Xu, Pu Zhao, Qingfeng Sun,
Xiubo Geng, Wenxiang Hu, Chongyang Tao, Jing
Ma, Qingwei Lin, and Daxin Jiang. **Wizardcoder:
Empowering code large language models with evol-
instruct**, 2023. [Paper](https://arxiv.org/abs/) 

### Efficient Tuning Techniques

<a id="ref69">[69]</a> Edward J Hu, Yelong Shen, Phillip Wallis, Zeyuan Allen-Zhu, Yuanzhi Li, Shean Wang, Lu Wang, and Weizhu Chen. 2021. 
**Lora: Low-rank adaptation of large language models**. arXiv preprint arXiv:2106.09685. [Paper](https://arxiv.org/abs/2106.09685) 


<a id="ref70">[70]</a> Hamish Ivison, Akshita Bhagia, Yizhong Wang, Hannaneh Hajishirzi, and Matthew E. Peters. 2022. 
**Hint: Hypernetwork instruction tuning for efficient zero-shot generalisation**. ArXiv, abs/2212.10315.
[Paper](https://arxiv.org/abs/2212.10315) 


<a id="ref71">[71]</a> Tim Dettmers, Artidoro Pagnoni, Ari Holtzman, and Luke Zettlemoyer. 2023. 
**Qlora: Efficient finetuning of quantized llms**. arXiv preprint arXiv:2305.14314.
[Paper](https://arxiv.org/abs/2305.14314) 


<a id="ref72">[72]</a> Kai Lv, Yuqing Yang, Tengxiao Liu, Qi jie Gao, Qipeng Guo, and Xipeng Qiu. 2023. 
**Full parameter fine-tuning for large language models with limited resources**.
[Paper](https://arxiv.org/abs/) 


<a id="ref72">[73]</a> Ning Ding, Yujia Qin, Guang Yang, Fu Wei, Zonghan Yang, Yusheng Su, Shengding Hu, Yulin Chen, Chi-Min Chan, 
Weize Chen, Jing Yi, Weilin Zhao, Xiaozhi Wang, Zhiyuan Liu, Haitao Zheng, Jianfei Chen, Y. Liu, Jie Tang, Juanzi Li, and Maosong Sun. 2023b. 
**Parameter-efficient fine-tuning of large-scale pre-trained language models. Nature Machine Intelligence**, 5:220–235.
[Paper](https://arxiv.org/abs/) 


## Contact 

If you have any questions or suggestions, please feel free to create an issue or send an e-mail to `xiaoya_li@shannonai.com`.

