# Ensemble Learning

## Overview

- **Ensemble Methods in Machine Learning** - Reviews voting, bagging, boosting, and Bayesian averaging; explains how statistical, computational, and representational differences between learners can make their combination useful. [Dietterich 2000](<https://www.cs.princeton.edu/courses/archive/spring10/cos424/papers/Dietterich-2000.pdf> "Ensemble Methods in Machine Learning; Multiple Classifier Systems").

## Bagging and randomized trees

- **Bagging Predictors** - Fits predictors on bootstrap samples and aggregates their outputs. Particularly useful for unstable learners whose predictions change substantially when the training data change. [Breiman 1996](<https://link.springer.com/article/10.1007/BF00058655> "Bagging predictors; Mach. Learn.").
- **Random Subspaces** - Builds decision trees on randomly selected feature subsets and combines their predictions. Feature sampling occurs per tree; Breiman's random forest also samples candidate features at individual splits. [Tin Kam Ho 1998](<https://doi.org/10.1109/34.709601> "The random subspace method for constructing decision forests; TPAMI").
- **Random Forests** - Combines randomized trees; the widely used construction couples bootstrap sampling with random feature subsets at each split. Individual tree strength and error correlation both affect ensemble performance. [Breiman 2001](<https://link.springer.com/article/10.1023/A:1010933404324> "Random Forests; Mach. Learn.").
- **Extremely Randomized Trees** - Randomizes candidate features and split thresholds, then selects among those candidates. The original Extra-Trees construction uses the full training sample rather than bootstrap replicates. [Geurts et al. 2006](<https://link.springer.com/article/10.1007/s10994-006-6226-1> "Extremely randomized trees; Mach. Learn.").
- **Random Forest Methodology and Practical Guidance** - Reviews tuning, implementations, applications, and pitfalls in bioinformatics, including biases in variable-importance measures. [Boulesteix et al. 2012](<https://epub.ub.uni-muenchen.de/13766/1/TR.pdf> "Overview of random forest methodology and practical guidance with emphasis on computational biology and bioinformatics; WIREs Data Min &amp; Knowl").
- **Variable Selection Using Random Forests** - Uses importance rankings and nested models to select variables; distinguishes identifying relevant variables from choosing a smaller set for prediction. [Genuer et al. 2010](<https://hal.science/hal-00755489/document> "Variable selection using random forests; Pattern Recognit. Lett.").
- **Bias in Random Forest Variable Importance** - Shows selection and importance biases with mixed predictor types or category counts; investigates conditional inference trees and subsampling as remedies. [Strobl et al. 2007](<https://link.springer.com/article/10.1186/1471-2105-8-25> "Bias in random forest variable importance measures: Illustrations, sources and a solution; BMC Bioinformatics").

## Boosting foundations

- **The Strength of Weak Learnability** - Proves equivalence of weak and strong learnability in the distribution-free PAC model. The result assumes a weak learner for the required distributions, not merely one classifier above chance on one dataset. [Schapire 1990](<https://link.springer.com/article/10.1007/BF00116037> "The strength of weak learnability; Mach. Learn.").
- **AdaBoost** - Sequentially reweights training examples and combines weak classifiers with error-dependent weights. Misclassified examples gain weight, directing later learners toward current errors. [Freund and Schapire 1997](<https://www.schapire.net/papers/FreundSc95.pdf> "A Decision-Theoretic Generalization of On-Line Learning and an Application to Boosting; JCSS").
- **Boosting the Margin** - Relates voting-classifier generalization bounds to the margin distribution, helping explain continued improvement after training error reaches zero. [Schapire et al. 1998](<https://www.schapire.net/papers/SchapireFrBaLe98.pdf> "Boosting the margin: a new explanation for the effectiveness of voting methods; Ann. Statist.").
- **Arcing the Edge** - Formulates adaptive reweighting as optimization of functions of the edge; develops an alternative perspective on the behavior of voting classifiers. [Breiman 1997](<https://statistics.berkeley.edu/sites/default/files/tech-reports/486.pdf> "Arcing the Edge; technical report").
- **A Short Introduction to Boosting** - Compact overview of AdaBoost, training-error bounds, margins, and connections with support-vector machines. [Freund and Schapire 1999](<https://www.yorku.ca/gisweb/eats4400/boost.pdf> "A Short Introduction to Boosting; J. Japanese Soc. AI").

## Gradient boosting

- **Boosting Algorithms as Gradient Descent** - Treats boosting as functional gradient descent on prediction or margin losses; introduces the DOOM II algorithm. [Mason et al. 1999](<https://papers.nips.cc/paper/1999/hash/96a93ba89a5b5c6c226e49b88973f46e-Abstract.html> "Boosting Algorithms as Gradient Descent; NeurIPS").
- **Gradient Boosting Machine** - Builds an additive model by fitting base learners to negative loss gradients. The loss determines the target: residuals for squared error, with other objectives supporting classification and robust regression. [Friedman 2001](<https://doi.org/10.1214/aos/1013203451> "Greedy function approximation: A gradient boosting machine.; Ann. Statist.").
- **Stochastic Gradient Boosting** - Fits each boosting update on a random subsample drawn without replacement. Adds row sampling to gradient boosting; distinct from stochastic gradient descent on model parameters. [Friedman 2002](<https://www.sciencedirect.com/science/article/pii/S0167947301000652> "Stochastic gradient boosting; Comput. Stat. Data Anal.").
- **XGBoost** - Combines regularized tree objectives, first- and second-order loss information, sparsity-aware split finding, and weighted quantile sketches with systems optimizations for large datasets. [Chen and Guestrin 2016](<https://arxiv.org/abs/1603.02754> "XGBoost: A Scalable Tree Boosting System; KDD").
- **LightGBM** - Introduces gradient-based one-side sampling, retaining large-gradient rows while sampling others, and exclusive feature bundling, combining sparse features that rarely take nonzero values together. [Ke et al. 2017](<https://proceedings.neurips.cc/paper_files/paper/2017/hash/6449f44a102fde848669bdd9eb6b76fa-Abstract.html> "LightGBM: A Highly Efficient Gradient Boosting Decision Tree; NeurIPS").
- **CatBoost** - Uses ordered boosting and permutation-based target statistics for categorical features to reduce prediction shift caused by reusing training targets. [Prokhorenkova et al. 2018](<https://arxiv.org/abs/1706.09516> "CatBoost: unbiased boosting with categorical features; NeurIPS").
- **Out-of-Core GPU Gradient Boosting** - Combines external-memory data access with gradient-based sampling in XGBoost to train on data exceeding GPU memory capacity while limiting the working set. [Ou 2020](<https://arxiv.org/abs/2005.09148> "Out-of-Core GPU Gradient Boosting; arXiv").

## Learning how to combine predictors

- **Voting and Averaging** - Hard voting combines class labels; soft voting averages predicted probabilities. Regression ensembles commonly average numerical predictions. Weights can be fixed or estimated on separate validation data. [docs](<https://scikit-learn.org/stable/modules/ensemble.html#voting-classifier>).
- **Stacked Generalization** - Trains a second-level model on base-model predictions for observations excluded from their fitting data. Learns how to combine predictors with different errors and biases. [Wolpert 1992](<https://www.sciencedirect.com/science/article/pii/S0893608005800231> "Stacked generalization; Neural Networks").
- **Super Learner** - Uses cross-validated risk to learn a combination of candidate prediction algorithms; theoretical guarantees depend on the loss and regularity conditions. [van der Laan et al. 2007](<https://biostats.bepress.com/ucbbiostat/paper222/> "Super Learner; Stat. Appl. Genet. Mol. Biol.").
- **Stacking predictive distributions** - Chooses mixture weights using held-out predictive scores, often via leave-one-out inference. Yao et al. target prediction when all candidate models may be wrong; weights are not posterior probabilities that models are true. [Yao et al. 2018](<https://arxiv.org/abs/1704.02030> "Using stacking to average Bayesian predictive distributions; Bayesian Anal.").
- **Ensemble Selection** - Greedily selects models from a fitted library to optimize ensemble performance on validation data. Selection with replacement permits unequal model weights. [Caruana et al. 2004](<https://www.cs.cornell.edu/~alexn/papers/shotgun.icml04.revised.rev2.pdf> "Ensemble selection from libraries of models; ICML").

## Distributional prediction and statistical estimation

- **Quantile Regression Forests** - Uses forest-derived observation weights to estimate the conditional response distribution and its quantiles, rather than only the conditional mean. [Meinshausen 2006](<https://jmlr.org/papers/v7/meinshausen06a.html> "Quantile Regression Forests; JMLR").
- **Generalized Random Forests** - Learns adaptive neighborhoods for local moment equations, supporting quantiles and heterogeneous effects. Its inference guarantees require the paper's sampling and regularity assumptions. [Athey et al. 2016](<https://arxiv.org/abs/1610.01271> "Generalized Random Forests; arXiv").
- **NGBoost** - Boosts parameters of a predictive distribution using natural gradients and a proper scoring rule. Produces distributional predictions instead of interpreting variation among ordinary trees as an interval. [Duan et al. 2020](<https://proceedings.mlr.press/v119/duan20a.html> "NGBoost: Natural Gradient Boosting for Probabilistic Prediction; ICML").
- **Jackknife+** - Combines leave-one-out residuals with test-point predictions to form intervals. Under exchangeability and symmetric fitting, the general coverage bound is 1−2α for nominal 1−α; near-nominal results need further stability assumptions. [Barber et al. 2019](<https://arxiv.org/abs/1905.02928> "Predictive inference with the jackknife+; arXiv").
- **SWAG** - Fits a Gaussian approximation to SGD iterates using their mean and a low-rank-plus-diagonal covariance; sampled weights yield averaged predictions and approximate Bayesian uncertainty. [Maddox et al. 2019](<https://arxiv.org/abs/1902.02476> "A Simple Baseline for Bayesian Uncertainty in Deep Learning; NeurIPS").

## Neural ensembles

- **Deep Ensembles** - Averages predictive distributions from separately initialized and trained networks. The method uses proper scoring rules and studies predictive uncertainty in classification and regression. [Lakshminarayanan et al. 2017](<https://arxiv.org/abs/1612.01474> "Simple and Scalable Predictive Uncertainty Estimation using Deep Ensembles; NeurIPS").
- **Snapshot Ensembles** - Uses cyclic learning rates to collect several model checkpoints along one training trajectory, then averages their predictions. Multiple checkpoints still require evaluation at inference time. [Huang et al. 2017](<https://arxiv.org/abs/1704.00109> "Snapshot Ensembles: Train 1, get M for free; arXiv").
- **BatchEnsemble** - Shares weight matrices across ensemble members and modulates them with member-specific rank-one factors. Reduces parameter storage while retaining separate predictions; members are not independently parameterized networks. [Wen et al. 2020](<https://arxiv.org/abs/2002.06715> "BatchEnsemble: An Alternative Approach to Efficient Ensemble and Lifelong Learning; ICLR").
- **TabM** - Adapts BatchEnsemble to tabular multilayer perceptrons, sharing most weights across predictors and averaging their outputs. [Gorishniy et al. 2025](<https://proceedings.iclr.cc/paper_files/paper/2025/hash/c1ba41c694834aeef91ae161711d4939-Abstract-Conference.html> "TabM: Advancing tabular deep learning with parameter-efficient ensembling; ICLR"); [code](<https://github.com/yandex-research/tabm>).
- **Fast Geometric Ensembling** - Uses short learning-rate cycles late in training to collect nearby predictors for an ensemble, motivated by low-loss paths connecting neural-network solutions. [Garipov et al. 2018](<https://arxiv.org/abs/1802.10026> "Loss Surfaces, Mode Connectivity, and Fast Ensembling of DNNs; NeurIPS").

## Model merging and compression

- **Knowledge Distillation** - Trains a student to match temperature-scaled teacher probabilities, including those from an ensemble. Retains information about relative class probabilities while reducing the models needed at inference. [Hinton et al. 2014](<https://arxiv.org/abs/1503.02531> "Distilling the Knowledge in a Neural Network; NeurIPS DL Workshop").
- **Model Soups** - Averages weights of compatible models fine-tuned from a shared pretrained initialization. Produces one model for inference; weight averaging is a different operation from averaging predictions. [Wortsman et al. 2022](<https://proceedings.mlr.press/v162/wortsman22a.html> "Model soups: averaging weights of multiple fine-tuned models improves accuracy without increasing inference time; ICML").
- **TIES-Merging** - Merges fine-tuned models by trimming small parameter changes, resolving conflicting update signs and combining sign-aligned changes; targets interference between task-specific updates. [Yadav et al. 2023](<https://arxiv.org/abs/2306.01708> "TIES-Merging: Resolving Interference When Merging Models; NeurIPS").

## Evaluation

- **Uncertainty Under Dataset Shift** - Compares uncertainty methods, including ensembles, across shifted classification datasets. Calibration on the original distribution does not establish calibration after a shift. [Ovadia et al. 2019](<https://arxiv.org/abs/1906.02530> "Can You Trust Your Model&#x27;s Uncertainty? Evaluating Predictive Uncertainty Under Dataset Shift; NeurIPS").
- **Out-of-Bag Evaluation** - Estimates performance using predictions from bootstrap members that excluded each observation. Reusing these scores for extensive model selection still calls for a separate final evaluation. [Breiman 2001](<https://doi.org/10.1023/A:1010933404324> "Random Forests; Mach. Learn."); [docs](<https://scikit-learn.org/stable/modules/ensemble.html#bagging-meta-estimator>).
- **Stacking Leakage** - Train the combiner on held-out or out-of-fold base predictions. The documented `prefit` mode risks overfitting when base models and the combiner use the same training observations. [docs](<https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.StackingClassifier.html>).
- **Recommended comparisons** - Compare the best member, uniform averaging, and learned combination on identical splits. Report task loss, calibration, training cost, latency, memory, and ensemble size. [Ovadia et al. 2019](<https://arxiv.org/abs/1906.02530> "Can You Trust Your Model&#x27;s Uncertainty? Evaluating Predictive Uncertainty Under Dataset Shift; NeurIPS"), [Wen et al. 2020](<https://arxiv.org/abs/2002.06715> "BatchEnsemble: An Alternative Approach to Efficient Ensemble and Lifelong Learning; ICLR").

## Software

- **scikit-learn** - Bagging, random forests, Extra-Trees, AdaBoost, gradient boosting, voting, and stacking with estimator APIs. Its guide distinguishes histogram-based and conventional gradient boosting. [docs](<https://scikit-learn.org/stable/modules/ensemble.html>).
- **XGBoost** - Tree boosting for classification, regression, and ranking, with CPU/GPU and external-memory workflows. [code](<https://github.com/dmlc/xgboost>), [docs](<https://xgboost.readthedocs.io/en/stable/>).
- **LightGBM** - Histogram-based tree boosting with leaf-wise growth, categorical splits, and distributed training. Algorithm and device settings determine which optimizations are used. [docs](<https://lightgbm.readthedocs.io/en/stable/Features.html>).
- **CatBoost** - Gradient boosting with categorical-feature processing, CPU/GPU training, and prediction tools. [docs](<https://catboost.ai/docs/en/features/categorical-features>), [docs](<https://catboost.ai/docs/en/>).
- **ranger** - C++ random forests with an R interface, including classification, regression, probability, and survival forests. [code](<https://cran.r-project.org/web/packages/ranger/>).
- **randomForest** - R classification and regression forests. Classification and Regression by randomForest explains fitting, out-of-bag estimates, and importance measures. [Liaw and Wiener 2002](<https://journal.r-project.org/articles/RN-2002-022/RN-2002-022.pdf> "Classification and Regression by randomForest; R News"); [code](<https://cran.r-project.org/web/packages/randomForest/>).
- **grf** - R/C++ generalized forests for regression, quantiles, causal effects, and other statistical targets. [code](<https://cran.r-project.org/web/packages/grf/>), [code](<https://github.com/grf-labs/grf>).
- **SuperLearner** - R implementation of cross-validated ensemble prediction, with wrappers for candidate learners and methods for estimating their combination. [code](<https://cran.r-project.org/web/packages/SuperLearner/>).

## Related topics

- [Models](https://mlpapers.org/models/)
- [Neural Networks](https://mlpapers.org/neural-nets/)
- [Feature Selection](https://mlpapers.org/feature-selection/)
- [Optimization](https://mlpapers.org/optimization/)
