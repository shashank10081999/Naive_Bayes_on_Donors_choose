# Naive_Bayes_on_Donors_choose


- Applied Multinomial NB on these feature sets
- Features that need to be considered
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

- Set 1: categorical, numerical features + preprocessed_eassay (BOW)
- Set 2: categorical, numerical features + preprocessed_eassay (TFIDF)
