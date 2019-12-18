# Oncogenic-Classification

### Overview
This project comes from a Kaggle compeition (https://www.kaggle.com/c/msk-redefining-cancer-treatment), where the essence is a multi-class classification problem using genetic variation data as well as medical text data. 


####  **Data**

Original training data included which of 9 oncogenic classes data an observation belonged to and its specific combination of gene + variation ('truncating mutation', 'promoter mutation', 'Q137R', 'W430A', etc.) as well as a text file (~6000 words for each observation) containing clinical information about that genetic variation that could help in classification.

### **Feature Engineering**

- I binarized the information in the variation column in a few ways. One was the type of mutation: missense, nonsense, promoter region-associated, deletion, insertion, insertion-deletion, etc.
 
- Furthermore, I broke down missense mutations into those that encoded an amino acid of a different chemical group (polar, nonpolar, acidic, basic). Sickle cell disease is an example of how a chemical group change of encoded amino acids could have a large effect, as Gluatamic Acid (acidic) is changed to Valine (nonpolar), and I hypothesized a strong change in protein function would affect oncogenic classification.

- For Natural Lanaguage Processing (NLP), I used NLTK and Scikit Learn. I sorted the text data by category and took the top words that were repeated at least in 1/4 of all documents within each group. Those were the features I then used in the whole data set, where I counted their occurence using Count Vectorizer. 

#### **Models**


- Created and validated Random Forest, Bernoulli and Multinomial Naïve Bayes, Support Vector Machines, and other models. Random forest ended up being my best model, accurately predicting just under 70% of the unseen test data into their correct classes. There were 9 total classes.   

- Validation through random search with each type of model (various hyperparameters for each), and using 10 stratified K Folds. 
