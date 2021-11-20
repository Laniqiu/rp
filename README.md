FORM RDC/1A
(Revised December 2018)



THE HONG KONG POLYTECHNIC UNIVERSITY

RESEARCH DEGREE PROPOSAL


Note:  Please note that the information given in this form will only be used for processing this application.

1.	Name of Proposed Chief Supervisor (if applicable):
	Emmanuele CHERSONI, Chu-Ren HUANG 
2.	Project Title:
	Towards an Entity-Level Financial Sentiment Analysis	
3.	Project Objectives:  (Purpose of proposed investigation)
This research intends to apply sentiment analysis to the financial domain on an entity level. Primarily, it aims to extract the explicit target aspects within financial texts such as news, reviews, corporate reports, or posts from social medias such Twitter or StockTwit and assign a sentiment type (i.e., positive, neutral and negative) or to be more specific, give a sentiment intensity score between -1 (extremely negative/bullish) and +1 (extremely positive/bearish) for each of them (Man, Luo and Lin, 2019). 
Details will be given in the following part.
4.	Scope and Background of Research:
	(Please identify key issues/problems to be addressed)
Financial sentiment analysis (FSA), as the term implies, is the application of sentiment analysis (SA) in the finance sector. Likewise, FSA leverages knowledge and methods in NLP and computational linguistics to identify and extract opinions from textual data. Technically, FSA is a fine-grained SA task – aspect-based sentiment analysis (ABSA), which suggests, instead of merely concluding what kind of attitude a text implies, it aims further to identify both the sentiment type and the target (Liu, 2012). Granular insights into opinions make more sense because an opinion is barely of use with an unidentified target. For instance, the sentence "I just love my camera for its good picture quality although its battery life is short" clearly reveals a positive tone, yet not absolutely. The opinion holder "I" expresses different attitudes about the entity, i.e., camera with regard to its two aspects, i.e., picture quality (positive) and battery life (negative) (Hu and Liu, 2004; Pang and Lee, 2008). The example illustrates that an opinion target, picture quality and battery life of the camera in this case, usually consist of certain entities and/or aspects, which could be explicit and implicit. Here, in the light of Liu’s (2012) definition, the noun phrase “picture quality” is an explicit aspect expression and those are not nouns or noun phrases are implicit aspect expressions. For example, “expensive” implies the aspect of “price”.  Liu (2012) also defined an opinion as a quintuple of (ei, aij, sijkl, hk, tl), i.e., entity, aspect, sentiment, opinion holder and time, or a quadruple of (g, s, h, t), i.e., target, sentiment, opinion holder and time, considering that an opinion target is decomposed into an entity and its associated aspects as discussed in the “camera” example.  Core tasks of ABSA are derived from the four or five elements, e.g., aspect extraction (AE), aspect sentiment analysis (ASA) and more. AE deals with the extraction of these objects with classification also involved sometimes, and ASA predicts a sentiment polarity or value for the aspect extracted in the previous phase (Liu, 2012; Nazir, 2020). Notably, "aspect" in AE is a collective term, which, depending on the actual situation, can be aspects, entities or opinion target expressions and so on (Liu 2012; Nazir, 2020). To avoid ambiguation and confusion, “aspect”, if not specified, hereinafter refers to its narrow sense of “feature”, “quality” or attribute, and “* expression” or “* term” denotes the actual words that appear in the text to indicate any element * in the quintuple/ quadruple.
FSA is deemed to be a difficult task even within the field. For starters, as any other ABSA work, it touches many sub-problems of NLP. For instance, AE alone could address implicit aspects, entity detection and classification. Besides, the finance and economic sector is more demanding regarding interpretability and accuracy. After all,  a single mistake could possibly cost a fortune. However, general SA models always end up with unsatisfactory performance when applied to the finance domain (Xing, et al 2020; Mishev et al, 2020). Data could take the blame. On the one hand, financial texts are usually unique in language structure and involve a large number of jargons and thus need special attention. On the other hand, well-annotated and domain-specific data for training is quite insufficient, partly because this is a relatively less explored area and that it requires expert knowledge for annotation. 
With regards to the challenges above, this research decides to follow a divide-and-conquer path by handling explicit aspects only and working at FSA on the entity-level. The latter decision is based on such a consumption: Participants in the financial sector already have a name in mind before their decision making, say, COSCO, they are more interested in the stock prices of COSCO, and the fact that it is a shipping company is not really influential. In this context, the target or at least part of it, i.e., entity, is determined for data analysis. Also, an entity-level work saves the trouble of recognizing entities during implementation, which further simplifies the extraction task and raises the feasibility. And, this research would make extra efforts on data collection, processing and augmentation to tackle the data problem.


Wang et al, 2017; 
some ABSA researches such as (Peng , 2020; Jian et al 2021; Mukherjee, 2021) regard aspect term, opinion words and associated sentiment and as an opinion triplet, arguing that opinion words could explain the sentiment expressed towards the aspect and thus offer a complete picture for readers about what is being discussed, how and why is the sentiment, which particularly makes sense in the scenario of making financial decisions.  

The main contributions would be: 
/...2
Missing entities are acceptable, of course,	syntactic strcuture句法信息，position information											
 
Form RDC/1A (page 2)
5.	Research Methodology:
Generally, methods used for FSA can be classified into lexicon-based, machine learning and deep learning. Carefully hand-crafted lexicons such as OpinionLex, SenticNet and Loughran and McDonal's word list (L&M) have been found to be useful yet insufficient to deal with financial texts for fine-grained analysis, and most regular machine learning approaches like Naive Bayes, SVM and fastText also seem to fall behind the deep learning approaches like bi-LSTM (Liu, 2012; Man et al, 2019; Xing, et al 2020; Mishev et al, 2020; Nazir et al, 2020; Consolia et al, 2021). Particularly, in cases of lack of large-scale, domain-specific and high-quality training data, transfer learning (or domain adaptation) that allows to utilize larger and related dataset for improving the target task offers a promising solution (Yang et al, 2018; Man et al, 2019). Among them, BERT, a pre-training model, and its variants have been applied into and achieved remarkable success in plenty of NLP tasks including general SA and FSA thanks to its capability to capture more complex contextual information in contrast with word2vec or Glove and the deeper representation methods like ELMo (Li et al, 2019; Xing et al, 2020; Mishev et al, 2020; Araci, 2019). Despite that BERT cannot be directly applied to FSA due to a large difference in domain knowledge, it is still an ideal architecture for learning effective representation (Sun et al, 2019; Mensah, 2021; Lekhtman et al, 2020). Hence, this research decides to follow the paradigm of deep learning and use BERT to represent the input.
Given a sentence or sequence s={w1, w2, ..., wn} with n words, which may contain more than one target, t= {t1, ..., tm}, with each ti defined as an entity-aspect pair that is composed of an entity ei and an aspect ai of a category of c, 
the goal is to identify ti=(ei, ai) within s and predict a sentiment polarity or degree for it. A special aspect GENERAL will be used when the opinion is about the entity as a whole (Liu, 2012). 
Take an example from the FiQA dataset, s="easyJet expects resilient demand to withstand security fears", the proposed approach is supposed to predict a slightly positive value (the labelled sentiment score is 0.165) for the entity "easyJet" with regard to an aspect category of "risks" (aspect level 2 in FiQA). In the extraction phase, this research focuses on an aspect level 2 classification over an aspect level 1 classification (i.e. entity classification) considering that the entity itself such as "easyJet" (instead of its category "corporate") is also a major concern for decision making in the financial and economic context, while details of its related aspects are possibly less crucial in the process. 
Note that this is an entity-level task, so the entity e of target ti is known, and in the scenario where an entity is missing from a sentence, then this task is decomposed into aspect extraction and aspect sentiment analysis. 

The extraction phase in ABSA of the abovementioned triplet, aspect-sentiment pair, or a single of them is mostly done using sequence-taggers with a BIO, BIEOS or a unified tagging scheme (Li et al, 2019; ). Causes error propagation problem or lose the contextual information between those elements 
Inspired by Mukherjee et al (2021) and Mensah et al (2021), 
word-level feature:Token embedding from BERT + position embedding 
sentence-level feature


位置信息对于提取opinion words以及interaction between aspect-opinion words极其重要，但bert对于position的捕捉能力不强，因此额外将position embedding嵌入，有人用GCN捕捉位置关系

很多研究将提取任务作为sequence tagging task并使用BIO或BIEOS tagging scheme，或者用unified tagging scheme (Li, et al 2019; Mukherjee et al, 2021), 分别提取aspect-sentiment pair和opinion words，再在第二阶段将sentiment和opinion words配对，这样会导致error propagation，




As stated before, data is a huge trouble in FSA and probably one major challenge in this area. Datasets that are available include SemEval 2017, StockTwits and FiQA and so on (Chen, et al, 2018; Xing et al, 2020). FiQA offers about 1,1000 samples for FSA training, including 435 news headlines and 675 tweets with each labeled with the target entity, aspect and a sentiment score ranging from -1 to 1 continuously (Maia et al., 2018). It is an open dataset from the WWW’18 conference and received a few papers dealing with two FSA tasks. FiQA data is well-annotated and finance-specific, yet it is rather small in quantity. Other datasets also have their problems such as too much noise, poor annotation, and so on. Therefore, this research intends to take advantage of the existing lexicon approaches such as L&M, which incorporate substantial financial knowledge, and thus may be used as a resource to enrich our training data or assist with data processing. 
Finally, the proposed method will be evaluated in respect to aspect classification and sentiment classification with indicators like precision, recall, F1-score, MSE and R^2. And since FiQA has received several papers, it could serve as a baseline for evaluation.

6.	Project Significance and Value:
Financial texts such as news, reviews, corporate reports, tweets and more, though unstructured, contain rich and valuable information. FSA, by making sense of these unstructed data sources, is expected to and has been approved to play a role in the financial and economic domain, like the market of stocks, oil, or foreign exchange and more (Chan & Chong, 2016; Man, Luo & Lin, 2019; Xing et al, 2020； Mishev et al, 2020). This proposed research is a response in time towards the increasing demand for and interests on such techniques and methods from the industry. The academia also looks forward to seeing improvements in this area. In this sense, the significance of this research can be twofold despite the fact that its value might be immediate or indirect: From an academic perspective, the work of this study is supposed to fill the gap around FSA and inspire further research, and from the perspective of pragmatism, it has the potential to ultimately yield results that assist in fast, reliable and comprehensive data analysis and decision making for financial markets and participants concerned. 

* Outline of Thesis 
  1. Introduction (background, objectives)
  2. Related Work
  3. Methodology (research design)
  4. Experiment (dataset, data processing and analysis, implementation details, etc.)
  5. Conclusion (summary, contributions and shortcomings, further research directions)

* Timeframe
2021.12 - 2022.09: early work, including literature reading, preliminary data collection, personal improvements in both theories and engineering skills
2022.10 - 2024.05: data collection, pre-processing and analysis, experiments, results interpretations and discussions
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
Samuel Mensah, Kai Sun, Nikolaos Aletras, 2021 An Empirical Study on Leveraging Position Embeddings for Target-oriented Opinion Words Extraction
Lekhtman, Entony & Ziser, Yftah & Reichart, Roi. (2021). DILBERT: Customized Pre-Training for Domain Adaptation withCategory Shift, with an Application to Aspect Extraction. 
Rajdeep Mukherjee∗ , Tapas Nayak∗ , Yash Butala et al PASTE: A Tagging-Free Decoding Framework Using Pointer Networks for Aspect Sentiment Triplet Extraction
Xin Li, Lidong Bing, Piji Li, and Wai Lam. 2019. A unified model for opinion target extraction and target sentiment prediction. In The Thirty-Third AAAI Con ference on Artificial Intelligence, AAAI 2019, The Thirty-First Innovative Applications of Artificial Intelligence Conference, IAAI 2019, The Ninth AAAI Symposium on Educational Advances in Artificial Intelligence, EAAI 2019, Honolulu, Hawaii, USA, January 27 - February 1, 2019, pages 6714–6721. AAAI Press
Samson Yu Bai Jian, ……….Aspect Sentiment Triplet Extraction Using Reinforcement Learning
Wenya Wang,†‡ Sinno Jialin Pan,† Daniel Dahlmeier,‡ Xiaokui Xiao, 2017, Coupled Multi-Layer Attentions for Co-Extraction of Aspect and Opinion Terms
Haiyun Peng,1 Lu Xu,∗1,2 Lidong Bing,1 Fei Huang,1 Wei Lu,2 Luo Si , 2020, What, How and Why: A Near Complete Solution for Aspect-Based Sentiment Analysis




/...3
 
Form RDC/1A (page 3)

7.	Details of Any External Collaboration:
In these circumstances, are there likely to be any complications associated with the publication of your thesis? Give details.
8.	Declaration of the Applicant
I wish to register for a research degree on the basis of the proposal given in this Form (RDC/1A).

I understand that, during the period of my registration with the University, I may not be a candidate for any other degree or award.

I understand that, except with the specific permission of the Research Committee, I must prepare and defend my thesis in English.  (You are required to seek permission if another language, which is considered more appropriate to the subject, is to be used in the presentation of the thesis.  Please submit the justification together with this application.)

I undertake to abide by the general regulations of the University.

Signature                                                                                	Date            		   	 
		               
Name                                                         	                   
                 


During the application period
After completing Sections 1 to 8, the applicant should upload this form to the eAdmission system at www.polyu.edu.hk/admission.

After admission
RPg students should submit this form to the General Office of the Department after completing Sections 1 to 8.


/...4

 
Form RDC/1A (page 4)
	For internal use only. Applicants should leave Sections 9 and 10 blank.		

9.	Endorsement by the Proposed Chief Supervisor

    9a.	Research Ethics/ Safety Approval

[For ethics approval, Chief Supervisor / Temporary Chief Supervisor please read the Ethical Clearance for Research or Teaching Projects or Investigations Involving Human Subjects, which are available at Section V of the Handbook for Projects and Grants at https://www.polyu.edu.hk/ro/staff/handbooks/HD_PG.pdf, and make sure that ethics approval is obtained if your project involves human subjects.  For safety approval, please read the policy and procedures for safety approval available at the Health, Safety & Environment Office Homepage.   Please attach the approval letter where appropriate.]

I confirm that approval:

* has been	* is not required	* will be obtained 
  Obtained		   before the start
                                                     	   of the project                              	                         		
Human Research Ethics					

Animal Research Ethics					

Biological Safety					

Ionizing Radiation Safety 					

Non-ionizing Radiation Safety 					

Chemical Safety					

(* Please tick as appropriate)


9b.	Research Facilities and Space
    

    I confirm, to the best of my knowledge, that adequate facilities and space are available to enable the student to conduct and complete the research programme in an efficient and safe manner.
  

    I would like to request the following additional research facilities and/or space to enable the student to conduct and complete the research programme in an efficient and safe manner:

Research Facilities	
Space (Other than the regular space provided by the Department for RPg students)	

Signature                		       	 Department/School 				
            (^ Chief Supervisor / Temporary Chief Supervisor)

Name 					 Date 									
            (^ Chief Supervisor / Temporary Chief Supervisor)

(^ Please delete as appropriate)



Form RDC/1A (page 5)

10.	Recommendation of Head of Affiliated Department in the University




    I support this application and understand, on the basis of the Chief Supervisor’s endorsement, that adequate research facilities and space are available to enable the student to conduct and complete the research programme in an efficient and safe manner. 



    I support this application and agree to provide the additional research facilities and/or space, as requested by the Chief Supervisor in section 9b above, to enable the student to conduct and complete the research programme in an efficient and safe manner.



Signature                                                                                  Date                                    		                             (Head of Department/Dean of School)




~ The completed form should be kept by the General Office of the Department. ~














































RDC/1A
