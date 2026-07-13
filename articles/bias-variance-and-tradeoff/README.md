# Bias, Variance, and the Trade-Off in Machine Learning

## Topic

Bias, variance, and the bias-variance trade-off in supervised machine learning. Covers the mathematical decomposition of expected prediction error, empirical estimation via repeated training experiments, cross-validation for model selection, Ridge regularisation, and the correct use of development and test sets.

## Target Audience

Python developers and aspiring data scientists who understand basic machine learning concepts and want to master model evaluation and debugging.

## Depth

Beginner-to-Intermediate

## Learning Outcome

After completing the article and notebook, the reader will be able to:

1. Explain bias and variance mathematically and intuitively.
2. Identify underfitting and overfitting from validation curves.
3. Compute an empirical bias-variance decomposition using repeated independent training experiments.
4. Use cross-validation on a development dataset to select model complexity and regularisation strength.
5. Evaluate a final model exactly once on a held-out test set.
6. Diagnose two critical model-selection failure modes.

## Prerequisites

- Basic Python programming
- Introductory NumPy (arrays, random number generation)
- Basic Scikit-Learn (fitting a LinearRegression or similar model)

## Implementation Scope

Small project: synthetic data generation, polynomial regression pipelines, empirical bias-variance decomposition, K-fold cross-validation, Ridge regularisation, training size experiments, failure case demonstrations.

## Environment Constraints

CPU only — no GPU required.

## Runtime Budget

Under 5 minutes. Typical execution time: 60–120 seconds.

## Article Title

Why Your Model Aces Training But Fails in Production: Understanding Bias, Variance, and the Trade-Off

## Learning Objectives

- Understand Bias, Variance, and σ² as distinct components of expected prediction error
- Read a validation curve to identify underfitting and overfitting
- Implement an empirical bias-variance decomposition with M=200 independent training experiments
- Apply CV-based degree selection and Ridge alpha selection
- Evaluate a final model correctly with a one-time test set evaluation
- Recognise and avoid two failure modes: training-error selection and repeated test-set use

## Generated Files

| File | Description |
|---|---|
| `article.md` | Written article, ~3,400 words prose body (~4,500 words total including code blocks, tables, and captions) |
| `notebooks/concept_walkthrough.ipynb` | Executed Jupyter Notebook (17 sections) |
| `assets/diagrams/bullseye.png` | Bullseye analogy diagram (V1) |
| `assets/images/data_scatter.png` | Synthetic dataset and true function (V2) |
| `assets/images/fit_comparison.png` | Three-panel underfit/good/overfit comparison (V3) |
| `assets/images/repeated_sampling.png` | Prediction variability overlay (V4) |
| `assets/images/validation_curve.png` | Training MSE vs CV MSE by degree (V5) |
| `assets/images/bias_variance_decomposition.png` | Empirical Bias²/Variance/Expected Error (V6) |
| `assets/images/sample_size_effect.png` | Training size effect on high-complexity model (V7) |
| `assets/images/ridge_alpha.png` | CV MSE vs Ridge alpha (V8) |
| `assets/images/final_test_evaluation.png` | Final model on untouched test set (V9) |
| `sources.md` | Research ledger with 7 sources |
| `requirements.txt` | Python package dependencies |

## Project Structure

```
bias-variance-and-tradeoff/
├── ARTICLE_SPEC.md
├── article.md
├── README.md
├── sources.md
├── requirements.txt
├── assets/
│   ├── diagrams/
│   │   └── bullseye.png
│   └── images/
│       ├── data_scatter.png
│       ├── fit_comparison.png
│       ├── repeated_sampling.png
│       ├── validation_curve.png
│       ├── bias_variance_decomposition.png
│       ├── sample_size_effect.png
│       ├── ridge_alpha.png
│       └── final_test_evaluation.png
└── notebooks/
    └── concept_walkthrough.ipynb
```

## Python Version

Developed and executed with Python 3.14.5. Minimum required: Python 3.9 (for PEP 585 generic type hint syntax used in `generate_dataset`).

## Installation

```bash
pip install -r requirements.txt
```

Verified package versions used during development:
- numpy 2.4.6
- matplotlib 3.10.9
- scikit-learn 1.9.0

## How to Run the Notebook

```bash
cd notebooks/
jupyter notebook concept_walkthrough.ipynb
```

Or with JupyterLab:

```bash
jupyter lab concept_walkthrough.ipynb
```

Execute all cells from top to bottom (Kernel → Restart & Run All). Do not skip cells — variables are defined sequentially.

## How to Preview the Article

Open `article.md` in any Markdown renderer. For a browser preview:

```bash
# With grip (GitHub-flavoured Markdown preview):
pip install grip
grip article.md
```

Visual references in the article use relative paths (`assets/images/...`, `assets/diagrams/...`) which resolve correctly from the article directory.

## Expected Runtime

| Step | Time |
|---|---|
| Environment setup and data generation | < 1 s |
| Three-complexity fit comparison | < 1 s |
| Repeated sampling overlay (50 × 2 fits) | ~3 s |
| Empirical decomposition (200 × 9 fits) | ~5 s |
| CV degree sweep (12 degrees × 5 folds) | ~2 s |
| Ridge alpha CV (25 alphas × 5 folds) | ~3 s |
| Training size experiment (50 × 5 sizes) | ~1 s |
| Final model fit and test evaluation | < 1 s |
| Rendering and saving 9 figures | ~10 s |
| **Total** | **~30–60 s** |

## Hardware Requirements

CPU only. A modern laptop is sufficient. No GPU, no cloud compute, no external services required.

## Dataset Information

Synthetic dataset generated from a known data-generating process:

```
f(x) = sin(1.5 * x),  x ~ Uniform[-3, 3]
y = f(x) + epsilon,   epsilon ~ N(0, 0.25)
```

- Development dataset: 80 samples, seed=42
- Final test set: 300 samples, seed=999 (independent; outside the decomposition seed range 0–199)
- Evaluation grid for decomposition: 300 evenly spaced points, [-3, 3]

No external datasets are downloaded. All data is generated at runtime from the declared configuration constants.

## Reproducibility Information

- All random seeds are declared as named constants (`RANDOM_SEED=42`, `TEST_SEED=999`)
- `TEST_SEED=999` is outside the decomposition range (0–199) and the overlay range (1000–1049), ensuring the test RNG stream is fully independent
- The empirical decomposition uses seeds 0 through M_BOOTSTRAP-1 for independent training datasets
- Experiment 3 (training size effect) uses `numpy.random.SeedSequence` with a single master seed (`EXP3_MASTER_SEED=8000`). For each `(size_index, repetition, role)` triple, a unique child `SeedSequence` is spawned hierarchically, guaranteeing no two datasets share an RNG stream regardless of the arithmetic values of sample size or repetition index. Role 0 = training dataset, role 1 = evaluation dataset. Uniqueness of all 500 child seeds is verified programmatically at runtime.
- `warnings.filterwarnings('ignore')` suppresses non-critical scikit-learn convergence messages

Results are fully reproducible given the same Python and package versions. Minor numerical differences (< 0.001) may occur across Python versions due to floating-point implementation differences.

## Assumptions

1. The data-generating process is stationary — train and test data come from the same distribution.
2. The true function is known (synthetic data only) — enabling exact bias and variance measurement.
3. Irreducible noise is Gaussian with known σ² = 0.25 — used directly in the decomposition table.
4. LinearRegression uses least squares (SVD internally) — no convergence parameters needed.
5. `PolynomialFeatures(include_bias=False)` — the linear model provides its own intercept.

## Known Limitations

1. **Numerical blow-up at small n:** Fitting a degree-12 polynomial with n=20 or n=40 samples produces near-singular design matrices and very large evaluation MSE (n=20: mean ~108,364; n=40: mean ~544). This is an educational observation (documented in Section 11) and intentionally left visible. The sample size chart excludes these sizes for readability.

2. **CV estimate vs test MSE:** The CV estimate (0.2277) is below the final test MSE (0.2908). With a CV fold standard deviation of 0.0773, the gap is within normal sampling variability. No systematic bias in either direction can be established from a single experiment.

3. **Empirical decomposition is an approximation:** M=200 independent training experiments is sufficient for stable educational estimates but is not infinite. The true theoretical Bias² and Variance are the limits as M → ∞.

4. **Ridge alpha selection result:** The best Ridge alpha for degree-12 (0.1778, CV MSE 0.2712) did not outperform the unregularised degree-12 CV MSE (0.2698). This is because 5-fold CV on 80 samples already exposes the degree-12 model's variance on held-out folds, producing an elevated CV MSE regardless of whether the model is regularised. Ridge constrains coefficient magnitudes and produces smoother fits, but that benefit is not captured by CV on 80 samples.

5. **No solutions notebook generated:** Exercises contain hints but no solutions notebook. Solutions can be created by modifying the relevant notebook sections per exercise instructions.
