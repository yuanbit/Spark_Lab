Dataset

    The dataset used for the experiments contains information collected from citeulike website (http://www.citeulike.org). 
    A website for helping researchers  keep track of relevant scientific papers. 
    Users can build their personalized libraries by adding selected papers to their libraries and annotate them with personalized tags tags.
    
    The dataset records information about a set of users, their libraries, and a set of scientific publications (papers).
    
    • # users = 28,416
    • # papers = 172,079
    • min library size = 10
    • max library size = 2000
    • min paper popularity = 3

Experiment 1

    • Created a script that computes for each user the top-10 most frequent words (stop words excluded) appearing in the papers she liked.
        ◦ Using RDD and DataFrames (Spark Data Models)
        ◦ The results are stored in experiment1-rddResult-yuan-fosoul.csv and experiment1-dfResult-yuan-fosoul.csv
            ▪ Each line contrains the user hash and the list of her retrieved words sorted by frequency (top 1 is the most frequent)
    • Basic Analysis of the dataset
