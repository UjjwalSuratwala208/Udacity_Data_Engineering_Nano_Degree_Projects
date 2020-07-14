Project Description
----------------------------
A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

Building an ETL pipeline that extracts their data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights in what songs their users are listening to.

To complete the project, you will need to load data from S3 to staging tables on Redshift and execute SQL statements that create the analytics tables from these staging tables.

Schema for Song Play Analysis
---------------------------------------
Using the song and event datasets, you'll need to create a star schema optimized for queries on song play analysis. This includes the following tables.


Fact Table:- 
--------------------
songplays - records in event data associated with song plays i.e. records with page NextSong
      -- songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

Dimension Tables:-
----------------------------- 
users - users in the app
   --user_id, first_name, last_name, gender, level

songs - songs in music database
  -- song_id, title, artist_id, year, duration

artists - artists in music database
  -- artist_id, name, location, lattitude, longitude

time - timestamps of records in songplays broken down into specific units
  -- start_time, hour, day, week, month, year, weekday


Staging Tables:- 
----------------------
stag_events dumping event log files from s3 directly in this table stag_songs dumping songs files from s3 directly in this table.


Scripts to execute:-
--------------------------
1) dwh.cfg - contains the details to connect to the redshift cluster.

2) sql_queries.py -contains CRUD statements for creating star schema and staging tables

3) create_tables.py - contains the functions to import from sql_queries.py for creating tables.

4) etl.py -  loads the json files for songs and logs dataset from the s3 folder on the db in the staging table and then insert into fact and dimension tables.