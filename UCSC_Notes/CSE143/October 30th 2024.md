#UCSC #CSE143

**Term-Document Matrices**

We take some text (sentence, document, etc) and represent it as a count of all of the words that occur.

This is useful if you're doing information retrieval, or just corpus linguistics. Take each of the bag of words vectors, tip them on their sides, and now consider each different document to be a column.


**More Common: word-word matrix or "term context matrix"**

Two words are similar in meaning if their context vectors are similar. Words with similar usages are going to have similar context vectors. We can use a cosine similarity for computing word similarity. 

Some words are more informative than others. If you see the word whale, that's clearly a content word and pretty informative. You might just remove all the "stop words". But there is a more principles approach that scales up to the important informative words. 

**Two common solutions for word weighting**
1. **tf-idf**
2. 




