# Information-Retrieval
In this project, the following are implemented: -
1. Boolean Information System
2. Page Ranking and HITS algorithms

## Boolean Information System: -
The dataset consists of textual data from various plays of Shakespeare. The project is aimed at designing and developing a Boolean Information Retrieval System that returns the document (play) names when given a Boolean query. The input Boolean query can consist of AND, OR, and NOT operations along with their combinations. 
The following features/pre-processing steps have been implemented: -
1. Stopword removal
2. Case folding
3. Stemming 
4. Wildcard query handling using Permuterm method
5. Spelling correction using Edit Distance

## Page Ranking and HITS Algorithm: -
The page ranking algorithm has been implemented with and without random teleportation by computing the principal left eigen vector of the probability transition matrix using the Power Iteration method. Further, the HITS algorithm is implemented to get the Hub and Authority scores of each node in the base set of the given query in order to find the dynamic page ranks. 
