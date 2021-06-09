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

**Note:** The credentials provided here are shared across all data contributors. Hence, the permissions granted to it are limited. The key-pair provided can only access the dedicated open data bucket `saphron-opendata-nlp` and **pull** objects there. 

1. Install MinIO client to access S3 (AWS Simple Storage Service) by following the steps listed [here](https://docs.min.io/docs/minio-client-complete-guide).
2. Set your connection to AWS S3 by running: 
  ```
  mc alias set <alias-for-opendata> https://s3.amazonaws.com AKIA6KOZY3ODLRYTJW6H 5L0Db6cJAeuLZ1CuQ+woYkvxHJ5VH59kYg9x79uz --api S3v4
  i.e.
  mc alias set unicef-opendata-pull-data https://s3.amazonaws.com AKIA6KOZY3ODLRYTJW6H 5L0Db6cJAeuLZ1CuQ+woYkvxHJ5VH59kYg9x79uz --api S3v4
  ```
3. Verify that you are connected:
  ```
  mc ls <alias-for-opendata>/<s3-bucket>
  i.e. 
  mc ls unicef-opendata-pull-data/saphron-opendata-nlp
  ```
  You should see something similar to this: 
  ```
  [2021-04-14 14:48:36]    0B derived/
  [2021-04-14 14:48:19]    0B eng-fil-corpus/
  ```
4. Pull our open data resources from `saphron-opendata-nlp` bucket:
  ```
  mc cp <alias-for-opendata>/saphron-opendata-nlp/<object-path> <destination-path-local>
  i.e.
  mc cp unicef-opendata-pull-data/saphron-opendata-nlp/eng-fil-corpus/test.txt test.txt
  ```
5. Confirm that the file has been copied to your local machine.
