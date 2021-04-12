# Language Processing Module

### Team - 

| S. no | Name | Enrollment no   |
| ----- | ---- | --------------- |
| 1 | Jay Puri Goswami  | [BT18CSE073]  |
| 2 | Anurag Baral  | [BT18CSE077]  |
| 3 | Prince Sharma    | [BT18CSE147]  |



#### Our project of Automatic Answer checking is divided into 2 modules -> 
##### 1) Converting given input image file into text file 
##### 2) Using the text file generated to find how correcrt the given answer is 


<b> This page deals with the second module . The crux of it is to use natural language processing to find document similarities and accordingly allocate marks to student . </b>

Document Similarity has many aspects and using just one algorithm won’t suffice. Other than capturing the syntactic similarity we also have to capture the semantic similarity and context and understand whether two given texts (though entirely different in words) are same or not.
So we have used 2 methods of WMD (Word mover’s distance) and USE (Universal sentence encoder) for calculating the similarity between 2 text answers.
 
### USE (Universal Sentence Encoder)
Universal Sentence Encoder encodes documents into high dimensional word vector space (512 dimensional space to be specific) and then the document encoded can be used for various applications. For our project we have mainly used it for cosine similarity calculation

### WMD (Word Mover’s distance)
WMD is a distance measurement technique between 2 documents. It leverages the word vector model to come up with a distance metric for documents with no common words/texts which overcomes basic distance measurement techniques.  WMD can be defined as the cumulative sum of minimum distance needed to travel from one word of document 1 to another word of document 2. Less the distance more similar the document is. We have used normalised WMD technique using gensim library and “Google news vector”
 
## Evaluation Technique
Our model takes the actual answer and given answer and the scoring function is divided into 2 parts –
Calculating syntactic and semantic similarity
Calculating WMD

### 1) Calculating Similarity 
While calculating similarity we split the given document around full stop and then for each “given answer” we look for the text from “actual answer” which matches the most and for both sentence we look for the semantic expression using the “negative word list” that we have. If the semantic expressions of both are different then the word vector of “given answer” is multiplied by -1 which will ensure that semantic similarity is taken into account while calculating similarity. Finally after repeating the above process for all statements of “given answer” all word vectors are combined and cosine similarity between “given answer” and “actual answer” is calculated.

### 2)  Calculating WMD 
Using WMD we calculate WMD distance between given and actual answer after removing stop words from both (to ensure better result) 

### 3) Calculating final score 
As discussed above, more USE similarity and less WMD distance will ensure a better similarity, so we return (USE similarity)/ (1+ WMD distance) as the score of similarity between 2 documents.


### References 
WMD (Word Mover’s Distance) - https://mkusner.github.io/publications/WMD.pdf <br>
USE - https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/46808.pdf <br>
TensorFlow Hub - https://tfhub.dev/google/universal-sentence-encoder/1
