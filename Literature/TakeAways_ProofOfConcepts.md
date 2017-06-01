## Take-Aways Student Report:
### Capturing political and ideological biases with word embeddings

Main take-aways, problems and questions when capturing biases in newspapers with **word2vec**.

#### 1. Data Collection

- same time frame
- comparable size of collection of newspaper articles (minimum size: ?)
- same distribution over topics (domestic, foreign policy, ucraine crisis,....)
- remove duplicates, too short or too long articles (avoid commercials leaking into the articles, ensure that no article has more weight than others)
- preprocessing?
	- Removal of stopwords/special characters
	- lowercase letters
	- lemmatization
	- split into sentences
- word2vec model: determine window size, vector length, minimal word count,...
--> compare to Bolukbasi et. al. (2016)


#### 2. Analysis

- test syntactic (depends on preprocessing) and semantic regularities of word2vec models 

- generate analogical relations (she:he, East:West, Christianity:Islam, good:bad)
- create word clouds word highly associated (> threshold) with keyword
- keyword projection
- difference in cosine similarity: is a keyword closer to *good* or to *bad*
- how to compare two vector spaces?


#### 3. Interpretation
- synonyms (U.S., USA, US, United States, United States of America,..)
--> averaging words?

- word usage and vocabulary differs between different cultural contexts
- the more frequent a word appears, the higher its possibility to appear in different contexts.
The word will be associated with different concepts and therefore the cosine similarity to a word representing only one of this contexts, is decreases.
--> filtering by cosine similarity threshold is questionable

- moral judgement is often implicit --> *good* or *bad* might not be good indicators to detect hidden preferences
- based on cultural experience we have a strong negative association with *propaganda*
- Careful interpretation is required as word associations are out of context, e.g. there is (no) freedom
--> use bi/trigrams and in-depth analysis of original articles
