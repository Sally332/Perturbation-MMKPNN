# Perturbation-MMKPNN: Interpretable Modeling of Single-Cell Perturbation Responses

![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![License](https://img.shields.io/badge/License-MIT-green)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17189224.svg)](https://doi.org/10.5281/zenodo.17189224)

**Interpretable modeling of how cells respond to genetic and chemical perturbations.**

---

## Overview

**Perturbation-MMKPNN** extends the Multimodal Knowledge-Primed Neural Network (MM-KPNN) to predict single-cell perturbation responses while keeping reasoning transparent through a **pathway/TF concept bottleneck**. Black-box predictors such as scGen and CPA achieve accuracy but fail to reveal **which pathways and subnetworks mediate response** or provide stable explanations across datasets. Perturbation-MMKPNN constrains learning through curated biological priors (Reactome, DoRothEA, MSigDB), transforming predictions into an interpretable mapping: **perturbation → regulatory program → transcriptional outcome**. Validated across **scPerturb, Perturb-seq, L1000, and DrugComb**, it benchmarks against scGen, CPA, and linear baselines, emphasizing **attribution stability** and **cross-dataset generalization**. This approach moves perturbation modeling from prediction to **mechanistic discovery**, identifying regulators of resistance and synthetic lethality with reproducibility and biological credibility.

---

## Architecture
<img width="817" height="405" alt="perturbation_mmkpnn_architecture" src="https://github.com/user-attachments/assets/4ca345b8-e2ce-400b-997b-193eb1629920" />

The architecture combines:  
- **Inputs:** single-cell expression profiles and perturbation metadata  
- **Encoder:** feature projection and dimensionality reduction  
- **Concept bottleneck:** pathways and transcription-factor modules that mediate predictions  
- **Prediction head:** outputs perturbed expression state or classification label  
- **Interpretability outputs:** pathway attributions, counterfactual edits, and driver ranking  

---

## Workflow
<img width="898" height="203" alt="perturbation_mmkpnn_workflow" src="https://github.com/user-attachments/assets/e45052ac-5d57-4ec0-834d-25f9db11769c" />

1. **Datasets:** scPerturb, Perturb-seq, L1000, and DrugComb  
2. **Modeling:** MM-KPNN backbone adapted for perturbation inputs  
3. **Evaluation:** predictive accuracy, attribution stability, cross-dataset validation  
4. **Outputs:** pathway maps, regulatory modules, and candidate resistance drivers  

---

## Methodology

Inputs consist of single-cell expression and perturbation metadata. An encoder projects cells into a latent space, which is constrained by a **biological bottleneck** of pathway and transcription-factor modules. The prediction head outputs either a perturbed signature or a categorical response label. Interpretability uses **Integrated Gradients** and **Gradient×Input** to obtain pathway-level attributions, and counterfactual experiments silence or boost bottleneck nodes to test causal relevance. Evaluation measures predictive accuracy, **attribution stability**, and **transferability** across datasets, perturbations, and donors.

---

## Project Roadmap (2025–2026)

**Objective:** Build a reproducible, interpretable framework for modeling single-cell perturbation responses, validated across multiple datasets and designed for biological discovery.

### 1. Robustness Analysis
- Quantify attribution stability under seed variation, subsampling, and noise injection.  
- Evaluate consistency of bottleneck activations across donors and perturbations.  
- Test counterfactual pathway edits to confirm causal relevance.
### 2. Cross-Dataset Validation
- Extend training to multiple sources (**scPerturb, L1000, Perturb-seq, DrugComb**).  
- Assess generalization across dataset boundaries and perturbation types.  
- Identify conserved pathway drivers and reproducible regulators of resistance.
### 3. Benchmark and Extension
- Compare performance and interpretability against **CPA** and **scGen** baselines.  
- Integrate transformer-based encoders (**scGPT, Geneformer**) for scalability.  
- Publish benchmark results and prepare manuscript submission.

---

## Limitations & Ongoing Work

Sensitive to label/guide imbalance and batch effects; ongoing efforts include **seed/noise robustness**, **leave-drug/gene-out validation**, and expanded **baseline comparisons** (CPA, scGen, and diffusion/backbone variants).

---

## Extensibility

The current MM-KPNN backbone can be replaced with **transformer-based encoders** or pretrained embeddings from large-scale biology models such as **scGPT** or **Geneformer**, enabling scalability while maintaining interpretability through pathway, TF, and ligand–receptor bottlenecks.

---

## References

1. Norman TM *et al.* *Perturb-seq* (2019).  
2. Replogle JM *et al.* *Combinatorial single-cell CRISPR screens.* **Nature** (2022).  
3. Subramanian A *et al.* *Connectivity Map.* **Science** (2017).  
4. Liu Q *et al.* *DrugCombDB.* **Nucleic Acids Research** (2020).  
5. Yepes S. *MM-KPNN* GitHub Repository (2025).  

---

## Citation

> Yepes, S. *Perturbation-MMKPNN: Interpretable Modeling of Single-Cell Perturbation Responses.* GitHub, 2025.  
> DOI: [10.5281/zenodo.17189224](https://doi.org/10.5281/zenodo.17189224)
