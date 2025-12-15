# Learn Data Analysis

Welcome to our curated collection of resources for learning data science, statistics, machine learning, deep learning, programming, automation, and modern data platforms.

## 🧭 Suggested Learning Path

If you’re brand new, a simple (and common) order that works well:

1. **SQL fundamentals** (selects, joins, aggregations, window functions)
2. **One general-purpose language**: Python *or* R (data wrangling + plotting)
3. **Core stats/probability** (distributions, uncertainty, hypothesis testing, Bayesian basics)
4. **Real-world workflows**: notebooks, Git, reproducibility, documentation
5. **Modern analytics stacks**: a warehouse/lakehouse + transformation layer (Snowflake/Databricks + dbt)
6. **ML / deep learning** (only after you can clean, join, and reason about data)

## 📚 Table of Contents

- [📊 Data Science and Statistics](#-data-science-and-statistics)
- [🤖 Machine Learning and Deep Learning](#-machine-learning-and-deep-learning)
- [💻 Programming and Automation](#-programming-and-automation)
- [🏗️ Data Engineering and Analytics Engineering](#-data-engineering-and-analytics-engineering)
- [📁 Data Sources](#-data-sources)
- [🛠️ Tools and Environments](#-tools-and-environments)
- [🧩 Practice and Projects](#-practice-and-projects)
- [📚 Reference Materials](#-reference-materials)
- [Acknowledgements](#acknowledgements)

## 📊 Data Science and Statistics

### Foundational Texts
- [R for Data Science (2e)](https://r4ds.hadley.nz/) by Hadley Wickham, Mine Çetinkaya-Rundel, and Garrett Grolemund
- [The Elements of Statistical Learning](https://hastie.su.domains/Papers/ESLII.pdf) by Trevor Hastie, Robert Tibshirani, and Jerome Friedman
- [Introduction to Probability](https://drive.google.com/file/d/1VmkAAGOYCTORq1wxSQqy255qLJjTNvBI/edit) by Joseph K. Blitzstein and Jessica Hwang
- [Think Stats: Exploratory Data Analysis in Python](https://greenteapress.com/thinkstats2/thinkstats2.pdf) by Allen B. Downey
- [An Introduction to Statistical Learning](https://www.statlearning.com/) by Gareth James, Daniela Witten, Trevor Hastie, and Robert Tibshirani

### Biostatistics and Epidemiology
- [OpenIntro Statistics](https://www.openintro.org/book/os/) — free introductory statistics textbook
- [Fundamentals of Biostatistics](https://www.cengage.com/c/fundamentals-of-biostatistics-8e-rosner/) by Bernard Rosner
- [Modern Epidemiology](https://shop.lww.com/Modern-Epidemiology/p/9781451193282) by Kenneth Rothman, Sander Greenland, and Timothy Lash

### Bayesian Statistics
- [Statistical Rethinking](https://xcelab.net/rm/statistical-rethinking/) by Richard McElreath (with accompanying [YouTube lectures](https://www.youtube.com/playlist?list=PLDcUM9US4XdPz-KxHM4XHt7uUVGWWVSus))
- [Bayesian Data Analysis (3e)](http://www.stat.columbia.edu/~gelman/book/) by Andrew Gelman et al.
- [Doing Bayesian Data Analysis (2e)](https://shop.elsevier.com/books/doing-bayesian-data-analysis/kruschke/978-0-12-405888-0) by John Kruschke
- [Bayesian Computation with R (2e)](https://link.springer.com/book/10.1007/978-0-387-92298-0) by Jim Albert
- [Reasoning with Data](https://www.guilford.com/books/Reasoning-with-Data/Jeffrey-Stanton/9781462530267) by Jeffrey M. Stanton (traditional + Bayesian inference in R)
- [Think Bayes](https://greenteapress.com/wp/think-bayes/) by Allen B. Downey
- [Probabilistic Programming & Bayesian Methods for Hackers](https://camdavidsonpilon.github.io/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/)

## 🤖 Machine Learning and Deep Learning

### Core Texts
- [Deep Learning with Python (2e)](https://www.manning.com/books/deep-learning-with-python-second-edition) by François Chollet
- [Machine Learning Mastery Books](https://github.com/jbrownlee/Books) by Jason Brownlee, PhD
- [Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow](https://www.oreilly.com/library/view/hands-on-machine-learning/9781492032632/) by Aurélien Géron
- [Pattern Recognition and Machine Learning](https://www.microsoft.com/en-us/research/uploads/prod/2006/01/Bishop-Pattern-Recognition-and-Machine-Learning-2006.pdf) by Christopher Bishop

### Online Courses
- [fast.ai Practical Deep Learning](https://course.fast.ai/) — free, practical approach to deep learning
- [Stanford CS229: Machine Learning](https://cs229.stanford.edu/) — Andrew Ng's foundational ML course
- [Stanford CS231n: CNNs for Visual Recognition](http://cs231n.stanford.edu/)
- [MIT 6.S191: Introduction to Deep Learning](http://introtodeeplearning.com/)

### NLP and LLMs
- [Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/) by Dan Jurafsky and James Martin
- [Hugging Face NLP Course](https://huggingface.co/learn/nlp-course/)
- [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) by Jay Alammar

## 💻 Programming and Automation

### Python
- [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/) by Al Sweigart
- [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/) by Jake VanderPlas
- [Effective Python](https://effectivepython.com/) by Brett Slatkin

### R
- [Advanced R](https://adv-r.hadley.nz/) by Hadley Wickham
- [R Packages](https://r-pkgs.org/) by Hadley Wickham and Jenny Bryan
- [ggplot2: Elegant Graphics for Data Analysis](https://ggplot2-book.org/)

### SQL
- [SQL for Data Scientists](https://sqlfordatascientists.com/) by Renee Teate
- [Mode SQL Tutorial](https://mode.com/sql-tutorial/)

### Quick References
- [Learn X in Y Minutes](https://learnxinyminutes.com/) — quick syntax references for many languages

## 🏗️ Data Engineering and Analytics Engineering

### dbt (Analytics Engineering)
- [dbt Learn: Course Catalog](https://learn.getdbt.com/catalog) — free, structured courses and walkthroughs
- [dbt Developer Hub (official docs)](https://docs.getdbt.com/) — the canonical reference
- [dbt Quickstarts](https://docs.getdbt.com/docs/get-started-dbt) — step-by-step getting started guides across platforms
- [dbt Core installation overview](https://docs.getdbt.com/docs/core/installation-overview) — local CLI-based setup
- [dbt Best Practices](https://docs.getdbt.com/best-practices) — project structure, style, testing, and deployment patterns
- [dbt Hub](https://hub.getdbt.com/) — community packages (e.g., `dbt_utils`, `codegen`)

### Databricks (Lakehouse / Spark)
- [Databricks documentation](https://www.databricks.com/databricks-documentation) — pick your cloud (AWS/Azure/GCP) and browse the docs
- [Get started tutorials on Databricks](https://docs.databricks.com/aws/en/getting-started/) — guided “first notebook” style tutorials
- [Databricks Free Edition](https://www.databricks.com/learn/free-edition) — no-cost environment for learning and experimentation
- [Databricks Training & Certification](https://www.databricks.com/learn/training/home) — role-based learning paths and courses

### Snowflake (Cloud Data Warehouse / AI Data Cloud)
- [Snowflake Getting Started](https://docs.snowflake.com/en/user-guide-getting-started) — official beginner docs + tutorials
- [Snowflake in 20 Minutes](https://docs.snowflake.com/en/user-guide/tutorials/snowflake-in-20minutes) — hands-on “hello world”
- [Snowflake Tutorials](https://docs.snowflake.com/en/learn-tutorials) — curated tutorials inside the docs
- [Snowflake Developer Guides](https://www.snowflake.com/en/developers/guides/) — hands-on guides and reference architectures
- [Snowflake Trial Signup](https://signup.snowflake.com/) — free trial account
- [Snowflake Education & Training](https://learn.snowflake.com/en/) — on-demand + instructor-led training

## 📁 Data Sources

### General
- [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/)
- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [data.world Health Datasets](https://data.world/datasets/health)
- [Google Dataset Search](https://datasetsearch.research.google.com/)
- [Awesome Public Datasets](https://github.com/awesomedata/awesome-public-datasets)

### Healthcare and Biomedical
- [New York Academy of Medicine Data Sets](https://www.nyam.org/library/collections-and-resources/data-sets/)
- [National Cancer Institute SEER](https://seer.cancer.gov/)
- [CMS Medicare Data](https://data.cms.gov/)
- [MIMIC Critical Care Database](https://mimic.mit.edu/)
- [PhysioNet](https://physionet.org/)

### Government and Census
- [Data.gov](https://data.gov/)
- [US Census Bureau](https://data.census.gov/)
- [CDC WONDER](https://wonder.cdc.gov/)
- [WHO Global Health Observatory](https://www.who.int/data/gho)

## 🛠️ Tools and Environments

### Development Environments
- [RStudio](https://posit.co/download/rstudio-desktop/)
- [JupyterLab](https://jupyter.org/)
- [VS Code](https://code.visualstudio.com/) with Python/R extensions
- [Google Colab](https://colab.research.google.com/) — free cloud notebooks with GPU

### Data Platforms
- [Databricks](https://www.databricks.com/) — notebooks + Spark + lakehouse tooling
- [Snowflake](https://www.snowflake.com/) — cloud data platform / warehouse
- [dbt](https://www.getdbt.com/) — transformation + analytics engineering workflow

### Version Control
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Skills](https://skills.github.com/)
- [Oh My Git!](https://ohmygit.org/) — learn Git through a game

### Visualization
- [From Data to Viz](https://www.data-to-viz.com/) — decision tree for chart selection
- [Datawrapper](https://www.datawrapper.de/)
- [Observable](https://observablehq.com/)

## 🧩 Practice and Projects

### Coding / Problem Solving
- [Advent of Code](https://adventofcode.com/) — seasonal programming puzzles (great for building fluency and persistence)
- [LeetCode](https://leetcode.com/) — practice problems (includes strong SQL + data structures tracks)

### Project Ideas (simple but realistic)
- **SQL analytics**: pick a public dataset and write a “metrics pack” (daily active users, retention, cohorts, top N)
- **dbt mini-project**: load CSVs into a warehouse/lakehouse, then build a small dbt project with staging → intermediate → marts + tests + docs
- **Databricks / Snowflake**: reproduce an official “getting started” tutorial, then extend it with your own dataset and a dashboard

## 📚 Reference Materials

See the [`references/`](references/) directory for:
- **[Common Statistical Tests](references/List_of_Common_Statistical_Tests.md)** — comprehensive guide to choosing and interpreting statistical tests in epidemiology and applied statistics

## Acknowledgements

A special thank you to [Golapri Rose Ila Dasgupta, PhD, MPH, MHI, MS](https://github.com/pritikadasgupta) (they/them/he/him/ze/zir) for compiling these resources.

---

*Contributions welcome! Please feel free to open a PR or issue to suggest additional resources.*
