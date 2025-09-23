# Perturbation-MMKPNN

**Interpretable Modeling of Single-Cell Perturbation Responses**

---

## Overview
Perturbation-MMKPNN extends the **Multimodal Knowledge-Primed Neural Network (MM-KPNN)** to model how cells respond to perturbations such as drugs or CRISPR interventions.  
It introduces a **pathway- and transcription-factor–based bottleneck layer** so that predictions remain biologically interpretable, highlighting latent subnetworks and regulatory programs that drive responses.  

The framework aims to move beyond black-box models (CPA, scGen) by emphasizing **robust interpretability, attribution stability, and cross-dataset generalization**.

---

## Architecture
<img width="817" height="405" alt="perturbation_mmkpnn_architecture" src="https://github.com/user-attachments/assets/4ca345b8-e2ce-400b-997b-193eb1629920" />

The architecture combines:
- **Inputs**: single-cell expression profiles + perturbation metadata  
- **Encoder**: feature reduction and preprocessing  
- **Concept bottleneck layer**: pathways / transcription factor modules  
- **Prediction head**: response labels (e.g., resistant vs sensitive, Δ expression state)  
- **Interpretability outputs**: attribution maps, pathway scores, counterfactual tests  

---

## Workflow
<img width="898" height="203" alt="perturbation_mmkpnn_workflow" src="https://github.com/user-attachments/assets/e45052ac-5d57-4ec0-834d-25f9db11769c" />

1. **Datasets**: scPerturb, Perturb-seq, L1000, and DrugComb provide harmonized perturbation-response single-cell data.  
2. **Modeling**: MM-KPNN framework adapted with biological bottlenecks.  
3. **Evaluation**: predictive accuracy, cross-dataset validation, attribution stability.  
4. **Outputs**: interpretable pathway maps, regulatory module identification, candidate resistance drivers.  

---

## Datasets
To avoid overfitting on a single source, this repo is designed to work with **multiple perturbation datasets**:  
- **scPerturb**: harmonized single-cell perturbation compendium  
- **Perturb-seq**: CRISPR-based perturbation experiments with transcriptional readouts  
- **L1000 (Connectivity Map)**: large-scale perturbation-response dataset  
- **DrugComb**: drug perturbation synergy data  

---

## Methodology
- **Model backbone**: MM-KPNN with biological priors encoded in the bottleneck layer.  
- **Loss functions**: cross-entropy for classification, contrastive losses for representation stability.  
- **Interpretability**:  
  - Gradient×Input and Integrated Gradients  
  - SHAP / Captum implementations  
  - Counterfactual perturbation analysis on subnetworks  
- **Evaluation metrics**:  
  - Prediction accuracy  
  - Attribution stability across runs  
  - Recovery of known pathways and regulators  

---

## Roadmap
- [ ] Upload initial preprocessing scripts for scPerturb and L1000  
- [ ] Implement MM-KPNN backbone with perturbation inputs  
- [ ] Add interpretability modules (Captum, SHAP)  
- [ ] Benchmark against CPA and scGen  
- [ ] Expand to multi-dataset integration (DrugComb, Perturb-seq)  
- [ ] Add robustness tests and cross-lab reproducibility checks  

---

## References
1. Norman TM et al. *Perturb-seq* (2019).  
2. Replogle JM et al. *Combinatorial single-cell CRISPR screens* (Nature, 2022).  
3. Subramanian A et al. *Connectivity Map* (Science, 2017).  
4. Liu Q et al. *DrugCombDB* (Nucleic Acids Research, 2020).  
5. Yepes S. *MM-KPNN* GitHub Repository (2025).  

---

## Citation
If you use or adapt this framework, please cite:

> Yepes S. *Perturbation-MMKPNN: Interpretable Modeling of Single-Cell Perturbation Responses*. GitHub, 2025.
