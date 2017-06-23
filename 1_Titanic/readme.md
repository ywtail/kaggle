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
- 使用模型及提交后得分
	- LogisticRegression：0.76077
	- SVC：0.61722
	- RandomForestClassifier：0.73206
	- KNeighborsClassifier：0.62201
	- GaussianNB：0.73206
	- GradientBoostingClassifier：0.77033
如果直接点击不能查看，可点击[这里](https://ywtail.github.io/kaggle/1_Titanic/Titanic-3.html)查看运行过程。


