## 目录结构
- test.csv：测试数据
- train.csv：训练数据
- Titanic-XXX.ipynb：实现过程
- submission_1.csv：Titanic-1.ipynb `RandomForestClassifier` 产生的提交结果。分数 0.76555
- submission_2.csv：Titanic-2.ipynb `RandomForestClassifier` 产生的提交结果。分数 0.76555
- submission_3_1_logreg.csv：Titanic-3.ipynb `LogisticRegression`：0.76077
- submission_3_2_svc.csv：Titanic-3.ipynb `SVC`：0.61722
- submission_3_3_rdforest.csv：Titanic-3.ipynb `RandomForestClassifier`：0.73206
- submission_3_4_knn.csv：Titanic-3.ipynb `KNeighborsClassifier`：0.62201
- submission_3_5_gaussian.csv：Titanic-3.ipynb `GaussianNB`：0.73206
- submission_3_6_gbdt.csv：Titanic-3.ipynb `GradientBoostingClassifier`：0.77033
- submission_4_1.csv：Titanic-4.ipynb`LogisticRegression`：0.76555
- submission_4_2.csv：Titanic-4.ipynb`SVC`：0.77990
- submission_4_3.csv：Titanic-4.ipynb`LinearSVC`：0.76555
- submission_4_4.csv：Titanic-4.ipynb`KNeighborsClassifier`：0.77033
- submission_4_5.csv：Titanic-4.ipynb`GaussianNB`：0.74163
- submission_4_6.csv：Titanic-4.ipynb`Perceptron`：0.75598
- submission_4_7.csv：Titanic-4.ipynb`SGDClassifier`：0.79426
- submission_4_8.csv：Titanic-4.ipynb`DecisionTreeClassifier`：0.78469
- submission_4_9.csv：Titanic-4.ipynb`RandomForestClassifier`：0.77990
- submission_4_10.csv：Titanic-4.ipynb`GradientBoostingClassifier`：0.79426

## Titanic-1.ipynb
只做了粗糙的缺失数据填充和调参，使用 RandomForestClassifier。

如果直接点击不能查看，可点击[这里](https://ywtail.github.io/kaggle/1_Titanic/Titanic-1.html)查看运行过程。

## Titanic-2.ipynb
参考：https://www.kaggle.com/mrisdal/exploring-survival-on-the-titanic

从 Name 得到 Title、从 Parch、SibSp 得到家庭人数，随机（[average - std, average + std]）生成了缺失的年龄，使用 RandomForestClassifier。

如果直接点击不能查看，可点击[这里](https://ywtail.github.io/kaggle/1_Titanic/Titanic-2.html)查看运行过程。

## Titanic-3.ipynb
参考：https://www.kaggle.com/omarelgabry/a-journey-through-titanic

**主要思路是：（get_dummies）删除 Survived 概率低的项**

大体流程如下：
- 删除不需要的项：PassengerId(训练数据中的)，Name，Ticket
- 处理缺失数据：Embarked，Fare，Age，Cabin（缺失太多直接删除）
- 特征工程：Family，Person，Pclass

使用模型及提交后得分：
- LogisticRegression：0.76077
- SVC：0.61722
- RandomForestClassifier：0.73206
- KNeighborsClassifier：0.62201
- GaussianNB：0.73206
- GradientBoostingClassifier：0.77033

如果直接点击不能查看，可点击[这里](https://ywtail.github.io/kaggle/1_Titanic/Titanic-3.html)查看运行过程。

## Titanic-4.ipynb
参考：https://www.kaggle.com/startupsci/titanic-data-science-solutions

Age的缺失值填充参考了 Pclass 和 Sex；Age 和 Fare 分段。

使用模型及提交后得分
- `LogisticRegression`：0.76555
- `SVC`：0.77990
- `LinearSVC`：0.76555
- `KNeighborsClassifier`：0.77033
- `GaussianNB`：0.74163
- `Perceptron`：0.75598
- `SGDClassifier`：0.79426
- `DecisionTreeClassifier`：0.78469
- `RandomForestClassifier`：0.77990
- `GradientBoostingClassifier`：0.79426

如果直接点击不能查看，可点击[这里](https://ywtail.github.io/kaggle/1_Titanic/Titanic-4.html)查看运行过程。