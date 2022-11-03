# Boolean IR System - Implementation ReadMe

This file contains the function names in our code, their description, and some test cases to evaluate them.

# Functions
###  DATA PREPROCESSING
> _CASE FOLDING_
- This function makes sure all the words in our document are in lower case.
```sh
def Case_Folding(data):
```

> _REMOVE PUNCTUATIONS_
- Removes symbols that are not useful for evaluation.
```sh
def Remove_Punctuations(data):
```
 
> _STOP WORD REMOVAL_
- Removes the most commonly occuring words that are again may not useful for retrieval and evaluation.
```sh
def Stop_Word_Removal(data):
```

> _STEMMING_
- Group inflected words to their origin word/root word.
```sh
def Stemming_fn(data):
```

> _SAVING UNIQUE WORDS_
- Avoid repition of words and create a vocabulary of distinct words.
```sh
def save_unique_words(data):
```

> _SAVING UNIQUE WORDS_
- Avoid repition of words and create a vocabulary of distinct words.
```sh
def save_unique_words(data):
```

### CREATING POSTING LIST 
- Inverted index data structure containg key as one of words from the vocabulary and the calue being a list of documents that contain the word.

```sh
def create_posting_list(data_dictionary):
```
### FUCTIONS FOR SPELL CHECK 
> _EDIT DISTANCE_
- Edit distance is a mathematical tool which evaluates the minimum no of steps required to change one word into another and using this parameter we find the closest resembling word to the wrongly spelled word by comparing with all the words from the vocabulary.

```sh
def EditDistDP(str1, str2):
```
### BOOLEAN INFORMATION RETRIEVAL
- Classical retrieval method based on whether the word is present in the document or not.This function takes in a string input and firstly determines if the query is a boolean query or if it is a spell check request .It finds out if the query is a spell check request if such a word does not beolng to the vocabulary .It finds out the documents which satisfy the boolean query and in case of a spell check it return the closest correctly spelt word.
```sh
def compute_documents(inp)
```

- After loading the dataset we can test the above using the below given sample testcases.
```sh
inp = "avail and bond" 
compute_documents(inp)

inp = "ador or sun"
compute_documents(inp)

inp = "azail and bknd"
compute_documents(inp)

inp = "worship NOT encount"
compute_documents(inp)

inp = "worshipzz NOT enocount"
compute_documents(inp)

inp = "anchoxd AND error AND chast" 
compute_documents(inp)

inp = "speedily AND happened OR honestly" 
#Speedily and happened = 1, 11, 14, 36. 'OR' this with 1,10,22,27,38
compute_documents(inp)

inp = "speedily OR honestly Not happened" 
#Speedily or honestly = 1, 36, 6, 38, 8, 10, 11, 14, 17, 21, 22, 27. From this remove 1, 7, 11, 12, 14, 22, 25, 33, 34, 36, 38
compute_documents(inp)

inp = "speedily or happened or honestly and likelihood" 
compute_documents(inp)
```
> By changing the inp value you can give your own test case and evaluate the compute_documents function.

### WILDCARD QUERIES USING BIGRAM MODEL
>Bigram model basically groups two letters together. So till now we had one word and a list of documents for that word.But now we have modified the model where instead of considering one word we now consider a word which basically is two letters joined together.
- creating a list of bigrams
```sh
def create_bigram_list(word):
```
- we also add reverse of the words to the dictionary to make sure all kinds of wildcard queries can be assessed.
- Now we add words from the vocabulary and take their reverse and compute bigram lists.

```sh
def bigram_save_unique_words(data):
```
- Now we take input of the wildquery and compute bigram lists using above functions of the strings based on the position of *.Using various set operation we finally get the document numbers containg such words.
```sh
def wildcard_compute_documents(inp):
```
- Following test case can be used to assess the function.using results from compute_documents we can check if they match.
```sh
inp = "spee*ly"
wildcard_compute_documents(inp)

inp = "speedily"
compute_documents(inp)
```
> _ISSUE FACED WHILE IMPLEMTING THE BIGRAM MODEL:_
>Since a combination of two letter is extremely likely to occur in most documents, almost all the documents were retrieved when a query was passed.Hence we tried to implement the K-gram model where instead of 2 we had a positive value k which inturn depends on the query given by the user.

### A MORE EFFICIENT APPROACH- K-GRAM MODEL

- Previously in the Bigram model we used 2 letter combinations and we faced some issues with such an implementation.
- Now K-gram model is used and the only difference now is that instead of two we choose the value of k depending on out query.
- We again use the concept of reverse words to handle any kind of wildcard query.
- Creates a list of k-grams.
```sh
def create_kgram_list(word, k):
```
- Consider each word its reverse and compute kgram lists of all possible combinations.
```sh
def kgram_save_unique_words(data, k):
```
- Using intersection of the lists obtained by creating lists of the strings obtained via the query which depends on the position of * we finally obtain the documents containing the wildcard query.
```sh
def wildcard_compute_documents(inp):
```
- The following sample test case is used to evaluate the function for queries of the form x*y.
```sh
inp = "aban*on" 
ct1 = 0
ct2 = 0 #Position of *
for i in inp: 
  if i!= "*":
    ct1 = ct1+1
  else:
    break

ct2 = len(inp)-ct1-1
```
- By changing the value of inp variable you can test any kind of wildcard query.
- Some more example testcases are given below by changing the value of inp you can check if the query is properly assessed.
-  Queries of the form xyz*
```sh
#Queries of form xyz* 
inp = "aban*" #1, 33, 4, 36, 38, 39, 40, 41, 10, 14, 18, 23, 30
inp = inp[:-1]
print(postings[inp])
print("The document names are: ")
for i in postings[inp]: 
    print(title_dict[i])
```
-  Queries of the form *xyz
```sh
#Queries of form *xyz
inp = "*bund" #Eg: abund
#1, 34, 5, 37, 39, 8, 9, 40, 16, 24, 25, 28, 30
#Search posting list for dnub*
inp = inp[1:]
inp = inp [::-1]
print(postings[inp])
print("The document names are: ")
for i in postings[inp]: 
    print(title_dict[i])
```
### END










