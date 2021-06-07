# Data Journal: nan.ai Open Data Corpus
This documentation describes the source of the data, how we curated it, and the process of creating the derived data sets.

# Data Sources
All data sources used were scraped from the internet. The following is the list of data sources used:

  >News
  
  >Twitter
  
  >Wattpad
  
  >Wikimedia
# Derived Datasets
  > News - CSV file containing news articles web scraped from Pilipino Star Ngayon.
  
  > Twitter - data of customer service tweets from various companies.
  
  > Wattpad - stories derived from Wattpad, a website and app for authors to publish new user-generated stories.
  
  > Wikimedia - English-Tagalog articles from Wikipedia.
## Eng-Fil stoplists

- What it contains
  > a list of stopwords (one for English another for Tagalog) derived from the list of open data sources.
- How it's processed
  > Implemented using Python.
  
  > Derived Datasets were scraped and pushed to aws s3.
 
  > Datasets were loaded to Apache Zeppelin notebook.
 
  > Data cleaning was done to the derived datasets.
 
  > Imported list of Tagalog and English stoplist from python library advertools.
  
  > English stoplist were translated using https://www.tagalogtranslate.com/translate.php and python library googletrans.
  
  > Translated tagalog stopwords to sms languages and added to list.
  
  > Data cleaned using defined tagalog and english stopwords.
  
  > Used term frequency to each dataset to get additional stopwords.
  
  > Added top 5% of dataset as stopwords.
  
  > Imported tagalog and english stoplists as csv file to s3 bucket.
- Future work
  > Add more datasets to extend stoplist.
- Update
- References
  > https://www.tagaloglang.com/filipino-sms-language/
  
  > https://github.com/stopwords-iso/stopwords-tl
  
  > https://advertools.readthedocs.io/en/master/advertools.stopwords.html
  
  > https://www.slideshare.net/anntp/natural-language-processing-and-python  


## Eng-Fil bigrams and trigrams
- What it contains
  > a list of bigrams and trigrams (one for English another for Tagalog) derived from the list of open data sources.
- How it's processed
  > Implemeted using Python.
  
  > Processed using the same notebook creating stopwords.

  > Filtered datasets by extracting rows which contains stopwords.
  
  > Imported python library nltk for bigrams and trigrams.

  > Created bigrams and trigrams from the filtered datasets.
  
  > Conducted term frequency for bigrams and trigrams derived.
  
  > All bigrams and trigrams occuring at least 100 times were added to the list.
  
  > Exported lists as csv file to s3.
  
- Future work
  > Add more open data to improve bigrams and trigrams list.

  > Derive N-grams (4 or 5) from the datasets as needed.
  
- Update
- References
  > https://stackabuse.com/implementing-word2vec-with-gensim-library-in-python
  
  > https://github.com/Kyubyong/wordvectors
  
  > https://github.com/Adrianogba/bigram-trigram-python/blob/master/bigram-trigram-tkinter.pyw
  
  > https://stackoverflow.com/questions/24347029/python-nltk-bigrams-trigrams-fourgrams
  
  > https://towardsdatascience.com/text-analysis-basics-in-python-443282942ec5
