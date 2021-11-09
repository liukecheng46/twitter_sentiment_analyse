# twitter_sentiment_analyse
machine learning practice  

## Goal
In this assignment, the task is predict the sentiment of Tweets about four technology companies, Apple, Microsoft, Google, and Twitter. Here are some examples of tweets with different sentiments:
  - **positive**: _"http://t.co/QV4m1Un9 Forget the phone.. Nice UI. Liking the Scroll Feature #android #google #nexus"_
  - **negative**: _"Have never had such poor customer service at @Apple before! What happened? (@ Apple Store w/ 2 others) http://t.co/GKlXMUi6"_
  - **neutral**: _"The lock screen now has facial recognition capability! #Google #Android #ICS"_.

our goal is to train a classifier to predict whether a tweet is positive, neutral, or negative sentiment.

大致思路：主要分为三部分。


第一部分是数据预处理。 


先使用nltk和正则进行标准化操作：

小写、去除标点符号、去除停顿词、提取词干、标注词性并使用词性来进行词形还原。

接着对format后的数据进行观察提取其他特征：  
   1）推特文本包含大量@XX、#XXX、rt（转发）、tweet（推文）和http开头的网页链接等对分类没有作用的无效名词，进行删除处理；  

2）并且每个推文都被标记与哪个公司有关，可考虑将公司名加入数据尾部。  

3）考虑删除数字   

4）大多数长度小于3的短单词都没什么用，考虑删除  

5）高频低频词汇考虑删除（k>300或k<=2，k表示至少在k个文档中出现，此k值根据freq_dist生成的频率图观察得到,在进行tf-idf时使用）

（有考虑删除的表示会根据是否提升分类效果来进行使用）
***


第二部分是特征提取

主要使用两种方法：tf-idf和word2vec。

tfidf将预处理并分完词的数据重新拼接为句子进行处理。  

word2vec使用gensim库
***


第三部分是训练模型并交叉验证寻找最优参数

使用了逻辑回归、多项式贝叶斯分类器、多层感知机、svm、adaboost、随机森林、cnn、lstm等模型。
