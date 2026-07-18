# Mitigating Label Flip Attacks via Data Evaluation

Repository for the AGENSYS Workshop 2026 submission.

**Author:** Hong Vy Ngoc Le
**Affiliation:** Università degli Studi di Milano, Milan, Italy
**Email:** [hongvyngoc.le@studenti.unimi.it](mailto:hongvyngoc.le@studenti.unimi.it)

---

## Abstract

Label flip attacks, a simple yet effective form of backdoor poisoning, corrupt training labels to degrade model performance or embed hidden behaviors. Most existing defenses rely on model-level diagnostics and fail to isolate the contribution of individual poisoned samples.

This work proposes a data-centric defense framework that mitigates label flip attacks through data evaluation. We assign each training sample an importance score using exact Leave-One-Out (LOO) evaluation, measured as its contribution to validation accuracy. Samples with low scores are considered suspicious and are removed from the training set.

Experiments on three standard benchmark datasets under increasing label flip ratios from 10% to 50% show that removing only the lowest 1% to 10% of samples by their data value effectively restores test accuracy, closely approaching the clean-data baseline.

---

## Repository Structure

```text
VN_AGENSYS_ECML_PKDD_26/
│
├── code_shield.ipynb      # Main experimental notebook
├── figures_shield.ipynb   # Figure generation and visualization
└── README.md
```

---

## Methodology

The proposed defense follows a data-centric approach:

1. Inject label-flip attacks into the training dataset.
2. Train a classifier on the poisoned data.
3. Compute exact Leave-One-Out (LOO) values for every training sample.
4. Rank samples according to their contribution to validation accuracy.
5. Remove the lowest-valued samples.
6. Retrain the model using the filtered dataset.

Samples with low or negative contributions are considered suspicious and likely to be poisoned.

---

## Experimental Setup

### Attack Scenario

* Label Flip Poisoning
* Poisoning Ratios:

  * 10%
  * 20%
  * 30%
  * 40%
  * 50%

### Defense Strategy

* Exact Leave-One-Out Data Valuation
* Data filtering based on sample importance
* Removal thresholds:

  * Bottom 1%
  * ...
  * Bottom 10%

### Datasets

Experiments are conducted on three benchmark classification datasets to evaluate the robustness of the proposed defense under increasing poisoning levels.

---

## Results

The proposed method demonstrates that:

* Poisoned samples tend to receive significantly lower data values.
* Exact Leave-One-Out evaluation can effectively identify harmful training examples.
* Removing a small fraction of low-valued samples substantially improves model performance.
* Test accuracy approaches the clean-data baseline even under severe poisoning conditions.

Detailed numerical results and visualizations can be reproduced using the notebooks provided in this repository.

---

## Reproducing the Experiments

### Requirements

* Python 3.10+
* NumPy
* Pandas
* Scikit-learn
* Matplotlib
* Jupyter Notebook

Install dependencies:

```bash
pip install numpy pandas scikit-learn matplotlib notebook
```

### Run Experiments

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open and execute:

```text
code_shield.ipynb
```

### Generate Figures

Open and execute:

```text
figures_shield.ipynb
```

---

## Citation

If you use this repository in your research, please cite:

```bibtex
@misc{le2026labelflip,
  author = {Le, Hong Vy Ngoc},
  title = {Mitigating Label Flip Attacks via Data Evaluation},
  year = {2026},
  note = {AGENSYS Workshop 2026 Submission},
  url = {https://github.com/Eiravy/VN_AGENSYS_ECML_PKDD_26}
}
```

---

## Repository

GitHub Repository:

https://github.com/Eiravy/VN_AGENSYS_ECML_PKDD_26

---

## License

This project is released for research and educational purposes.
