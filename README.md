---
title: "Ensemble Learning"
aliases: ["Ensemble methods", "Model ensembles"]
tags:
  - ensemble
  - supervised
  - boosting
---
# Ensemble learning
> In statistics and machine learning, ensemble methods use multiple learning algorithms to obtain better predictive performance than could be obtained from any of the constituent learning algorithms alone ([Wiki](https://en.wikipedia.org/wiki/Ensemble_learning))

### Boosting ([Wiki](https://en.wikipedia.org/wiki/Boosting_(machine_learning))
- [The Strength of Weak Learnability](https://www.cs.princeton.edu/~schapire/papers/strengthofweak.pdf) (1990) *Robert Schapire*
- [Arcing the edge](https://statistics.berkeley.edu/sites/default/files/tech-reports/486.pdf) (1997) *Leo Breiman*
- [A Short Introduction to Boosting](https://www.yorku.ca/gisweb/eats4400/boost.pdf) (1999) *Yoav Freund, Robert E. Schapire*
- [Boosting Algorithms as Gradient Descent](http://papers.nips.cc/paper/1766-boosting-algorithms-as-gradient-descent.pdf) (2000) *Llew Mason, Jonathan Baxter, Peter Bartlett, Marcus Frean*
- **AdaBoost** ([Wiki](https://en.wikipedia.org/wiki/AdaBoost))
  - [Boosting the margin: A new explanation for the effectiveness of voting methods](https://www.cc.gatech.edu/~isbell/tutorials/boostingmargins.pdf) (1998) *Robert E. Schapire, Yoav Freund, Peter Bartlett, Wee Sun Lee*

### Tree based ensembles
- **Random Forests** ([Wiki](https://en.wikipedia.org/wiki/Random_forest), [CRAN](https://cran.r-project.org/web/packages/randomForest/), [PyPI](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html#sklearn.ensemble.RandomForestClassifier))<br>
  - [Random Forests](https://link.springer.com/article/10.1023/A:1010933404324) (2001) *Leo Breiman*
  - [Overview of Random Forest Methodology and Practical Guidance with Emphasis on Computational Biology and Bioinformatic](https://epub.ub.uni-muenchen.de/13766/1/TR.pdf) (2012) *Anne-Laure Boulesteix, Silke Janitza, Jochen Kruppa, Inke R. Konig*
  - [Variable selection using random forests](https://hal.archives-ouvertes.fr/hal-00755489/file/PRLv4.pdf) (2010) *Robin Genuer, Jean-Michel Poggi, Christine Tuleau-Malot*
  - [Bias in random forest variable importance measures: Illustrations, sources and a solution](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC1796903/pdf/1471-2105-8-25.pdf) (2007) *Carolin Strobl, Anne-Laure Boulesteix, Achim Zeileis and Torsten Hothorn*
  - Package: ranger ([CRAN](https://cran.r-project.org/web/packages/ranger/))
  - Package: randomForest ([CRAN](https://cran.r-project.org/web/packages/randomForest/), [Paper](http://cogns.northwestern.edu/cbmg/LiawAndWiener2002.pdf)) (2002) *Andy Liaw, Matthew Wiener. Based on work by Leo Breiman and Adele Cutler*
  - **Generalized Random Forests** ([Code](https://github.com/grf-labs/grf), [CRAN](https://cran.r-project.org/web/packages/grf/))
    - [Generalized Random Forests](https://arxiv.org/abs/1610.01271) (2016) *Susan Athey, Julie Tibshirani, Stefan Wager*
- **Gradient Boosting, Stochastic Gradient Boosting** ([Wiki](https://en.wikipedia.org/wiki/Gradient_boosting))
  - [Greedy Function Approximation: A Gradient Boosting Machine](https://statweb.stanford.edu/~jhf/ftp/trebst.pdf) (1999) *Jerome H. Friedman*
  - [Stochastic Gradient Descent](https://statweb.stanford.edu/~jhf/ftp/stobst.pdf) (1999) *Jerome H. Friedman*
  - [XGBoost: A Scalable Tree Boosting System](https://www.kdd.org/kdd2016/papers/files/rfp0697-chenAemb.pdf) (2016) *Tianqi Chen, Carlos Guestrin*
  - [Out-of-Core GPU Gradient Boosting](https://arxiv.org/pdf/2005.09148.pdf) (2020) *Rong Ou*
  - Package: XGBoost ([Wiki](https://en.wikipedia.org/wiki/XGBoost), [Code](https://github.com/dmlc/xgboost))
  - Package: CatBoost
  - Package: LightGBM

## Related Topics
- [Models](https://mlpapers.org/models/)
- [Neural Networks](https://mlpapers.org/neural-nets/)
- [Feature Selection](https://mlpapers.org/feature-selection/)
- [Optimization](https://mlpapers.org/optimization/)
