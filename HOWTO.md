# How nan.ai-opendata-corpus works

This open data repository hosted on AWS S3, currently updated and curated as the project progresses. Currently it contains:

```
├─ derived
│  └─ pre-processing
└─ eng-fil-corpus
```

## Running sample notebooks (Apache Zeppelin)
The notebooks are created using Python in Apache Zeppelin. In case you are still on exploratory mode, these notebooks will help you navigate throughout our data pre-processing, curation, and mini use cases we created to build our machine learning model for the [`nan.ai after-sales chatbot`](https://github.com/Saphron-Asia/nan.ai-ml-nlu).

Apache Zeppelin 0.8.2
Python 3.x

1. Install Apache Zeppelin to open the sample notebooks in json format by following the steps listed [here](http://zeppelin.incubator.apache.org/docs/0.8.0/quickstart/install.html).
2. Access Apache Zeppelin on your machine by opening your web browser and navigating to `http://localhost:8080/` (by default, it is on port 8080)
3. On the Apache Zeppelin landing page, click the link that says `Import note` and select the sample notebook you retrieved from our repository.  
4. Open the new notebook that will appear on the landing page. Explore away!

**Note:** The data used in the notebooks can be retrieved from the AWS S3 access provided in the next section.

## Pulling data data from sources (AWS S3)

**Note:** The credentials provided here are shared across all data contributors. Hence, the permissions granted to it are limited. The key-pair provided can only access the dedicated open data bucket `saphron-opendata-nlp` and **upload** objects there. Make sure that the data to be uploaded is the correct version/copy because only the **Project Maintainers** are capable of deleting S3 files/ojbects. 

1. Install MinIO client to access S3 (AWS Simple Storage Service) by following the steps listed [here](https://docs.min.io/docs/minio-client-complete-guide).
2. Set your connection to AWS S3 by running: 
  ```
  mc alias set <alias-for-opendata> https://s3.amazonaws.com AKIA6KOZY3ODHZ3MPK5H PQB85WBcrdFPNI3SD6RRPluNT8S0Xgyq+9dBKoCY --api S3v4
  i.e.
  mc alias set unicef-opendata https://s3.amazonaws.com AKIA6KOZY3ODHZ3MPK5H PQB85WBcrdFPNI3SD6RRPluNT8S0Xgyq+9dBKoCY --api S3v4
  ```
3. Verify that you are connected:
  ```
  mc ls <alias-for-opendata>
  i.e. 
  mc ls unicef-opendata
  ```
  You should see something similar to this: 
  ```
  [2021-04-14 14:48:36]    0B saphron-opendata-nlp/
  [2021-04-14 14:48:19]    0B saphron-opendata-ocr/
  [2021-04-16 11:38:37]    0B saphron-opendata-submissions/
  ```
4. Pull our open data resources from `saphron-opendata-nlp` bucket:
  ```
  mc cp <your-file> <alias-for-opendata>/saphron-opendata-submissions
  ```
5. Confirm that your file has been downloaded from the S3 bucket successfully:
  ```
  mc ls <alias-for-opendata>/saphron-opendata-submissions
  ```