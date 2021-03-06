#  Predicting Citation Count

***

## Objective

In research, the citation count of a paper can be deemed as a measure of the success of the published material. Can this value be predicted? The goal of this project was to use journal metadata, publishing insitution metadata, and abstract topics to predict the citation count.

***
 
## Methods

BeautifulSoup was used to scrape 1,700 Genetics papers from Nature.com, from July 2017 to June 2018.

To examine how the topic matter of the abstract affects citation count, I conducted topic modeling two times. First, the topics were modeled with 5 topics, to capture broader meta-topics. Second, the topcis were modeled with 38 topics, to capture more granular sub-topics.

With the metadeta and topic divisions, the following features were engineered:
* Number of authors
* Length of title
* Publishing journal Impact Factor
* If the publishing journal was in the top 100 publishing journals in Nature
* Publication date
* For each sub-topic and meta-topic:
    * Abstract sub-topic/meta-topic
    * Topic percent contribution of the paper to its sub-topic/meta-topic
    * The average topic percent contribution of all papers in that sub-topic/meta-topic
    * How many other papers of that sub-topic/meta-topic were published in that same month
    * How long since the month with the most papers of that sub-topic/meta-topic
    * The difference in topic percent contribution with the highest contributing paper of that sub-topic/meta-topic

***

## Takeaways

The best model was a Poisson model, regularized with Lasso. This model produced a MSE of 30.1 and a MAE of 13.4.

The 3 features with the higest coefficients were journal Impact Factor, the meta-topic of Sequencing and Population Genetics, and the number papers published in the same month with the same meta-topic.
