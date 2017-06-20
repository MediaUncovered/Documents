# Word Embeddings

## Definition Word Embedding

In order to effectively automate text analysis and processing tasks such as text classification, information retrieval, machine translation or text generation a word representation, that is able to capture as much information as possible about a words meaning(s), semantic/syntactic relationships and contexts in which it appears, is necessary.
A word embedding is a real-valued feature vector representing a word.


### Differene to distributional semantic models

There two main distinctions in word embeddings or so called distributional semantic models: *count-based models* and *prediction-based models*.

*Count-based models* capture the co-occurrences of neighbouring words in a large text corpus and map this count-statistics down to a small dense vector for each word. Typical methods include Latent Semantic Analysis (LSA) and Latent Dirichlet Allocation (LDA).
They are effective in identifying word similarity but are computationally costly.

*Predictive models*, in contrast, try to predict a word from its neighbors by learning embedding vectors (parameters of the model).
Baroni et al. (2014) demonstrate that, in nearly all tasks, predictive models consistently outperform count-based models.

## Implementations of count-based models

### GloVe
Word embeddings are obtained by reducing the dimensionality of the co-occurrence matrix. Factorization yields a word x feature matrix which represents the word embeddings. So the ration of co-occurrence probabilities of two words (rather than just their co-occurrence probabilities) are encoded.
Advantage: easier to parallize --> easier to train on large dataset


### WordRank

WordRank is also based on the co-occurrence matrix. But obtains the word embeddings by formulating a ranking problem. 
That is, given a word w, it aims to output an ordered list (c1, c2, · · ·) of context words such that words that co-occur with w appear at the top of the list. This formulation fits naturally to popular word embedding tasks such as word similarity/analogy since instead of the likelihood of each word, we are interested in finding the most relevant words in a given contex

WordRank results are more inclined towards attributes of a word, such as *crowned*, *throne*, etc. for *king*, while word2vec finds more synonyms or words with a similar context *eochaid*, *canute*,...

## Implementations of predictive models

### Word2Vec
Word2Vec is a computationally-efficient predictive model and can be divided into:
* *Continuous Bag-of-Words (cBOW)* - uses context, n words before and after, to predict a target word w. The order of the context is not important, so the distributional information is smoothed which is particularry useful for smaller datasets.

* *Skip-Gram* - uses the target word to predict its context. Each context-target pair is treated as a new observation which works better for larger datasets. 


### FastText
FastText is an extension of word2vec that treats each word as a composition of character n-grams ( *apple* is the sum of the n-gram vectors *ap*,*app*,*appl*,*apple*,*ppl*,...).
Advantages:
- obtain better word embeddings for rare words
- able to process out of vocabulary words
- better at encoding syntactic information due the usage of n-grams

But, word2vec performs better on semantic tasks


## References

Sebastian Ruder - [On word embeddings](http://sebastianruder.com/word-embeddings-1/)

Jordy Van Landeghem - [A Survey of Word Embedding Literature: Context Representations and the Challenge of Ambiguity](https://www.researchgate.net/publication/301779119_A_Survey_of_Word_Embedding_Literature_Context_Representations_and_the_Challenge_of_Ambiguity)


Analytics Vidhya (NSS) - [An Intuitive Understanding of Word Embeddings: From Count Vectors to Word2Vec](https://www.analyticsvidhya.com/blog/2017/06/word-embeddings-count-word2veec/)

Parul Sethi - [WordRank embedding: “crowned” is most similar to “king”, not word2vec’s “Canute”](https://rare-technologies.com/wordrank-embedding-crowned-is-most-similar-to-king-not-word2vecs-canute/)

TensorFlow - [Vector Representations of Words](https://www.tensorflow.org/tutorials/word2vec)
