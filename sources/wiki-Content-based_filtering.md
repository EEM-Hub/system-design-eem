---
source: https://en.wikipedia.org/wiki/Content-based_filtering
fetched: 2026-06-19
---

System to predict users' preferences 

 
| Recommender systems |
| --- |
| Concepts |
| Accuracy barrierCollective intelligenceRelevanceStar ratingsLong tail |
| Methods and challenges |
| Cold startCollaborative filteringDimensionality reductionImplicit data collectionItem-item collaborative filteringMatrix factorizationPreference elicitationSimilarity search |
| Implementations |
| Collaborative search engineContent discovery platformDecision support systemMusic Genome ProjectProduct finder |
| Research |
| GroupLens ResearchMovieLensNetflix PrizeACM Conference on Recommender Systems |
| vte |

 "The algorithm" redirects here. For other uses, see [Algorithm (disambiguation)](./Algorithm_(disambiguation)). 

A **recommender system**, also called a **recommendation algorithm**, **recommendation engine**, or **recommendation platform**, is a type of [information filtering system](./Information_filtering_system) that suggests items most relevant to a particular user.[[1]](./Recommender_system#cite_note-handbook-1)[[2]](./Recommender_system#cite_note-2)[[3]](./Recommender_system#cite_note-3) The value of these systems becomes particularly evident in scenarios where users must select from a large number of options, such as products, media, or content.[[1]](./Recommender_system#cite_note-handbook-1)[[4]](./Recommender_system#cite_note-ResnickVarian-4) Major [social media](./Social_media) platforms and [streaming services](./Streaming_service) rely on recommender systems that employ [machine learning](./Machine_learning) to analyze user behavior and preferences, thereby enabling personalized content feeds.[[5]](./Recommender_system#cite_note-5)[[6]](./Recommender_system#cite_note-6)

 

Typically, the suggestions refer to a variety of [decision-making processes](./Decision-making_process), including the selection of a product, musical selection, or online news source to read.[[1]](./Recommender_system#cite_note-handbook-1) The implementation of recommender systems is pervasive, with commonly recognised examples including the generation of [playlist](./Playlist) for video and music services, the provision of product recommendations for e-commerce platforms, and the recommendation of content on social media platforms and the open web.[[7]](./Recommender_system#cite_note-twitterwtf2-7)[[8]](./Recommender_system#cite_note-8) These systems can operate using a single type of input, such as music, or multiple inputs from diverse platforms, including news, books and search queries. Additionally, popular recommender systems have been developed for specific topics, such as restaurants and [online dating](./Online_dating) services. Recommender systems have also been developed to explore research articles and experts,[[9]](./Recommender_system#cite_note-expertseer-9) collaborators,[[10]](./Recommender_system#cite_note-collabseer-10) and financial services.[[11]](./Recommender_system#cite_note-financialrec-11)

 

A **content discovery platform** is a [software](./Software) recommendation [platform](./Computing_platform) that employs recommender system tools. It utilizes user [metadata](./Metadata) in order to identify and suggest relevant content, whilst reducing ongoing maintenance and development costs. A content discovery platform delivers personalized content to [websites](./Website), [mobile devices](./Mobile_device), and [set-top boxes](./Set-top_boxes). A large range of content discovery platforms currently exist for various forms of content ranging from news articles and [academic journal](./Academic_journal) articles[[12]](./Recommender_system#cite_note-nature1-12) to television.[[13]](./Recommender_system#cite_note-13) As operators compete to serve as the gateway to home entertainment, personalized television emerges as a key service differentiator. Academic content discovery has recently become another area of interest, the emergence of numerous companies dedicated to assisting academic researchers in keeping up to date with relevant academic content and facilitating serendipitous discovery of new content.[[12]](./Recommender_system#cite_note-nature1-12)

 

## Overview

 

Recommender systems usually make use of either or both [collaborative filtering](./Collaborative_filtering) and content-based filtering, as well as other systems such as [knowledge-based systems](./Knowledge-based_systems). Collaborative filtering approaches build a model from a user's past behavior (e.g., items previously purchased or selected and/or numerical ratings given to those items) as well as similar decisions made by other users. This model is then used to predict items (or ratings for items) that the user may have an interest in.[[14]](./Recommender_system#cite_note-Recommender2010-14) Content-based filtering approaches utilize a series of discrete, pre-tagged characteristics of an item in order to recommend additional items with similar properties.[[15]](./Recommender_system#cite_note-mooney99-15)

 

### Example

 

The differences between collaborative and content-based filtering can be demonstrated by comparing two early music recommender systems, [Last.fm](./Last.fm) and [Pandora Radio](./Pandora_Radio). 

 
- Last.fm creates a "station" of recommended songs by observing what bands and individual tracks the user has listened to on a regular basis and comparing those against the listening behavior of other users. Last.fm will play tracks that do not appear in the user's library, but are often played by other users with similar interests. As this approach leverages the behavior of users, it is an example of a [collaborative filtering](./Collaborative_filtering) technique.[[16]](./Recommender_system#cite_note-16)
- Pandora uses the properties of a song or artist (a subset of the 450 attributes provided by the [Music Genome Project](./Music_Genome_Project)[[17]](./Recommender_system#cite_note-17)) to seed a "station" that plays music with similar properties. User feedback is used to refine the station's results, deemphasizing certain attributes when a user "dislikes" a particular song and emphasizing other attributes when a user "likes" a song. This is an example of a content-based approach.

 

Each type of system has its strengths and weaknesses. In the above example, Last.fm requires a large amount of information about a user to make accurate recommendations. This is an example of the [cold start](./Cold_start_(recommender_systems)) problem, and is common in collaborative filtering systems.[[18]](./Recommender_system#cite_note-:3-18)[[19]](./Recommender_system#cite_note-rubens2016-19)[[20]](./Recommender_system#cite_note-20)[[21]](./Recommender_system#cite_note-elahi2016-21)[[22]](./Recommender_system#cite_note-schein02-22)[[23]](./Recommender_system#cite_note-bi2017-23) Whereas Pandora needs very little information to start, it is far more limited in scope (for example, it can only make recommendations that are similar to the original seed).

 

### Alternative implementations

 

Recommender systems are a useful alternative to [search algorithms](./Search_algorithm) since they help users discover items they might not have found otherwise. Of note, recommender systems are often implemented using search engines indexing non-traditional data. In some cases, like in the [Gonzalez v. Google](./Gonzalez_v._Google_LLC) Supreme Court case, may argue that search and recommendation algorithms are different technologies.[[24]](./Recommender_system#cite_note-24)

 

Recommender systems have been the focus of several granted patents,[[25]](./Recommender_system#cite_note-25)[[26]](./Recommender_system#cite_note-26)[[27]](./Recommender_system#cite_note-27)[[28]](./Recommender_system#cite_note-28)[[29]](./Recommender_system#cite_note-29) and there are more than 50 software libraries[[30]](./Recommender_system#cite_note-30) that support the development of recommender systems including LensKit,[[31]](./Recommender_system#cite_note-31)[[32]](./Recommender_system#cite_note-32) RecBole,[[33]](./Recommender_system#cite_note-33) ReChorus[[34]](./Recommender_system#cite_note-34) and RecPack.[[35]](./Recommender_system#cite_note-35)

 

## History

 

[Elaine Rich](./Elaine_Rich) created the first recommender system in 1979, called Grundy.[[36]](./Recommender_system#cite_note-36)[[37]](./Recommender_system#cite_note-37) She looked for a way to recommend users books they might like. Her idea was to create a system that asks users specific questions and classifies them into classes of preferences, or "stereotypes", depending on their answers. Depending on users' stereotype membership, they would then get recommendations for books they might like.

 

Another early recommender system, called a "digital bookshelf", was described in a 1990 technical report by [Jussi Karlgren](./Jussi_Karlgren) at Columbia University,
[[38]](./Recommender_system#cite_note-38)
and implemented at scale and worked through in technical reports and publications from 1994 onwards by [Jussi Karlgren](./Jussi_Karlgren), then at [SICS](./SICS),[[39]](./Recommender_system#cite_note-39)[[40]](./Recommender_system#cite_note-40)
and research groups led by [Pattie Maes](./Pattie_Maes) at MIT,[[41]](./Recommender_system#cite_note-41) Will Hill at Bellcore,[[42]](./Recommender_system#cite_note-42) and [Paul Resnick](./Paul_Resnick), also at MIT,[[43]](./Recommender_system#cite_note-43)[[4]](./Recommender_system#cite_note-ResnickVarian-4) whose work with GroupLens was awarded the 2010 [ACM Software Systems Award](./ACM_Software_Systems_Award).

 

Montaner provided the first overview of recommender systems from an intelligent agent perspective.[[44]](./Recommender_system#cite_note-44) [Adomavicius](./Gediminas_Adomavicius?action=edit&redlink=1) provided a new, alternate overview of recommender systems.[[45]](./Recommender_system#cite_note-Toward_the_Next_Generation_of_Recommender_Systems-45)  Herlocker provides an additional overview of evaluation techniques for recommender systems,[[46]](./Recommender_system#cite_note-46) and [Beel](./Joeran_Beel?action=edit&redlink=1) et al. discussed the problems of offline evaluations.[[47]](./Recommender_system#cite_note-:0-47) Beel et al. have also provided literature surveys on available research paper recommender systems and existing challenges.[[48]](./Recommender_system#cite_note-48)[[49]](./Recommender_system#cite_note-49)

 

## Approaches

 

### Collaborative filtering

 Main article: [Collaborative filtering](./Collaborative_filtering) [![](//upload.wikimedia.org/wikipedia/commons/thumb/b/bc/Collaborative_filtering_network.gif/250px-Collaborative_filtering_network.gif)](./File:Collaborative_filtering_network.gif)[![](//upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Collaborative_filtering_table.gif/250px-Collaborative_filtering_table.gif)](./File:Collaborative_filtering_table.gif)An example of predicting of the user's rating using collaborative filtering.
- *Left:* At first, people rate different items (like videos, images, games).
- *Right:* After that, the system makes [predictions](./Prediction) about a user's rating for an item which they have not personally rated yet. These predictions are built upon the existing ratings of other users, who have similar ratings with the active user. For instance, in our case the system has made a prediction, that the user in the bottom left of the network will not like the video.

 

One approach to the design of recommender systems that has wide use is [collaborative filtering](./Collaborative_filtering).[[50]](./Recommender_system#cite_note-Breese98-50) Collaborative filtering is based on the assumption that people who agreed in the past will agree in the future, and that they will like similar kinds of items as they liked in the past. The system generates recommendations using only information about rating profiles for different users or items. By locating peer users/items with a rating history similar to the current user or item, they generate recommendations using this neighborhood.

 

The collaborative filtering approach does not rely on machine analyzable content and therefore it is capable of accurately recommending complex items such as movies without requiring an "understanding" of the item itself. Many algorithms have been used in measuring user similarity or item similarity in recommender systems. For example, the [k-nearest neighbor](./K-nearest_neighbors_algorithm) (k-NN) approach[[51]](./Recommender_system#cite_note-51) and the [Pearson Correlation](./Pearson_correlation) as first implemented by Allen.[[52]](./Recommender_system#cite_note-52)

 

Collaborative filtering approaches often suffer from three problems: [cold start](./Cold_start_(computing)), scalability, and sparsity.[[53]](./Recommender_system#cite_note-Lee2007-53)

 
- **Cold start**: For a new user or item, there is not enough data to make accurate recommendations. Note: one commonly implemented solution to this problem is the [multi-armed bandit algorithm](./Multi-armed_bandit).[[54]](./Recommender_system#cite_note-54)[[18]](./Recommender_system#cite_note-:3-18)[[19]](./Recommender_system#cite_note-rubens2016-19)[[21]](./Recommender_system#cite_note-elahi2016-21)[[23]](./Recommender_system#cite_note-bi2017-23)
- **Scalability**: There are millions of users and products in many of the environments in which these systems make recommendations. Thus, a large amount of computation power is often necessary to calculate recommendations.
- **Sparsity**: The number of items sold on major e-commerce sites is extremely large. The most active users will only have rated a small subset of the overall database. Thus, even the most popular items have very few ratings.

 

[Social networking services](./Social_networking_service) have used collaborative filtering to recommend new friends, groups, and other social connections by examining the network of connections between a user and their friends.[[1]](./Recommender_system#cite_note-handbook-1)

 

### Content-based filtering

 

Another common approach when designing recommender systems is **content-based filtering**. Content-based filtering methods are based on a description of the item and a profile of the user's preferences.[[55]](./Recommender_system#cite_note-Aggarwal16Book-55)[[56]](./Recommender_system#cite_note-56) These methods are best suited to situations where there is known data on an item (name, location, description, etc.), but not on the user. Content-based recommenders treat recommendation as a user-specific classification problem and learn a classifier for the user's likes and dislikes based on an item's features.

 

In this system, keywords are used to describe the items, and a [user profile](./User_profile) is built to indicate the type of item this user likes. In other words, these algorithms try to recommend items similar to those that a user liked in the past or is examining in the present. It does not rely on a user sign-in mechanism to generate this often temporary profile. In particular, various candidate items are compared with items previously rated by the user, and the best-matching items are recommended. This approach has its roots in [information retrieval](./Information_retrieval) and [information filtering](./Information_filtering) research.

 

To create a [user profile](./User_profile), the system mostly focuses on two types of information:

 
1. A model of the user's preference.
2. A history of the user's interaction with the recommender system.

 

Basically, these methods use an item profile (i.e., a set of discrete attributes and features) characterizing the item within the system. To abstract the features of the items in the system, an item presentation algorithm is applied. A widely used algorithm is the [tf–idf](./Tf–idf) representation (also called vector space representation).[[57]](./Recommender_system#cite_note-57) The system creates a content-based profile of users based on a weighted vector of item features. The weights denote the importance of each feature to the user and can be computed from individually rated content vectors using a variety of techniques. Simple approaches use the average values of the rated item vector while other sophisticated methods use machine learning techniques such as [Bayesian Classifiers](./Naive_Bayes_classifier), [cluster analysis](./Cluster_analysis), [decision trees](./Decision_trees), and [artificial neural networks](./Artificial_neural_networks) in order to estimate the probability that the user is going to like the item.[[58]](./Recommender_system#cite_note-58)

 

A key issue with content-based filtering is whether the system can learn user preferences from users' actions regarding one content source and use them across other content types. When the system is limited to recommending content of the same type as the user is already using, the value from the recommendation system is significantly less than when other content types from other services can be recommended. For example, recommending news articles based on news browsing is useful. Still, it would be much more useful when music, videos, products, discussions, etc., from different services, can be recommended based on news browsing. To overcome this, most content-based recommender systems now use some form of the hybrid system.

 

Content-based recommender systems can also include opinion-based recommender systems. In some cases, users are allowed to leave text reviews or feedback on the items. These user-generated texts are implicit data for the recommender system because they are potentially rich resources of both feature/aspects of the item and users' evaluation/sentiment to the item. Features extracted from the user-generated reviews are improved [metadata](./Metadata) of items, because as they also reflect aspects of the item like metadata, extracted features are widely concerned by the users. Sentiments extracted from the reviews can be seen as users' rating scores on the corresponding features. Popular approaches of opinion-based recommender system utilize various techniques including [text mining](./Text_mining), [information retrieval](./Information_retrieval), [sentiment analysis](./Sentiment_analysis) (see also [Multimodal sentiment analysis](./Multimodal_sentiment_analysis)) and [deep learning](./Deep_learning).[[59]](./Recommender_system#cite_note-59)

 

### Hybrid recommendations approaches

 

Most recommender systems now use a hybrid approach, combining [collaborative filtering](./Collaborative_filtering), content-based filtering, and other approaches. Hybrid approaches can be implemented in several ways: by making content-based and collaborative-based predictions separately and then combining them; by adding content-based capabilities to a collaborative-based approach (and vice versa); or by unifying the approaches into one model.[[45]](./Recommender_system#cite_note-Toward_the_Next_Generation_of_Recommender_Systems-45) Several studies that empirically compared the performance of the hybrid with the pure collaborative and content-based methods and demonstrated that the hybrid methods can provide more accurate recommendations than pure approaches. These methods can also be used to overcome some of the common problems in recommender systems such as cold start and the sparsity problem, as well as the [knowledge engineering](./Knowledge_engineering) bottleneck in [knowledge-based](./Knowledge_base) approaches.[[60]](./Recommender_system#cite_note-60)

 

[Netflix](./Netflix) uses a hybrid recommender systems to make recommendations by comparing the watching and searching habits of similar users (i.e., collaborative filtering) as well as by offering movies that share characteristics with films that a user has rated highly (content-based filtering).[[61]](./Recommender_system#cite_note-61)

 

Some hybridization techniques include:

 
- **Weighted**: Combining the score of different recommendation components numerically.
- **Switching**: Choosing among recommendation components and applying the selected one.
- **Mixed**: Recommendations from different recommenders are presented together to give the recommendation.
- **Cascade**: Recommenders are given strict priority, with the lower priority ones breaking ties in the scoring of the higher ones.
- **Meta-level**: One recommendation technique is applied and produces some sort of model, which is then the input used by the next technique.[[62]](./Recommender_system#cite_note-hybrids-62)

 

## Technologies

 

### Session-based recommender systems

 

These recommender systems use the interactions of a user within a session[[63]](./Recommender_system#cite_note-a-63) to generate recommendations. Session-based recommender systems are used at YouTube[[64]](./Recommender_system#cite_note-yt-64) and Amazon.[[65]](./Recommender_system#cite_note-amzn-65) These are particularly useful when history (such as past clicks, purchases) of a user is not available or not relevant in the current user session. Domains where session-based recommendations are particularly relevant include video, e-commerce, travel, music and more. Most instances of session-based recommender systems rely on the sequence of recent interactions within a session without requiring any additional details (historical, demographic) of the user. Techniques for session-based recommendations are mainly based on generative sequential models such as [recurrent neural networks](./Recurrent_neural_network),[[63]](./Recommender_system#cite_note-a-63)[[66]](./Recommender_system#cite_note-66) [transformers](./Transformer_(deep_learning_architecture)),[[67]](./Recommender_system#cite_note-67) and other deep-learning-based approaches.[[68]](./Recommender_system#cite_note-68)[[69]](./Recommender_system#cite_note-69)

 

### Reinforcement learning for recommender systems

 

The recommendation problem can be seen as a special instance of a [reinforcement learning](./Reinforcement_learning) problem whereby the user is the environment upon which the agent, the recommendation system acts upon in order to receive a reward, for instance, a click or engagement by the user.[[64]](./Recommender_system#cite_note-yt-64)[[70]](./Recommender_system#cite_note-srl-70)[[71]](./Recommender_system#cite_note-sQ-71) One aspect of reinforcement learning that is of particular use in the area of recommender systems is the fact that the models or policies can be learned by providing a reward to the recommendation agent. This is in contrast to traditional learning techniques which rely on [supervised learning](./Supervised_learning) approaches that are less flexible, reinforcement learning recommendation techniques allow to potentially train models that can be optimized directly on metrics of engagement, and user interest.[[72]](./Recommender_system#cite_note-jd-72)

 

### Multi-criteria recommender systems

 

Multi-criteria recommender systems (MCRS) can be defined as recommender systems that incorporate preference information upon multiple criteria. Instead of developing recommendation techniques based on a single criterion value, the overall preference of user u for the item i, these systems try to predict a rating for unexplored items of u by exploiting preference information on multiple criteria that affect this overall preference value. Several researchers approach MCRS as a multi-criteria decision making (MCDM) problem, and apply MCDM methods and techniques to implement MCRS systems.[[73]](./Recommender_system#cite_note-73) See this chapter[[74]](./Recommender_system#cite_note-74) for an extended introduction.

 

### Risk-aware recommender systems

 

The majority of existing approaches to recommender systems focus on recommending the most relevant content to users using contextual information, yet do not take into account the risk of disturbing the user with unwanted notifications. It is important to consider the risk of upsetting the user by pushing recommendations in certain circumstances, for instance, during a professional meeting, early morning, or late at night. Therefore, the performance of the recommender system depends in part on the degree to which it has incorporated the risk into the recommendation process. One option to manage this issue is *DRARS*, a system which models the context-aware recommendation as a [bandit problem](./Multi-armed_bandit). This system combines a content-based technique and a contextual bandit algorithm.[[75]](./Recommender_system#cite_note-Bouneffouf2013-75)

 

### Mobile recommender systems

 Further information: [Location based recommendation](./Location_based_recommendation) 

Mobile recommender systems make use of internet-accessing [smartphones](./Smartphone) to offer personalized, context-sensitive recommendations. This is a particularly difficult area of research as mobile data is more complex than data that recommender systems often have to deal with. It is heterogeneous, noisy, requires spatial and temporal auto-correlation, and has validation and generality problems.[[76]](./Recommender_system#cite_note-taxirecommender-76)

 

There are three factors that could affect the mobile recommender systems and the accuracy of prediction results: the context, the recommendation method and privacy.[[77]](./Recommender_system#cite_note-77) Additionally, mobile recommender systems suffer from a transplantation problem – recommendations may not apply in all regions (for instance, it would be unwise to recommend a recipe in an area where all of the ingredients may not be available).

 

One example of a mobile recommender system are the approaches taken by companies such as [Uber](./Uber) and [Lyft](./Lyft) to generate driving routes for taxi drivers in a city.[[76]](./Recommender_system#cite_note-taxirecommender-76) This system uses GPS data of the routes that taxi drivers take while working, which includes location (latitude and longitude), time stamps, and operational status (with or without passengers). It uses this data to recommend a list of pickup points along a route, with the goal of optimizing occupancy times and profits.

 

### Generative recommenders

 

Generative recommenders (GR) represent an approach that transforms recommendation tasks into [sequential transduction](./Seq2seq) problems, where user actions are treated like tokens in a generative modeling framework. In one method, known as HSTU (Hierarchical Sequential Transduction Units),[[78]](./Recommender_system#cite_note-78) high-[cardinality](./Cardinality), non-stationary, and streaming datasets are efficiently processed as sequences, enabling the model to learn from trillions of parameters and to handle user action histories orders of magnitude longer than before. By turning all of the system’s varied data into a single stream of tokens and using a custom [self-attention](./Attention_(machine_learning)) approach instead of [traditional neural network layers](./Neural_network_(machine_learning)), generative recommenders make the model much simpler and less memory-hungry. As a result, it can improve recommendation quality in test simulations and in real-world tests, while being faster than previous [Transformer](./Transformer_(deep_learning_architecture))-based systems when handling long lists of user actions. Ultimately, this approach allows the model’s performance to grow steadily as more computing power is used, laying a foundation for efficient and scalable “[foundation models](./Foundation_model)” for recommendations.

 

## The Netflix Prize

 Main article: [Netflix Prize](./Netflix_Prize) 

One of the events that energized research in recommender systems was the [Netflix Prize](./Netflix_Prize). From 2006 to 2009, Netflix sponsored a competition, offering a grand prize of $1,000,000 to the team that could take an offered dataset of over 100 million movie ratings and return recommendations that were 10% more accurate than those offered by the company's existing recommender system. This competition energized the search for new and more accurate algorithms. On 21 September 2009, the grand prize of US$1,000,000 was given to the BellKor's Pragmatic Chaos team using tiebreaking rules.[[79]](./Recommender_system#cite_note-nytimes.com-79)

 

The most accurate algorithm in 2007 used an ensemble method of 107 different algorithmic approaches, blended into a single prediction. As stated by the winners, Bell et al.:[[80]](./Recommender_system#cite_note-80)

 

Predictive accuracy is substantially improved when blending multiple predictors. *Our experience is that most efforts should be concentrated in deriving substantially different approaches, rather than refining a single technique.*  Consequently, our solution is an ensemble of many methods.

 

Many benefits accrued to the web due to the Netflix project. Some teams have taken their technology and applied it to other markets. Some members from the team that finished second place founded [Gravity R&D](./Gravity_R&D), a recommendation engine that's active in the [RecSys community](./ACM_Conference_on_Recommender_Systems).[[79]](./Recommender_system#cite_note-nytimes.com-79)[[81]](./Recommender_system#cite_note-81) 4-Tell, Inc. created a Netflix project–derived solution for ecommerce websites.

 

A number of privacy issues arose around the dataset offered by Netflix for the Netflix Prize competition. Although the data sets were anonymized in order to preserve customer privacy, in 2007 two researchers from the University of Texas were able to identify individual users by matching the data sets with film ratings on the [Internet Movie Database (IMDb)](./IMDb).[[82]](./Recommender_system#cite_note-82) As a result, in December 2009, an anonymous Netflix user sued Netflix in Doe v. Netflix, alleging that Netflix had violated United States fair trade laws and the [Video Privacy Protection Act](./Video_Privacy_Protection_Act) by releasing the datasets.[[83]](./Recommender_system#cite_note-83) This, as well as concerns from the [Federal Trade Commission](./Federal_Trade_Commission), led to the cancellation of a second Netflix Prize competition in 2010.[[84]](./Recommender_system#cite_note-nfcancel-84)

 

## Evaluation

 

### Performance measures

 

Evaluation is important in assessing the effectiveness of recommendation algorithms. To measure the [effectiveness](./Effectiveness) of recommender systems, and compare different approaches, three types of [evaluations](./Evaluation) are available: user studies, [online evaluations (A/B tests)](./A/B_testing), and offline evaluations.[[47]](./Recommender_system#cite_note-:0-47)

 

The commonly used metrics are the [mean squared error](./Mean_squared_error) and [root mean squared error](./Root_mean_squared_error), the latter having been used in the Netflix Prize. The information retrieval metrics such as [precision and recall](./Precision_and_recall) or [discounted cumulative gain (DCG)](./Discounted_Cumulative_Gain) are useful to assess the quality of a recommendation method. Diversity, novelty, and coverage are also considered as important aspects in evaluation.[[85]](./Recommender_system#cite_note-85) However, many of the classic evaluation measures are [highly criticized](./Accuracy_barrier).[[86]](./Recommender_system#cite_note-Turpin2001-86)

 

Evaluating the performance of a recommendation algorithm on a fixed test dataset will always be extremely challenging as it is impossible to accurately predict the reactions of real users to the recommendations. Hence any metric that computes the effectiveness of an algorithm in offline data will be imprecise.

 

User studies are rather a small scale. A few dozens or hundreds of users are presented recommendations created by different recommendation approaches, and then the users judge which recommendations are best.

 

In A/B tests, recommendations are shown to typically thousands of users of a real product, and the recommender system randomly picks at least two different recommendation approaches to generate recommendations. The effectiveness is measured with implicit measures of effectiveness such as [conversion rate](./Conversion_rate) or [click-through rate](./Click-through_rate).

 

Offline evaluations are based on historic data, e.g. a dataset that contains information about how users previously rated movies.[[87]](./Recommender_system#cite_note-87)

 

The effectiveness of recommendation approaches is then measured based on how well a recommendation approach can predict the users' ratings in the dataset. While a rating is an explicit expression of whether a user liked a movie, such information is not available in all domains. For instance, in the domain of citation recommender systems, users typically do not rate a citation or recommended article. In such cases, offline evaluations may use implicit measures of effectiveness. For instance, it may be assumed that a recommender system is effective that is able to recommend as many articles as possible that are contained in a research article's reference list. However, this kind of offline evaluations is seen critical by many researchers.[[88]](./Recommender_system#cite_note-:4-88)[[89]](./Recommender_system#cite_note-89)[[90]](./Recommender_system#cite_note-:1-90)[[47]](./Recommender_system#cite_note-:0-47) For instance, it has been shown that results of offline evaluations have low correlation with results from user studies or A/B tests.[[90]](./Recommender_system#cite_note-:1-90)[[91]](./Recommender_system#cite_note-91) A dataset popular for offline evaluation has been shown to contain duplicate data and thus to lead to wrong conclusions in the evaluation of algorithms.[[92]](./Recommender_system#cite_note-BasaranNtoutsi2017-92) Often, results of so-called offline evaluations do not correlate with actually assessed user-satisfaction.[[93]](./Recommender_system#cite_note-93) This is probably because offline training is highly biased toward the highly reachable items, and offline testing data is highly influenced by the outputs of the online recommendation module.[[88]](./Recommender_system#cite_note-:4-88)[[94]](./Recommender_system#cite_note-cañamares2018-94) Researchers have concluded that the results of offline evaluations should be viewed critically.[[95]](./Recommender_system#cite_note-cañamares2020-95)

 

### Beyond accuracy

 

Typically, research on recommender systems is concerned with finding the most accurate recommendation algorithms. However, there are a number of factors that are also important.

 
- **Diversity** – Users tend to be more satisfied with recommendations when there is a higher intra-list diversity, e.g. items from different artists.[[96]](./Recommender_system#cite_note-Ziegler2005-96)[[97]](./Recommender_system#cite_note-castells2015-97)

 
- **Recommender persistence** – In some situations, it is more effective to re-show recommendations,[[98]](./Recommender_system#cite_note-Beel2013e-98) or let users re-rate items,[[99]](./Recommender_system#cite_note-Cosley2003-99) than showing new items. There are several reasons for this. Users may ignore items when they are shown for the first time, for instance, because they had no time to inspect the recommendations carefully.
- **Privacy** – Recommender systems usually have to deal with privacy concerns[[100]](./Recommender_system#cite_note-Pu2012-100) because users have to reveal sensitive information. Building [user profiles](./User_profiles) using collaborative filtering can be problematic from a privacy point of view. Many European countries have a strong culture of [data privacy](./Information_privacy), and every attempt to introduce any level of user [profiling](./Profiling_(information_science)) can result in a negative customer response. Much research has been conducted on ongoing privacy issues in this space. The [Netflix Prize](./Netflix_Prize) is particularly notable for the detailed personal information released in its dataset. Ramakrishnan et al. have conducted an extensive overview of the trade-offs between [personalization](./Personalization) and privacy and found that the combination of weak ties (an unexpected connection that provides serendipitous recommendations) and other data sources can be used to uncover identities of users in an anonymized dataset.[[101]](./Recommender_system#cite_note-privacyoverview-101)

 
- **User demographics** – Beel et al. found that user demographics may influence how satisfied users are with recommendations.[[102]](./Recommender_system#cite_note-Beel2013f-102) In their paper they show that elderly users tend to be more interested in recommendations than younger users.
- **Robustness** – When users can participate in the recommender system, the issue of fraud must be addressed.[[103]](./Recommender_system#cite_note-Konstan2012-103)
- **Serendipity** – [Serendipity](./Serendipity) is a measure of "how surprising the recommendations are".[[104]](./Recommender_system#cite_note-Ricci2011-104)[[97]](./Recommender_system#cite_note-castells2015-97) For instance, a recommender system that recommends milk to a customer in a grocery store might be perfectly accurate, but it is not a good recommendation because it is an obvious item for the customer to buy. "[Serendipity] serves two purposes: First, the chance that users lose interest because the choice set is too uniform decreases. Second, these items are needed for algorithms to learn and improve themselves".[[105]](./Recommender_system#cite_note-105)
- **Trust** – A recommender system is of little value for a user if the user does not trust the system.[[106]](./Recommender_system#cite_note-Montaner2002-106) Trust can be built by a recommender system by explaining how it generates recommendations, and why it recommends an item.
- **Labelling** – User satisfaction with recommendations may be influenced by the labeling of the recommendations.[[107]](./Recommender_system#cite_note-Beel2013a-107) For instance, in the cited study [click-through rate](./Click-through_rate) (CTR) for recommendations labeled as "Sponsored" were lower (CTR=5.93%) than CTR for identical recommendations labeled as "Organic" (CTR=8.86%). Recommendations with no label performed best (CTR=9.87%) in that study.

 

### Reproducibility

 

Recommender systems are notoriously difficult to evaluate offline, with some researchers claiming that this has led to a [reproducibility crisis](./Reproducibility_crisis) in recommender systems publications. The topic of reproducibility seems to be a recurrent issue in some Machine Learning publication venues, but does not have a considerable effect beyond the world of scientific publication. In the context of recommender systems a 2019 paper surveyed a small number of hand-picked publications applying deep learning or neural methods to the top-k recommendation problem, published in top conferences (SIGIR, KDD, WWW, [RecSys](./ACM_Conference_on_Recommender_Systems), IJCAI), has shown that on average less than 40% of articles could be reproduced by the authors of the survey, with as little as 14% in some conferences. The articles considers a number of potential problems in today's research scholarship and suggests improved scientific practices in that area.[[108]](./Recommender_system#cite_note-108)[[109]](./Recommender_system#cite_note-109)[[110]](./Recommender_system#cite_note-110)
More recent work on benchmarking a set of the same methods came to qualitatively very different results[[111]](./Recommender_system#cite_note-111) whereby neural methods were found to be among the best performing methods. Deep learning and neural methods for recommender systems have been used in the winning solutions in several recent recommender system challenges, WSDM,[[112]](./Recommender_system#cite_note-112) [RecSys Challenge](./RecSys_Challenge?action=edit&redlink=1).[[113]](./Recommender_system#cite_note-113)
Moreover, neural and deep learning methods are widely used in industry where they are extensively tested.[[114]](./Recommender_system#cite_note-ntfx-114)[[64]](./Recommender_system#cite_note-yt-64)[[65]](./Recommender_system#cite_note-amzn-65) The topic of reproducibility is not new in recommender systems. By 2011, [Ekstrand](./Michael_Ekstrand?action=edit&redlink=1), [Konstan](./Joseph_A._Konstan), et al. criticized that "it is currently difficult to reproduce and extend recommender systems research results," and that evaluations are "not handled consistently".[[115]](./Recommender_system#cite_note-115) Konstan and Adomavicius conclude that "the Recommender Systems research community is facing a crisis where a significant number of papers present results that contribute little to collective knowledge [...] often because the research lacks the [...] evaluation to be properly judged and, hence, to provide meaningful contributions."[[116]](./Recommender_system#cite_note-116) As a consequence, much research about recommender systems can be considered as not reproducible.[[117]](./Recommender_system#cite_note-:2-117) Hence, operators of recommender systems find little guidance in the current research for answering the question, which recommendation approaches to use in a recommender systems. [Said](./Alan_Said?action=edit&redlink=1) and [Bellogín](./Alejandro_Bellogín?action=edit&redlink=1) conducted a study of papers published in the field, as well as benchmarked some of the most popular frameworks for recommendation and found large inconsistencies in results, even when the same algorithms and data sets were used.[[118]](./Recommender_system#cite_note-118) Some researchers demonstrated that minor variations in the recommendation algorithms or scenarios led to strong changes in the effectiveness of a recommender system. They conclude that seven actions are necessary to improve the current situation:[[117]](./Recommender_system#cite_note-:2-117) "(1) survey other research fields and learn from them, (2) find a common understanding of reproducibility, (3) identify and understand the determinants that affect reproducibility, (4) conduct more comprehensive experiments (5) modernize publication practices, (6) foster the development and use of recommendation frameworks, and (7) establish best-practice guidelines for recommender-systems research."

 

## Artificial intelligence applications in recommendation

 
|  | This sectionneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sourcesin this section. Unsourced material may be challenged and removed.(October 2023)(Learn how and when to remove this message) |
| --- | --- |

 

[Artificial intelligence](./Artificial_intelligence) (AI) applications in recommendation systems are the advanced methodologies that leverage AI technologies, to enhance the performance recommendation engines. The AI-based recommender can analyze complex data sets, learning from user behavior, preferences, and interactions to generate highly accurate and personalized content or product suggestions.[[119]](./Recommender_system#cite_note-119) The integration of AI in recommendation systems has marked a significant evolution from traditional recommendation methods. Traditional methods often relied on inflexible algorithms that could suggest items based on general user trends or apparent similarities in content. In comparison, AI-powered systems have the capability to detect patterns and subtle distinctions that may be overlooked by traditional methods.[[120]](./Recommender_system#cite_note-120) These systems can adapt to specific individual preferences, thereby offering recommendations that are more aligned with individual user needs. This approach marks a shift towards more personalized, user-centric suggestions.

 

Recommendation systems widely adopt AI techniques such as [machine learning](./Machine_learning), [deep learning](./Deep_learning), and [natural language processing](./Natural_language_processing).[[121]](./Recommender_system#cite_note-Artificial_intelligence_in_recommen-121) These advanced methods enhance system capabilities to predict user preferences and deliver personalized content more accurately. Each technique contributes uniquely. The following sections will introduce specific AI models utilized by a recommendation system by illustrating their theories and functionalities.[*[citation needed](./Wikipedia:Citation_needed)*]

 

### KNN-based collaborative filters

 

[Collaborative filtering](./Collaborative_filtering) (CF) is one of the most commonly used recommendation system algorithms. It generates personalized suggestions for users based on explicit or implicit behavioral patterns to form predictions.[[122]](./Recommender_system#cite_note-122) Specifically, it relies on external feedback such as star ratings, purchasing history and so on to make judgments. CF make predictions about users' preference based on similarity measurements. Essentially, the underlying theory is: "if user A is similar to user B, and if A likes item C, then it is likely that B also likes item C."

 

There are many models available for collaborative filtering. For AI-applied collaborative filtering, a common model is called [K-nearest neighbors](./K-nearest_neighbors_algorithm). The ideas are as follows:

 
1. **Data Representation**: Create a n-dimensional space where each axis represents a user's trait (ratings, purchases, etc.). Represent the user as a point in that space.
2. **Statistical Distance**: 'Distance' measures how far apart users are in this space. See [statistical distance](./Statistical_distance) for computational details
3. **Identifying Neighbors**: Based on the computed distances, find k nearest neighbors of the user to which we want to make recommendations
4. **Forming Predictive Recommendations**: The system will analyze the similar preference of the k neighbors. The system will make recommendations based on that similarity

 

### Neural networks

 

An [artificial neural network](./Artificial_neural_network) (ANN), is a deep learning model structure which aims to mimic a human brain. They comprise a series of neurons, each responsible for receiving and processing information transmitted from other interconnected neurons.[[123]](./Recommender_system#cite_note-123) Similar to a human brain, these neurons will change activation state based on incoming signals (training input and backpropagated output), allowing the system to adjust activation weights during the network learning phase. ANN is usually designed to be a [black-box](./Black_box) model. Unlike regular machine learning where the underlying theoretical components are formal and rigid, the collaborative effects of neurons are not entirely clear, but modern experiments has shown the predictive power of ANN.

 

ANN is widely used in recommendation systems for its power to utilize various data. Other than feedback data, ANN can incorporate non-feedback data which are too intricate for collaborative filtering to learn, and the unique structure allows ANN to identify extra signal from non-feedback data to boost user experience.[[121]](./Recommender_system#cite_note-Artificial_intelligence_in_recommen-121) Following are some examples:

 
- **Time and Seasonality**: what specify time and date or a season that a user interacts with the platform
- **User Navigation Patterns**: sequence of pages visited, time spent on different parts of a website, mouse movement, etc.
- **External Social Trends**: information from outer social media

 

#### Two-Tower Model

 

The Two-Tower model is a neural architecture[[124]](./Recommender_system#cite_note-124) commonly employed in large-scale recommendation systems, particularly for candidate retrieval tasks.[[125]](./Recommender_system#cite_note-125) It consists of two neural networks:

 
- **User Tower**: Encodes user-specific features, such as interaction history or demographic data.
- **Item Tower**: Encodes item-specific features, such as [metadata](./Metadata) or content embeddings.

 

The outputs of the two towers are fixed-length embeddings that represent users and items in a shared vector space. A similarity metric, such as [dot product](./Dot_product) or [cosine similarity](./Cosine_similarity), is used to measure relevance between a user and an item.

 

This model is highly efficient for large datasets as embeddings can be pre-computed for items, allowing rapid retrieval during inference. It is often used in conjunction with ranking models for end-to-end recommendation pipelines.

 

### Natural language processing

 

Natural language processing is a series of AI algorithms to make natural human language accessible and analyzable to a machine.[[126]](./Recommender_system#cite_note-126) It is a fairly modern technique inspired by the growing amount of textual information. For application in recommendation system, a common case is the Amazon [customer review](./Customer_review). Amazon will analyze the feedbacks comments from each customer and report relevant data to other customers for reference. The recent years have witnessed the development of various text analysis models, including [latent semantic analysis](./Latent_semantic_analysis) (LSA), [singular value decomposition](./Singular_value_decomposition) (SVD), [latent Dirichlet allocation](./Latent_Dirichlet_allocation) (LDA), etc. Their uses have consistently aimed to provide customers with more precise and tailored recommendations.

 

## See also

  
- [Algorithmic radicalization](./Algorithmic_radicalization)
- [ACM Conference on Recommender Systems](./ACM_Conference_on_Recommender_Systems)
- [Cold start](./Cold_start_(recommender_systems))
- [Collaborative filtering](./Collaborative_filtering)
- [Collective intelligence](./Collective_intelligence)
- [Configurator](./Configurator)
- [Content moderation](./Content_moderation)
- [Enterprise bookmarking](./Enterprise_bookmarking)
- [Filter bubble](./Filter_bubble)
- [Information filtering system](./Information_filtering_system)
- [Information explosion](./Information_explosion)
- [K.G.M. v. Meta et al.](./K.G.M._v._Meta_et_al.)
- [Media monitoring service](./Media_monitoring_service)
- [Pattern recognition](./Pattern_recognition)
- [Personalized marketing](./Personalized_marketing)
- [Personalized search](./Personalized_search)
- [Preference elicitation](./Preference_elicitation)
- [Product finder](./Product_finder)
- [Rating site](./Rating_site)
- [Reputation management](./Reputation_management)
- [Reputation system](./Reputation_system)

  

## References

 
1. [1](./Recommender_system#cite_ref-handbook_1-0) [2](./Recommender_system#cite_ref-handbook_1-1) [3](./Recommender_system#cite_ref-handbook_1-2) [4](./Recommender_system#cite_ref-handbook_1-3) Ricci, Francesco; Rokach, Lior; Shapira, Bracha (2022). ["Recommender Systems: Techniques, Applications, and Challenges"](https://link.springer.com/chapter/10.1007/978-1-0716-2197-4_1). In Ricci, Francesco; Rokach, Lior; Shapira, Bracha (eds.). *Recommender Systems Handbook* (3 ed.). New York: Springer. pp. 1–35. [doi](./Doi_(identifier)):[10.1007/978-1-0716-2197-4_1](https://doi.org/10.1007%2F978-1-0716-2197-4_1). [ISBN](./ISBN_(identifier)) [978-1-0716-2196-7](./Special:BookSources/978-1-0716-2196-7).
2. [↑](./Recommender_system#cite_ref-2) Lev Grossman (May 27, 2010). ["How Computers Know What We Want — Before We Do"](https://web.archive.org/web/20100530064045/http://www.time.com/time/magazine/article/0,9171,1992403,00.html). *TIME*. Archived from [the original](http://www.time.com/time/magazine/article/0,9171,1992403,00.html) on May 30, 2010. Retrieved June 1, 2015.
3. [↑](./Recommender_system#cite_ref-3) Roy, Deepjyoti; Dutta, Mala (2022). ["A systematic review and research perspective on recommender systems"](https://doi.org/10.1186%2Fs40537-022-00592-5). *[Journal of Big Data](./Journal_of_Big_Data)*. **9** (59) 59. [doi](./Doi_(identifier)):[10.1186/s40537-022-00592-5](https://doi.org/10.1186%2Fs40537-022-00592-5).
4. [1](./Recommender_system#cite_ref-ResnickVarian_4-0) [2](./Recommender_system#cite_ref-ResnickVarian_4-1) Resnick, Paul, and Hal R. Varian. "Recommender systems." Communications of the ACM 40, no. 3 (1997): 56–58.
5. [↑](./Recommender_system#cite_ref-5) ["Twitter/The-algorithm"](https://github.com/twitter/the-algorithm). *[GitHub](./GitHub)*.
6. [↑](./Recommender_system#cite_ref-6) ["Xai-org/X-algorithm"](https://github.com/xai-org/x-algorithm). *[GitHub](./GitHub)*.
7. [↑](./Recommender_system#cite_ref-twitterwtf2_7-0) Gupta, Pankaj; Goel, Ashish; Lin, Jimmy; Sharma, Aneesh; Wang, Dong; Zadeh, Reza (2013). "WTF: the who to follow service at Twitter". *Proceedings of the 22nd International Conference on World Wide Web*. Association for Computing Machinery. pp. 505–514. [doi](./Doi_(identifier)):[10.1145/2488388.2488433](https://doi.org/10.1145%2F2488388.2488433). [ISBN](./ISBN_(identifier)) [9781450320351](./Special:BookSources/9781450320351).
8. [↑](./Recommender_system#cite_ref-8) Baran, Remigiusz; Dziech, Andrzej; Zeja, Andrzej (June 1, 2018). ["A capable multimedia content discovery platform based on visual content analysis and intelligent data enrichment"](https://doi.org/10.1007%2Fs11042-017-5014-1). *Multimedia Tools and Applications*. **77** (11): 14077–14091. [doi](./Doi_(identifier)):[10.1007/s11042-017-5014-1](https://doi.org/10.1007%2Fs11042-017-5014-1). [ISSN](./ISSN_(identifier)) [1573-7721](https://search.worldcat.org/issn/1573-7721). [S2CID](./S2CID_(identifier)) [36511631](https://api.semanticscholar.org/CorpusID:36511631).
9. [↑](./Recommender_system#cite_ref-expertseer_9-0) H. Chen, A. G. Ororbia II, C. L. Giles [ExpertSeer: a Keyphrase Based Expert Recommender for Digital Libraries](https://arxiv.org/abs/1511.02058), in arXiv preprint 2015
10. [↑](./Recommender_system#cite_ref-collabseer_10-0) Chen, Hung-Hsuan; Gou, Liang; Zhang, Xiaolong; Giles, Clyde Lee (2011). ["CollabSeer: a search engine for collaboration discovery"](https://clgiles.ist.psu.edu/pubs/JCDL2011-CollabSeer.pdf) (PDF). *Proceedings of the 11th Annual International ACM/IEEE Joint Conference on Digital Libraries*. Association for Computing Machinery. pp. 231–240. [doi](./Doi_(identifier)):[10.1145/1998076.1998121](https://doi.org/10.1145%2F1998076.1998121). [ISBN](./ISBN_(identifier)) [9781450307444](./Special:BookSources/9781450307444).
11. [↑](./Recommender_system#cite_ref-financialrec_11-0) Felfernig, Alexander; Isak, Klaus; Szabo, Kalman; Zachar, Peter (2007). ["The VITA Financial Services Sales Support Environment"](https://cdn.aaai.org/AAAI/2007/AAAI07-274.pdf) (PDF). In William Cheetham (ed.). *Proceedings of the 19th National Conference on Innovative Applications of Artificial Intelligence, vol. 2*. pp. 1692–1699. [ISBN](./ISBN_(identifier)) [9781577353232](./Special:BookSources/9781577353232). [ACM Copy](https://dl.acm.org/doi/10.5555/1620113.1620117).
12. [1](./Recommender_system#cite_ref-nature1_12-0) [2](./Recommender_system#cite_ref-nature1_12-1) jobs (September 3, 2014). ["How to tame the flood of literature : Nature News & Comment"](https://doi.org/10.1038%2F513129a). *Nature*. **513** (7516). Nature.com: 129–130. [doi](./Doi_(identifier)):[10.1038/513129a](https://doi.org/10.1038%2F513129a). [PMID](./PMID_(identifier)) [25186906](https://pubmed.ncbi.nlm.nih.gov/25186906). [S2CID](./S2CID_(identifier)) [4460749](https://api.semanticscholar.org/CorpusID:4460749).
13. [↑](./Recommender_system#cite_ref-13) Analysis (December 14, 2011). ["Netflix Revamps iPad App to Improve Content Discovery"](https://www.wired.com/2011/12/netflix-revamps-ipad-app-to-improve-content-discovery/). WIRED. Retrieved December 31, 2015.
14. [↑](./Recommender_system#cite_ref-Recommender2010_14-0) Melville, Prem; Sindhwani, Vikas (2010). ["Recommender Systems"](http://www.prem-melville.com/publications/recommender-systems-eml2010.pdf) (PDF). In Claude Sammut; Geoffrey I. Webb (eds.). *Encyclopedia of Machine Learning*. Springer. pp. 829–838. [doi](./Doi_(identifier)):[10.1007/978-0-387-30164-8_705](https://doi.org/10.1007%2F978-0-387-30164-8_705). [ISBN](./ISBN_(identifier)) [978-0-387-30164-8](./Special:BookSources/978-0-387-30164-8).
15. [↑](./Recommender_system#cite_ref-mooney99_15-0) R. J. Mooney & L. Roy (1999). *Content-based book recommendation using learning for text categorization*. In Workshop Recom. Sys.: Algo. and Evaluation.
16. [↑](./Recommender_system#cite_ref-16) Haupt, Jon (June 1, 2009). "Last.fm: People-Powered Online Radio". *Music Reference Services Quarterly*. **12** (1–2): 23–24. [doi](./Doi_(identifier)):[10.1080/10588160902816702](https://doi.org/10.1080%2F10588160902816702). [ISSN](./ISSN_(identifier)) [1058-8167](https://search.worldcat.org/issn/1058-8167). [S2CID](./S2CID_(identifier)) [161141937](https://api.semanticscholar.org/CorpusID:161141937).
17. [↑](./Recommender_system#cite_ref-17) ["About The Music Genome Project®"](https://web.archive.org/web/20140814183042/https://www.pandora.com/about/mgp). *www.pandora.com*. Archived from [the original](https://www.pandora.com/about/mgp) on August 14, 2014. Retrieved June 3, 2025.
18. [1](./Recommender_system#cite_ref-:3_18-0) [2](./Recommender_system#cite_ref-:3_18-1) Chen, Hung-Hsuan; Chen, Pu (January 9, 2019). "Differentiating Regularization Weights -- A Simple Mechanism to Alleviate Cold Start in Recommender Systems". *ACM Transactions on Knowledge Discovery from Data*. **13**: 1–22. [doi](./Doi_(identifier)):[10.1145/3285954](https://doi.org/10.1145%2F3285954). [S2CID](./S2CID_(identifier)) [59337456](https://api.semanticscholar.org/CorpusID:59337456).
19. [1](./Recommender_system#cite_ref-rubens2016_19-0) [2](./Recommender_system#cite_ref-rubens2016_19-1) Rubens, Neil; Elahi, Mehdi; Sugiyama, Masashi; Kaplan, Dain (2016). ["Active Learning in Recommender Systems"](https://rd.springer.com/book/10.1007/978-1-4899-7637-6). In Ricci, Francesco; Rokach, Lior; Shapira, Bracha (eds.). *Recommender Systems Handbook* (2 ed.). Springer US. pp. 809–846. [doi](./Doi_(identifier)):[10.1007/978-1-4899-7637-6_24](https://doi.org/10.1007%2F978-1-4899-7637-6_24). [ISBN](./ISBN_(identifier)) [978-1-4899-7637-6](./Special:BookSources/978-1-4899-7637-6).
20. [↑](./Recommender_system#cite_ref-20) Bobadilla, J.; Ortega, F.; Hernando, A.; Alcalá, J. (2011). "Improving collaborative filtering recommender system results and performance using genetic algorithms". *Knowledge-Based Systems*. **24** (8): 1310–1316. [doi](./Doi_(identifier)):[10.1016/j.knosys.2011.06.005](https://doi.org/10.1016%2Fj.knosys.2011.06.005).
21. [1](./Recommender_system#cite_ref-elahi2016_21-0) [2](./Recommender_system#cite_ref-elahi2016_21-1)  Elahi, Mehdi; Ricci, Francesco; Rubens, Neil (2016). ["A survey of active learning in collaborative filtering recommender systems"](https://bia.unibz.it/view/delivery/39UBZ_INST/12291577960001241/13291617600001241). *Computer Science Review*. **20**: 29–50. [doi](./Doi_(identifier)):[10.1016/j.cosrev.2016.05.002](https://doi.org/10.1016%2Fj.cosrev.2016.05.002). 
22. [↑](./Recommender_system#cite_ref-schein02_22-0)  Andrew I. Schein; Alexandrin Popescul; [Lyle H. Ungar](./Lyle_Ungar); David M. Pennock (2002). [*Methods and Metrics for Cold-Start Recommendations*](https://archive.org/details/sigir2002proceed0000inte/page/253). Proceedings of the 25th Annual International [ACM](./Association_for_Computing_Machinery) [SIGIR](./Special_Interest_Group_on_Information_Retrieval) Conference on Research and Development in Information Retrieval (SIGIR 2002). [ACM](./Association_for_Computing_Machinery). pp. [253–260](https://archive.org/details/sigir2002proceed0000inte/page/253). [ISBN](./ISBN_(identifier)) [1-58113-561-0](./Special:BookSources/1-58113-561-0). Retrieved February 2, 2008. 
23. [1](./Recommender_system#cite_ref-bi2017_23-0) [2](./Recommender_system#cite_ref-bi2017_23-1) Bi, Xuan; Qu, Annie; Wang, Junhui; Shen, Xiaotong (2017). ["A group-specific recommender system"](https://figshare.com/articles/journal_contribution/A_Group-Specific_Recommender_System/3803748/1/files/5921967.pdf) (PDF). *Journal of the American Statistical Association*. **112** (519): 1344–1353. [doi](./Doi_(identifier)):[10.1080/01621459.2016.1219261](https://doi.org/10.1080%2F01621459.2016.1219261). [S2CID](./S2CID_(identifier)) [125187672](https://api.semanticscholar.org/CorpusID:125187672).
24. [↑](./Recommender_system#cite_ref-24) Bengani, Jonathan Stray, Luke Thorburn, Priyanjana (October 16, 2023). ["What's the Difference Between Search and Recommendation? | TechPolicy.Press"](https://techpolicy.press/whats-the-difference-between-search-and-recommendation). *Tech Policy Press*. Retrieved June 3, 2025.`{{cite web}}`:  CS1 maint: multiple names: authors list ([link](./Category:CS1_maint:_multiple_names:_authors_list))
25. [↑](./Recommender_system#cite_ref-25) Stack, Charles. "[System and method for providing recommendation of goods and services based on recorded purchasing history](https://patentimages.storage.googleapis.com/pdfs/US6782370.pdf)." U.S. Patent 7,222,085, issued May 22, 2007.
26. [↑](./Recommender_system#cite_ref-26) Herz, Frederick SM. "Customized electronic newspapers and advertisements." U.S. Patent 7,483,871, issued January 27, 2009.

27. [↑](./Recommender_system#cite_ref-27) 
Herz, Frederick, Lyle Ungar, Jian Zhang, and David Wachob. "[System and method for providing access to data using customer profiles](https://patentimages.storage.googleapis.com/3c/1b/54/5c6688e454a63a/US8056100.pdf)." U.S. Patent 8,056,100, issued November 8, 2011.

28. [↑](./Recommender_system#cite_ref-28) 
Harbick, Andrew V., Ryan J. Snodgrass, and Joel R. Spiegel. "[Playlist-based detection of similar digital works and work creators](https://patents.google.com/patent/US8468046B2/en)." U.S. Patent 8,468,046, issued June 18, 2013.

29. [↑](./Recommender_system#cite_ref-29) 
Linden, Gregory D., Brent Russell Smith, and Nida K. Zada. "[Automated detection and exposure of behavior-based relationships between browsable items](https://patentimages.storage.googleapis.com/3c/f6/13/d5f70fcdcf1b6d/US9070156.pdf)." U.S. Patent 9,070,156, issued June 30, 2015.
30. [↑](./Recommender_system#cite_ref-30) ["Recommender-System Software Libraries & APIs – RS_c"](https://recommender-systems.com/resources/software-libraries/). Retrieved November 18, 2024.
31. [↑](./Recommender_system#cite_ref-31) Ekstrand, Michael (August 21, 2018). ["The LKPY Package for Recommender Systems Experiments"](https://scholarworks.boisestate.edu/cs_facpubs/147/). *Computer Science Faculty Publications and Presentations*. Boise State University, ScholarWorks. [doi](./Doi_(identifier)):[10.18122/cs_facpubs/147/boisestate](https://doi.org/10.18122%2Fcs_facpubs%2F147%2Fboisestate).
32. [↑](./Recommender_system#cite_ref-32) Vente, Tobias; Ekstrand, Michael; Beel, Joeran (September 14, 2023). ["Introducing LensKit-Auto, an Experimental Automated Recommender System (AutoRecSys) Toolkit"](https://dl.acm.org/doi/10.1145/3604915.3610656). *Proceedings of the 17th ACM Conference on Recommender Systems*. ACM. pp. 1212–1216. [doi](./Doi_(identifier)):[10.1145/3604915.3610656](https://doi.org/10.1145%2F3604915.3610656). [ISBN](./ISBN_(identifier)) [979-8-4007-0241-9](./Special:BookSources/979-8-4007-0241-9).
33. [↑](./Recommender_system#cite_ref-33) Zhao, Wayne Xin; Mu, Shanlei; Hou, Yupeng; Lin, Zihan; Chen, Yushuo; Pan, Xingyu; Li, Kaiyuan; Lu, Yujie; Wang, Hui; Tian, Changxin; Min, Yingqian; Feng, Zhichao; Fan, Xinyan; Chen, Xu; Wang, Pengfei (October 26, 2021). ["RecBole: Towards a Unified, Comprehensive and Efficient Framework for Recommendation Algorithms"](https://dl.acm.org/doi/10.1145/3459637.3482016). *Proceedings of the 30th ACM International Conference on Information & Knowledge Management*. ACM. pp. 4653–4664. [arXiv](./ArXiv_(identifier)):[2011.01731](https://arxiv.org/abs/2011.01731). [doi](./Doi_(identifier)):[10.1145/3459637.3482016](https://doi.org/10.1145%2F3459637.3482016). [ISBN](./ISBN_(identifier)) [978-1-4503-8446-9](./Special:BookSources/978-1-4503-8446-9).
34. [↑](./Recommender_system#cite_ref-34) Li, Jiayu; Li, Hanyu; He, Zhiyu; Ma, Weizhi; Sun, Peijie; Zhang, Min; Ma, Shaoping (October 8, 2024). ["ReChorus2.0: A Modular and Task-Flexible Recommendation Library"](https://dl.acm.org/doi/10.1145/3640457.3688076). *18th ACM Conference on Recommender Systems*. ACM. pp. 454–464. [doi](./Doi_(identifier)):[10.1145/3640457.3688076](https://doi.org/10.1145%2F3640457.3688076). [ISBN](./ISBN_(identifier)) [979-8-4007-0505-2](./Special:BookSources/979-8-4007-0505-2).
35. [↑](./Recommender_system#cite_ref-35) Michiels, Lien; Verachtert, Robin; Goethals, Bart (September 18, 2022). ["RecPack: An(other) Experimentation Toolkit for Top-N Recommendation using Implicit Feedback Data"](https://dl.acm.org/doi/10.1145/3523227.3551472). *Proceedings of the 16th ACM Conference on Recommender Systems*. ACM. pp. 648–651. [doi](./Doi_(identifier)):[10.1145/3523227.3551472](https://doi.org/10.1145%2F3523227.3551472). [ISBN](./ISBN_(identifier)) [978-1-4503-9278-5](./Special:BookSources/978-1-4503-9278-5).
36. [↑](./Recommender_system#cite_ref-36) BEEL, Joeran, et al. Paper recommender systems: a literature survey. International Journal on Digital Libraries, 2016, 17. Jg., Nr. 4, S. 305–338.
37. [↑](./Recommender_system#cite_ref-37) RICH, Elaine. User modeling via stereotypes. Cognitive science, 1979, 3. Jg., Nr. 4, S. 329–354.
38. [↑](./Recommender_system#cite_ref-38) Karlgren, Jussi. "[An Algebra for Recommendations.](https://jussikarlgren.wordpress.com/wp-content/uploads/1990/09/algebrawp.pdf)[Archived](https://web.archive.org/web/20240525022319/https://jussikarlgren.wordpress.com/wp-content/uploads/1990/09/algebrawp.pdf) 2024-05-25 at the [Wayback Machine](./Wayback_Machine).  Syslab Working Paper 179 (1990). " 
39. [↑](./Recommender_system#cite_ref-39) Karlgren, Jussi. "[Newsgroup Clustering Based On User Behavior-A Recommendation Algebra](http://soda.swedish-ict.se/2225/2/T94_04.pdf) [Archived](https://web.archive.org/web/20210227090805/http://soda.swedish-ict.se/2225/2/T94_04.pdf) February 27, 2021, at the [Wayback Machine](./Wayback_Machine)." SICS Research Report (1994).
40. [↑](./Recommender_system#cite_ref-40) Karlgren, Jussi (October 2017). ["A digital bookshelf: original work on recommender systems"](https://jussikarlgren.wordpress.com/2017/10/01/a-digital-bookshelf-original-work-on-recommender-systems/). Retrieved October 27, 2017.
41. [↑](./Recommender_system#cite_ref-41) 
Shardanand, Upendra, and Pattie Maes. "[Social information filtering: algorithms for automating "word of mouth"](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.30.6583&rep=rep1&type=pdf)." In Proceedings of the SIGCHI conference on Human factors in computing systems, pp. 210–217. ACM Press/Addison-Wesley Publishing Co., 1995.

42. [↑](./Recommender_system#cite_ref-42) Hill, Will, Larry Stead, Mark Rosenstein, and George Furnas. "[Recommending and evaluating choices in a virtual community of use](http://zhang.ist.psu.edu/teaching/501/readings/Hill.pdf) [Archived](https://web.archive.org/web/20181221074205/http://zhang.ist.psu.edu/teaching/501/readings/Hill.pdf) 2018-12-21 at the [Wayback Machine](./Wayback_Machine)." In Proceedings of the SIGCHI conference on Human factors in computing systems, pp. 194–201. ACM Press/Addison-Wesley Publishing Co., 1995.
43. [↑](./Recommender_system#cite_ref-43) Resnick, Paul, Neophytos Iacovou, Mitesh Suchak, Peter Bergström, and John Riedl. "[GroupLens: an open architecture for collaborative filtering of netnews](https://sites.ualberta.ca/~golmoham/SW/web%20mining%2023Jan2008/GroupLens%20An%20Open%20Architecture%20for%20Collaborating%20Filtering%20%20of%20Netnews.pdf)." In Proceedings of the 1994 ACM conference on Computer supported cooperative work, pp. 175–186. ACM, 1994.
44. [↑](./Recommender_system#cite_ref-44) Montaner, M.; Lopez, B.; de la Rosa, J. L. (June 2003). "A Taxonomy of Recommender Agents on the Internet". *Artificial Intelligence Review*. **19** (4): 285–330. [doi](./Doi_(identifier)):[10.1023/A:1022850703159](https://doi.org/10.1023%2FA%3A1022850703159). [S2CID](./S2CID_(identifier)) [16544257](https://api.semanticscholar.org/CorpusID:16544257)..
45. [1](./Recommender_system#cite_ref-Toward_the_Next_Generation_of_Recommender_Systems_45-0) [2](./Recommender_system#cite_ref-Toward_the_Next_Generation_of_Recommender_Systems_45-1) Adomavicius, G.; [Tuzhilin, A.](./Alexander_Tuzhilin) (June 2005). ["Toward the Next Generation of Recommender Systems: A Survey of the State-of-the-Art and Possible Extensions"](http://portal.acm.org/citation.cfm?id=1070611.1070751). *IEEE Transactions on Knowledge and Data Engineering*. **17** (6): 734–749. [Bibcode](./Bibcode_(identifier)):[2005IDSO...17..734A](https://ui.adsabs.harvard.edu/abs/2005IDSO...17..734A). [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.107.2790](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.107.2790). [doi](./Doi_(identifier)):[10.1109/TKDE.2005.99](https://doi.org/10.1109%2FTKDE.2005.99). [S2CID](./S2CID_(identifier)) [206742345](https://api.semanticscholar.org/CorpusID:206742345)..
46. [↑](./Recommender_system#cite_ref-46) Herlocker, J. L.; Konstan, J. A.; Terveen, L. G.; Riedl, J. T. (January 2004). "Evaluating collaborative filtering recommender systems". *ACM Trans. Inf. Syst*. **22** (1): 5–53. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.78.8384](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.78.8384). [doi](./Doi_(identifier)):[10.1145/963770.963772](https://doi.org/10.1145%2F963770.963772). [S2CID](./S2CID_(identifier)) [207731647](https://api.semanticscholar.org/CorpusID:207731647)..
47. [1](./Recommender_system#cite_ref-:0_47-0) [2](./Recommender_system#cite_ref-:0_47-1) [3](./Recommender_system#cite_ref-:0_47-2) Beel, J.; Genzmehr, M.; Gipp, B. (October 2013). ["A comparative analysis of offline and online evaluations and discussion of research paper recommender system evaluation"](https://web.archive.org/web/20160417222305/http://docear.org/papers/a_comparative_analysis_of_offline_and_online_evaluations_and_discussion_of_research_paper_recommender_system_evaluation.pdf) (PDF). *Proceedings of the International Workshop on Reproducibility and Replication in Recommender Systems Evaluation*. pp. 7–14. [doi](./Doi_(identifier)):[10.1145/2532508.2532511](https://doi.org/10.1145%2F2532508.2532511). [ISBN](./ISBN_(identifier)) [978-1-4503-2465-6](./Special:BookSources/978-1-4503-2465-6). [S2CID](./S2CID_(identifier)) [8202591](https://api.semanticscholar.org/CorpusID:8202591). Archived from [the original](http://docear.org/papers/a_comparative_analysis_of_offline_and_online_evaluations_and_discussion_of_research_paper_recommender_system_evaluation.pdf) (PDF) on April 17, 2016. Retrieved October 22, 2013.
48. [↑](./Recommender_system#cite_ref-48) Beel, J.; Langer, S.; Genzmehr, M.; Gipp, B.; Breitinger, C. (October 2013). ["Research paper recommender system evaluation: A quantitative literature survey"](http://docear.org/papers/research_paper_recommender_system_evaluation--a_quantitative_literature_survey.pdf) (PDF). [*Proceedings of the International Workshop on Reproducibility and Replication in Recommender Systems Evaluation*](http://nbn-resolving.de/urn:nbn:de:bsz:352-0-285593). pp. 15–22. [doi](./Doi_(identifier)):[10.1145/2532508.2532512](https://doi.org/10.1145%2F2532508.2532512). [ISBN](./ISBN_(identifier)) [978-1-4503-2465-6](./Special:BookSources/978-1-4503-2465-6). [S2CID](./S2CID_(identifier)) [4411601](https://api.semanticscholar.org/CorpusID:4411601).
49. [↑](./Recommender_system#cite_ref-49) Beel, J.; Gipp, B.; Langer, S.; Breitinger, C. (July 26, 2015). ["Research Paper Recommender Systems: A Literature Survey"](http://nbn-resolving.de/urn:nbn:de:bsz:352-0-311312). *International Journal on Digital Libraries*. **17** (4): 305–338. [doi](./Doi_(identifier)):[10.1007/s00799-015-0156-0](https://doi.org/10.1007%2Fs00799-015-0156-0). [S2CID](./S2CID_(identifier)) [207035184](https://api.semanticscholar.org/CorpusID:207035184).
50. [↑](./Recommender_system#cite_ref-Breese98_50-0) John S. Breese; David Heckerman & Carl Kadie (1998). *Empirical analysis of predictive algorithms for collaborative filtering*. In Proceedings of the Fourteenth conference on Uncertainty in artificial intelligence (UAI'98). [arXiv](./ArXiv_(identifier)):[1301.7363](https://arxiv.org/abs/1301.7363). 
51. [↑](./Recommender_system#cite_ref-51) Sarwar, B.; Karypis, G.; Konstan, J.; Riedl, J. (2000). ["Application of Dimensionality Reduction in Recommender System A Case Study"](https://web.archive.org/web/20190114043334/http://glaros.dtc.umn.edu/gkhome/node/122). Archived from [the original](http://glaros.dtc.umn.edu/gkhome/node/122) on January 14, 2019. Retrieved January 29, 2008.,
52. [↑](./Recommender_system#cite_ref-52) Allen, R.B. (1990). *User Models: Theory, Method, Practice*. International J. Man-Machine Studies.
53. [↑](./Recommender_system#cite_ref-Lee2007_53-0) Sanghack Lee and Jihoon Yang and Sung-Yong Park, [Discovery of Hidden Similarity on Collaborative Filtering to Overcome Sparsity Problem](https://books.google.com/books?id=u4qzlZAEjegC&dq=sparsity+problem+content-based&pg=PA396), Discovery Science, 2007.
54. [↑](./Recommender_system#cite_ref-54) Felício, Crícia Z.; Paixão, Klérisson V.R.; Barcelos, Celia A.Z.; Preux, Philippe (July 9, 2017). ["A Multi-Armed Bandit Model Selection for Cold-Start User Recommendation"](https://doi.org/10.1145/3079628.3079681). [*Proceedings of the 25th Conference on User Modeling, Adaptation and Personalization*](https://hal.inria.fr/hal-01517967/file/umap2017.4hal.pdf) (PDF). UMAP '17. Bratislava, Slovakia: Association for Computing Machinery. pp. 32–40. [doi](./Doi_(identifier)):[10.1145/3079628.3079681](https://doi.org/10.1145%2F3079628.3079681). [ISBN](./ISBN_(identifier)) [978-1-4503-4635-1](./Special:BookSources/978-1-4503-4635-1). [S2CID](./S2CID_(identifier)) [653908](https://api.semanticscholar.org/CorpusID:653908).
55. [↑](./Recommender_system#cite_ref-Aggarwal16Book_55-0) Aggarwal, Charu C. (2016). *Recommender Systems: The Textbook*. Springer. [ISBN](./ISBN_(identifier)) [978-3-319-29657-9](./Special:BookSources/978-3-319-29657-9).
56. [↑](./Recommender_system#cite_ref-56) [Peter Brusilovsky](./Peter_Brusilovsky) (2007). [*The Adaptive Web*](https://archive.org/details/adaptivewebmetho00brus). Springer. p. [325](https://archive.org/details/adaptivewebmetho00brus/page/n331). [ISBN](./ISBN_(identifier)) [978-3-540-72078-2](./Special:BookSources/978-3-540-72078-2).
57. [↑](./Recommender_system#cite_ref-57) Wang, Donghui; Liang, Yanchun; Xu, Dong; Feng, Xiaoyue; Guan, Renchu (2018). ["A content-based recommender system for computer science publications"](https://doi.org/10.1016%2Fj.knosys.2018.05.001). *Knowledge-Based Systems*. **157**: 1–9. [doi](./Doi_(identifier)):[10.1016/j.knosys.2018.05.001](https://doi.org/10.1016%2Fj.knosys.2018.05.001).
58. [↑](./Recommender_system#cite_ref-58) Blanda, Stephanie (May 25, 2015). ["Online Recommender Systems – How Does a Website Know What I Want?"](http://blogs.ams.org/mathgradblog/2015/05/25/online-recommender-systems-website-want/). *American Mathematical Society*. Retrieved October 31, 2016.
59. [↑](./Recommender_system#cite_ref-59) X.Y. Feng, H. Zhang, Y.J. Ren, P.H. Shang, Y. Zhu, Y.C. Liang, R.C. Guan, D. Xu, (2019), "[The Deep Learning–Based Recommender System "Pubmender" for Choosing a Biomedical Publication Venue: Development and Validation Study](https://www.jmir.org/2019/5/e12957/)", *[Journal of Medical Internet Research](./Journal_of_Medical_Internet_Research)*, 21 (5): e12957
60. [↑](./Recommender_system#cite_ref-60) Rinke Hoekstra, [The Knowledge Reengineering Bottleneck](http://www.semantic-web-journal.net/sites/default/files/swj32.pdf), Semantic Web – Interoperability, Usability, Applicability 1 (2010) 1, IOS Press
61. [↑](./Recommender_system#cite_ref-61) Gomez-Uribe, Carlos A.; Hunt, Neil (December 28, 2015). ["The Netflix Recommender System"](https://doi.org/10.1145%2F2843948). *ACM Transactions on Management Information Systems*. **6** (4): 1–19. [doi](./Doi_(identifier)):[10.1145/2843948](https://doi.org/10.1145%2F2843948).
62. [↑](./Recommender_system#cite_ref-hybrids_62-0) Robin Burke, [Hybrid Web Recommender Systems](http://www.dcs.warwick.ac.uk/~acristea/courses/CS411/2010/Book%20-%20The%20Adaptive%20Web/HybridWebRecommenderSystems.pdf) [Archived](https://web.archive.org/web/20140912085014/http://www.dcs.warwick.ac.uk/~acristea/courses/CS411/2010/Book%20-%20The%20Adaptive%20Web/HybridWebRecommenderSystems.pdf) 2014-09-12 at the [Wayback Machine](./Wayback_Machine), pp. 377-408, The Adaptive Web, Peter Brusilovsky, Alfred Kobsa, Wolfgang Nejdl (Ed.), Lecture Notes in Computer Science, Springer-Verlag, Berlin, Germany, Lecture Notes in Computer Science, Vol. 4321, May 2007, 978-3-540-72078-2.
63. [1](./Recommender_system#cite_ref-a_63-0) [2](./Recommender_system#cite_ref-a_63-1) Hidasi, Balázs; Karatzoglou, Alexandros; Baltrunas, Linas; Tikk, Domonkos (March 29, 2016). "Session-based Recommendations with Recurrent Neural Networks". [arXiv](./ArXiv_(identifier)):[1511.06939](https://arxiv.org/abs/1511.06939) [[cs.LG](https://arxiv.org/archive/cs.LG)].
64. [1](./Recommender_system#cite_ref-yt_64-0) [2](./Recommender_system#cite_ref-yt_64-1) [3](./Recommender_system#cite_ref-yt_64-2) Chen, Minmin; Beutel, Alex; Covington, Paul; Jain, Sagar; Belletti, Francois; Chi, Ed (2018). "Top-K Off-Policy Correction for a REINFORCE Recommender System". [arXiv](./ArXiv_(identifier)):[1812.02353](https://arxiv.org/abs/1812.02353) [[cs.LG](https://arxiv.org/archive/cs.LG)].
65. [1](./Recommender_system#cite_ref-amzn_65-0) [2](./Recommender_system#cite_ref-amzn_65-1) Yifei, Ma; Narayanaswamy, Balakrishnan; Haibin, Lin; Hao, Ding (2020). "Temporal-Contextual Recommendation in Real-Time". *Proceedings of the 26th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining*. Association for Computing Machinery. pp. 2291–2299. [doi](./Doi_(identifier)):[10.1145/3394486.3403278](https://doi.org/10.1145%2F3394486.3403278). [ISBN](./ISBN_(identifier)) [978-1-4503-7998-4](./Special:BookSources/978-1-4503-7998-4). [S2CID](./S2CID_(identifier)) [221191348](https://api.semanticscholar.org/CorpusID:221191348).
66. [↑](./Recommender_system#cite_ref-66) Hidasi, Balázs; Karatzoglou, Alexandros (October 17, 2018). ["Recurrent Neural Networks with Top-k Gains for Session-based Recommendations"](https://doi.org/10.1145/3269206.3271761). *Proceedings of the 27th ACM International Conference on Information and Knowledge Management*. CIKM '18. Torino, Italy: Association for Computing Machinery. pp. 843–852. [arXiv](./ArXiv_(identifier)):[1706.03847](https://arxiv.org/abs/1706.03847). [doi](./Doi_(identifier)):[10.1145/3269206.3271761](https://doi.org/10.1145%2F3269206.3271761). [ISBN](./ISBN_(identifier)) [978-1-4503-6014-2](./Special:BookSources/978-1-4503-6014-2). [S2CID](./S2CID_(identifier)) [1159769](https://api.semanticscholar.org/CorpusID:1159769).
67. [↑](./Recommender_system#cite_ref-67) Kang, Wang-Cheng; McAuley, Julian (2018). "Self-Attentive Sequential Recommendation". [arXiv](./ArXiv_(identifier)):[1808.09781](https://arxiv.org/abs/1808.09781) [[cs.IR](https://arxiv.org/archive/cs.IR)].
68. [↑](./Recommender_system#cite_ref-68) Li, Jing; Ren, Pengjie; Chen, Zhumin; Ren, Zhaochun; Lian, Tao; Ma, Jun (November 6, 2017). ["Neural Attentive Session-based Recommendation"](https://doi.org/10.1145/3132847.3132926). *Proceedings of the 2017 ACM on Conference on Information and Knowledge Management*. CIKM '17. Singapore, Singapore: Association for Computing Machinery. pp. 1419–1428. [arXiv](./ArXiv_(identifier)):[1711.04725](https://arxiv.org/abs/1711.04725). [doi](./Doi_(identifier)):[10.1145/3132847.3132926](https://doi.org/10.1145%2F3132847.3132926). [ISBN](./ISBN_(identifier)) [978-1-4503-4918-5](./Special:BookSources/978-1-4503-4918-5). [S2CID](./S2CID_(identifier)) [21066930](https://api.semanticscholar.org/CorpusID:21066930).
69. [↑](./Recommender_system#cite_ref-69) Liu, Qiao; Zeng, Yifu; Mokhosi, Refuoe; Zhang, Haibin (July 19, 2018). ["STAMP"](https://doi.org/10.1145/3219819.3219950). *Proceedings of the 24th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining*. KDD '18. London, United Kingdom: Association for Computing Machinery. pp. 1831–1839. [doi](./Doi_(identifier)):[10.1145/3219819.3219950](https://doi.org/10.1145%2F3219819.3219950). [ISBN](./ISBN_(identifier)) [978-1-4503-5552-0](./Special:BookSources/978-1-4503-5552-0). [S2CID](./S2CID_(identifier)) [50775765](https://api.semanticscholar.org/CorpusID:50775765).
70. [↑](./Recommender_system#cite_ref-srl_70-0) Xin, Xin; Karatzoglou, Alexandros; Arapakis, Ioannis; Jose, Joemon (2020). "Self-Supervised Reinforcement Learning for Recommender Systems". [arXiv](./ArXiv_(identifier)):[2006.05779](https://arxiv.org/abs/2006.05779) [[cs.LG](https://arxiv.org/archive/cs.LG)].
71. [↑](./Recommender_system#cite_ref-sQ_71-0) Ie, Eugene; Jain, Vihan; Narvekar, Sanmit; Agarwal, Ritesh; Wu, Rui; Cheng, Heng-Tze; Chandra, Tushar; Boutilier, Craig (2019). ["SlateQ: A Tractable Decomposition for Reinforcement Learning with Recommendation Sets"](https://research.google/pubs/pub48200/). *Proceedings of the Twenty-Eighth International Joint Conference on Artificial Intelligence (IJCAI-19)*: 2592–2599.
72. [↑](./Recommender_system#cite_ref-jd_72-0) Zou, Lixin; Xia, Long; Ding, Zhuoye; Song, Jiaxing; Liu, Weidong; Yin, Dawei (2019). ["Reinforcement Learning to Optimize Long-term User Engagement in Recommender Systems"](https://dl.acm.org/doi/10.1145/3292500.3330668). *Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining*. KDD '19. pp. 2810–2818. [arXiv](./ArXiv_(identifier)):[1902.05570](https://arxiv.org/abs/1902.05570). [doi](./Doi_(identifier)):[10.1145/3292500.3330668](https://doi.org/10.1145%2F3292500.3330668). [ISBN](./ISBN_(identifier)) [978-1-4503-6201-6](./Special:BookSources/978-1-4503-6201-6). [S2CID](./S2CID_(identifier)) [62903207](https://api.semanticscholar.org/CorpusID:62903207).
73. [↑](./Recommender_system#cite_ref-73) Lakiotaki, K.; Matsatsinis; Tsoukias, A (March 2011). "Multicriteria User Modeling in Recommender Systems". *IEEE Intelligent Systems*. **26** (2): 64–76. [Bibcode](./Bibcode_(identifier)):[2011IISys..26b..64L](https://ui.adsabs.harvard.edu/abs/2011IISys..26b..64L). [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.476.6726](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.476.6726). [doi](./Doi_(identifier)):[10.1109/mis.2011.33](https://doi.org/10.1109%2Fmis.2011.33). [S2CID](./S2CID_(identifier)) [16752808](https://api.semanticscholar.org/CorpusID:16752808).
74. [↑](./Recommender_system#cite_ref-74) Gediminas Adomavicius; Nikos Manouselis; YoungOk Kwon. ["Multi-Criteria Recommender Systems"](https://web.archive.org/web/20140630021251/http://ids.csom.umn.edu/faculty/gedas/NSFCareer/MCRS-chapter-2010.pdf) (PDF). Archived from [the original](http://ids.csom.umn.edu/faculty/gedas/NSFCareer/MCRS-chapter-2010.pdf) (PDF) on June 30, 2014.
75. [↑](./Recommender_system#cite_ref-Bouneffouf2013_75-0) Bouneffouf, Djallel (2013). [*DRARS, A Dynamic Risk-Aware Recommender System*](http://tel.archives-ouvertes.fr/tel-01026136/fr/) (Ph.D. thesis). Institut National des Télécommunications.
76. [1](./Recommender_system#cite_ref-taxirecommender_76-0) [2](./Recommender_system#cite_ref-taxirecommender_76-1) Yong Ge; Hui Xiong; Alexander Tuzhilin; Keli Xiao; Marco Gruteser; Michael J. Pazzani (2010). [*An Energy-Efficient Mobile Recommender System*](http://www.winlab.rutgers.edu/~gruteser/papers/KDD10.pdf) (PDF). Proceedings of the 16th ACM SIGKDD Int'l Conf. on Knowledge Discovery and Data Mining. [New York City, New York](./New_York_City): [ACM](./Association_for_Computing_Machinery). pp. 899–908. Retrieved November 17, 2011. 
77. [↑](./Recommender_system#cite_ref-77) Pimenidis, Elias; Polatidis, Nikolaos; Mouratidis, Haralambos (August 3, 2018). "Mobile recommender systems: Identifying the major concepts". *Journal of Information Science*. **45** (3): 387–397. [arXiv](./ArXiv_(identifier)):[1805.02276](https://arxiv.org/abs/1805.02276). [doi](./Doi_(identifier)):[10.1177/0165551518792213](https://doi.org/10.1177%2F0165551518792213). [S2CID](./S2CID_(identifier)) [19209845](https://api.semanticscholar.org/CorpusID:19209845).
78. [↑](./Recommender_system#cite_ref-78) Zhai, Jiaqi; Liao, Lucy; Liu, Xing; Wang, Yueming; Li, Rui; Cao, Xuan; Gao, Leon; Gong, Zhaojie; Gu, Fangda (May 6, 2024). "Actions Speak Louder than Words: Trillion-Parameter Sequential Transducers for Generative Recommendations". [arXiv](./ArXiv_(identifier)):[2402.17152](https://arxiv.org/abs/2402.17152) [[cs.LG](https://arxiv.org/archive/cs.LG)].
79. [1](./Recommender_system#cite_ref-nytimes.com_79-0) [2](./Recommender_system#cite_ref-nytimes.com_79-1) Lohr, Steve (September 22, 2009). ["A $1 Million Research Bargain for Netflix, and Maybe a Model for Others"](https://www.nytimes.com/2009/09/22/technology/internet/22netflix.html). *The New York Times*.
80. [↑](./Recommender_system#cite_ref-80) R. Bell; Y. Koren; C. Volinsky (2007). ["The BellKor solution to the Netflix Prize"](https://web.archive.org/web/20120304173001/http://www.netflixprize.com/assets/ProgressPrize2007_KorBell.pdf) (PDF). Archived from [the original](http://www.netflixprize.com/assets/ProgressPrize2007_KorBell.pdf) (PDF) on March 4, 2012. Retrieved April 30, 2009.
81. [↑](./Recommender_system#cite_ref-81) Bodoky, Thomas (August 6, 2009). ["Mátrixfaktorizáció one million dollars"](http://index.hu/tech/net/2009/08/07/matrixfaktorizacio_egymillio_dollarert/). *Index*.
82. [↑](./Recommender_system#cite_ref-82) [Rise of the Netflix Hackers](https://www.wired.com/science/discoveries/news/2007/03/72963) [Archived](https://web.archive.org/web/20120124011808/http://www.wired.com/science/discoveries/news/2007/03/72963) January 24, 2012, at the [Wayback Machine](./Wayback_Machine)
83. [↑](./Recommender_system#cite_ref-83) ["Netflix Spilled Your Brokeback Mountain Secret, Lawsuit Claims"](https://www.wired.com/2009/12/netflix-privacy-lawsuit/). *WIRED*. December 17, 2009. Retrieved March 31, 2025.
84. [↑](./Recommender_system#cite_ref-nfcancel_84-0) ["Netflix Prize Update"](https://web.archive.org/web/20111127084829/http://blog.netflix.com/2010/03/this-is-neil-hunt-chief-product-officer.html). Netflix Prize Forum. March 12, 2010. Archived from [the original](http://blog.netflix.com/2010/03/this-is-neil-hunt-chief-product-officer.html) on November 27, 2011. Retrieved December 14, 2011.
85. [↑](./Recommender_system#cite_ref-85) Lathia, N., Hailes, S., Capra, L., Amatriain, X.: [Temporal diversity in recommender systems](http://www.academia.edu/download/46585553/lathia_sigir10.pdf)[*[dead link](./Wikipedia:Link_rot)*]. In: Proceedings of the 33rd International ACMSIGIR Conference on Research and Development in Information Retrieval, SIGIR 2010, pp. 210–217. ACM, New York
86. [↑](./Recommender_system#cite_ref-Turpin2001_86-0) Turpin, Andrew H; Hersh, William (2001). "Why batch and user evaluations do not give the same results". *Proceedings of the 24th annual international ACM SIGIR conference on Research and development in information retrieval*. pp. 225–231.
87. [↑](./Recommender_system#cite_ref-87) ["MovieLens dataset"](https://grouplens.org/datasets/movielens/). September 6, 2013.
88. [1](./Recommender_system#cite_ref-:4_88-0) [2](./Recommender_system#cite_ref-:4_88-1) Chen, Hung-Hsuan; Chung, Chu-An; Huang, Hsin-Chien; Tsui, Wen (September 1, 2017). "Common Pitfalls in Training and Evaluating Recommender Systems". *ACM SIGKDD Explorations Newsletter*. **19**: 37–45. [doi](./Doi_(identifier)):[10.1145/3137597.3137601](https://doi.org/10.1145%2F3137597.3137601). [S2CID](./S2CID_(identifier)) [10651930](https://api.semanticscholar.org/CorpusID:10651930).
89. [↑](./Recommender_system#cite_ref-89) Jannach, Dietmar; Lerche, Lukas; Gedikli, Fatih; Bonnin, Geoffray (June 10, 2013). "What Recommenders Recommend – an Analysis of Accuracy, Popularity, and Sales Diversity Effects". In Carberry, Sandra; Weibelzahl, Stephan; Micarelli, Alessandro; Semeraro, Giovanni (eds.). [*User Modeling, Adaptation, and Personalization*](https://archive.org/details/usermodelingadap00pero). Lecture Notes in Computer Science. Vol. 7899. Springer Berlin Heidelberg. pp. [25](https://archive.org/details/usermodelingadap00pero/page/n44)–37. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.465.96](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.465.96). [doi](./Doi_(identifier)):[10.1007/978-3-642-38844-6_3](https://doi.org/10.1007%2F978-3-642-38844-6_3). [ISBN](./ISBN_(identifier)) [978-3-642-38843-9](./Special:BookSources/978-3-642-38843-9).
90. [1](./Recommender_system#cite_ref-:1_90-0) [2](./Recommender_system#cite_ref-:1_90-1) Turpin, Andrew H.; Hersh, William (January 1, 2001). ["Why batch and user evaluations do not give the same results"](https://archive.org/details/proceedingsof24t0000inte/page/225). *Proceedings of the 24th annual international ACM SIGIR conference on Research and development in information retrieval*. SIGIR '01. New York, NY, USA: ACM. pp. [225–231](https://archive.org/details/proceedingsof24t0000inte/page/225). [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.165.5800](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.165.5800). [doi](./Doi_(identifier)):[10.1145/383952.383992](https://doi.org/10.1145%2F383952.383992). [ISBN](./ISBN_(identifier)) [978-1-58113-331-8](./Special:BookSources/978-1-58113-331-8). [S2CID](./S2CID_(identifier)) [18903114](https://api.semanticscholar.org/CorpusID:18903114).
91. [↑](./Recommender_system#cite_ref-91) Langer, Stefan (September 14, 2015). "A Comparison of Offline Evaluations, Online Evaluations, and User Studies in the Context of Research-Paper Recommender Systems". In Kapidakis, Sarantos; Mazurek, Cezary; Werla, Marcin (eds.). *Research and Advanced Technology for Digital Libraries*. Lecture Notes in Computer Science. Vol. 9316. Springer International Publishing. pp. 153–168. [doi](./Doi_(identifier)):[10.1007/978-3-319-24592-8_12](https://doi.org/10.1007%2F978-3-319-24592-8_12). [ISBN](./ISBN_(identifier)) [978-3-319-24591-1](./Special:BookSources/978-3-319-24591-1).
92. [↑](./Recommender_system#cite_ref-BasaranNtoutsi2017_92-0) Basaran, Daniel; Ntoutsi, Eirini; Zimek, Arthur (2017). *Proceedings of the 2017 SIAM International Conference on Data Mining*. pp. 390–398. [doi](./Doi_(identifier)):[10.1137/1.9781611974973.44](https://doi.org/10.1137%2F1.9781611974973.44). [ISBN](./ISBN_(identifier)) [978-1-61197-497-3](./Special:BookSources/978-1-61197-497-3).
93. [↑](./Recommender_system#cite_ref-93) Beel, Joeran; Genzmehr, Marcel; Langer, Stefan; Nürnberger, Andreas; Gipp, Bela (January 1, 2013). "A comparative analysis of offline and online evaluations and discussion of research paper recommender system evaluation". *Proceedings of the International Workshop on Reproducibility and Replication in Recommender Systems Evaluation*. RepSys '13. New York, NY, USA: ACM. pp. 7–14. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.1031.973](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.1031.973). [doi](./Doi_(identifier)):[10.1145/2532508.2532511](https://doi.org/10.1145%2F2532508.2532511). [ISBN](./ISBN_(identifier)) [978-1-4503-2465-6](./Special:BookSources/978-1-4503-2465-6). [S2CID](./S2CID_(identifier)) [8202591](https://api.semanticscholar.org/CorpusID:8202591).
94. [↑](./Recommender_system#cite_ref-cañamares2018_94-0) Cañamares, Rocío; Castells, Pablo (July 2018). [*Should I Follow the Crowd? A Probabilistic Analysis of the Effectiveness of Popularity in Recommender Systems*](https://web.archive.org/web/20210414070127/http://ir.ii.uam.es/pubs/sigir2018.pdf) (PDF). 41st Annual International ACM SIGIR Conference on Research and Development in Information Retrieval (SIGIR 2018). Ann Arbor, Michigan, USA: ACM. pp. 415–424. [doi](./Doi_(identifier)):[10.1145/3209978.3210014](https://doi.org/10.1145%2F3209978.3210014). Archived from [the original](http://ir.ii.uam.es/pubs/sigir2018.pdf) (PDF) on April 14, 2021. Retrieved March 5, 2021.
95. [↑](./Recommender_system#cite_ref-cañamares2020_95-0) Cañamares, Rocío; Castells, Pablo; Moffat, Alistair (March 2020). ["Offline Evaluation Options for Recommender Systems"](https://web.archive.org/web/20210331224711/http://ir.ii.uam.es/pubs/irj2020.pdf) (PDF). *Information Retrieval*. **23** (4). Springer: 387–410. [doi](./Doi_(identifier)):[10.1007/s10791-020-09371-3](https://doi.org/10.1007%2Fs10791-020-09371-3). [hdl](./Hdl_(identifier)):[10486/703029](https://hdl.handle.net/10486%2F703029). [S2CID](./S2CID_(identifier)) [213169978](https://api.semanticscholar.org/CorpusID:213169978). Archived from [the original](http://ir.ii.uam.es/pubs/irj2020.pdf) (PDF) on March 31, 2021. Retrieved March 5, 2021.
96. [↑](./Recommender_system#cite_ref-Ziegler2005_96-0) Ziegler CN, McNee SM, Konstan JA, Lausen G (2005). "Improving recommendation lists through topic diversification". *Proceedings of the 14th international conference on World Wide Web*. pp. 22–32.
97. [1](./Recommender_system#cite_ref-castells2015_97-0) [2](./Recommender_system#cite_ref-castells2015_97-1) Castells, Pablo; Hurley, Neil J.; Vargas, Saúl (2015). ["Novelty and Diversity in Recommender Systems"](https://link.springer.com/chapter/10.1007/978-1-4899-7637-6_26). In Ricci, Francesco; Rokach, Lior; Shapira, Bracha (eds.). *Recommender Systems Handbook* (2 ed.). Springer US. pp. 881–918. [doi](./Doi_(identifier)):[10.1007/978-1-4899-7637-6_26](https://doi.org/10.1007%2F978-1-4899-7637-6_26). [ISBN](./ISBN_(identifier)) [978-1-4899-7637-6](./Special:BookSources/978-1-4899-7637-6).
98. [↑](./Recommender_system#cite_ref-Beel2013e_98-0) Joeran Beel; Stefan Langer; Marcel Genzmehr; Andreas Nürnberger (September 2013). ["Persistence in Recommender Systems: Giving the Same Recommendations to the Same Users Multiple Times"](http://docear.org/papers/persistence_in_recommender_systems_--_giving_the_same_recommendations_to_the_same_users_multiple_times.pdf) (PDF). In Trond Aalberg; Milena Dobreva; Christos Papatheodorou; Giannis Tsakonas; Charles Farrugia (eds.). *Proceedings of the 17th International Conference on Theory and Practice of Digital Libraries (TPDL 2013)*. Lecture Notes of Computer Science (LNCS). Vol. 8092. Springer. pp. 390–394. Retrieved November 1, 2013.
99. [↑](./Recommender_system#cite_ref-Cosley2003_99-0) Cosley, D.; Lam, S.K.; Albert, I.; Konstan, J.A.; Riedl, J (2003). ["Is seeing believing?: how recommender system interfaces affect users' opinions"](https://pdfs.semanticscholar.org/d7d5/47012091d11ba0b0bf4a6630c5689789c22e.pdf) (PDF). *Proceedings of the SIGCHI conference on Human factors in computing systems*. pp. 585–592. [S2CID](./S2CID_(identifier)) [8307833](https://api.semanticscholar.org/CorpusID:8307833).
100. [↑](./Recommender_system#cite_ref-Pu2012_100-0) Pu, P.; Chen, L.; Hu, R. (2012). ["Evaluating recommender systems from the user's perspective: survey of the state of the art"](http://doc.rero.ch/record/317166/files/11257_2011_Article_9115.pdf) (PDF). *User Modeling and User-Adapted Interaction*: 1–39.
101. [↑](./Recommender_system#cite_ref-privacyoverview_101-0) Naren Ramakrishnan; Benjamin J. Keller; Batul J. Mirza; Ananth Y. Grama; George Karypis (2001). ["Privacy risks in recommender systems"](https://archive.org/details/sigir2002proceed0000inte/page/54). *IEEE Internet Computing*. **5** (6). Piscataway, NJ: [IEEE Educational Activities Department](./IEEE_Educational_Activities_Department?action=edit&redlink=1): [54–62](https://archive.org/details/sigir2002proceed0000inte/page/54). [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.2.2932](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.2.2932). [doi](./Doi_(identifier)):[10.1109/4236.968832](https://doi.org/10.1109%2F4236.968832). [ISBN](./ISBN_(identifier)) [978-1-58113-561-9](./Special:BookSources/978-1-58113-561-9). [S2CID](./S2CID_(identifier)) [1977107](https://api.semanticscholar.org/CorpusID:1977107). 
102. [↑](./Recommender_system#cite_ref-Beel2013f_102-0) Joeran Beel; Stefan Langer; Andreas Nürnberger; Marcel Genzmehr (September 2013). ["The Impact of Demographics (Age and Gender) and Other User Characteristics on Evaluating Recommender Systems"](http://docear.org/papers/the_impact_of_users'_demographics_(age_and_gender)_and_other_characteristics_on_evaluating_recommender_systems.pdf) (PDF). In Trond Aalberg; Milena Dobreva; Christos Papatheodorou; Giannis Tsakonas; Charles Farrugia (eds.). *Proceedings of the 17th International Conference on Theory and Practice of Digital Libraries (TPDL 2013)*. Springer. pp. 400–404. Retrieved November 1, 2013.
103. [↑](./Recommender_system#cite_ref-Konstan2012_103-0) Konstan JA, Riedl J (2012). ["Recommender systems: from algorithms to user experience"](https://link.springer.com/content/pdf/10.1007/s11257-011-9112-x.pdf) (PDF). *User Modeling and User-Adapted Interaction*. **22** (1–2): 1–23. [doi](./Doi_(identifier)):[10.1007/s11257-011-9112-x](https://doi.org/10.1007%2Fs11257-011-9112-x). [S2CID](./S2CID_(identifier)) [8996665](https://api.semanticscholar.org/CorpusID:8996665).
104. [↑](./Recommender_system#cite_ref-Ricci2011_104-0) Ricci F, Rokach L, Shapira B, Kantor BP (2011). *Recommender systems handbook*. pp. 1–35. [Bibcode](./Bibcode_(identifier)):[2011rsh..book.....R](https://ui.adsabs.harvard.edu/abs/2011rsh..book.....R).
105. [↑](./Recommender_system#cite_ref-105) Möller, Judith; Trilling, Damian; Helberger, Natali; van Es, Bram (July 3, 2018). ["Do not blame it on the algorithm: an empirical assessment of multiple recommender systems and their impact on content diversity"](https://www.tandfonline.com/doi/full/10.1080/1369118X.2018.1444076). *Information, Communication & Society*. **21** (7): 959–977. [doi](./Doi_(identifier)):[10.1080/1369118X.2018.1444076](https://doi.org/10.1080%2F1369118X.2018.1444076). [hdl](./Hdl_(identifier)):[11245.1/4242e2e0-3beb-40a0-a6cb-d8947a13efb4](https://hdl.handle.net/11245.1%2F4242e2e0-3beb-40a0-a6cb-d8947a13efb4). [ISSN](./ISSN_(identifier)) [1369-118X](https://search.worldcat.org/issn/1369-118X). [S2CID](./S2CID_(identifier)) [149344712](https://api.semanticscholar.org/CorpusID:149344712).
106. [↑](./Recommender_system#cite_ref-Montaner2002_106-0) Montaner, Miquel; López, Beatriz; de la Rosa, Josep Lluís (2002). ["Developing trust in recommender agents"](https://www.researchgate.net/publication/221454720). *Proceedings of the first international joint conference on Autonomous agents and multiagent systems: part 1*. pp. 304–305.
107. [↑](./Recommender_system#cite_ref-Beel2013a_107-0) Beel, Joeran, Langer, Stefan, Genzmehr, Marcel (September 2013). ["Sponsored vs. Organic (Research Paper) Recommendations and the Impact of Labeling"](http://docear.org/papers/sponsored_vs._organic_(research_paper)_recommendations_and_the_impact_of_labeling.pdf) (PDF). In Trond Aalberg, Milena Dobreva, Christos Papatheodorou, Giannis Tsakonas, Charles Farrugia (eds.). *Proceedings of the 17th International Conference on Theory and Practice of Digital Libraries (TPDL 2013)*. pp. 395–399. Retrieved December 2, 2013.
108. [↑](./Recommender_system#cite_ref-108) Ferrari Dacrema, Maurizio; Boglio, Simone; Cremonesi, Paolo; Jannach, Dietmar (January 8, 2021). ["A Troubling Analysis of Reproducibility and Progress in Recommender Systems Research"](https://dl.acm.org/doi/10.1145/3434185). *ACM Transactions on Information Systems*. **39** (2): 1–49. [arXiv](./ArXiv_(identifier)):[1911.07698](https://arxiv.org/abs/1911.07698). [doi](./Doi_(identifier)):[10.1145/3434185](https://doi.org/10.1145%2F3434185). [hdl](./Hdl_(identifier)):[11311/1164333](https://hdl.handle.net/11311%2F1164333). [S2CID](./S2CID_(identifier)) [208138060](https://api.semanticscholar.org/CorpusID:208138060).
109. [↑](./Recommender_system#cite_ref-109) Ferrari Dacrema, Maurizio; Cremonesi, Paolo; Jannach, Dietmar (2019). ["Are we really making much progress? A worrying analysis of recent neural recommendation approaches"](https://dl.acm.org/authorize?N684126). *Proceedings of the 13th ACM Conference on Recommender Systems*. RecSys '19. ACM. pp. 101–109. [arXiv](./ArXiv_(identifier)):[1907.06902](https://arxiv.org/abs/1907.06902). [doi](./Doi_(identifier)):[10.1145/3298689.3347058](https://doi.org/10.1145%2F3298689.3347058). [hdl](./Hdl_(identifier)):[11311/1108996](https://hdl.handle.net/11311%2F1108996). [ISBN](./ISBN_(identifier)) [978-1-4503-6243-6](./Special:BookSources/978-1-4503-6243-6). [S2CID](./S2CID_(identifier)) [196831663](https://api.semanticscholar.org/CorpusID:196831663). Retrieved October 16, 2019.
110. [↑](./Recommender_system#cite_ref-110) Rendle, Steffen; Krichene, Walid; Zhang, Li; Anderson, John (September 22, 2020). "Neural Collaborative Filtering vs. Matrix Factorization Revisited". *Fourteenth ACM Conference on Recommender Systems*. pp. 240–248. [arXiv](./ArXiv_(identifier)):[2005.09683](https://arxiv.org/abs/2005.09683). [doi](./Doi_(identifier)):[10.1145/3383313.3412488](https://doi.org/10.1145%2F3383313.3412488). [ISBN](./ISBN_(identifier)) [978-1-4503-7583-2](./Special:BookSources/978-1-4503-7583-2).
111. [↑](./Recommender_system#cite_ref-111) Sun, Zhu; Yu, Di; Fang, Hui; Yang, Jie; Qu, Xinghua; Zhang, Jie; Geng, Cong (2020). ["Are We Evaluating Rigorously? Benchmarking Recommendation for Reproducible Evaluation and Fair Comparison"](https://dl.acm.org/doi/10.1145/3383313.3412489). *Fourteenth ACM Conference on Recommender Systems*. ACM. pp. 23–32. [doi](./Doi_(identifier)):[10.1145/3383313.3412489](https://doi.org/10.1145%2F3383313.3412489). [ISBN](./ISBN_(identifier)) [978-1-4503-7583-2](./Special:BookSources/978-1-4503-7583-2). [S2CID](./S2CID_(identifier)) [221785064](https://api.semanticscholar.org/CorpusID:221785064).
112. [↑](./Recommender_system#cite_ref-112) Schifferer, Benedikt; Deotte, Chris; Puget, Jean-François; de Souza Pereira, Gabriel; Titericz, Gilberto; Liu, Jiwei; Ak, Ronay. ["Using Deep Learning to Win the Booking.com WSDM WebTour21 Challenge on Sequential Recommendations"](https://web.archive.org/web/20210325063047/https://web.ec.tuwien.ac.at/webtour21/wp-content/uploads/2021/03/shifferer.pdf) (PDF). *WSDM '21: ACM Conference on Web Search and Data Mining*. ACM. Archived from [the original](https://web.ec.tuwien.ac.at/webtour21/wp-content/uploads/2021/03/shifferer.pdf) (PDF) on March 25, 2021. Retrieved April 3, 2021.
113. [↑](./Recommender_system#cite_ref-113) Volkovs, Maksims; Rai, Himanshu; Cheng, Zhaoyue; Wu, Ga; Lu, Yichao; Sanner, Scott (2018). ["Two-stage Model for Automatic Playlist Continuation at Scale"](https://dl.acm.org/doi/10.1145/3267471.3267480). *Proceedings of the ACM Recommender Systems Challenge 2018*. ACM. pp. 1–6. [doi](./Doi_(identifier)):[10.1145/3267471.3267480](https://doi.org/10.1145%2F3267471.3267480). [ISBN](./ISBN_(identifier)) [978-1-4503-6586-4](./Special:BookSources/978-1-4503-6586-4). [S2CID](./S2CID_(identifier)) [52942462](https://api.semanticscholar.org/CorpusID:52942462).
114. [↑](./Recommender_system#cite_ref-ntfx_114-0) Yves Raimond, Justin Basilico [Deep Learning for Recommender Systems](https://www2.slideshare.net/moustaki/deep-learning-for-recommender-systems-86752234), Deep Learning Re-Work SF Summit 2018
115. [↑](./Recommender_system#cite_ref-115) Ekstrand, Michael D.; Ludwig, Michael; Konstan, Joseph A.; Riedl, John T. (January 1, 2011). "Rethinking the recommender research ecosystem". *Proceedings of the fifth ACM conference on Recommender systems*. RecSys '11. New York, NY, USA: ACM. pp. 133–140. [doi](./Doi_(identifier)):[10.1145/2043932.2043958](https://doi.org/10.1145%2F2043932.2043958). [ISBN](./ISBN_(identifier)) [978-1-4503-0683-6](./Special:BookSources/978-1-4503-0683-6). [S2CID](./S2CID_(identifier)) [2215419](https://api.semanticscholar.org/CorpusID:2215419).
116. [↑](./Recommender_system#cite_ref-116) Konstan, Joseph A.; Adomavicius, Gediminas (January 1, 2013). "Toward identification and adoption of best practices in algorithmic recommender systems research". *Proceedings of the International Workshop on Reproducibility and Replication in Recommender Systems Evaluation*. RepSys '13. New York, NY, USA: ACM. pp. 23–28. [doi](./Doi_(identifier)):[10.1145/2532508.2532513](https://doi.org/10.1145%2F2532508.2532513). [ISBN](./ISBN_(identifier)) [978-1-4503-2465-6](./Special:BookSources/978-1-4503-2465-6). [S2CID](./S2CID_(identifier)) [333956](https://api.semanticscholar.org/CorpusID:333956).
117. [1](./Recommender_system#cite_ref-:2_117-0) [2](./Recommender_system#cite_ref-:2_117-1) Breitinger, Corinna; Langer, Stefan; Lommatzsch, Andreas; Gipp, Bela (March 12, 2016). ["Towards reproducibility in recommender-systems research"](http://nbn-resolving.de/urn:nbn:de:bsz:352-0-324818). *User Modeling and User-Adapted Interaction*. **26** (1): 69–101. [doi](./Doi_(identifier)):[10.1007/s11257-016-9174-x](https://doi.org/10.1007%2Fs11257-016-9174-x). [ISSN](./ISSN_(identifier)) [0924-1868](https://search.worldcat.org/issn/0924-1868). [S2CID](./S2CID_(identifier)) [388764](https://api.semanticscholar.org/CorpusID:388764).
118. [↑](./Recommender_system#cite_ref-118) Said, Alan; Bellogín, Alejandro (October 1, 2014). "Comparative recommender system evaluation". *Proceedings of the 8th ACM Conference on Recommender systems*. RecSys '14. New York, NY, USA: ACM. pp. 129–136. [doi](./Doi_(identifier)):[10.1145/2645710.2645746](https://doi.org/10.1145%2F2645710.2645746). [hdl](./Hdl_(identifier)):[10486/665450](https://hdl.handle.net/10486%2F665450). [ISBN](./ISBN_(identifier)) [978-1-4503-2668-1](./Special:BookSources/978-1-4503-2668-1). [S2CID](./S2CID_(identifier)) [15665277](https://api.semanticscholar.org/CorpusID:15665277).
119. [↑](./Recommender_system#cite_ref-119) Verma, P.; Sharma, S. (2020). "Artificial Intelligence based Recommendation System". *2020 2nd International Conference on Advances in Computing, Communication Control and Networking (ICACCCN)*. pp. 669–673. [doi](./Doi_(identifier)):[10.1109/ICACCCN51052.2020.9362962](https://doi.org/10.1109%2FICACCCN51052.2020.9362962). [ISBN](./ISBN_(identifier)) [978-1-7281-8337-4](./Special:BookSources/978-1-7281-8337-4). [S2CID](./S2CID_(identifier)) [232150789](https://api.semanticscholar.org/CorpusID:232150789).
120. [↑](./Recommender_system#cite_ref-120) Khanal, S.S. (July 2020). "A systematic review: machine learning based recommendation systems for e-learning". *Educ Inf Technol*. **25** (4): 2635–2664. [doi](./Doi_(identifier)):[10.1007/s10639-019-10063-9](https://doi.org/10.1007%2Fs10639-019-10063-9). [S2CID](./S2CID_(identifier)) [254475908](https://api.semanticscholar.org/CorpusID:254475908).
121. [1](./Recommender_system#cite_ref-Artificial_intelligence_in_recommen_121-0) [2](./Recommender_system#cite_ref-Artificial_intelligence_in_recommen_121-1) Zhang, Q. (February 2021). ["Artificial intelligence in recommender systems"](https://doi.org/10.1007%2Fs40747-020-00212-w). *Complex and Intelligent Systems*. **7**: 439–457. [doi](./Doi_(identifier)):[10.1007/s40747-020-00212-w](https://doi.org/10.1007%2Fs40747-020-00212-w).
122. [↑](./Recommender_system#cite_ref-122) Wu, L. (May 2023). "A Survey on Accuracy-Oriented Neural Recommendation: From Collaborative Filtering to Information-Rich Recommendation". *IEEE Transactions on Knowledge and Data Engineering*. **35** (5): 4425–4445. [arXiv](./ArXiv_(identifier)):[2104.13030](https://arxiv.org/abs/2104.13030). [Bibcode](./Bibcode_(identifier)):[2023ITKDE..35.4425W](https://ui.adsabs.harvard.edu/abs/2023ITKDE..35.4425W). [doi](./Doi_(identifier)):[10.1109/TKDE.2022.3145690](https://doi.org/10.1109%2FTKDE.2022.3145690).
123. [↑](./Recommender_system#cite_ref-123) Samek, W. (March 2021). ["Explaining Deep Neural Networks and Beyond: A Review of Methods and Applications"](https://doi.org/10.1109%2FJPROC.2021.3060483). *Proceedings of the IEEE*. **109** (3): 247–278. [arXiv](./ArXiv_(identifier)):[2003.07631](https://arxiv.org/abs/2003.07631). [doi](./Doi_(identifier)):[10.1109/JPROC.2021.3060483](https://doi.org/10.1109%2FJPROC.2021.3060483).
124. [↑](./Recommender_system#cite_ref-124) Yi, X., Hong, L., Zhong, E., Tewari, A., & Dhillon, I. S. (2019). "A scalable two-tower model for estimating user interest in recommendations." *Proceedings of the 13th ACM Conference on Recommender Systems*.
125. [↑](./Recommender_system#cite_ref-125) Google Cloud Blog. \"Scaling Deep Retrieval with Two-Tower Models.\" Published November 30, 2022. [Accessed December 2024](https://cloud.google.com/blog/products/ai-machine-learning/scaling-deep-retrieval-tensorflow-two-towers-architecture).
126. [↑](./Recommender_system#cite_ref-126) Eisenstein, J. (October 2019). *Introduction to natural language processing*. MIT press. [ISBN](./ISBN_(identifier)) [9780262042840](./Special:BookSources/9780262042840).

 

## Further reading

 Books 
- Kim Falk (d 2019), Practical Recommender Systems, Manning Publications, [ISBN](./ISBN_(identifier)) [9781617292705](./Special:BookSources/9781617292705)
- Bharat Bhasker; K. Srikumar (2010). [*Recommender Systems in E-Commerce*](https://web.archive.org/web/20100901164550/http://www.tatamcgrawhill.com/html/9780070680678.html). CUP. [ISBN](./ISBN_(identifier)) [978-0-07-068067-8](./Special:BookSources/978-0-07-068067-8). Archived from [the original](http://www.tatamcgrawhill.com/html/9780070680678.html) on September 1, 2010.
- Jannach, Dietmar; Markus Zanker; Alexander Felfernig; Gerhard Friedrich (2010). [*Recommender Systems: An Introduction*](https://web.archive.org/web/20150831032309/http://www.cambridge.org/uk/catalogue/catalogue.asp?isbn=9780521493369). CUP. [ISBN](./ISBN_(identifier)) [978-0-521-49336-9](./Special:BookSources/978-0-521-49336-9). Archived from [the original](http://www.cambridge.org/uk/catalogue/catalogue.asp?isbn=9780521493369) on August 31, 2015.
- Seaver, Nick (2022). *Computing Taste: Algorithms and the Makers of Music Recommendation*. University of Chicago Press.

 Scientific articles 
- Robert M. Bell; Jim Bennett; Yehuda Koren & Chris Volinsky (May 2009). ["The Million Dollar Programming Prize"](https://web.archive.org/web/20090511144610/http://www.spectrum.ieee.org/may09/8788). *[IEEE Spectrum](./IEEE_Spectrum)*. Archived from [the original](http://www.spectrum.ieee.org/may09/8788) on May 11, 2009. Retrieved December 10, 2018.
- Prem Melville, [Raymond J. Mooney](./Raymond_J._Mooney), and Ramadass Nagarajan. (2002) [Content-Boosted Collaborative Filtering for Improved Recommendations.](http://www.cs.utexas.edu/users/ml/papers/cbcf-aaai-02.pdf) *Proceedings of the Eighteenth National Conference on Artificial Intelligence* (AAAI-2002), pp. 187–192, Edmonton, Canada, July 2002.

 
| Authority control databases |
| --- |
| International | GND |
| National | United StatesFranceBnF dataCzech RepublicIsrael |
| Other | Yale LUX |