<div align="center">

# Hi, I'm Andreas

### MSc Computer Science student at Aalborg University · Machine learning research · LLMs · Recommender systems

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=18&pause=1200&center=true&vCenter=true&width=640&lines=Machine+learning+research;Fine-tuning+LLMs+with+LoRA+and+QLoRA;Distilling+LLMs+for+faster+inference;Recommender+systems;Reproducible+ML+research" alt="Typing SVG" />

</div>

---

## About me

I'm a master's student in computer science at Aalborg University, Denmark, working on machine learning research. I care about the gap between what machine learning methods are claimed to do and what they actually do, so I analyse methods from first principles, reproduce published results under controlled conditions, and build small, well-tested research software that makes results easy to verify.

## What I work on

- **Machine learning research**: how training choices such as loss functions, reweighting and regularisation change what a model actually learns, backed by proofs and controlled experiments.
- **LLMs and generative AI**: parameter-efficient fine-tuning with **LoRA** and **QLoRA**, 4-bit quantisation, and open models such as **Qwen**.
- **LLM inference optimisation**: distilling large language models into smaller, faster ones, the topic of my bachelor's project.
- **Recommender systems**: multimodal and cold-start recommendation, graph-based recommenders, and the reproducibility of published models.
- **Reproducible research**: controlled experiments, sound statistics, and long training runs on GPU clusters.

## Projects

### tinydistill ![Work in progress](https://img.shields.io/badge/status-work%20in%20progress-orange?style=flat-square)

Distil an LLM classification prompt into a small, fast model that runs on a CPU. Describe the task in a short YAML file and give it unlabelled texts: an instruction-tuned LLM labels them with soft targets, a small encoder learns to imitate them, and the result is exported to ONNX, optionally int8. It continues my bachelor's project on inference optimisation by distilling LLMs. [Code](https://github.com/Andreas-Hum/tinydistill)

```mermaid
flowchart LR
    A["Task prompt +<br/>unlabelled texts"] --> B["LLM teacher<br/>(Qwen2.5)"]
    B -- "soft labels" --> C["Small encoder<br/>student"]
    C --> D["ONNX / int8<br/>export"]
    D --> E["Fast CPU<br/>inference"]
```

### Distillation Playground

<table>
<tr>
<td>
An interactive, in-browser demo of knowledge distillation. A teacher network and two small students train side by side on 2D data, one from the labels alone and one from the teacher's soft targets; sliders for the temperature, the mixing weight and the student size show when distillation helps. Written from scratch in TypeScript, with no ML library and gradient-checked backpropagation.
<br><br>
<b><a href="https://andreas-hum.github.io/distillation-playground/">Try the live demo</a></b> · <a href="https://github.com/Andreas-Hum/distillation-playground">Code</a>
</td>
<td width="340">
<a href="https://andreas-hum.github.io/distillation-playground/"><img src="https://raw.githubusercontent.com/Andreas-Hum/distillation-playground/main/docs/screenshot.png" alt="Distillation Playground" width="320"></a>
</td>
</tr>
</table>

## Tech stack

**Languages**

<img src="https://skillicons.dev/icons?i=py,ts,js,java,c,cs,haskell,matlab,latex&perline=9" alt="Languages" />

**Machine learning**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)
![PEFT](https://img.shields.io/badge/PEFT%20·%20LoRA%20·%20QLoRA-FF9D00?style=for-the-badge&logo=huggingface&logoColor=white)
![bitsandbytes](https://img.shields.io/badge/bitsandbytes-4--bit-6E40C9?style=for-the-badge)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

**Methods and models**

`LoRA` `QLoRA` `PEFT` `Quantisation` `Knowledge distillation` `Inference optimisation` `Hashing` `Qwen` `Transformers`
`Recommender systems` `Graph neural networks` `Multimodal learning` `Class imbalance` `Statistical testing`

**Research and infrastructure**

<img src="https://skillicons.dev/icons?i=git,github,linux,bash,vscode&perline=5" alt="Tools" />

![Slurm](https://img.shields.io/badge/Slurm-GPU%20clusters-0B3D91?style=for-the-badge)
![NVIDIA](https://img.shields.io/badge/NVIDIA-GPU%20training-76B900?style=for-the-badge&logo=nvidia&logoColor=white)
![LaTeX](https://img.shields.io/badge/LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white)

**Web (earlier projects)**

<img src="https://skillicons.dev/icons?i=vue,angular,nodejs,html,css,php&perline=6" alt="Web" />

## Education

- **MSc in Computer Science**, Aalborg University (ongoing)
- **BSc in Computer Science**, Aalborg University, with a bachelor's project on inference optimisation by distilling LLMs

## Currently

- Writing up research on machine learning training objectives
- Pre-thesis project on multimodal recommender systems
- Open to collaborations on machine learning research and tooling

---

<div align="center">

*"Measure what models actually learn, not what they are claimed to learn."*

</div>
