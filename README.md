## Distributed Computing Using Spark Lab, University of Freiburg

    Case-Study: Recommender systems for scientific papers using Apache Spark and Python

Dataset

    The dataset used for the experiments contains information collected from http://www.citeulike.org, a website for helping researchers keep track of relevant scientific papers. 
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
        ◦ The results were stored in experiment1-rddResult-yuan-fosoul.csv and experiment1-dfResult-yuan-fosoul.csv
            ▪ Each line contrains the user hash and the list of her retrieved words sorted by frequency (top 1 is the most frequent)
    • Basic Analysis of the dataset

Experiment 2: Collaborative Filtering Recommender System

    • Advanced Analysis
        ◦ Examined the sparsity of the ratings matrix
        ◦ Studied the users’ behavior and papers' popularity by calculating and plotting the rank-frequency distributions
    • Rating matrix preparation
        ◦ Implemented a python program that uses Spark to load users ratings into a rating matrix with the following properties:
            ▪ Positive rating: all papers appear in the user’s library are relevant and have the same rating: 1
            ▪ Unknown rating: Papers which don’t appear in the user’s library are “unrated papers” and are irrelevant with rating: 0.
    • Implemented a Collaborative Filtering Recommender System
        ◦ The system applies the Alternating Least Squares (ALS) algorithm to predict missing entries of the users-papers ratings matrix. 
        ◦ ALS is a collaborative filtering algorithm based on matrix factorization
    • Developed an evaluatation system using the Root Mean Squared Error (RMSE) for the ALS-based recommender system 

Experiment 3: Text Processing and Topic Modeling

    • Implemented a program that extracts useful features from textual content using the bag-of-words representation
        ◦ Applied Tokenization, Stop word removal, and Stemming using NLTK
    • Modeled each paper using the Term Frequency-Inverse Document Frequency (TF-IDF) model
    • Applied the K-means algorithm to cluster the users given their profiles and measured the quality of generated clusters with the Davies-Bouldin index
    • Applied the Latent Direchlet Allocation (LDA) algorithm to show the top 5 terms for each extracted latent topic.
        ◦ Calculated the LDA-based profiles for each user as the summation of the paper-topics vectors of the papers from the user’s library
        ◦ Applied the K-means algorithm to cluster the users using their LDA-profiles and evaluated the clusters using the Davies-Bouldin index

Experiment 4: Evaluating a Content-based Recommender System

    • Implemented two kinds of Content-based Recommender Systems (CBRS) based on the TF-IFD scores of the papers and LDA.
        ◦ The CBRS ranks for each user all papers in the catalog with respect to her profile and return the top-k papers with the highest scores
        ◦ Representations of user and paper profiles were modeled using TF-IDF scores or LDA
    • Conducted an off-line evaluation (Precision, Recall, MRR)	 to evaluate the systems’ performances
    
Experiment 5: word2vec Recommender System

    • Computed word embeddings using word2vec and used them to generate paper recommendations
        ◦ Trained a word2vec model using different text preprocessing strategies
        ◦ Used the word embeddings to create both paper and user profiles
        ◦ Implemented a Recommender System to find matches between those profiles
        ◦ Improved the word2vec Recommender System by TF-IDF scores 
        ◦ Evaluated the performance of the implemented Recommender System
        ◦ Implemented a python function which linearizes analogies and uses the word2vec model to solve analogies
      
Experiment 6: Classification

    • Modeled the recommendation problem as a classification task
    • Preprocessed features and transformed categorical features (e.g. paper type) into a numerical representation using one hot encoding
    • Applied Support Vector Machine (SVM) and Decision trees (Random forest) algorithms to classify the papers as relevant or irrelevant
    • Evaluated the performance of the algorithms with RMSE
      
