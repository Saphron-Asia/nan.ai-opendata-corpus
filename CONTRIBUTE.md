# How to contribute

We welcome efforts to improve this project, and we are open to contributions for process improvements, and general good ideas. Please use this guide to help structure your contributions and to make it easier for us to consider your contributions and provide feedback. If we do use your work we will acknowledge your contributions to the best of ability, and all contributions will be governed under the license terms specified in the LICENSE.md file in this project. To get started, sign the Contributor License Agreement.
In general we use the structure provided by GitHub for our workflow management, so if you're new to GitHub please see this [`guide`](https://guides.github.com/activities/contributing-to-open-source/#contributing) first. 
Your contributions have the potential to have a positive impact on not just us, but everyone who is impacted by anyone who uses this project. So, consider that a big thanks in advance.


## Reporting an issue

We use GitHub Issue Tracking [`here`](https://github.com/Saphron-Asia/nanai-opendata-ocr/issues) to track issues. This is a good place to start and can be a helpful place to manage both technical and non-technical issues.


## New sources

* Have a potential source? Fantastic! Follow these steps to help us get it into the project as fast as possible!    
  - Check the wiki [link to a wiki page containing collated data sources; see sample on comment] to make sure it isn't listed there.

* Still a new source? Awesome!  
  - If the source costs money, please add it to the Commercial Wiki [insert link]
  - If you have an awesome link/contact but no data, add it to the Outreach Wiki [insert link]
  - Finally if you have raw data, open an issue [issue page] and we'll add it for you or add it yourself.


## Adding data sources (AWS S3)

**Note:** The credentials provided here are shared across all data contributors. Hence, the permissions granted to it are limited. The key-pair provided can only access the dedicated open data bucket `saphron-opendata-submissions` and **upload** objects there. Make sure that the data to be uploaded is the correct version/copy because only the **Project Maintainers** are capable of deleting S3 files/ojbects. 

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
  [2021-04-14 14:48:36]    0B raw-data-ocr-chatbot/
  [2021-04-14 14:48:19]    0B raw-data-ocr/
  [2021-04-16 11:38:37]    0B saphron-opendata-submissions/
  ```
4. Upload your data to the `saphron-opendata-submissions` bucket:
  ```
  mc cp <your-file> <alias-for-opendata>/saphron-opendata-submissions
  ```
5. Confirm that your file has been uploaded to the S3 bucket successfully:
  ```
  mc ls <alias-for-opendata>/saphron-opendata-submissions
  ```
  And check if your file is in the returned objects list.
