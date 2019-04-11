# Data Modeling using POSTGRESQL 
### A project at Udacity Data Engineering Nanodegree

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to.

Data source is divided by two main sources, songs meta-data and logs of what users are listening (user activity) which they are currently stored as JSON files.

#### Let's see an example for both sources:
##### Songs meta-data:
![Songs meta-data!](/images/songs.png "Songs meta-data")

##### Logs:
![Logs!](/images/logs.png "Logs")


The company goal is to query this data sets and find some analytics and insights. One example is to counts songs that are played this month for a specific artist.

#### Solution
##### Step1: Design the star schema 


![Entity Relationship Diagram!](/images/diagram.png "Entity Relationship Diagram")

##### Step2: Extract the requeried data from JSON files. 
Using Pandas, I have did the following:
1. Read the data from songs and logs JSON files.
2. Process the data and extract only the requeired fields.
3. Insert the data to their corresponsing fields.

##### Step3: Answer the query to find the song ID and artist ID based on the song title, artist name, and duration of a song.
Joining Artists and Songs tables to find songs that match the above criteria in the log files, and insert the results into a new table songplays_table.

Example of the resulting query:
![Result Query!](/images/result-query.png "Result Query")

##### Step4: Find some insights about the result data.
In the dashboard.ipynb we can find some visualization and statistcs about users who used the app.

Example: Top users who used the app after getting their names from users table
![top_users!](/images/top_users2.png "Top Users")

#### Project Files:
1. etl.ipynb: a jupyter notebook that process only one song and log files, to make sure that all code functionality works without any problem. (Work on small data sets and then apply the solution to larger dataset.)
2. etl.py: The actual python script file which will process all Json files and datasets.
3. create_tables.py: A python script to create the designed star schema.
4. sql_queries: SQL queries that will apply at create_tables.py 
5. test.ipynb: A Jupyter notebook for testing purposes and querying the database.
6. dashboard.ipunb: A Jupyter notebook where we can do some analytics queries.

#### How to run the project:
1. Make sure that your songs inside /data/song_data sub-directory and your logs data inside /data/log_data and they're in JSON format.
2. I assume that your POSTGRES server is up, running and you have the permissions of creating new database.
3. run create_tables.py
4. run etl.py
5. Using test.ipynb, you can see your results in songplays_table.
