# SO_word2vec
A word2vec model trained on Stack Overflow posts

This repository contains information related to the word2vec model 
presented in paper **_'Word Embeddings for the Software Engineering domain'_** 
as published on the data showcase track of MSR'18. 

## Model file
The the pre-trained model is stored in a .bin file (of approximate size 1.5 GB) 
which can be accessed at this link:
http://doi.org/10.5281/zenodo.1199620

## Instructions on how to use the model
To load the model you will need Python 3.5 and 
[gensim](https://radimrehurek.com/gensim/) library.
### Loading the model

```
from gensim.models.keyedvectors import KeyedVectors
word_vect = KeyedVectors.load_word2vec_format("SO_vectors_200.bin", binary=True)
```

### Querying the model
Examples of semantic similarity queries
```
words=['virus','java','mysql']
for w in words:
    try:
        print(word_vect.most_similar(w))
    except KeyError as e:
            print(e)          
```
```
print(word_vect.doesnt_match("java c++ python bash".split()))
```

Examples of analogy queries
```
print(word_vect.most_similar(positive=['python', 'eclipse'], negative=['java']))
```

## Reference
If you want to use this model please cite

Efstathiou, V., Chatzilenas, C., Spinellis, D., 2018. "Word Embeddings for the Software Engineering Domain". In *Proceedings of the 15th International Conference on Mining Software Repositories.* ACM.


