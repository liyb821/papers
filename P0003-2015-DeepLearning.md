# Key Points

### 关于raw data

> Conventional machine-learning techniques were limited in their ability to process natural data in their raw form. 即：传统的机器学习在处理raw data方面能力欠缺，所以需要feature engineering和domain expertise将raw data变为internal representation或者feature vector。

### 关于representation learning

> Representation learning is a set of methods that allows a machine to be fed with raw data and to automatically discover the representations needed for detection or classification. 

### deep learing和representation learning的关系

> Deep-learning methods are representation-learning methods with multiple levels of representation, obtained by composing simple but non-linear modules that each transform the representation at one level (starting with the raw input) into a representation at a higher, slightly more abstract level.

### SGD中stochastic的含义

> It is called stochastic because each small set of examples gives a noisy estimate of the average gradient over all examples.


# CNN

在利用自然信号的属性方面，CNN有四个核心ideas:

1. local connections
2. shared weights
3. pooling
4. multi-layers

### 1. local connections和shared weights的优势

> First, in array data such as images, local groups of values are often highly correlated, forming distinctive local motifs that are easily detected. Second, the local statistics of images and other signals are invariant to location.

1. 局部特征有更好的相似性(selectivity),比如，两幅图像中的两个窗口比两幅完整的图像更容易相似；
2. 局部特征有更好的不变形(invariance),比如，局部特征有更好的位置不变形；

### 2. pooling的作用

1. 降维
2. 增加鲁棒性

> The pooling allows representations to vary very little when elements in the previouslayer vary in position and appearance.






