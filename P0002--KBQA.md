# 核心思想

> We present a novel method for question answering which infers on both structured and unstructured resources. Our method consists of two main steps as outlined in §2. In the first step we extract answers for a given question using a structured KB (here Freebase) by jointly performing entity linking and relation extraction (§3). In the next step we validate these answers using an unstructured resource (here Wikipedia) to prune out the wrong answers and select the correct ones.

本文是基于IE的方法的，核心步骤为：

1.  KB-based joint inference
2.  Wiki-based inference

具体又分为四个步骤：

1. Entity Linking
2. Relation Extraction
3. KB-based joint inference
4. Wiki-based inference (refinement model)


# Entity Linking

1. entity mention 
2. retrieve the entity candidates in KB
3. rank the candidates 

在论文中，作者采用的是S-MART系统，对于每个entity mention取top 5的entity candidates.


# Relation Extraction

在小的数据集上，relation是个有限的集合，可以抽象为分类问题。在本文中，作者采用了MCCNN的分类器，其本质上就是一个textcnn，只是在输入层做了一个multi-channels：

1. 依存句法channel
2. 句子单词channel


# KB-based joint inference

entity和relation之间有很强的strong selectional preferences，比如：entity(刘德华)和relation(公司地址)之间不搭。我们就可以利用这种搭配选择关系，来对entity-relation pairs做选择。

本文将其作为一个rank问题来做，具体算法采用rank svm：

### 1. point-wise ranker

1. epred = egold and rpred = rgold,   3
2. epred != egold and rpred = rgold,  2
3. epred = egold and rpred != rgold,  2
4. epred != egold and rpred != rgold, 1


### 2. features

1. Entity Clues
2. Relation Clues
3. Answer Clues


# Wiki-based inference

这是本文的一个亮点，就是利用非结构化信息来对前面的结果做进一步的过滤。比如“what is the largest nation in europe”，利用知识库给出的答案是“Kazakhstan, Turkey, Russia,...” （这是基于IE的方法的缺陷，没法表达max这种概念），但是利用了wiki这种非结构化数据后，就可以得到答案“Russia”，因为在wiki中有对europe最大国家的描述可以使用。

# limitations

这也是所有IE方法的缺点，没法表示复杂relation （multi-hop relations），比如：

> who is the mother of the father of prince william



P0002-2016-ACL-Question Answering on Freebase via Relation Extraction and Textual Evidence