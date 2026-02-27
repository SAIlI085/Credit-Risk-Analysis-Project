# Credit Risk Modeling Project: PD, LGD, and EAD
本项目是一个基于 Python 的端到端信用风险建模项目。利用 LendingClub 真实数据集，构建了巴塞尔协议框架下的三大核心模型，用于量化预期损失 (Expected Loss)。

## 📌 项目概述 (Project Overview)
本项目旨在评估信用贷款的风险水平，主要包含以下三个模型：
* **PD (Probability of Default)**: 违约概率模型，评估借款人违约的可能性。
* **LGD (Loss Given Default)**: 违约损失率模型，估算违约发生后无法收回的资金比例。
* **EAD (Exposure at Default)**: 违约风险敞口模型，测算违约时的总风险余额。

## 📊 数据来源 (Data Source)
数据集采用 **LendingClub Loan Data (2007-2014)**。
* **数据链接**: [Kaggle - Lending Club Loan Data](https://www.kaggle.com/datasets/adarshsng/lending-club-loan-data-csv)
* *注：由于数据集文件较大，本项目仓库未包含原始数据，请前往上述链接下载。*

## 🚀 核心工作流 (Workflow)
### 1. 数据预处理与特征工程
* **数据清洗**: 处理缺失值、异常值以及不一致的日期格式。
* **WoE (Weight of Evidence)**: 对分类变量和连续变量进行分箱处理，将原始数据转化为线性相关的证据权重。
* **IV (Information Value)**: 通过信息值筛选对违约预测最有解释力的特征。

### 2. 模型开发
* **PD Model**: 使用 **Logistic Regression** 进行预测，并生成了标准的信用评分卡 (Scorecard)。
* **LGD & EAD Model**: 采用双阶段建模思想（先判断是否为 0 损失，再预测损失比例），结合线性回归进行估算。
* **EL (Expected Loss)**: 综合三大模型结果，计算贷款组合的预期损失：
  $$EL = PD \times LGD \times EAD$$

### 3. 模型评估
* 使用 **ROC-AUC/ Gini系数 / K-S统计量** 评估 PD 模型的区分能力。
* 利用 **Population Stability Index (PSI)** 监控模型稳定性。

## 🛠️ 技术栈 (Tech Stack)
* **Language**: Python 3.x
* **Libraries**: Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Pickle
* **Tools**: Jupyter Notebook, VS Code

## 📁 文件说明 (File Descriptions)
* `PD model.ipynb`: 违约概率模型的训练与评估脚本。
* `LGD and EAD Models.ipynb`: 损失率与风险敞口模型的建模过程。
* `Preparation.ipynb`: 数据预处理与特征工程细节。
* `.sav files`: 已训练完成的模型序列化文件，可直接用于预测。

