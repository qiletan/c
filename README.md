# Home Credit Default Risk: my 2nd Kaggle competition 

This repository has part of my solution to the [Home Credit Default Risk challenge](https://www.kaggle.com/c/home-credit-default-risk) :house_with_garden:.
and some useful functions/code that I think I can reuse for my next competition/future work.

# Final ranking
I ranked top 4% at the end and received a Silver medal.

# Learnings:
A few learnings that I want to record and share from this competition. Specifically:
1. The sample is quite unbalanced with less than 10% 1s. The common way to deal withi this in Tree Boosting algorithms is 
to use stratified sampling in your CV. However, as pointed out by the winner, since we do not know the true distribution of the target, 
simply using stratified is to assume the distribution in test is the same as train, which could (not) be true. Detailed discussion can be
found at this [thread](https://www.kaggle.com/c/home-credit-default-risk/discussion/59954)

2. Hyperparameter tuning overfitted my models a lot

3. Feature selection did not work well in this one. I ended up using 1700+ features in my main model and the result is better when I used the top 
50% most important features

4. Great [open solution](https://github.com/neptune-ml/open-solution-home-credit). I blended this to my final submissions. It boosted up my results
by at least 10 to 20%

5. Imputation for the EX_SOURCE helped. The three external scores turns out to be the top performing features for most of the teams and it was established quite early on during the comp. However, I didn't see any one trying to impute the missing values for those. I used 
LightGBM to predict the missing values by using the main application data only. To train the model, I used really simple parameters to help overfitting and 2-fold cv to help speedup. The objective function I used is RMSE.
