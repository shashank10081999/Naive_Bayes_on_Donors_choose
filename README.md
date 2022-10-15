# Naive_Bayes_on_Donors_choose
Minimum data points need to be considered for people having 4GB RAM is 50k and for 8GB RAM is 100k
When you are using ramdomsearchcv or gridsearchcv you need not split the data into X_train,X_cv,X_test. As the above methods use kfold. The model will learn better if train data is more so splitting to X_train,X_test will suffice.
If you are writing for loops to tune your model then you need split the data into X_train,X_cv,X_test.
While splitting the data explore stratify parameter.
Apply Multinomial NB on these feature sets
Features that need to be considered
essay
while encoding essay, try to experiment with the max_features and n_grams parameter of vectorizers and see if it increases AUC score.
categorical features
- teacher_prefix
- project_grade_category
- school_state
- clean_categories
- clean_subcategories
numerical features
- price
- teacher_number_of_previously_posted_projects
while encoding the numerical features check this and this
Set 1: categorical, numerical features + preprocessed_eassay (BOW)
Set 2: categorical, numerical features + preprocessed_eassay (TFIDF)
The hyper paramter tuning(find best alpha:smoothing parameter)
Consider alpha values in range: 10^-5 to 10^2 like [0.00001,0.0005, 0.0001,0.005,0.001,0.05,0.01,0.1,0.5,1,5,10,50,100]
Explore class_prior = [0.5, 0.5] parameter which can be present in MultinomialNB function(go through this ) then check how results might change.
Find the best hyper parameter which will give the maximum AUC value
For hyper parameter tuning using k-fold cross validation(use GridsearchCV or RandomsearchCV)/simple cross validation data (write for loop to iterate over hyper parameter values)
You need to plot the performance of model both on train data and cross validation data for each hyper parameter, like shown in the figure
-while plotting take log(alpha) on your X-axis so that it will be more readable
Once after you found the best hyper parameter, you need to train your model with it, and find the AUC on test data and plot the ROC curve on both train and test.
Along with plotting ROC curve, you need to print the confusion matrix with predicted and original labels of test data points
-plot the confusion matrix in heatmaps, while plotting the confusion matrix go through the link
find the top 20 features from either from feature Set 1 or feature Set 2 using values of `feature_log_prob_ ` parameter of `MultinomialNB` (https://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.MultinomialNB.html) and print BOTH positive as well as negative corresponding feature names.
- go through the link
You need to summarize the results at the end of the notebook, summarize it in the table format
