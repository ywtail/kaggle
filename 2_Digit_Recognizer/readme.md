## 目录结构
- test.csv：测试数据
- train.csv：训练数据
- XXXX.ipynb：实现过程
- submission_X.csv 上面XXXX.ipynb产生的提交文件

## 1-SVC【0.90929】.ipynb 实现过程
探索数据，流程如下：
- 取5000个样本进行训练。
- 特征缩放：大于1的特征取1。
- 使用SVC，提交得分 0.90929

## 2-softmax【0.90971】.ipynb
y=softmax(xW+b)（特征缩放：特征/255）
代价函数：交叉熵
最小化代价函数：梯度下降 GradientDescentOptimizer，学习率0.01

详细分析见：[TensorFlow (2): Softmax Regression识别手写数字](http://ywtail.github.io/2017/06/02/TensorFlow-2-Softmax-Regression%E8%AF%86%E5%88%AB%E6%89%8B%E5%86%99%E6%95%B0%E5%AD%97/)

## 3-多层感知机 【0.96486】.ipynb
Softmax Regression 和传统意义上的神经网络的最大区别是没有隐含层。
这里实现的多层感知机实际上是在 Softmax Regression 的基础上加上一个隐含层。
结构如下：
- x=tf.placeholder(tf.float32,[None,784])
- hidden1=tf.nn.relu(tf.matmul(x,W1)+b1)
- hidden1_drop=tf.nn.dropout(hidden1,keep_prob)
- y=tf.nn.softmax(tf.matmul(hidden1_drop,W2)+b2)
- 代价函数：交叉熵
- 最小化代价函数：AdagradOptimizer，学习率0.01

详细分析见：[TensorFlow (3): 多层感知机识别手写数字](http://ywtail.github.io/2017/06/03/TensorFlow-3-%E5%A4%9A%E5%B1%82%E6%84%9F%E7%9F%A5%E6%9C%BA%E8%AF%86%E5%88%AB%E6%89%8B%E5%86%99%E6%95%B0%E5%AD%97/)

## 4-CNN-Tensorflow【0.98957】.ipynb
结构如下：
- x_image=tf.reshape(x,[-1,28,28,1])
- h_conv1=tf.nn.relu(conv2d(x_image,W_conv1)+b_conv1)
- h_pool1=max_pool_2x2(h_conv1)
- h_conv2=tf.nn.relu(conv2d(h_pool1,W_conv2)+b_conv2)
- h_pool2=max_pool_2x2(h_conv2)
- h_pool2_flat=tf.reshape(h_pool2,[-1,7*7*64])
- h_fc1=tf.nn.relu(tf.matmul(h_pool2_flat,W_fc1)+b_fc1)
- h_fc1_drop=tf.nn.dropout(h_fc1,keep_prob)
- y_conv=tf.nn.softmax(tf.matmul(h_fc1_drop,W_fc2)+b_fc2)
- 代价函数：交叉熵
- 最小化代价函数：AdamOptimizer，学习率1e-4

详细分析见：[TensorFlow (4): 卷积神经网络识别手写数字](http://ywtail.github.io/2017/06/05/TensorFlow-4-%E5%8D%B7%E7%A7%AF%E7%A5%9E%E7%BB%8F%E7%BD%91%E7%BB%9C%E8%AF%86%E5%88%AB%E6%89%8B%E5%86%99%E6%95%B0%E5%AD%97/)

## 5-CNN-Keras【0.99514】.ipynb
Top: 12%，198/1789

参考：https://www.kaggle.com/toregil/welcome-to-deep-learning-cnn-99
结构如下：
```python
model.add(Conv2D(filters = 16, kernel_size = (3, 3), activation='relu',
                 input_shape = (28, 28, 1)))
model.add(BatchNormalization())
model.add(Conv2D(filters = 16, kernel_size = (3, 3), activation='relu'))
model.add(BatchNormalization())
model.add(MaxPool2D(strides=(2,2)))
model.add(Dropout(0.25))

model.add(Conv2D(filters = 32, kernel_size = (3, 3), activation='relu'))
model.add(BatchNormalization())
model.add(Conv2D(filters = 32, kernel_size = (3, 3), activation='relu'))
model.add(BatchNormalization())
model.add(MaxPool2D(strides=(2,2)))
model.add(Dropout(0.25))

model.add(Flatten())
model.add(Dense(512, activation='relu'))
model.add(Dropout(0.25))
model.add(Dense(1024, activation='relu'))
model.add(Dropout(0.5))
model.add(Dense(10, activation='softmax'))

model.compile(loss='categorical_crossentropy', optimizer = Adam(lr=1e-4), metrics=["accuracy"])
```



