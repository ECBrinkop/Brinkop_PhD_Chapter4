Multi-Modal Deep Learning for Asset Pricing
Code repository for the fourth chapter of my PhD thesis Essays on Deep Learning in Asset Pricing (University of Reading, ICMA Centre, 2025).
Overview
This project introduces a multi-modal deep learning architecture for asset pricing that simultaneously incorporates information across multiple frequencies and durations — weekly, monthly, and quarterly — within a single model. The architecture addresses a fundamental limitation of standard return prediction models: the implicit assumption that all signals carry equal informational value regardless of their age.
The key contributions are:
Mixed-frequency, mixed-duration learning. The model processes signals from different temporal horizons simultaneously, learning separate representations for weekly, monthly, and quarterly data rather than collapsing them into a single input vector.
Age-decay kernel estimation. The model learns explicit kernel functions governing how the predictive value of each signal decays as information ages. This allows the model to discriminate between recent and stale information in a data-driven way, rather than imposing a fixed decay structure.
Flexible input modalities. The architecture can in principle incorporate heterogeneous data sources — price and volume signals, news sentiment, and macroeconomic indicators — across multiple time periods simultaneously, with age kernels operating independently per modality.
Orthogonalised variable importance. The paper introduces a novel variable importance methodology that isolates each variable's marginal contribution independently of all others. Standard SHAP values and permutation importance measures are contaminated by feature correlations, making it difficult to attribute predictive power cleanly. This approach uses PCA-based orthogonalisation of feature innovations to achieve 100% separation of individual contributions — a cleaner diagnostic tool for understanding what drives model predictions.
Applications
The model is evaluated on three tasks using an enhanced version of the Gu, Kelly & Xiu (2020) dataset:

Weekly return prediction — forecasting cross-sectional equity returns at a weekly horizon
Portfolio optimisation — using model outputs as inputs to a portfolio construction objective
Volatility prediction — forecasting realised volatility as an alternative prediction target

Results
The multi-modal architecture demonstrates that mixed-frequency, age-aware learning is a viable approach to asset pricing. Full realisation of the framework's potential requires further architectural simplification and tuning. The orthogonalised variable importance analysis yields interpretable and theoretically clean attribution results across all three applications.
Code Structure

PhD_PP_4.py — data preprocessing pipeline; extends and enhances the Gu, Kelly & Xiu (2020) dataset with additional features
PhD_4_script.py — model specification, hyperparameter estimation, and training across all three applications
PhD_4_PM.py — performance measurement and evaluation of results

Dependencies
Python 3.x, NumPy, Pandas, PyTorch, scikit-learn, Numba
Reference
Gu, S., Kelly, B., & Xiu, D. (2020). Empirical asset pricing via machine learning. Review of Financial Studies, 33(5), 2223–2273.
