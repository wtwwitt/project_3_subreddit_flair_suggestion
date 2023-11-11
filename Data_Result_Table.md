### Data
|File|Description|Lemmatize|Stopwords|NLP Lib|
|---|---|---|---|---|
|cvec_lemmatized.csv|Count vectorized with custom tokenizer|Yes|English|spaCy|
|tvec_lemmatized.csv|TF-IDF vectorized with custom tokenizer|Yes|English|spaCy|
|tvec_lemmatized_150.csv|TF-IDF vectorized with custom tokenizer, max_feature = 150|Yes|English|spaCy|
|tvec_lemmatized_250_max_df_0.2.csv|TF-IDF vectorized with custom tokenizer, max_feature = 250, max_df=0.2|Yes|English|spaCy|
|tvec_lemmatized_500_max_df_0.2.csv|TF-IDF vectorized with custom tokenizer, max_feature = 500, max_df=0.2|Yes|English|spaCy|
|tvec_lemmatized_1000.csv|TF-IDF vectorized with custom tokenizer, max_feature = 1000|Yes|English|spaCy|
|tvec_lemmatized_1500.csv|TF-IDF vectorized with custom tokenizer, max_feature = 1500|Yes|English|spaCy|
|tvec_lemmatized_3000.csv|TF-IDF vectorized with custom tokenizer, max_feature = 3000|Yes|English|spaCy|
|tvec_lemmatized_5000.csv|TF-IDF vectorized with custom tokenizer, max_feature = 5000|Yes|English|spaCy|
|tvec_lemmatized_10000.csv|TF-IDF vectorized with custom tokenizer, max_feature = 10000|Yes|English|spaCy|


### Trial Model Results
|Model|Hyperparams|Data|Baseline|F1 Train (Micro)|F1 Test (Micro)|Confusion Matrix|
|---|---|---|---|---|---|---|
|TVEC + Logistic Regression|{'C': 5}|tvec_lemmatized.csv (combine class Discussion/QA/Tech Support/Config)|0.399|0.996|0.661|cm_tvec_lr_1.png|
|TVEC + Logistic Regression|{'C': 7}|tvec_lemmatized_10000.csv (combine class Discussion/QA/Tech Support/Config)|0.399|0.996|0.662|cm_tvec_lr_2.png|
|TVEC + Logistic Regression|{'C': 3}|tvec_lemmatized_5000.csv|0.174|0.985|0.542|cm_tvec_lr_3.png|
|TVEC + Logistic Regression|{'C': 7}|tvec_lemmatized_5000.csv (combine class Discussion/QA/Tech Support/Config)|0.399|0.994|0.662|cm_tvec_lr_4.png|
|TVEC + Logistic Regression|{'C': 3}|tvec_lemmatized_3000.csv|0.174|0.976|0.558|cm_tvec_lr_5.png|
|TVEC + Logistic Regression|{'C': 2}|tvec_lemmatized_3000.csv (combine class Discussion/QA/Tech Support/Config)|0.399|0.946|0.671|cm_tvec_lr_6.png|
|TVEC + Logistic Regression|{'C': 2}|tvec_lemmatized_1500.csv|0.174|0.916|0.531|cm_tvec_lr_7.png|
|TVEC + Logistic Regression|{'C': 3}|tvec_lemmatized_1500.csv (combine class Discussion/QA/Tech Support/Config)|0.399|0.937|0.667|cm_tvec_lr_8.png|
|TVEC + Logistic Regression|{'C': 3}|tvec_lemmatized_1000.csv (combine class Discussion/QA/Tech Support/Config)|0.399|0.917|0.671|cm_tvec_lr_9.png|
|TVEC + Logistic Regression|{'C': 3}|tvec_lemmatized_1000.csv|0.174|0.91|0.516|cm_tvec_lr_10.png|
|TVEC + Random Forest|{'ccp_alpha': 0, 'min_samples_leaf': 1}|tvec_lemmatized.csv|0.174|0.997|0.503|cm_tvec_rf_1.png|
|TVEC + Random Forest|{'ccp_alpha': 0, 'min_samples_leaf': 1}|tvec_lemmatized_3000.csv|0.174|0.992|0.485|cm_tvec_rf_2.png|
|TVEC + Random Forest|{'ccp_alpha': 0, 'min_samples_leaf': 1}|tvec_lemmatized_3000.csv (combine class Discussion/QA/Tech Support/Config)|0.399|0.991|0.645|cm_tvec_rf_3.png|
|TVEC + Random Forest|{'ccp_alpha': 0, 'min_samples_leaf': 1}|tvec_lemmatized_1500.csv|0.174|0.981|0.493|cm_tvec_rf_4.png|
|TVEC + Naive Bayes|{'alpha': 0.1}|tvec_lemmatized_3000.csv|0.174|0.913|0.524|cm_tvec_nb_1.png|
|TVEC + Naive Bayes|{'alpha': 0.1}|tvec_lemmatized_3000.csv (combine class Discussion/QA/Tech Support/Config)|0.399|0.925|0.686|cm_tvec_nb_2.png|
|TVEC + Naive Bayes|{'alpha': 0.1}|tvec_lemmatized_3000.csv|0.174|0.86|0.511|cm_tvec_nb_3.png|
|TVEC + Naive Bayes|{'alpha': 0.1}|tvec_lemmatized_1500.csv|0.174|0.86|0.511|cm_tvec_nb_4.png|
|TVEC + Naive Bayes|{'alpha': 0.1}|tvec_lemmatized_1500.csv (combine class Discussion/QA/Tech Support/Config)|0.399|0.883|0.67|cm_tvec_nb_5.png|

** There are other models that are not recorded due to the performance is not significantly different

### Final Models
||Model|Hyperparams|Data|Baseline|F1 Train (Micro)|F1 Test (Micro)|Confusion Matrix|Suggestion Performance|
|---|---|---|---|---|---|---|---|---|
||TVEC + Logistic Regression|{'C': 0.4}|tvec_lemmatized_3000.csv (remove Video and Picture tag)|0.207|0.781|0.542|final_model_1.png|0.796|
||TVEC + Logistic Regression|{'C': 0.4}|tvec_lemmatized_1500.csv (remove Video and Picture tag)|0.207|0.757|0.529|final_model_2.png|0.783|
|**Selected**|**TVEC + Logistic Regression**|**{'C': 0.4}**|**tvec_lemmatized_1000.csv (remove Video and Picture tag)**|**0.207**|**0.736**|**0.522**|**final_model_3.png**|**0.783**|
||TVEC + Logistic Regression|{'C': 0.4}|tvec_lemmatized_500_max_df_0.2.csv (remove Video and Picture tag)|0.207|0.68|0.499|final_model_4.png|0.747|