# IR-ASSIGNMENT-1 
## _DESIGN DOCUMENT_



This document contains important data structures and the time complexities of functions used.

# DATA STRUCTURES USED
>Below are some notable data structures used in our code.
- DICTIONARY : title_dict,postings(key= word,value=list of docs)
- SET : stop_words
- LIST: data,clean_data,vocab,global_vocab
- STRINGS: 2d-string in case of edit distance DP,inp


# TIME COMPLEXITIES OF FUNCTIONS 

###  _DATA PREPROCESSING_
###
###

>len(data)=D
>len(global_vocab)=G
>len(word)=W
>len(Stop words)=S

| Function| Time Complexity|
| ----------- | ----------- |
| def Case_Folding(data)| O(D*W)|
|def Remove_Punctuations(data)|O(D*W) |
|def Stemming_fn(data) | Porters Algo|
| def Stop_Word_Removal(data)| O(S*D)|
| def save_unique_words(data)| O(D)|

### _BUILDING INDEX_
###
###
>no of words in each document=N_W
>no of documents=N_D

| Function| Time Complexity|
| ----------- | ----------- |
| def create_posting_list(data_dictionary)| O(N_W* N_D)|
|def create_bigram_list(word)|O(N_D* N_W)|
|def create_Kgram_list(word)|O(N_D* N_W) |
|def wildcard_compute_documents(inp)-BIGRAM|O(product of number of bigrams)|
|def wildcard_compute_documents(inp)-KGRAM|O(product of number of kgrams)|

### _SEARCH AND RETRIEVAL_
###
###
>total words in vocabulary=V
>len(word)=W
>len(query_word)=W'

| Function| Time Complexity|
| ----------- | ----------- |
|def compute_documents(inp)-QUERY|depends on number of sub queries O(N^q)(Polynomial order)|
|def compute_documents(inp)-SPELL CHECK|O(V* W * W') |
|def wildcard_compute_documents(inp)-BIGRAM|O(product of number of bigrams)|
|def wildcard_compute_documents(inp)-KGRAM|O(product of number of kgrams)|

