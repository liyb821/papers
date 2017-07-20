# 定义

> We dene entity linking as matching a textual entitymention, possibly identied by a named entity recognizer, to a KB entry, such asa Wikipedia page that is a canonical entry for that entity.

# Entity Linking的难点

### 1. Name Variations

* 缩写
* 简称
* 别称
* ……

### 2. Entity Ambiguity

一个mention在KB中能够找到多个entity

### 3. Absence

无论KB多大，总存在收录不全的问题

# Entity Linking的方案

### 1. Candidate Selection for Name Variants

利用规则线性暴力扫描KB，或者做一些优化（非暴力扫描）。

### 2. Entity Linking as Ranking

* 可以作为二分类问题
* 也可以作为ranking问题，比如采用rank svm来做

抽象为rank问题比较好。接下来最重要的工作就是feature了。


### 3. Predicting NIL Mentions

实现拒识能力。




[1]（Entity Linking: Finding Extracted Entities in aKnowledge Base）