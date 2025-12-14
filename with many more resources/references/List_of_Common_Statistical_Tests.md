# Common Statistical Tests in Epidemiology and Applied Statistics

A comprehensive guide to selecting and interpreting statistical tests, organized by analysis type.

## Quick Reference: Choosing a Test

| Your Question | Variables | Consider |
|---------------|-----------|----------|
| Compare 2 group means | 1 categorical (2 levels), 1 continuous | Independent t-test or Mann-Whitney U |
| Compare paired/matched means | 1 categorical (paired), 1 continuous | Paired t-test or Wilcoxon signed-rank |
| Compare 3+ group means | 1 categorical (3+ levels), 1 continuous | ANOVA or Kruskal-Wallis |
| Association between categories | 2 categorical | Chi-square or Fisher's exact |
| Predict continuous outcome | 1+ predictors, 1 continuous | Linear regression |
| Predict binary outcome | 1+ predictors, 1 binary | Logistic regression |
| Predict count outcome | 1+ predictors, 1 count | Poisson or negative binomial |
| Time-to-event analysis | 1+ predictors, survival time | Kaplan-Meier, log-rank, Cox regression |
| Repeated/clustered data | Multiple measures per subject | Mixed models or GEE |

---

## 1. Tests for Comparing Groups

### Parametric Tests

| Test | Independent Variable | Dependent Variable | Covariates | Use-Case & Assumptions |
|------|---------------------|-------------------|------------|------------------------|
| **Independent t-test** | Categorical (2 groups) | Continuous (≈ normal) | None | Compares means between **two independent groups** (e.g., treatment vs. control). Assumes: independent samples, normally distributed populations, equal variances (Welch's t-test relaxes equal variance assumption). |
| **Paired t-test** | Categorical (paired, 2 levels) | Continuous (≈ normal) | None | Tests mean difference between **two matched measurements** (e.g., before vs. after in same subjects). Assumes: differences are normally distributed, pairs are independent. |
| **One-way ANOVA** | Categorical (≥2 levels) | Continuous (≈ normal) | None | Tests for mean differences across **3+ independent groups**. Assumes: normal residuals, homogeneity of variances (Levene's test), independent observations. Post-hoc tests (Tukey, Bonferroni) identify which groups differ. |
| **Repeated-Measures ANOVA** | Categorical (within-subject factor) | Continuous (≈ normal) | None | Compares means across **3+ related conditions** for same subjects (e.g., measurements at multiple time points). Assumes: sphericity (equal variances of differences)—violations require Greenhouse-Geisser or Huynh-Feldt corrections. |
| **Mixed ANOVA** | Between- and within-subject factors | Continuous | Categorical (between-subject) | Tests **interactions between within-subject and between-subject factors**. Example: Do treatment groups show different trends over time? Combines repeated-measures and between-groups designs. |
| **ANCOVA** | Categorical (≥2 groups) | Continuous (≈ normal) | Continuous (covariate) | Compares group means while **adjusting for a continuous covariate**. Example: Compare outcomes by treatment, controlling for baseline values. Assumes: linear covariate-outcome relationship, parallel slopes (no interaction), plus ANOVA assumptions. |
| **MANOVA** | Categorical (≥2 groups) | Multiple continuous | None | Tests group differences across **multiple outcomes simultaneously**. Example: Compare treatment groups on blood pressure AND cholesterol together. Assumes: multivariate normality, equal covariance matrices. A significant result requires follow-up univariate tests. |
| **MANCOVA** | Categorical (≥2 groups) | Multiple continuous | Continuous/Categorical | Multivariate extension of ANCOVA—compares multivariate means while **controlling for covariates**. |

### Nonparametric Tests

| Test | Independent Variable | Dependent Variable | Covariates | Use-Case & Assumptions |
|------|---------------------|-------------------|------------|------------------------|
| **Mann-Whitney U** (Wilcoxon rank-sum) | Categorical (2 groups) | Continuous/Ordinal | None | Compares **distributions between two independent groups** when normality is violated. Uses ranks rather than raw values. Assumes: similarly-shaped distributions (tests location shift). |
| **Wilcoxon Signed-Rank Test** | Categorical (paired) | Continuous/Ordinal | None | Tests whether **median of paired differences equals zero**. More powerful than sign test because it considers magnitude of differences. Assumes: symmetric distribution of differences. |
| **Kruskal-Wallis Test** | Categorical (≥3 groups) | Continuous/Ordinal | None | Nonparametric alternative to one-way ANOVA for **3+ independent groups**. Tests whether at least one group distribution differs. Post-hoc: Dunn's test. |
| **Friedman Test** | Categorical (≥3 related conditions) | Continuous/Ordinal | None | Nonparametric alternative to repeated-measures ANOVA. Tests **ranked differences across conditions within subjects**. Example: Patients rank pain relief across 3 treatments. |

### Tests for Categorical Associations

| Test | Independent Variable | Dependent Variable | Covariates | Use-Case & Assumptions |
|------|---------------------|-------------------|------------|------------------------|
| **Chi-Square Test of Independence** | Categorical | Categorical | None | Tests **association between two categorical variables** in a contingency table. Assumes: expected cell counts ≥5 (>80% of cells), independent observations. Reports χ² statistic and p-value. |
| **Fisher's Exact Test** | Categorical | Categorical | None | Tests association in **small-sample contingency tables** where chi-square assumptions fail. Provides exact p-value using hypergeometric distribution. Preferred when expected counts <5 in >20% of cells. |
| **McNemar's Test** | Categorical (paired 2×2) | Categorical (binary) | None | Tests **change in proportions for paired/matched binary data**. Example: Did the proportion of positive responses change pre- vs. post-intervention? Tests marginal homogeneity. |
| **Cochran's Q Test** | Categorical (≥3 related measures) | Binary | None | Extension of McNemar's for **>2 related binary outcomes**. Example: Compare success rates across 3 treatment attempts on same patients. |

---

## 2. Correlation and Regression Models

### Correlation

| Test | Variables | Covariates | Use-Case & Assumptions |
|------|-----------|------------|------------------------|
| **Pearson Correlation** | Two continuous | None | Measures **linear relationship** between two variables (r = -1 to +1). Assumes: bivariate normality, linearity, no extreme outliers, independent observations. |
| **Spearman's Rank Correlation** | Two continuous/ordinal | None | Measures **monotonic relationship** using ranks. Use when: Pearson assumptions violated, ordinal data, or nonlinear but monotonic relationships exist. |
| **Partial Correlation** | Two continuous | Continuous (controlled) | Measures correlation between two variables **controlling for one or more other variables**. Removes confounding influence of control variables. |

### Linear Regression

| Model | Independent Variable | Dependent Variable | Covariates | Use-Case & Assumptions |
|-------|---------------------|-------------------|------------|------------------------|
| **Simple Linear Regression** | Single continuous | Continuous | None | Models $Y = \beta_0 + \beta_1X + \varepsilon$. Predicts outcome from one predictor. Assumes: linearity, independent errors, normal residuals (for inference), homoscedasticity. |
| **Multiple Linear Regression** | Multiple continuous/categorical | Continuous | Multiple | Models outcome from **several predictors simultaneously**, allowing control for confounders. Additional assumption: no strong multicollinearity (check VIF). |
| **Hierarchical (Blockwise) Regression** | Predictors entered in stages | Continuous | — | Predictors added in **sequential blocks** to assess incremental variance explained (ΔR²). Example: Step 1: demographics; Step 2: add clinical variables. Tests whether added predictors significantly improve model. |
| **Polynomial Regression** | Continuous (with polynomial terms) | Continuous | — | Models **curvilinear relationships** by including X², X³, etc. Check for overfitting; use when theory suggests nonlinear effects. |

### Generalized Linear Models (GLMs)

| Model | Independent Variable | Dependent Variable | Covariates | Use-Case & Assumptions |
|-------|---------------------|-------------------|------------|------------------------|
| **Logistic Regression** (Binary) | Continuous/Categorical | Binary (0/1) | Multiple | Models **log-odds of binary outcome**. Outputs odds ratios. Example: Predict disease (yes/no) from risk factors. Assumes: independent observations, linearity on log-odds scale, no multicollinearity. |
| **Ordinal Logistic Regression** | Continuous/Categorical | Ordinal (ordered categories) | Multiple | Models **cumulative odds** of ordered outcomes (e.g., mild/moderate/severe). Key assumption: **proportional odds**—effect of predictors is constant across cut-points. Test with Brant test. |
| **Multinomial Logistic Regression** | Continuous/Categorical | Nominal (≥3 unordered categories) | Multiple | Predicts probabilities of **multiple unordered outcomes** (e.g., treatment choice A/B/C). Compares each category to a reference. No ordering assumption. |
| **Ordered Probit Regression** | Continuous/Categorical | Ordinal | Multiple | Alternative to ordinal logistic using probit link (normal distribution). Similar applications; choice between logit/probit often makes little practical difference. |
| **Poisson Regression** | Continuous/Categorical | Count | Multiple | Models **count data** assuming Poisson distribution (mean = variance). Example: Number of hospital visits. If variance > mean (overdispersion), consider negative binomial. |
| **Negative Binomial Regression** | Continuous/Categorical | Count (overdispersed) | Multiple | Models **overdispersed count data** where variance exceeds mean. Adds dispersion parameter to Poisson. Preferred when Poisson shows poor fit due to overdispersion. |
| **Zero-Inflated Models** (ZIP, ZINB) | Continuous/Categorical | Count (excess zeros) | Multiple | Two-part models for counts with **excess zeros** beyond what Poisson/NB predicts. Models: (1) probability of structural zero vs. (2) count process for non-zeros. Example: Smoking frequency where many are non-smokers. |
| **Tobit Regression** | Continuous/Categorical | Continuous (censored) | Multiple | Models **censored continuous outcomes** (floor or ceiling effects). Example: Income data censored at detection limits, or test scores with floor effects. Assumes: underlying normal distribution, censoring mechanism is known. |

### Mixed-Effects and Multilevel Models

| Model | Independent Variable | Dependent Variable | Covariates | Use-Case & Assumptions |
|-------|---------------------|-------------------|------------|------------------------|
| **Linear Mixed-Effects Model** (LME) | Continuous/Categorical (fixed effects) | Continuous | Random effects for grouping | Handles **hierarchical/repeated-measures data** by including random effects. Example: Patient-specific intercepts for longitudinal blood pressure. Accounts for within-cluster correlation. Assumes: normal residuals and random effects, independent clusters. |
| **Hierarchical Linear Modeling** (HLM) | Continuous/Categorical | Continuous | Random effects at each level | Synonym for multilevel model—handles **nested data** (e.g., students within schools within districts). Allows intercepts/slopes to vary by higher-level groups. |
| **Generalized Linear Mixed Model** (GLMM) | Continuous/Categorical | Any GLM outcome | Random effects | Mixed-effects extension of GLMs (logistic, Poisson, etc.) for clustered non-normal outcomes. Example: Repeated binary outcomes within patients. |
| **Generalized Estimating Equations** (GEE) | Continuous/Categorical | Any | Working correlation | Alternative to mixed models for **correlated data**—estimates **population-averaged** (marginal) effects. Specify working correlation structure (exchangeable, AR(1), etc.). Robust SEs valid even if correlation misspecified. Does not provide subject-specific effects. |

---

## 3. Survival Analysis

| Method | Independent Variable | Dependent Variable | Covariates | Use-Case & Assumptions |
|--------|---------------------|-------------------|------------|------------------------|
| **Kaplan-Meier Estimator** | Categorical (optional grouping) | Time-to-event | None | Non-parametric estimation of **survival function** $S(t)$. Produces survival curves showing probability of surviving past time $t$. Handles right-censoring. Assumes: **non-informative censoring** (censored subjects have same future risk as those remaining). |
| **Log-Rank Test** | Categorical (typically 2 groups) | Time-to-event | None | Tests whether **survival curves differ** between groups. Non-parametric, gives equal weight to all time points. Assumes: non-informative censoring, proportional hazards (sensitive to crossing curves). For >2 groups, tests overall difference. |
| **Cox Proportional Hazards Regression** | Continuous/Categorical | Time-to-event | Multiple | **Semi-parametric survival regression** estimating hazard ratios. Does not assume specific survival distribution. Key assumption: **proportional hazards**—HR constant over time. Check with Schoenfeld residuals; violations may require stratification or time-varying covariates. |
| **Parametric Survival Models** (Exponential, Weibull, etc.) | Continuous/Categorical | Time-to-event | Multiple | Assume specific distribution for survival times. Weibull is flexible (includes exponential as special case). Provide baseline hazard estimates (unlike Cox). Model selection based on AIC/BIC and distributional fit. |
| **Competing Risks Analysis** | Categorical | Time-to-event with competing events | Multiple | Handles situations where **multiple event types** can occur (e.g., death precludes observing stroke). Uses cumulative incidence function (CIF). Gray's test compares CIF between groups. Fine-Gray model provides subdistribution hazard ratios. |
| **Frailty Models** | Continuous/Categorical | Time-to-event | Random effects | Survival models with **random effects** (frailties) to account for unobserved heterogeneity or clustering. Example: Hospital-level random effects in multi-center trial. |

---

## 4. Multivariate Analysis and Dimension Reduction

### Dimension Reduction (Unsupervised)

| Method | Input | Output | Use-Case & Assumptions |
|--------|-------|--------|------------------------|
| **Principal Component Analysis (PCA)** | Multiple continuous variables | Principal components | Reduces dimensionality by creating **uncorrelated linear combinations** maximizing variance. First PC captures most variance, etc. Useful for data visualization, removing multicollinearity. Assumes: linear relationships, meaningful to maximize variance. |
| **Factor Analysis** (Exploratory) | Multiple continuous variables | Latent factors | Identifies **underlying latent constructs** explaining correlations among observed variables. Example: Find "anxiety" factor from symptom questionnaire items. Rotation methods (varimax, oblimin) aid interpretation. Assumes: sufficient correlations exist, factor structure is meaningful. |
| **Cluster Analysis** (K-means, Hierarchical) | Multiple variables | Cluster assignments | **Groups observations** into homogeneous clusters based on similarity. Unsupervised—no outcome variable. Number of clusters often chosen by silhouette score, elbow plot, or domain knowledge. |
| **Multidimensional Scaling (MDS)** | Distance/dissimilarity matrix | Low-dimensional coordinates | **Visualizes similarities** by placing items in 2D/3D space where distances reflect dissimilarities. Useful for perceptual mapping, genetic distances. |

### Classification and Structural Modeling

| Method | Independent Variable | Dependent Variable | Use-Case & Assumptions |
|--------|---------------------|-------------------|------------------------|
| **Discriminant Analysis** | Multiple continuous | Categorical (group membership) | **Classifies cases** into predefined groups using linear combinations of predictors. Assumes: multivariate normality within groups, equal covariances. Often replaced by logistic regression for binary outcomes. |
| **Canonical Correlation** | Set of continuous variables | Set of continuous variables | Examines **relationships between two variable sets**. Finds pairs of canonical variates (one from each set) that are maximally correlated. |
| **Structural Equation Modeling (SEM)** | Observed and latent variables | Observed and latent outcomes | Combines factor analysis and path analysis to test **complex theoretical models** with latent variables and multiple pathways. Provides fit indices (CFI, RMSEA, etc.). Requires large samples; assumes multivariate normality for ML estimation. |
| **Path Analysis** | Multiple observed variables | Multiple outcomes | Special case of SEM without latent variables—models **direct and indirect effects** in causal networks. Tests mediational and directional hypotheses. |
| **Mediation Analysis** | X, Mediator M | Outcome Y | Tests whether X's effect on Y is **transmitted through mediator M**. Traditional: Baron-Kenny steps. Modern: bootstrapped indirect effects (more robust). Assumes: causal ordering X→M→Y, no unmeasured confounding of M→Y. |
| **Moderation Analysis** | X, Moderator | Outcome Y | Tests whether X→Y relationship **depends on moderator level**. Implemented via interaction term (X × Moderator). Significant interaction indicates moderation. Center continuous variables for interpretability. |

---

## 5. Time Series Analysis

| Model | Independent Variable | Dependent Variable | Use-Case & Assumptions |
|-------|---------------------|-------------------|------------------------|
| **ARIMA** (p, d, q) | Lagged values of series | Continuous time series | **Forecasting model** using autoregressive (p), differencing (d), and moving average (q) components. Requires **stationarity** (achieved via differencing). Model selection via ACF/PACF plots, AIC. SARIMA adds seasonal components. |
| **Seasonal Decomposition** | Time | Continuous series | Decomposes series into **trend, seasonal, and residual** components. Additive or multiplicative. Useful for understanding patterns before modeling. |
| **Cross-Correlation Function (CCF)** | Two time series | Correlation at lags | Identifies **lagged relationships** between series. Example: Does temperature lead infection rates by 2 weeks? Requires stationary or differenced series. |
| **Vector Autoregression (VAR)** | Multiple lagged series | Multiple series | **Multivariate time series model** where each variable depends on its own lags and lags of other variables. Captures feedback relationships. Requires joint stationarity. |
| **Interrupted Time Series (ITS)** | Time, intervention indicator | Continuous series | Evaluates **effect of interventions** on outcomes over time. Tests for level and/or slope changes at intervention point. Quasi-experimental design. |
| **ARCH/GARCH** | Lagged variances | Variance of series | Models **time-varying volatility** (conditional heteroscedasticity). Common in finance. GARCH generalizes ARCH by including past variances. |

---

## 6. Other Specialized Methods

| Method | Variables | Use-Case & Assumptions |
|--------|-----------|------------------------|
| **Bayesian Inference** | Any | Statistical paradigm combining **prior beliefs with data** via Bayes' theorem to obtain posterior distributions. Provides credible intervals (direct probability statements about parameters). Requires prior specification; results sensitive to priors with small samples. Applicable to any model (regression, survival, etc.). |
| **Propensity Score Methods** | Treatment indicator, covariates | Reduces confounding in **observational studies** by balancing groups on propensity (predicted probability) of treatment. Methods: matching, stratification, weighting (IPTW), or as covariate. Assumes: no unmeasured confounders (strong ignorability), adequate overlap (positivity). |
| **Meta-Analysis** | Effect sizes from multiple studies | Synthesizes evidence across studies to estimate **pooled effect size**. Fixed-effect (assumes common true effect) vs. random-effects (accounts for between-study heterogeneity). Assess heterogeneity (I², Q statistic) and publication bias (funnel plots, Egger's test). |
| **ROC Curve Analysis** | Continuous predictor/score | Binary outcome | Evaluates **diagnostic/predictive accuracy**. Plots sensitivity vs. 1-specificity across thresholds. AUC summarizes discrimination (0.5 = chance, 1.0 = perfect). Compare AUCs with DeLong test. |
| **Network Meta-Analysis** | Effect sizes from RCTs with shared comparators | Combines direct and indirect evidence to compare **multiple treatments simultaneously**, even those never compared head-to-head. Assumes: transitivity (indirect comparisons valid), consistency (direct/indirect estimates agree). |
| **Instrumental Variables (IV) / 2SLS** | Instrument, endogenous predictor | Outcome | Addresses **endogeneity** (unmeasured confounding, reverse causation) using an instrument that affects outcome only through the exposure. Example: Mendelian randomization uses genetic variants as instruments. Assumptions: relevance, exclusion, independence. |

---

## Assumptions Quick Reference

### Common Assumption Violations and Solutions

| Assumption | How to Check | Solutions if Violated |
|------------|--------------|----------------------|
| **Normality** | Histogram, Q-Q plot, Shapiro-Wilk test | Transform data (log, sqrt), use nonparametric tests, bootstrap, or rely on CLT for large samples |
| **Homoscedasticity** | Residual plots, Breusch-Pagan test | Robust SEs, weighted least squares, transform outcome |
| **Independence** | Study design, Durbin-Watson (autocorrelation) | Mixed models, GEE, cluster-robust SEs, time series methods |
| **Linearity** | Residual vs. fitted plots, component+residual plots | Add polynomial/spline terms, transform variables, use GAMs |
| **Proportional Hazards** (Cox) | Schoenfeld residuals, log-log plots | Stratify, add time-varying covariates, use parametric models |
| **Proportional Odds** (ordinal logistic) | Brant test, score test | Partial proportional odds model, multinomial logistic |
| **No Multicollinearity** | VIF, correlation matrix | Remove/combine variables, use ridge regression, PCA |

---

## Effect Size Guidelines

| Statistic | Small | Medium | Large |
|-----------|-------|--------|-------|
| **Cohen's d** (mean difference) | 0.2 | 0.5 | 0.8 |
| **Pearson's r** (correlation) | 0.1 | 0.3 | 0.5 |
| **η²** (eta-squared, ANOVA) | 0.01 | 0.06 | 0.14 |
| **Odds Ratio** | 1.5 | 2.5 | 4.0 |
| **Cohen's w** (chi-square) | 0.1 | 0.3 | 0.5 |

*Note: Effect size interpretation should consider context and practical significance, not just these benchmarks.*

---

## Software Implementation Notes

| Analysis | R Packages | Python Libraries | Other |
|----------|------------|------------------|-------|
| Basic tests | `stats`, `car` | `scipy.stats`, `pingouin` | SPSS, Stata |
| Regression | `lm()`, `glm()`, `MASS` | `statsmodels`, `sklearn` | SAS PROC REG/LOGISTIC |
| Mixed models | `lme4`, `nlme` | `statsmodels.mixedlm` | SAS PROC MIXED |
| Survival | `survival`, `survminer` | `lifelines`, `scikit-survival` | SAS PROC PHREG |
| SEM/Path | `lavaan`, `semTools` | `semopy` | Mplus, AMOS |
| Time series | `forecast`, `tseries` | `statsmodels.tsa` | EViews |
| Bayesian | `brms`, `rstanarm`, `rjags` | `pymc`, `arviz` | Stan, JAGS |
| Meta-analysis | `meta`, `metafor` | `pymare` | CMA, RevMan |

---

## References and Further Reading

### Textbooks
- Agresti, A. (2013). *Categorical Data Analysis* (3rd ed.). Wiley.
- Hosmer, D.W., Lemeshow, S., & Sturdivant, R.X. (2013). *Applied Logistic Regression* (3rd ed.). Wiley.
- Kleinbaum, D.G. & Klein, M. (2012). *Survival Analysis: A Self-Learning Text* (3rd ed.). Springer.
- Raudenbush, S.W. & Bryk, A.S. (2002). *Hierarchical Linear Models* (2nd ed.). Sage.
- Vittinghoff, E. et al. (2012). *Regression Methods in Biostatistics* (2nd ed.). Springer.

### Online Resources
- UCLA Statistical Consulting: https://stats.oarc.ucla.edu/
- Penn State STAT 500-509 Online Courses: https://online.stat.psu.edu/
- Laerd Statistics: https://statistics.laerd.com/

---


