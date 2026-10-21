# Ensemble learning

## Overview

- **[Ensemble Methods in Machine Learning](https://www.cs.princeton.edu/courses/archive/spring10/cos424/papers/Dietterich-2000.pdf)** (Dietterich, 2000). Reviews voting, bagging, boosting, and Bayesian averaging; explains how statistical, computational, and representational differences between learners can make their combination useful.

## Bagging and randomized trees

- **[Bagging Predictors](https://link.springer.com/article/10.1007/BF00058655)** (Breiman, 1996). Fits predictors on bootstrap samples and aggregates their outputs. Particularly useful for unstable learners whose predictions change substantially when the training data change.
- **[Random Subspaces](https://doi.org/10.1109/34.709601)** (Ho, 1998). Builds decision trees on randomly selected feature subsets and combines their predictions. Feature sampling occurs per tree; Breiman's random forest also samples candidate features at individual splits.
- **[Random Forests](https://link.springer.com/article/10.1023/A:1010933404324)** (Breiman, 2001). Combines randomized trees; the widely used construction couples bootstrap sampling with random feature subsets at each split. Individual tree strength and error correlation both affect ensemble performance.
- **[Extremely Randomized Trees](https://link.springer.com/article/10.1007/s10994-006-6226-1)** (Geurts et al., 2006). Randomizes candidate features and split thresholds, then selects among those candidates. The original Extra-Trees construction uses the full training sample rather than bootstrap replicates.
- **[Random Forest Methodology and Practical Guidance](https://epub.ub.uni-muenchen.de/13766/1/TR.pdf)** (Boulesteix et al., 2012). Reviews tuning, implementations, applications, and pitfalls in bioinformatics, including biases in variable-importance measures.
- **[Variable Selection Using Random Forests](https://hal.science/hal-00755489/document)** (Genuer et al., 2010). Uses importance rankings and nested models to select variables; distinguishes identifying relevant variables from choosing a smaller set for prediction.
- **[Bias in Random Forest Variable Importance](https://link.springer.com/article/10.1186/1471-2105-8-25)** (Strobl et al., 2007). Shows selection and importance biases with mixed predictor types or category counts; investigates conditional inference trees and subsampling as remedies.

## Boosting foundations

- **[The Strength of Weak Learnability](https://link.springer.com/article/10.1007/BF00116037)** (Schapire, 1990). Proves equivalence of weak and strong learnability in the distribution-free PAC model. The result assumes a weak learner for the required distributions, not merely one classifier above chance on one dataset.
- **[AdaBoost](https://www.schapire.net/papers/FreundSc95.pdf)** (Freund & Schapire, 1997 journal paper). Sequentially reweights training examples and combines weak classifiers with error-dependent weights. Misclassified examples gain weight, directing later learners toward current errors.
- **[Boosting the Margin](https://www.schapire.net/papers/SchapireFrBaLe98.pdf)** (Schapire et al., ICML 1997; journal 1998). Relates voting-classifier generalization bounds to the margin distribution, helping explain continued improvement after training error reaches zero.
- **[Arcing the Edge](https://statistics.berkeley.edu/sites/default/files/tech-reports/486.pdf)** (Breiman, 1997 technical report). Formulates adaptive reweighting as optimization of functions of the edge; develops an alternative perspective on the behavior of voting classifiers.
- **[A Short Introduction to Boosting](https://www.yorku.ca/gisweb/eats4400/boost.pdf)** (Freund & Schapire, 1999). Compact overview of AdaBoost, training-error bounds, margins, and connections with support-vector machines.

## Gradient boosting

- **[Boosting Algorithms as Gradient Descent](https://papers.nips.cc/paper/1999/hash/96a93ba89a5b5c6c226e49b88973f46e-Abstract.html)** (Mason et al., NIPS 1999; proceedings 2000). Treats boosting as functional gradient descent on prediction or margin losses; introduces the DOOM II algorithm.
- **[Gradient Boosting Machine](https://doi.org/10.1214/aos/1013203451)** (Friedman, 2001). Builds an additive model by fitting base learners to negative loss gradients. The loss determines the target: residuals for squared error, with other objectives supporting classification and robust regression.
- **[Stochastic Gradient Boosting](https://www.sciencedirect.com/science/article/pii/S0167947301000652)** (Friedman, 2002). Fits each boosting update on a random subsample drawn without replacement. Adds row sampling to gradient boosting; distinct from stochastic gradient descent on model parameters.
- **[XGBoost](https://arxiv.org/abs/1603.02754)** (Chen & Guestrin, 2016). Combines regularized tree objectives, first- and second-order loss information, sparsity-aware split finding, and weighted quantile sketches with systems optimizations for large datasets.
- **[LightGBM](https://proceedings.neurips.cc/paper_files/paper/2017/hash/6449f44a102fde848669bdd9eb6b76fa-Abstract.html)** (Ke et al., 2017). Introduces gradient-based one-side sampling, retaining large-gradient rows while sampling others, and exclusive feature bundling, combining sparse features that rarely take nonzero values together.
- **[CatBoost](https://arxiv.org/abs/1706.09516)** (Prokhorenkova et al., 2017 preprint; NeurIPS 2018). Uses ordered boosting and permutation-based target statistics for categorical features to reduce prediction shift caused by reusing training targets.
- **[Out-of-Core GPU Gradient Boosting](https://arxiv.org/abs/2005.09148)** (Ou, 2020, preprint). Combines external-memory data access with gradient-based sampling in XGBoost to train on data exceeding GPU memory capacity while limiting the working set.

## Learning how to combine predictors

- **[Voting and Averaging](https://scikit-learn.org/stable/modules/ensemble.html#voting-classifier)** — Hard voting combines class labels; soft voting averages predicted probabilities. Regression ensembles commonly average numerical predictions. Weights can be fixed or estimated on separate validation data.
- **[Stacked Generalization](https://www.sciencedirect.com/science/article/pii/S0893608005800231)** (Wolpert, 1992). Trains a second-level model on base-model predictions for observations excluded from their fitting data. Learns how to combine predictors with different errors and biases.
- **[Super Learner](https://biostats.bepress.com/ucbbiostat/paper222/)** (van der Laan et al., 2007). Uses cross-validated risk to learn a combination of candidate prediction algorithms; theoretical guarantees depend on the loss and regularity conditions.
- **[Stacking predictive distributions](https://arxiv.org/abs/1704.02030)** — 2017/2018. Chooses mixture weights using held-out predictive scores, often via leave-one-out inference. Yao et al. target prediction when all candidate models may be wrong; weights are not posterior probabilities that models are true.
- **[Ensemble Selection](https://www.cs.cornell.edu/~alexn/papers/shotgun.icml04.revised.rev2.pdf)** (Caruana et al., 2004). Greedily selects models from a fitted library to optimize ensemble performance on validation data. Selection with replacement permits unequal model weights.

## Distributional prediction and statistical estimation

- **[Quantile Regression Forests](https://jmlr.org/papers/v7/meinshausen06a.html)** (Meinshausen, 2006). Uses forest-derived observation weights to estimate the conditional response distribution and its quantiles, rather than only the conditional mean.
- **[Generalized Random Forests](https://arxiv.org/abs/1610.01271)** (Athey et al., 2016 preprint; Annals of Statistics 2019). Learns adaptive neighborhoods for local moment equations, supporting quantiles and heterogeneous effects. Its inference guarantees require the paper's sampling and regularity assumptions.
- **[NGBoost](https://proceedings.mlr.press/v119/duan20a.html)** (Duan et al., 2020). Boosts parameters of a predictive distribution using natural gradients and a proper scoring rule. Produces distributional predictions instead of interpreting variation among ordinary trees as an interval.
- **[Jackknife+](https://arxiv.org/abs/1905.02928)** — 2019/2021. Combines leave-one-out residuals with test-point predictions to form intervals. Under exchangeability and symmetric fitting, the general coverage bound is 1−2α for nominal 1−α; near-nominal results need further stability assumptions.
- **[SWAG](https://arxiv.org/abs/1902.02476)** — 2019. Fits a Gaussian approximation to SGD iterates using their mean and a low-rank-plus-diagonal covariance; sampled weights yield averaged predictions and approximate Bayesian uncertainty.

## Neural ensembles

- **[Deep Ensembles](https://arxiv.org/abs/1612.01474)** (Lakshminarayanan et al., 2016 preprint; NeurIPS 2017). Averages predictive distributions from separately initialized and trained networks. The method uses proper scoring rules and studies predictive uncertainty in classification and regression.
- **[Snapshot Ensembles](https://arxiv.org/abs/1704.00109)** (Huang et al., 2017). Uses cyclic learning rates to collect several model checkpoints along one training trajectory, then averages their predictions. Multiple checkpoints still require evaluation at inference time.
- **[BatchEnsemble](https://arxiv.org/abs/2002.06715)** (Wen et al., 2020). Shares weight matrices across ensemble members and modulates them with member-specific rank-one factors. Reduces parameter storage while retaining separate predictions; members are not independently parameterized networks.
- **[TabM](https://proceedings.iclr.cc/paper_files/paper/2025/hash/c1ba41c694834aeef91ae161711d4939-Abstract-Conference.html)** (Gorishniy et al., 2024 preprint; ICLR 2025). Adapts BatchEnsemble to tabular multilayer perceptrons, sharing most weights across predictors and averaging their outputs. [Code](https://github.com/yandex-research/tabm).
- **[Fast Geometric Ensembling](https://arxiv.org/abs/1802.10026)** — 2018. Uses short learning-rate cycles late in training to collect nearby predictors for an ensemble, motivated by low-loss paths connecting neural-network solutions.

## Model merging and compression

- **[Knowledge Distillation](https://arxiv.org/abs/1503.02531)** (Hinton et al., 2015, preprint). Trains a student to match temperature-scaled teacher probabilities, including those from an ensemble. Retains information about relative class probabilities while reducing the models needed at inference.
- **[Model Soups](https://proceedings.mlr.press/v162/wortsman22a.html)** (Wortsman et al., 2022). Averages weights of compatible models fine-tuned from a shared pretrained initialization. Produces one model for inference; weight averaging is a different operation from averaging predictions.
- **[TIES-Merging](https://arxiv.org/abs/2306.01708)** — 2023. Merges fine-tuned models by trimming small parameter changes, resolving conflicting update signs and combining sign-aligned changes; targets interference between task-specific updates.

## Evaluation

- **[Uncertainty Under Dataset Shift](https://arxiv.org/abs/1906.02530)** (Ovadia et al., 2019). Compares uncertainty methods, including ensembles, across shifted classification datasets. Calibration on the original distribution does not establish calibration after a shift.
- **[Out-of-Bag Evaluation](https://scikit-learn.org/stable/modules/ensemble.html#bagging-meta-estimator)** — Estimates performance using predictions from bootstrap members that excluded each observation. Reusing these scores for extensive model selection still calls for a separate final evaluation.
- **[Stacking Leakage](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.StackingClassifier.html)** — Train the combiner on held-out or out-of-fold base predictions. The documented `prefit` mode risks overfitting when base models and the combiner use the same training observations.
- **Recommended comparisons.** Compare the best member, uniform averaging, and learned combination on identical splits. Report task loss, calibration, training cost, latency, memory, and ensemble size. [Uncertainty benchmark](https://arxiv.org/abs/1906.02530), [BatchEnsemble](https://arxiv.org/abs/2002.06715).

## Software

- **[scikit-learn](https://scikit-learn.org/stable/modules/ensemble.html)** — Bagging, random forests, Extra-Trees, AdaBoost, gradient boosting, voting, and stacking with estimator APIs. Its guide distinguishes histogram-based and conventional gradient boosting.
- **[XGBoost](https://xgboost.readthedocs.io/en/stable/)** — Tree boosting for classification, regression, and ranking, with CPU/GPU and external-memory workflows. [Code](https://github.com/dmlc/xgboost).
- **[LightGBM](https://lightgbm.readthedocs.io/en/stable/Features.html)** — Histogram-based tree boosting with leaf-wise growth, categorical splits, and distributed training. Algorithm and device settings determine which optimizations are used.
- **[CatBoost](https://catboost.ai/docs/en/)** — Gradient boosting with categorical-feature processing, CPU/GPU training, and prediction tools. [Categorical-feature documentation](https://catboost.ai/docs/en/features/categorical-features).
- **[ranger](https://cran.r-project.org/web/packages/ranger/)** — C++ random forests with an R interface, including classification, regression, probability, and survival forests.
- **[randomForest](https://cran.r-project.org/web/packages/randomForest/)** — R classification and regression forests. [Classification and Regression by randomForest](https://journal.r-project.org/articles/RN-2002-022/RN-2002-022.pdf) (Liaw & Wiener, 2002) explains fitting, out-of-bag estimates, and importance measures.
- **[grf](https://github.com/grf-labs/grf)** — R/C++ generalized forests for regression, quantiles, causal effects, and other statistical targets. [CRAN](https://cran.r-project.org/web/packages/grf/).
- **[SuperLearner](https://cran.r-project.org/web/packages/SuperLearner/)** — R implementation of cross-validated ensemble prediction, with wrappers for candidate learners and methods for estimating their combination.

## Related topics

- [Models](https://mlpapers.org/models/)
- [Neural Networks](https://mlpapers.org/neural-nets/)
- [Feature Selection](https://mlpapers.org/feature-selection/)
- [Optimization](https://mlpapers.org/optimization/)
