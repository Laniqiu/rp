2.	Project Title:
Towards Financial Sentiment Analysis	########## entity（分entity和target）+ aspect（attribute可能没有）,换个题??， entity level sentiment classification 
3.	Project Objectives:  (Purpose of proposed investigation)
This research intends to apply sentiment analysis to the financial domain on an aspect level. Primarily, it aims to extract the target aspects within financial texts and predict a sentiment type (i.e., positive, neutral and negative) or to be more specific, give a sentiment insentity score for each of them.
Details shall be given in the following part.

4.	Scope and Background of Research:
	(Please identify key issues/problems to be addressed)
Financial sentiment analysis (FSA), as the term implies, is the application of sentiment analysis (SA )in the finance sector (维基百科，或找一篇综述). Likewise, FSA leverages knowledge and methods in NLP and computational linguistics to identify and extract opinions from text data. 加参考文献 However, it is deemed to be more challenging than other tasks within the field, such as SA for general purpose or of business reviews, in that it lacks (可能要修改) large-scale and high-quality (well-annotated) data for training, which is one of the reasons that FSA models usually get unsatisfactory performance. 第一篇综述2021和2018的论文
 
Technically, FSA is a fine-grained SA task – aspect-based sentiment analysis (AbSA), which suggests, instead of merely concluding what kind of attitude a text implies, it aims further to identify both the sentiment type and the target, and sometimes the attribute or aspect that the 指向. 

Generally, methods used for FSA includes lexicon-based, machine learning and deep learning 这里讲现行的方法和难点？lexicon
 
The contribution of this research would be 创新主要工作 NER sentiment 

 ########aspect  多涵义，选一篇论文的定义再改
* Challenges:
1. 高质量数据少
2. 
/...2 
Form RDC/1A (page 2)

The contribution of this research would be ….

5.	Research Methodology: 研究设计、数据、论文大纲, 相关工作这里讲ABSA的大概流程，以及本文的目标：entity

Basically, AbSA includes three phases: a

*Data: see https://sites.google.com/view/fiqa/home#h.p_5YO6tqDxC23c
Financial texts can present themselves as news, reviews, corporate reports, or posts from social medias such Twitter or StockTwits (Man, Luo and Lin, 2019). 有些人自己搜集数据， FiQA, an open dataset from the WWW’18 conference,  offers about 1,1000 labeled samples for FSA training, including 435 news headlines and 675 tweets with each labeled with the target entity, aspect and a sentiment score ranging from -1 to 1 continuously (Maia et al., 2018). (加表，展示数据类型或示例)

Despite the fact FiQA contains well-annotated and finance-specific data, it is rather small in quantity. 未得到 书增强、 


* Research Design
评估
* Evaluation
The proposed model will be evaluated in respect to three parts: aspect classification, sentimnet classification and aspect-sentiment attachment/mapping #######不确定with indicators like precesion, recall, F1-score, MSE and R^2. 





* Timeframe
2021.11 - 2022.09: early work, including literature reading, premilinary data collection, personal improvments in both theories and engineering skills
2022.10 - 2024.05: data collection, preprocessing and analysis, experiments, results interpretations and disscussions
2024.06 - 2024.12: production of the thesis

* Outline of Thesis 
  1. Introduction (background, objectives)
  2. Related Work
  3. Methodology (research design)
  4. Experiment (including dataset, data processing and analysis, implementation details, etc.)
  5. Conclusion (summary, contributions and shortcomings, further research directions)

6.	Project Significance and Value:

Financial texts such as news, reviews, corporate reports, tweets and more, though unstructured, contain rich and valuable information. FSA, by making sense of these unstructed data sources, is expected to and has actually been approved to play a role in the financial and economic domain, like the market of stocks, oil, or foreign exchange (Man, Luo and Lin, 2019). This proposed research is a response in time towards the increasing demand for and interests on such techniques and methods from  the industry. The academia also look forward to seeing improvments in this area. In this sense, the significance of this research can be twofold despite the fact that its value might be immediate or indirect: From an academic perspective, the work of this research is supposed to fill the gap around FSA and inspire further research, and from the perspectve of pragmatism, it has the potential to ultimately yield results that assist in fast, reliable and comprehensive data analysis and decision making for financial markets and participants concerned. 




例子 steve loves iphone and hates galaxy
展望： 多语言、多样化

社交平台 social media outlets



* Reference
