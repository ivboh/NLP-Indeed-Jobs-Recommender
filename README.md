# Data Scientist Position Recommender


__Abstract:__
This project is to build a recommender for people looking for data scientist positions.

__Conclusion:__
The model can successfully recommend job listings based on input resume.

---
# Intruduction: background and motivation 
If one searches for job posts with keywords "data science" or "data scientist" without further filtering on for example indeed.com, one ends up having tens of thousands of posts as search result. There might be a better way for data science folks to do this.

---
# NLP and model

### Model 
The main model is to find the highest cosine similarities scores of job posts and resume after TFIDF vectorization of their text content.

### NLP and initial EDA
The initial EDA of term frequency and NMF suggests: 

- N-grams for tokenization
- Stemming/lemmitazation 
- Customized stop words set

The topics from NMF can idenfity

- Varies sets of skill sets required by different industry, for exmple,  consulting, health care, defense, traveling, maketing, sales and etc.
- The topic of Legal perspects in hiring process also clustered as a topic, the most frequent terms include for example "equal oppotunity employer" and "sexural orientation". Ideally whose words can be removed from the analysis for this project, however, by returning the highest similarity score I can keep those words as those words are rare in a data scientist's resume and those words are common across job posts from different company. 


### Feature selection

- 580+ components are required to retain >90% of the power from SVD, i.e. the number of words for vectorizer will be greater than 500. 
- Most frequent bi-grams and tri-grams were pre-identified in the text before tokenization.
- The parameter 1,000 was used as the maximum number of features in TFIDF vectorizer for the final model.


---
# Processing flow

### N-grams processing:
0. Job description were monogram tokenized and lemmatized using wordnet lemmatizer.

1. Tokens from step 0 were detokenized 

2. String from step 1 was tokenized in bi, tri and four grams.

2. Most frequent bigrams and trigrams were identified and added to to N-grams set. Four grams are not meaning and ignored.

3. Words in tri-gram set and bi-gram set were hyphenated in string from step 1. 


### Tfidf vectorizing:
0. Take the n-gram processed the job description, and tokenize as monogram

1. Fit and transfer a Tfidf vectorizer using tokens from step 0. The maximum number of features is set to 1,000.

2. Transfer a resume using the Tfidf vectorizer fit from step 1.


### Cosine similarities:

0. Compute the cosine similarity of the vecotor of resume and of each job description.

1.



---
# Result

### Test of resume from different background
- Five examplar resumes were downloaded online, for data scientist, web developer, software engineer, accountant and data base administrator respectively.
- The recommender outputs relevant job posts for each resume.

### Test of using two data scientist resume of different flavor
- Use resume of two data scientists from different backgroud.
- The recommender is able to pick up the difference and recommend more senior and more academia related positions to the data scientist with a Ph.D. 


---
# Data source and tools

### Data source
- 14000+ job listing from indeed.com

### Tools
- Web scraper on AWS EC2
- BeautifulSoup web parser
- Postgres SQL
- Python libraries for NLP
  

---
# Future work

- Seperate paraph of Quailification from other topics in the job posts and only match resume using the qualification content

- Deploy a web app


---
# Acknowledgements 
I'd like to thank Joseph Gartner, Dan Rupp and Brent Goldberg for their guidance, feedback and technical support for this project.


---
# Reference

---
# Web app
TBA
