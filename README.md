2.  Project Title:
Utilizing BERT for an Entity-levl Financial Sentiment Analysis 

3.  Project Objectives:  (Purpose of proposed investigation)
This research intends to apply sentiment analysis to the financial domain on an entity level. Primarily, it aims to extract the target aspects within financial texts which can present themselves as news, reviews, corporate reports, or posts from social medias such Twitter or StockTwit and assign a sentiment type (i.e., positive, neutral and negative) or to be more specific, give a sentiment intensity score between -1(extremely negative/bullish) and +1 (extremely positive/bearish) for each of them  (Man, Luo and Lin, 2019).
Details will be given in the following part.

4.  Scope and Background of Research:
  (Please identify key issues/problems to be addressed)

Financial sentiment analysis (FSA), as the term implies, is the application of sentiment analysis (SA )in the finance sector. Likewise, FSA leverages knowledge and methods in NLP and computational linguistics to identify and extract opinions from text data. Technically, FSA is a fine-grained SA task – aspect-based sentiment analysis (AbSA or ABSA), which suggests, instead of merely concluding what kind of attitude a text implies, it aims further to identify both the sentiment type and the target (Liu, 2012). Granular insights into opinions actually make more sense because an opinion is barely of use with an unidentified target. For instance, the sentence "I just love my camera for its good picture quality although its battery life is short" clearly reveals a positive tone, yet not absolutely. The opinion holder "I" expresses different abou the entity, i.e., camera with regard to its two aspects or "features", i.e., picture quality (positive) and battery life (negative) (Hu and Liu, 2004; Pang and Lee, 2008). Besides, the example illustrates that opinion targets, picture quality and battery life of the camera in this case, usually consist of certain entities and/or aspects. Hence, ABSA needs to address both entities and aspects. That leads to the first phase of ABSA: aspect extraction (AE), followed by a second phase of aspect sentiment analysis or ASA for short. Notably, "aspect" here is a collective term, which, depending on the actual situation, can be aspects (explicit or implicit), entities or opinion tagret expressions (actual words or phrases in the text to indicate opinion targets) and so on. AE deals with the extraction of these objects, and sometimes classification is also involved during, while ASA predicts a sentiment polarity or value for the aspect extracted previsouly (Liu, 2012; Nazir, 2020). 
ABSA is challenging because it touches many sub-problems of NLP (Liu, 2012). And FSA is deemed to be more difficult than other tasks within the field, such as SA for general purpose or of business reviews. Reasons could be many. One the one hand, financial application is more demanding with regard to interpretability and accuracy because a single mistake could possibly cost a fortune, while on the other hand, well-annotated and domain-specific data for training is quiet insufficient partly because finance is a relatively less explored area and that it requires expert or domain knowledge for annotation. The fact that financial texts involve a large number of jargons possibly explains why general SA models usually get unsatisfactory performance when applied to the finance domain (Xing, et al 2020; Mishev et al, 2020). 
This research proposed to work at FSA on the entity-level based on such a consumption: In the scenario of finance, specific targets instead of their categories are valued for decision making. Participants have a name in mind already, say, COSCO, they are mostly interested in the stcok prices of COSCO, and the fact that it is a shipping company is not really influencial. In this context, the target or at least part of it (i.e. entity) is given when analyzing a financial text. This entity-level research is a divide-and-conquer method in FSA and it saves the trouble of recognizing entities during implementation. 

/...2 
Form RDC/1A (page 2)

5.  Research Methodology
*******************lexicon方法可以用来做数据处理或增强， Mishev et al, 2020
************ bert做representation
************** rnn做序列标注即ae，cnn做分类比如chen 2018，Jangid et al 2018  看layoutlm和vibert的论文

Generally, methods used for FSA can be classified into lexicon-based, machine learning and deep learning. Among them, carefully collected or designed lexicons such as OpinionLex, SenticNet and Loughran and McDonal's word list (L&M) have been found to be useful, but insufficient to deal with financial texts for fine-grained analysis, and most regular machine learning approches like Naive Bayes, SVM and fastText also seem to fall behind the deep learning approaches like bi-LSTM (Liu, 2012; Man et al, 2019; Xing, et al 2020; Mishev et al, 2020; Nazir et al, 2020; Consolia et al, 2021). Particularily, in cases where lack of large-scale, domain-specific and high-quality training data has been found to be a huge trouble, transfer learning (or domain adaptation) that allows to utilize larger and related dataset for improving the target task seems to offer a promising solution (Yang et al, 2018; Man et al, 2019). And the pre-trained model BERT or its variants have been applied into and achived remarkable success in plenty of NLP tasks including general SA and FSA thanks to its capability to capature more complex contextual information in contrast with word2vec or Glove and the deeper reprentation methods like ELMo (Li et al, 2019; Xing et al, 2020; Mishev et al, 2020; Sun et al, 2019; Araci, 2019). Hence, this research decides to follow the paradigm of deep learning and utilize BERT for text representation. 

Here is a task description. Given a sentence or sequence s, which may have more than one target, t= {t1, ..., tm}, and ti (1=<i<=m) is defined as a one-to-many pair with a single entity ei and possibly mulitiple aspects of different categories, ai={ai1, ..., aik}, the goal is to identify t within s and predict a sentiment polarity or degree for each ti. A special aspect GENERAL will be used when the opinion is about the entity as a whole (Liu, 2012). Take an example from the Fiqa dataset, s="easyJet expects resilient demand to withstand security fears", the proposed approach is supposed to predict a slightly positive value (the labeled sentiment score is 0.165) for the entity "easyJet" with regard to an aspect category of "risks" (aspect level 2 in fiqa). In the AE phase, this research focuses on an aspect level 2 classification over an aspect level 1 classification (i.e. entity classification) considering that the entity itself such as "easyJet" (instead of its category "corporate") is also a major concern for decision making in the financial and economic context, while details of its related aspects are possibly less crucial in the process. Note that this is an entity-level task, so the entity of each target is known, then this task is decomposed into aspect classification and aspect sentiment analysis. To avoid ambiguation, the term "aspect", if not specified, hereinafter refers to its narrow sense of "feature". 因为aspect可能是implicit，所以用classification， entity-aspect matching, target-sentiment matching, 

于是这整个就成了一个为句子中的aspect（显性或隐性）分类并mapping到特定的entity（大概率只有一个），然后为每个entity-aspect pair即target做asa
对整个sentence 先判断是否有多个target（多个target的话可能polarity不一致），若只有一个target即，就只需要识别
opinion expressions不重要，重要的是polarity， opinion expressions作为sentiment analysis的特征，最后将sentiment和target mapping，

Datasets that are avaliable include SemEval 2017, StockTwits and FiQA and so on (Chen, et al, 2018; Xing et al, 2020). FiQA offers about 1,1000 samples for FSA training, including 435 news headlines and 675 tweets with each labeled with the target entity, aspect and a sentiment score ranging from -1 to 1 continuously (Maia et al., 2018). It is an open dataset from the WWW’18 conference and received a few papers dealing with two FSA tasks. FiQA data is well-annotated and finance-specific （加表，展示数据类型或示例), yet it is rather small in quantity. Other datasets also have their problems such as too much noise, poor annotation, and so on. Therefore, besides from pre-training language models, this research intends to apply data augmentation by taking advantage of the existing lexicon approaches such as L&M, which incorporate substantial financial knowledge, and thus may be used as a resource to enrich our traning data. 数据增强的具体方法，替换等，而且要改成这里适用的格式

Finally, the proposed method will be evaluated in respect to aspect classification and sentimnet classification with indicators like precesion, recall, F1-score, MSE and R^2. And since FiQA has recieved several papers, it could serve as a baseline for evaluation.


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

