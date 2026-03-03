<h1 align="center">Multi-Modal Deep Learning for Asset Pricing</h1>

<p align="center">
Code repository for the fourth chapter of my PhD thesis <em>Essays on Deep Learning in Asset Pricing</em><br>
University of Reading, ICMA Centre (2025)
</p>

<hr>

<h2>Overview</h2>

<p>
This project introduces a <strong>multi-modal deep learning architecture</strong> for asset pricing that simultaneously incorporates information across multiple frequencies and durations — weekly, monthly, and quarterly — within a single unified model.
</p>

<p>
The framework addresses a fundamental limitation of standard return prediction models: the implicit assumption that all signals carry equal informational value regardless of their age.
</p>

<hr>

<h2>Key Contributions</h2>

<ul>
  <li>
    <strong>Mixed-frequency, mixed-duration learning.</strong><br>
    The model processes signals from different temporal horizons simultaneously, learning separate representations for weekly, monthly, and quarterly data rather than collapsing them into a single input vector.
  </li>
  <br>
  <li>
    <strong>Age-decay kernel estimation.</strong><br>
    The model learns explicit kernel functions governing how the predictive value of each signal decays as information ages. This allows the model to discriminate between recent and stale information in a fully data-driven manner, rather than imposing a fixed decay structure.
  </li>
  <br>
  <li>
    <strong>Flexible input modalities.</strong><br>
    The architecture can incorporate heterogeneous data sources — price and volume signals, news sentiment, and macroeconomic indicators — across multiple time periods simultaneously, with age kernels operating independently per modality.
  </li>
  <br>
  <li>
    <strong>Orthogonalised variable importance.</strong><br>
    The paper introduces a novel variable importance methodology that isolates each variable's marginal contribution independently of all others. Standard SHAP values and permutation importance measures are contaminated by feature correlations, complicating attribution. This approach uses PCA-based orthogonalisation of feature innovations to achieve complete separation of individual contributions, yielding a cleaner and theoretically consistent diagnostic tool.
  </li>
</ul>

<hr>

<h2>Applications</h2>

<p>
The model is evaluated on three tasks using an enhanced version of the Gu, Kelly &amp; Xiu (2020) dataset:
</p>

<ul>
  <li><strong>Weekly return prediction</strong> — forecasting cross-sectional equity returns at a weekly horizon</li>
  <li><strong>Portfolio optimisation</strong> — using model outputs within a portfolio construction objective</li>
  <li><strong>Volatility prediction</strong> — forecasting realised volatility as an alternative prediction target</li>
</ul>

<hr>

<h2>Results</h2>

<p>
The multi-modal architecture demonstrates that mixed-frequency, age-aware learning is a viable approach to asset pricing. Full realisation of the framework’s potential requires further architectural simplification and tuning.
</p>

<p>
The orthogonalised variable importance analysis yields interpretable and theoretically consistent attribution results across all three applications.
</p>

<hr>

<h2>Code Structure</h2>

<pre>
PhD_PP_4.py        — Data preprocessing pipeline; extends and enhances the Gu, Kelly & Xiu (2020) dataset
PhD_4_script.py    — Model specification, hyperparameter estimation, and training
PhD_4_PM.py        — Performance measurement and evaluation
</pre>

<hr>

<h2>Dependencies</h2>

<ul>
  <li>Python 3.x</li>
  <li>NumPy</li>
  <li>Pandas</li>
  <li>PyTorch</li>
  <li>scikit-learn</li>
  <li>Numba</li>
</ul>

<hr>

<h2>Reference</h2>

<p>
Gu, S., Kelly, B., &amp; Xiu, D. (2020). <em>Empirical asset pricing via machine learning.</em> Review of Financial Studies, 33(5), 2223–2273.
</p>
