Dataset

    The dataset used for the experiments contains information collected from citeulike website (http://www.citeulike.org). 
    A website for helping researchers  keep track of relevant scientific papers. 
    Users can build their personalized libraries by adding selected papers to their libraries and annotate them with personalized tags tags.
    
    The dataset records information about a set of users, their libraries, and a set of scientific publications (papers).
    
    • # users = 28,416
    • # papers = 172,079
    • min library size = 10
    • max library size = 2,000
    • min paper popularity = 3

Experiment 1

    • Created a script that computes for each user the top-10 most frequent words (stop words excluded) appearing in the papers she liked.
        ◦ Using RDD and DataFrames (Spark Data Models)
        ◦ The results are stored in experiment1-rddResult-yuan-fosoul.csv and experiment1-dfResult-yuan-fosoul.csv
            ▪ Each line contrains the user hash and the list of her retrieved words sorted by frequency (top 1 is the most frequent)
    • Basic Analysis of the dataset

Experiment 2: Collaborative filtering Recommender System

    • Advanced Analysis
        ◦ Examined the sparsity of the ratings matrix
        ◦ Study the users’ behavior and papers popularity by calculating and plotting the rank-frequency distributions
    • Rating matrix preparation
        ◦ Implemented a python program that uses spark to load users ratings into a rating matrix with the following properties:
            ▪ Positive rating: all papers appear in the user’s library are relevant and have the same rating: 1
            ▪ Unknown rating: Papers which don’t appear in the user’s library are “unrated papers” and are irrelevant with rating: 0.
    • Implemented a Collaborative Filtering (CF) Recommender System
        ◦ The system applies the Alternating Least Squares (ALS) algorithm to predict missing entries of the users-papers ratings matrix. 
        ◦ ALS is a collaborative filtering algorithm based on matrix factorization
    • Developed a python program to that uses Spark to evaluate the ALS-based recommender system 
        ◦ The program splits the ratings randomly into training set and test set with 70% and 30% of the ratings respectively
        ◦ Fit a model on the training set.
        ◦ Calculate the Root Mean Squared Error (RMSE) over the test set

Experiment 3: Text processing

    • Implemented a program that uses spark to extract useful features from textual content using the bag-of-words representation
        ◦ Applied Tokenization, Stop word removal, and Stemming using NLTK
    • Modeled each paper using the Term Frequency- Inverse Document Frequency (TF-IDF) model
    • Applied the K-means algorithm to cluster the users given their profiles and measured the quality of generated clusters by calculating the Davies-Bouldin index
    • Applied the Latent Direchlet Allocation (LDA) algorithm to show the top 5 terms for each extracted latent topic.
        ◦ Calculated the LDA-based profiles for each user as the summation of the paper-topics vectors of the papers from the user’s library
        ◦ Applied the K-means algorithm to cluster the users using their LDA-profiles and evaluated the clusters using the Davies-Bouldin index

Experiment 4: Evaluating a Content-based Recommender System

    • Implemented two kinds of Content-based Recommender Systems (CBRS) based on the TF-IFD scores of the papers or LDA.
        ◦ The CBRS ranks for each user all papers in the catalog with respect to her profile and return the top-k papers with the highest scores
        ◦ A representation of the papers are modeled using TF-IDF scores or LDA
        ◦ A representation of the users are modeled using the aggregating the paper representations (TF-ID or LDA) for each user with respect to her library
    • Conducted an off-line evaluation (Precision, Recall, MRR)	 to evaluate the systems’ performances
    
Experiment 5: word2vec Recommender System

    • Constructed and improved a word2vec system by TF-IDF scores that pre-processes texts and computes word embeddings to generate paper recommendations
      
Experiment 6: Classification

    • Applied SVM and Random forest to classify the papers as relevant or irrelevant
      
