# Project 3: Data Warhouse- ETL, Cloud Computing with Amazon S3, Redshift 

## Introduction
A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

The task of project is to build an ETL pipeline that extracts their data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights into what songs their users are listening to.


## Project Dataset

Two datasets that reside in S3. Here are the S3 links for each:

```
Song data: s3://udacity-dend/song_data
Log data: s3://udacity-dend/log_data
Log data json path: s3://udacity-dend/log_json_path.json

```
### Song Dataset

The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are file paths to two files in this dataset.

```
song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json
```

And below is an example of what a single song file, TRAABJL12903CDCF1A.json, looks like: 

```
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}
```

### Log Dataset

The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate app activity logs from an imaginary music streaming app based on configuration settings. The dataset is hosted at S3 bucket:

```
s3://udacity-dend/log_data.
```
### Schema for Song Play Analysis

There is fact table: 
* songplays.

Coming with linked 4 dimension tables: 
* songs 
* time 
* users
* artists.

The schema is designed base on Star- Schema. This schema helps users saving time by delivering quicker results within minimum number of "SQL-JOIN". 

In AWS S3 Bucket there are 2 tables: `staging_events` and `staging_events`. Two tables act as "staging" or "parking" tables where data is imported in AWS Redshift.



## Project Template

| Files  | Functions |
| ------------- |:-------------:|
|create_table.py     | Where  fact and dimension tables are created for the star schema in Redshift.     |
| etl.py      |  Load data from S3 into staging tables on Redshift and then process that data into analytics tables on Redshift.    |
| sql_queries.py      |  SQL statements, which will be imported into the two other files above.|
| README.md| Information about project   |