# Sources

---

## SOURCE 1

- **SOURCE:** The Elements of Statistical Learning (ESL), 2nd Edition
- **URL:** https://hastie.su.domains/ElemStatLearn/
- **SOURCE TYPE:** Authoritative textbook
- **AUTHOR OR ORGANIZATION:** Trevor Hastie, Robert Tibshirani, Jerome Friedman
- **PUBLICATION OR UPDATE DATE:** 2009 (2nd ed.); PDF freely available from authors
- **DATE ACCESSED:** 2026-07-13
- **CLAIMS SUPPORTED:** Formal derivation of the bias-variance decomposition of expected prediction error (Chapter 2, Section 2.9; Chapter 7, Section 7.3). Mathematical definition of Bias, Variance, and irreducible noise. The decomposition formula E[(y − f̂)²] = Bias² + Variance + σ².
- **ARTICLE SECTIONS SUPPORTED:** "What Bias and Variance Actually Are", "The Decomposition", mathematical notation throughout
- **NOTEBOOK SECTIONS SUPPORTED:** Section 8 (mathematical derivation), Section 8 (empirical decomposition algorithm)
- **WHY TRUSTWORTHY:** Primary academic reference for statistical learning theory. Authors are among the founding contributors to regularisation, tree methods, and model selection methodology in statistics and machine learning.

---

## SOURCE 2

- **SOURCE:** An Introduction to Statistical Learning (ISLR), 2nd Edition
- **URL:** https://www.statlearning.com/
- **SOURCE TYPE:** Authoritative textbook (pedagogical)
- **AUTHOR OR ORGANIZATION:** Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani
- **PUBLICATION OR UPDATE DATE:** 2021 (2nd ed., with Python companion)
- **DATE ACCESSED:** 2026-07-13
- **CLAIMS SUPPORTED:** Bias-variance trade-off at beginner-to-intermediate level (Chapter 2). Cross-validation methodology and correct use of training/validation/test sets (Chapter 5). Regularisation via Ridge (Chapter 6).
- **ARTICLE SECTIONS SUPPORTED:** "Model Selection: Cross-Validation, Not Training Error", "Regularisation: Reining In a Complex Model", "Two Failure Modes to Know"
- **NOTEBOOK SECTIONS SUPPORTED:** Section 9 (Experiment 1), Section 10 (Experiment 4), Section 12 (final evaluation), Section 13 (failure cases)
- **WHY TRUSTWORTHY:** Pedagogically focused companion to ESL by the same senior authors. Widely adopted in academic courses. Python edition verified to use scikit-learn idioms.

---

## SOURCE 3

- **SOURCE:** scikit-learn documentation — PolynomialFeatures
- **URL:** https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.PolynomialFeatures.html
- **SOURCE TYPE:** Official library documentation
- **AUTHOR OR ORGANIZATION:** scikit-learn developers
- **PUBLICATION OR UPDATE DATE:** Verified against scikit-learn 1.9.0 (stable as of 2026-07-13)
- **DATE ACCESSED:** 2026-07-13
- **CLAIMS SUPPORTED:** `include_bias=False` parameter behaviour. `degree` parameter accepts int or tuple. No deprecations in current stable release.
- **ARTICLE SECTIONS SUPPORTED:** Code blocks using `PolynomialFeatures`
- **NOTEBOOK SECTIONS SUPPORTED:** `make_poly_pipeline` helper, all polynomial fitting cells
- **WHY TRUSTWORTHY:** Primary source for scikit-learn API behaviour. Verified against the installed version (1.9.0) used during notebook execution.

---

## SOURCE 4

- **SOURCE:** scikit-learn documentation — Ridge
- **URL:** https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Ridge.html
- **SOURCE TYPE:** Official library documentation
- **AUTHOR OR ORGANIZATION:** scikit-learn developers
- **PUBLICATION OR UPDATE DATE:** Verified against scikit-learn 1.9.0 (stable as of 2026-07-13)
- **DATE ACCESSED:** 2026-07-13
- **CLAIMS SUPPORTED:** `alpha` parameter behaviour and objective function (L2 penalty). No deprecations in current stable release. Default `tol` changed from 1e-3 to 1e-4 in v1.2 (noted, not a deprecation).
- **ARTICLE SECTIONS SUPPORTED:** "Regularisation: Reining In a Complex Model", Ridge objective function formula
- **NOTEBOOK SECTIONS SUPPORTED:** Section 10 (Experiment 4), `make_poly_pipeline` with `ridge_alpha`
- **WHY TRUSTWORTHY:** Primary source for Ridge API. Version confirmed via executed notebook output (scikit-learn 1.9.0).

---

## SOURCE 5

- **SOURCE:** scikit-learn documentation — cross_val_score
- **URL:** https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_val_score.html
- **SOURCE TYPE:** Official library documentation
- **AUTHOR OR ORGANIZATION:** scikit-learn developers
- **PUBLICATION OR UPDATE DATE:** Verified against scikit-learn 1.9.0 (stable as of 2026-07-13)
- **DATE ACCESSED:** 2026-07-13
- **CLAIMS SUPPORTED:** `scoring='neg_mean_squared_error'` is a valid scoring string. `cv` accepts a KFold object. `groups` routing change in v1.4 (not relevant to this notebook's usage).
- **ARTICLE SECTIONS SUPPORTED:** "Model Selection: Cross-Validation, Not Training Error" code block
- **NOTEBOOK SECTIONS SUPPORTED:** Section 9 (Experiment 1), Section 10 (Experiment 4)
- **WHY TRUSTWORTHY:** Primary source for cross-validation API. Behaviour confirmed via notebook execution.

---

## SOURCE 6

- **SOURCE:** scikit-learn documentation — KFold
- **URL:** https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.KFold.html
- **SOURCE TYPE:** Official library documentation
- **AUTHOR OR ORGANIZATION:** scikit-learn developers
- **PUBLICATION OR UPDATE DATE:** Verified against scikit-learn 1.9.0 (stable as of 2026-07-13)
- **DATE ACCESSED:** 2026-07-13
- **CLAIMS SUPPORTED:** `shuffle=True` with `random_state` produces reproducible folds. No deprecations in current stable release.
- **ARTICLE SECTIONS SUPPORTED:** CV methodology description
- **NOTEBOOK SECTIONS SUPPORTED:** `kf = KFold(n_splits=5, shuffle=True, random_state=42)` used throughout Sections 9 and 10
- **WHY TRUSTWORTHY:** Primary source for KFold API. Reproducibility behaviour confirmed via consistent notebook results across runs.

---

## SOURCE 7

- **SOURCE:** Bias-Variance Decomposition of Mean Squared Error — Chris Yeh
- **URL:** https://chrisyeh96.github.io/2019/07/18/bias-variance-decomposition.html
- **SOURCE TYPE:** Technical educational reference
- **AUTHOR OR ORGANIZATION:** Chris Yeh (Stanford PhD student at time of publication)
- **PUBLICATION OR UPDATE DATE:** 2019-07-18
- **DATE ACCESSED:** 2026-07-13
- **CLAIMS SUPPORTED:** Mathematical derivation of the bias-variance decomposition from first principles. Precise definitions of Bias, Variance, and noise components. Confirms that the decomposition uses expectation over training datasets.
- **ARTICLE SECTIONS SUPPORTED:** "What Bias and Variance Actually Are", "The Decomposition" — used to cross-check the mathematical derivation against ESL
- **NOTEBOOK SECTIONS SUPPORTED:** Section 8 markdown cells (mathematical explanation)
- **WHY TRUSTWORTHY:** Rigorous mathematical derivation with explicit steps; consistent with ESL Chapter 2 and Chapter 7 derivations. Used as a secondary cross-check, not a primary source.

---

*All sources listed here were actually consulted during research. No sources are included that were not accessed. No statistics, benchmarks, or claims are sourced from undocumented origins.*
