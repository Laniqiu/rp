2.  Project Title:
Towards End-to-End Financial Sentiment Analysis  #######

3.  Project Objectives:  (Purpose of proposed investigation)
This research intends to apply sentiment analysis to the financial domain on an aspect level. Primarily, it aims to extract the target aspects within financial texts and assign a sentiment type (i.e., positive, neutral and negative) or to be more specific, give a sentiment intensity score between -1(extremely negative/bullish) and +1 (extremely positive/bearish) for each of them.
Details will be given in the following part.

4.  Scope and Background of Research:
  (Please identify key issues/problems to be addressed)

Financial sentiment analysis (FSA), as the term implies, is the application of sentiment analysis (SA )in the finance sector. Likewise, FSA leverages knowledge and methods in NLP and computational linguistics to identify and extract opinions from text data. Technically, FSA is a fine-grained SA task – aspect-based sentiment analysis (AbSA or ABSA), which suggests, instead of merely concluding what kind of attitude a text implies, it aims further to identify both the sentiment type and the target (Liu, 2012). Granular insights into opinions actually make more sense because an opinion is barely of use with an unidentified target. For instance, the sentence “I just love my camera for its good picture quality although its battery life is short" clearly expresses a positive tone, yet not absolutely. The opinion holder "I" is positive about one aspect, i.e., picture quality, and negative about the other aspect, i.e., battery life, of the entity, i.e., camera. “aspect” was referred to as "feature" (Hu and Liu, 2004; Pang and Lee, 2008). Besides, the example illustrates that opinion targets, picture quality and battery life of the camera in this case, usually consist of certain entities and/or aspects. Hence, ABSA needs to address both entities and aspects. That leads to the first phase of ABSA: aspect extraction (AE), followed by a second phase of aspect sentiment analysis or ASA for short. AE deals with the extraction of aspects which，depending on the actual situation, can be aspects (explicit or implicit), entities or opinion tagret expressions (actual words or phrases in the text to indicate opinions), while ASA predicts a sentiment polarity or value for the object extracted previsouly (Liu, 2012; Nazir, 2020). 
端到端，
The AE phase in this proposed research extracts both possible entities and aspects and a special aspect GENERAL will be used when the opinion is about the entity as a whole (Liu, 2012). 
看成key-value extraction，entity作为key，aspect 作为value，二者之间是mapping的，其余都是无需的，对一个字段，先判断是key还是value，若是value进一步判断分类
之后再对这个key-value对进行sentiment analysis，具体实现的话。。


把AE看作序列标注任务，除了entity和aspect，还有二者之间的关系mapping relation between entity and aspect(可能是implicit)，然后asa，对entity-aspect pair做sentiment analysis

fsa的不同之处，Different from traditional SA, FSA is 
命名实体识别 CRF，
难点：coreference resolution和word sense disambiguation（后者通过contexualied representation应该可以解决）

This study 说明absa的难点，引入fsa的难点：数据，讲明本文的rq和研究对象、贡献等。。。。。。。。。。。。。说明本文extract的目标是什么 2. fas和通用sa的不同 ## 难点或挑战 和其他领域的absa不同，金融领域一个问题在于数据少，标注难。应该着重数据这里，
It is similar to named entity recognition (NER) of information extraction (IE),

大概阶段：identity target， 2是对target做sentiment analysis，target可能有多个aspect（aspect和entity可能是同一个），对aspect进行sentiment打分，可以是positive negative neutral或给一个sentiment score，后者可能是回归问题
对第一个任务task，可以看成是一个binary classification？识别是target，是entity或aspect，和sentiment score联系？但是任务其实很多，应该细化，xing 等认为的分治法，一次解决一个sub problem；；；需要解决的问题：

*******************lexicon方法可以用来做数据处理或增强， Mishev et al, 2020
************ bert做representation
************** rnn做序列标注即ae，cnn做分类比如chen 2018，Jangid et al 2018  看layoutlm和vibert的论文
本文也认为aspect 2级别的分类
######################
*难点
 And FSA is deemed to be more difficult than other tasks within the field, such as SA for general purpose or of business reviews. Reasons could be many. One the one hand, financial application is more demanding with regard to interpretability and accuracy because a single mistake could possibly cost a fortune, while on the other hand, well-annotated and domain-specific data for training is quiet insufficient partly because finance is a relatively less explored area and that it requires expert or domain knowledge for annotation. The fact that financial texts involve a large number of jargons in the finance- and econmonic-sector possibly explains why general SA models usually get unsatisfactory performance when applied to the finance domain (Xing, et al 2020; Mishev et al, 2020). 
贡献################
The contribution of this research would be: 1. Data 2.  ….贡献：1.是数据，2.是模型或方法？？
/...2 
Form RDC/1A (page 2)
########################################################
5.  Research Methodology

Generally, methods used for FSA can be classified into lexicon-based, machine learning and deep learning. Among them, traditional lexicon-based such as OpinionLex, SenticNet and Loughran and McDonal's word list have been found to be useful, but insufficient to deal with financial texts for fine-grained analysis, and most regular machine learning approches like Naive Bayes, SVM and fastText also seem to fall behind the deep learning approaches like bi-LSTM (Liu, 2012; Man et al, 2019; Xing, et al 2020; Mishev et al, 2020; Nazir et al, 2020; Consolia et al, 2021). Particularily, in cases where lack of large-scale, domain-specific and high-quality training data has been found to be a huge concern, transfer learning (or domain adaptation) that allows to utilize larger and related dataset for improving the target task seems to offer a promising solution (Yang et al, 2018; Man et al, 2019). And the pre-trained model BERT or its variants have achived remarkable success in plenty of NLP tasks including general SA and FSA thanks to its capability to capature more complex contextual information in contrast with word2vec or Glove and the deeper reprentation methods like ELMo (Li et al, 2019; Xing et al, 2020; Mishev et al, 2020; Sun et al, 2019; Araci, 2019). Hence, this research decides to follow the paradigm of deep learning and utilize BERT for text representation. 
针对挑战： 1. 是数据，2是方法


把asa看作是分类任务？把ae看作是ner或sequence labeling task
看layoutlm和vibert？

fiqa数据集的sentiment分数不是三元而是-1到1的数据，但这样的话标注打分会很困难，也会主观？？

# 缺数据，一个是bert，fsa的数据一个是数据增强，
。。
20那篇总数，证明Bert能取得较好的结果，因此还是用bert？用了stocksen数据集，

*Data 数据，还有个sem see https://sites.google.com/view/fiqa/home#h.p_5YO6tqDxC23c
SemEval 2017 Task 5 
Financial phrase bank
StockTwits (Chen, et al, 2018) chen对数据做了处理，和fiqa的适配， chen这里不用做ner，用sigmoid替代softmax预测sentiment degree
Financial texts can present themselves as news, reviews, corporate reports, or posts from social medias such Twitter or StockTwits (Man, Luo and Lin, 2019). 有些人自己搜集数据， 
FiQA, an open dataset from the WWW’18 conference, offers about 1,1000 samples for FSA training, including 435 news headlines and 675 tweets with each labeled with the target entity, aspect and a sentiment score ranging from -1 to 1 continuously (Maia et al., 2018). (加表，展示数据类型或示例)
Despite the fact FiQA contains well-annotated and finance-specific data, it is rather small in quantity. 未得到 书增强、 
StockTwist Sentiment dataset （Xing et al, 2020, 数量少，可请求使用)
SemEval-2017
训练数据、测试数据
The proposed method will be evaluated in respect to aspect classification and sentimnet classification with indicators like precesion, recall, F1-score, MSE and R^2.
* Outline of Thesis 
  1. Introduction (background, objectives)
  2. Related Work
  3. Methodology (research design)
  4. Experiment (including dataset, data processing and analysis, implementation details, etc.)
  5. Conclusion (summary, contributions and shortcomings, further research directions)

6.  Project Significance and Value:

Financial texts such as news, reviews, corporate reports, tweets and more, though unstructured, contain rich and valuable information. FSA, by making sense of these unstructed data sources, is expected to and has actually been approved to play a role in the financial and economic domain, like the market of stocks, oil, or foreign exchange and more (Chan & Chong, 2016; Man, Luo & Lin, 2019; Xing et al, 2020； Mishev et al, 2020). This proposed research is a response in time towards the increasing demand for and interests on such techniques and methods from  the industry. The academia also look forward to seeing improvments in this area. In this sense, the significance of this research can be twofold despite the fact that its value might be immediate or indirect: From an academic perspective, the work of this study is supposed to fill the gap around FSA and inspire further research, and from the perspectve of pragmatism, it has the potential to ultimately yield results that assist in fast, reliable and comprehensive data analysis and decision making for financial markets and participants concerned. 

* Timeframe
2021.11 - 2022.09: early work, including literature reading, premilinary data collection, personal improvments in both theories and engineering skills
2022.10 - 2024.05: data collection, preprocessing and analysis, experiments, results interpretations and disscussions
2024.06 - 2024.12: production of the thesis


* Reference
L. Lee and B. Pang, "Opinion Mining and Sentiment Analysis," Foundations and Trends® in Information Retrieval, vol. 2, no. 1–2, pp. 1-135, 2008.
Liu, Bing. (2012). Sentiment Analysis and Opinion Mining. Synthesis Lectures on Human Language Technologies. 5. 10.2200/S00416ED1V01Y201204HLT016. 
Chan, Samuel & Chong, Mickey. (2016). Sentiment Analysis in Financial Texts. Decision Support Systems. 94. 10.1016/j.dss.2016.10.006. 
X. Man, T. Luo and J. Lin, "Financial Sentiment Analysis(FSA): A Survey," 2019 IEEE International Conference on Industrial Cyber Physical Systems (ICPS), 2019, pp. 617-622, doi: 10.1109/ICPHYS.2019.8780312.
Xing, F. Z. , Malandri, L. , Zhang, Y. , & Cambria, E. . (2020). Financial Sentiment Analysis: An Investigation into Common Mistakes and Silver Bullets. COLING.
Nazir, A. ,  Rao, Y. ,  Wu, L. , &  Sun, L. . (2020). Issues and challenges of aspect-based sentiment analysis: a comprehensive survey. IEEE Transactions on Affective Computing, PP(99), 1-1.
Hitkul Jangid, Shivangi Singhal, Rajiv Ratn Shah, and Roger Zimmermann. 2018. Aspect-Based Financial Sentiment Analysis using Deep Learning. In
WWW ’18 Companion: The 2018 Web Conference Companion, April 23–27, 2018, Lyon, France. ACM, New York, NY, USA, 6 pages. https://doi.org/10.1145/3184558.3191827
C.C. Chen, H.H. Huang, and H.H. Chen. 2018. Fine-Grained Analysis of Financial Tweets. In The 2018 Web Conference Companion (WWW 2018), April 23-27, 2018, Lyon, France, ACM, New York, NY, 7 pages. DOI: https://doi.org/10.1145/3184558.3191824
Cortis, K., Freitas, A., Daudert, T., Huerlimann, M., Zarrouk, M., Handschuh, S., & Davis, B. 2017. Semeval-2017 task 5: Fine-Grained Sentiment Analysis on Financial Microblogs and News. In Proceedings of the 11th International Workshop on Semantic Evaluation, pages 519-535
Mishev, K. ,  Gjorgjevikj, A. ,  Vodenska, I. ,  Chitkushev, L. T. , &  Trajanov, D. . (2020). Evaluation of sentiment analysis in finance: from lexicons to transformers. IEEE Access, PP(99), 1-1.
Xin Li, Lidong Bing, Wenxuan Zhang and Wai Lam (2019) Exploiting BERT for End-to-End Aspect-based Sentiment Analysis
Yang, S. ,  Rosenfeld, J. , &  Makutonin, J. . (2018). Financial aspect-based sentiment analysis using deep representations.
Chi Sun, Luyao Huang, Xipeng Qiu 2019 Utilizing BERT for Aspect-Based Sentiment Analysis via Constructing Auxiliary Sentence
Sergio Consolia, Luca Barbagliaa, and Sebastiano Manzan (2021)  Fine-grained, aspect-based sentiment analysis on economic and financial lexicon
Araci, D. . (2019). Finbert: financial sentiment analysis with pre-trained language models.

