---
layout: post
title: Predicting IMDB Film ratings
date: 20/11/16
---

# Executive Report

**The aim of the following report is to examine what factors lead to certain ratings for movies. From these factors a model can then be produced to accurately predict ratings for films. The accuracy of the model will be judged on how well the model performs in its predictions, indicated by the R2 score**

**Approach:**

The data used for this project comes from the top 250 films, indicated by score, from IMDB. The following are some of the features included in the dataset which could be used to determine a films rating:

- Genre
- Actor
- Release Year
- Awards
- Gross revenue

A possible disadvantage of only using this dataset is that it doesn't give a good representation of the entire spectrum of films. For this reason the model produced, although might perform well on films with high ratings, when applied to films with lower ratings, may not produce realistic outcomes.

The model itself will be a tree based model, chosen for its accuracy with tasks like the one we have at hand. 

**Anlaysis of Data Set:**

- The average IMDB rating of a top 250 film was 8.3 / 10.0. The following chart shows the distribution of scores across all 250 films.

![](https://lh3.googleusercontent.com/S94VH90LykEeogttRSexqe9rOemR7ez4pNt1TODX7FYtYnpdJQTOIgAZM0F2iuFdJXjDKStUF5FyORQVyJ2cRdKByRiRkv6i4M9Q-p_aHB80FWolSiYvAKWgOasRhKeMXMGG3a-B-F13b41pKldu1fYFk9_ceua_Ng1Vf16ciZ-FTB6IF9etY84GIov71Ae1I8VeTRYkLlgsJJ758yn3P8SjS5D85U9_3lTHkNASPULBQEKn42soNrIYS0oEp21JtFXIBm7SB4BkukeMtssqUTSPoEVuI9E6Dx4oM0gHTIVqz_ZOGbgPN4ttv9_EfA_ojM8OMFo-hC_d9QswlbsZ2YtaakhG4wtaZnTWnTmAUBoYHo8lGN1yCMhfDA7eSSvURW05aqlD5XhUqC3ym3DLe6DIhejfj9mLeXgZ3g0wJahEq33DSMJWVe0hdxvuWCg-q0pfrpAtB8jEr-m4jU01D6J_fHDiIFZKyxLUSFFC9KAqT1G_eF_tTU9MbSAbeLsWESS4ohCwGIeLaCIDydzlvHtW8olG70kJIPHFPliRlUpUPD8uBIRmw-gMJEqk8E0yWuJlMVtl=w1280-h699)

- The film with the highest rating of 9.3 was The Shawshank Redemption, followed closely by The Godfather.
- The top grossing film was Star Wars: The Force Awakens, with a revenue of 936,627,416 USD.
- 174 films were classed at drama - the largest group by genre.
- The Actors which appeared in the most films were; Leonardo Dicaprio, Harrison Ford and Robert Deniro. Each appearing in 7 films.
- The directors who directed the most films were; Christopher Nolan, Stanley Kubrick, Steven Spielberg and Martin Scorsese. Each directing 7 films.
- The largest producer of films was the USA, producing a total of 178 films.

**Modelling:**

From the analysis, the following features were selected to be included in the model as an aid in predicting ratings.

- Genre
- Gross revenue
- Year produced
- The number of votes
- Production country
- Number of awards and nominations 

The target variable rating was treated as a continuous variable so our model could be run with films with differnent ratings from the ones that appear in the top 250.

The model itself was contructed from an ensemble of Random Forests, optimally tuned. The main advantage of ensembles of different regressors is that it is unlikely that all regressors will make the same mistake when modelling. A disadvantage of this approach, although producing a more accurate model, is that it is difficult to determine feature importance and also hard to visualise.

**Results**

The following chart shows the performance of our model on unseen data:

![](https://lh3.googleusercontent.com/Bau_JGMCUpM2ktsbpTc5j8lqfFupvjkBJ6TwIuGN2HNdd0fVJYthgsuu4pTdHMz276VGc225F32hCDNQneSg7d2SXm6CsAbFn2_3ib8t9BNWB9LiY5N36wsdsxYiBqpD7aEX0F0pWWHw57q9Bzol1afPnUFS8dXPubjVeydBDQU3kYc-08DxGMFaQyGSYKlqbgN-LQJsCy20O_11gEmCtAsEUOUfOSJYPl1SJru3oZLrEE3tU5VQ5RQKzDV7-rhXllvDJVRG02mxlvEMSg3QLJO-Cq_Dbmyn3gdOW_-pnu2b0TnF1DQDr1_P_UffZXcIAfyK6ipbRro8N6N92IShSNh_aTmPygW2ux0Dt3yLbc0h-Ed6SsM-hsThTvsCeYjff9W4uMYMSONx56UUnjtpdMOIiajV-zUgBEjQld2iLKjGN6dtmj7RqlcPNGvKEwJOUA2L59MrJOgIuYiHFtlu6VgV9SgpkRPtWp_DTJNcE2wLC_YxPvGObqboMXN4sFSVzqX04-AE4Pbt1oVIzZob8Fpis_7OsmNjBsYh6-JKmpmWnkP3CnLgPv2BwssdlhPq95fK2U5-=w1280-h699)

If we had a perfect model, all points on the graph should lie on the diagonal (predicted = actual). What this graph shows is that our model can only explain 43% of the variability in our data set, indicated by the r2_score. 

**Next Steps**

A more accurate model might be found by adding more features such as Directors or Actors. A good feature to include could be reviews by critics. Another approach could be to use a much larger data set that also accounts for movies with lower ratings.