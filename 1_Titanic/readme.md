## 目录结构
- test.csv：测试数据
- train.csv：训练数据
- Titanic-1.ipynb：实现过程，只做了粗糙的缺失数据填充和调参，使用 RandomForestClassifier。如果直接点击不能查看，可点击[这里](https://ywtail.github.io/kaggle/1_Titanic/Titanic-1.html)查看运行过程。
- Titanic-2.ipynb：实现过程，从 Name 得到 Title、从 Parch、SibSp 得到家庭人数，随机（[average - std, average + std]）生成了缺失的年龄，使用 RandomForestClassifier。如果直接点击不能查看，可点击[这里](https://ywtail.github.io/kaggle/1_Titanic/Titanic-2.html)查看运行过程。
- submission_1.csv：Titanic-1.ipynb 产生的提交结果。分数 0.76555
- submission_2.csv：Titanic-2.ipynb 产生的提交结果。分数 0.76555