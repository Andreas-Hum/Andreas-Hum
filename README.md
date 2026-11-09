<div align="center">

# Andreas Hummelmose

### MSc Computer Science student at Aalborg University · Machine learning research · LLMs · Recommender systems

<a href="mailto:Andreas@hummelmose.dk"><img src="https://img.shields.io/badge/Email-Andreas%40hummelmose.dk-D14836?style=flat-square&logo=gmail&logoColor=white" alt="Email" /></a>
<a href="https://www.linkedin.com/in/andreas-hummelmose-77580a252/"><img src="https://img.shields.io/badge/LinkedIn-Andreas%20Hummelmose-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="https://huggingface.co/Shroomy"><img src="https://img.shields.io/badge/Hugging%20Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black" alt="Hugging Face" /></a>

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

### tinydistill

[![PyPI](https://img.shields.io/pypi/v/tinydistill?style=flat-square&logo=pypi&logoColor=white)](https://pypi.org/project/tinydistill/)
[![CI](https://img.shields.io/github/actions/workflow/status/Andreas-Hum/tinydistill/ci.yml?branch=main&style=flat-square&label=CI&logo=github)](https://github.com/Andreas-Hum/tinydistill/actions/workflows/ci.yml)
[![Models on Hugging Face](https://img.shields.io/badge/Hugging%20Face-distilled%20models-FFD21E?style=flat-square&logo=huggingface&logoColor=black)](https://huggingface.co/collections/Shroomy/tinydistill)

Distil an LLM classification prompt into a small, fast model that runs on a CPU. Describe the task in a short YAML file and give it unlabelled texts: an instruction-tuned LLM labels them with soft targets, a small encoder learns to imitate them, and the result is exported to ONNX, optionally int8. It continues my bachelor's project on inference optimisation by distilling LLMs.

**[Try the live demo](https://andreas-hum.github.io/tinydistill/demo/)** · [Documentation](https://andreas-hum.github.io/tinydistill/) · [Code](https://github.com/Andreas-Hum/tinydistill) · `pip install tinydistill`

```mermaid
flowchart LR
    A["Task prompt +<br/>unlabelled texts"] --> B["LLM teacher(s)<br/>Qwen · Gemma · Mistral · ..."]
    T["tune: test and rewrite<br/>the task file"] -.-> B
    S["Synthetic texts<br/>(synth)"] -.-> B
    V["vLLM server ·<br/>hosted API"] -.-> B
    K["A few gold labels<br/>per class"] -.-> B
    K -.-> C
    B -- "soft labels<br/>(ensembled)" --> C["Small encoder<br/>student"]
    C --> D["ONNX / int8<br/>export"]
    D --> E["Fast CPU<br/>inference"]
    D --> W["Browser · server · Hub ·<br/>Python (Distiller)"]
    E -.-> F["Cascade: unsure<br/>texts to the LLM"]
    F -. "refresh: retrain<br/>on what it asked" .-> C
    C -. "improve: new texts<br/>for its confusions" .-> S
```

**Results on Banking77** (77 intents, 3,080 held-out test texts; latency per text on an RTX 4090 for the teacher and 2
CPU threads for the students; the students learn from the teacher's soft labels plus 8 gold labels per class;
[all benchmarks](https://github.com/Andreas-Hum/tinydistill/blob/main/RESULTS.md)):

| Model | Runs on | Accuracy | Latency | Size | Speed-up |
|---|---|---|---|---|---|
| Teacher: Qwen2.5-7B, 4-bit, 8-shot | GPU | 0.783 | 264 ms | 5.4&nbsp;GB | 1x |
| Student: MiniLM-L6, int8 | CPU | **0.814** | 1.2 ms | 23&nbsp;MB | **214x** |
| Student: static embeddings, int8 | CPU | 0.802 | 0.1 ms | 8&nbsp;MB | **3244x** |

The students are more accurate than their teacher and hundreds of times faster on a CPU than the teacher on a GPU.

### Distillation Playground

<table>
<tr>
<td>
An interactive, in-browser demo of knowledge distillation. A teacher network and three small students train side by side on 2D data: one from the labels alone, one from the teacher's hard answers and one from its soft targets. A live view of each neuron, the probabilities of every model at any point, and sliders for the temperature, the mixing weight, the student size and the teacher's quality show when distillation helps. Written from scratch in TypeScript, with no ML library and gradient-checked backpropagation.
<br><br>
<b><a href="https://andreas-hum.github.io/distillation-playground/">Try the live demo</a></b> · <a href="https://github.com/Andreas-Hum/distillation-playground">Code</a>
</td>
<td width="340">
<a href="https://andreas-hum.github.io/distillation-playground/"><img src="https://raw.githubusercontent.com/Andreas-Hum/distillation-playground/main/docs/screenshot.png?v=2" alt="Distillation Playground" width="320"></a>
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
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)
![ONNX Runtime](https://img.shields.io/badge/ONNX%20Runtime-int8-005CED?style=for-the-badge&logo=onnx&logoColor=white)
![vLLM](https://img.shields.io/badge/vLLM-serving-30A2FF?style=for-the-badge)

**Methods and models**

`LoRA` `QLoRA` `PEFT` `Quantisation` `Knowledge distillation` `Inference optimisation` `Hashing` `Qwen` `Transformers`
`Recommender systems` `Graph neural networks` `Multimodal learning` `Class imbalance` `Statistical testing`
`Closed-form recommenders` `Cold-start recommendation` `Pre-registered evaluation`

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
- Pre-thesis project on reproducibility and cold-start ranking in multimodal recommender systems
- Contributor to Hugging Face transformers ([fix for Doge's MoE load-balancing loss](https://github.com/huggingface/transformers/pull/50266))
- Open to collaborations on machine learning research and tooling

## Contributions

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Andreas-Hum/Andreas-Hum/output/github-snake-dark.svg">
  <img alt="Contribution graph as an animated snake" src="https://raw.githubusercontent.com/Andreas-Hum/Andreas-Hum/output/github-snake.svg">
</picture>
