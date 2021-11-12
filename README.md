2.	Project Title:
Towards Financial Sentiment Analysis: Aspect Extraction ??####待定，
3.	Project Objectives:  (Purpose of proposed investigation)
This research intends to apply sentiment analysis to the financial domain on an aspect level. Primarily, it aims to extract the target aspects within financial texts and predict a sentiment type (i.e., positive, neutral and negative) or to be more specific, give a sentiment insentity score for each of them.
Details will be given in the following part.

4.	Scope and Background of Research:
	(Please identify key issues/problems to be addressed)

Financial sentiment analysis (FSA), as the term implies, is the application of sentiment analysis (SA )in the finance sector. Likewise, FSA leverages knowledge and methods in NLP and computational linguistics to identify and extract opinions from text data. (加参考文献) Technically, FSA is a fine-grained SA task – aspect-based sentiment analysis (AbSA or ABSA), which suggests, instead of merely concluding what kind of attitude a text implies, it aims further to identify both the sentiment type and the target (Liu, 2012). Granular insights into opinions actually make more sense in that an opinion is barely of use with an unidentified target. For instance, the sentence “I just love my camera for its good picture quality although its battery life is short" clearly expresses a positive tone, yet not abosolutely. Actually, the opinion holder "I" is positive about one aspect, i.e., picture quality, and negative about the other aspect, i.e., battery life, of the entity, i.e., camera. “aspect” was referred to as "feature" (Hu and Liu, 2004; Pang and Lee, 2008). Besides, the sentence illustrates that opinion targets, picture quality and battery life of the camera in this case, usually consist of certain entities and/or aspects. Hence, ABSA need to address both entities and aspects. 
And FSA is deemed to be more challenging than other tasks within the field, such as SA for general purpose or of business reviews, considering that it usually get unsatisfactory performance (Xing et al, 2020; Nazir et al, 2020). 
<!-- One of the frequently challenge that has been frequently brought up is the lack of large-scale and high-quality (well-annotated) data in finance-specific domain. (加各种论文，主要是fiqa的) -->

*难点: general, absa和fsa，具体到金融领域，In terms of finance-specific SA, one major challenge would be lack of large-scale and well-annotated data, partly because it is a relatively less explored area and that it requires expert or domain knowledge for annotation (第一篇总论以及fiqa的几篇论文). 和其他absa的难点在哪里：数据？
* Challenges and Issues:
one general challenge in SA or FSA lies in data. Data 
general, 
SA或ABSA的问题，以及金融领域特定的难点specific to the financial domain, 
1. 高质量数据少（标注需要专业知识）, FSA对解释性要求更高 对精度要求更高因为错误可能造成极大损失，  Xing et al 2020  
训练数据有限，语言风格独特， Xing et al 2020  需要divide and conquer approach即分治法，把大问题分解成sub problems
2. sa 是一个nlp难题，但好在不需要全部理解
aspect 分explicit 和implicit


讲方法和难点？？ 
结构化数据
细讲金融领域


当做key-value MAPPING  问题Based on this level of 
analysis, a structured summary of opinions about entities and their 
aspects can be produced, which turns unstructured text to structured data 
and can be used for all kinds of qualitative and quantitative analyses. 
opinion分两种regular和comparative


This finer-grained analysis can be 
it is more difficult. 
大概阶段：identity target， 2是对target做sentiment analysis，target可能有多个aspect（aspect和entity可能是同一个），对aspect进行sentiment打分，可以是positive negative neutral或给一个sentiment score，后者可能是回归问题
对第一个任务task，可以看成是一个binary classification？识别是target，是entity或aspect，和sentiment score联系？但是任务其实很多，应该细化，xing 等认为的分治法，一次解决一个sub problem；；；需要解决的问题：
1. target identification
  1.1 entity，可能explicit或implicit
  1.2 aspect 可能explicit或implicit
2. sentiment analysis  这可能是回归的问题？

本文也认为aspect 2级别的分类
fiqa数据集的sentiment分数不是三元而是-1到1的数据，但这样的话标注打分会很困难，也会主观？？


This study focuses on two core phases in ABSA: aspect extraction and aspect sentiment classification (Liu, 2012)
Aspect extraction actually include two sub-tasks: entity extraction and aspect extraction. It is similar to named entity recognition (NER) of information extraction (IE), 传统的方法HMM, CRF

as stated above, this research aims to 
这里讲难点，research question，目的等


可行性personally, 个人经验，代码和项目能力，

The contribution of this research would be  ….贡献：1.是数据，2.是模型或方法？？
/...2 
Form RDC/1A (page 2)


5.	Research Methodology: 研究设计、数据、论文大纲, 相关工作这里讲ABSA的大概流程，以及本文的目标是entity， aspect？？

* Related Work相关工作：3篇综述+ 
Generally, methods used for FSA includes lexicon-based, machine learning and deep learning 两篇总论 investigation和issues()
迁移学习、bert和。。。
20那篇总数，证明Bert能取得较好的结果，因此还是用bert？用了stocksen数据集，

* Methodology
*Data 数据，还有个sem see https://sites.google.com/view/fiqa/home#h.p_5YO6tqDxC23c
Financial texts can present themselves as news, reviews, corporate reports, or posts from social medias such Twitter or StockTwits (Man, Luo and Lin, 2019). 有些人自己搜集数据， 
FiQA, an open dataset from the WWW’18 conference, offers about 1,1000 samples for FSA training, including 435 news headlines and 675 tweets with each labeled with the target entity, aspect and a sentiment score ranging from -1 to 1 continuously (Maia et al., 2018). (加表，展示数据类型或示例)
Despite the fact FiQA contains well-annotated and finance-specific data, it is rather small in quantity. 未得到 书增强、 
StockTwist Sentiment dataset （Xing et al, 2020, 数量少，可请求使用)
SemEval-2017
训练数据、测试数据
* Evaluation评估
The proposed model will be evaluated in respect to three parts: aspect classification, sentimnet classification and aspect-sentiment attachment/mapping #######不确定with indicators like precesion, recall, F1-score, MSE and R^2. MCC (Matthews, Correlation Coefficient, 专门为不平衡数据)(Xing et al 2020)，benchmark??
第一篇综述: simply using a domain adapted lexicon does not necessarily solve the FSA problem.； bert在精度和mcc方面在stocksen数据集上表现最好，但是f值的话 sltm最好， sltm是sentence state lstm； 基于lexicon 的方法效果可能很差，
* Outline of Thesis 
  1. Introduction (background, objectives)
  2. Related Work
  3. Methodology (research design)
  4. Experiment (including dataset, data processing and analysis, implementation details, etc.)
  5. Conclusion (summary, contributions and shortcomings, further research directions)

6.	Project Significance and Value:

Financial texts such as news, reviews, corporate reports, tweets and more, though unstructured, contain rich and valuable information. FSA, by making sense of these unstructed data sources, is expected to and has actually been approved to play a role in the financial and economic domain, like the market of stocks, oil, or foreign exchange and more (Chan & Chong, 2016; Man, Luo & Lin, 2019; Xing et al, 2020). This proposed research is a response in time towards the increasing demand for and interests on such techniques and methods from  the industry. The academia also look forward to seeing improvments in this area. In this sense, the significance of this research can be twofold despite the fact that its value might be immediate or indirect: From an academic perspective, the work of this study is supposed to fill the gap around FSA and inspire further research, and from the perspectve of pragmatism, it has the potential to ultimately yield results that assist in fast, reliable and comprehensive data analysis and decision making for financial markets and participants concerned. 

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
Nazir, A. ,  Rao, Y. ,  Wu, L. , &  Sun, L. . (2020). Issues and challenges of aspect-based sentiment analysis: a comprehensive survey. IEEE Transactions on Affective Computing, PP(99), 1-1.  18年还是19年出来，2020年登出
Hitkul Jangid, Shivangi Singhal, Rajiv Ratn Shah, and Roger Zimmermann. 2018. Aspect-Based Financial Sentiment Analysis using Deep Learning. In
WWW ’18 Companion: The 2018 Web Conference Companion, April 23–27, 2018, Lyon, France. ACM, New York, NY, USA, 6 pages. https://doi.org/10.1145/3184558.3191827
C.C. Chen, H.H. Huang, and H.H. Chen. 2018. Fine-Grained Analysis of Financial Tweets. In The 2018 Web Conference Companion (WWW 2018), April 23-27, 2018, Lyon, France, ACM, New York, NY, 7 pages. DOI: https://doi.org/10.1145/3184558.3191824

Cortis, K., Freitas, A., Daudert, T., Huerlimann, M., Zarrouk, M., Handschuh, S., 
& Davis, B. 2017. Semeval-2017 task 5: Fine-Grained Sentiment Analysis on 
Financial Microblogs and News. In Proceedings of the 11th International 
Workshop on Semantic Evaluation, pages 519-535
