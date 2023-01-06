Congratulations! You’ve just been hired as a Data Engineer at a biotech research firm. Your first project is to build out a data pipeline to ingest Covid-19 statistics data then perform exploration on that data to answer some questions that your team has been eager to figure out.


## Data source

The data source is the covidtracking.com API (v2). You can hit the below endpoint to get Covid statistics for a given US state and date. Feel free to replace the state `ca` with any US state you’re interested in getting the data for. The date parameter should be in `YYYY-MM-DD` format. No API key is required.

**https://api.covidtracking.com/v2/states/ca/{date}.json**


## Challenge prompt
Submit a Python/SQL script, better yet - a **Jupyter notebook**, that satisfies the below requirements:

1. Hit the Covid tracking API endpoint above and retrieve data for the entire month of both January and February 2021. The dataset should contain the following fields: `date`, `state`, `cases`, `population_percent`, `change_from_prior_day`, `seven_day_change_percent`. You are welcomed to use any Python libraries or frameworks you desire to accomplish this task. Show the code for this process in your script/notebook.


2. Save that data to a “data lake” (AWS S3, GCP Cloud Storage, Azure Blob, etc.). You do not have to actually connect and write the data file to a real cloud storage bucket in your script/notebook. Just show what that code would look like in your script/notebook.
    *  Questions to keep in mind:
        * What file type are you saving the file as? Why?
        * How would you partition this data if you were building out this pipeline in production to store data for every US state over the span of multiple years?


3. Spin up either a local instance of a free relational database (Postgres, Mysql, etc.) or create a free trial account for a cloud-native relational database (Snowflake, Redshift, AWS RDS, etc.). You will soon copy the data file from your “data lake” to this database.


4. Create a table in your database to store the Covid statistics data from your data file. Your table should have the following columns: `date`, `state`, `cases`, `population_percent`, `change_from_prior_day`, `seven_day_change_percent` and `weekday_name` ("Monday", "Tuesday", etc.). Show the `CREATE TABLE` statement in your script/notebook
    - Questions to keep in mind:
        * What data type would you declare for each column?
        * What constraints, if any, would you declare for your table? Why?


5. Copy the data file into the table you just created above. Again, the file being copied into your table does not need to be from a cloud storage bucket. However, you should actually copy that data file (presumably from your local disk) into your local/cloud database so that you query it later. Show your “copy into” statement in your script/notebook.
    * Questions to keep in mind:
        * How would you populate the `weekday_name` field?
        * How would you make sure that the data you’re copying into the table doesn’t already exist (thus duplicating data)?


6. Finally, answer the below questions regarding the Covid statistics dataset you ingested by querying your table using a **single** SQL query for each of the three question. Show the SQL query (`SELECT` statements) for each question in your script/notebook.
    1. Which week day (`weekday_name`) in January had more combined cases than any other week day? Return a single `weekday_name` value.
    2. What date in January had the second highest case change from prior day? Return a single `date` value.
    3. What are the single worst dates in terms of cases for January and February? What is the case count for these two dates? What day of the week (`weekday_name`) are these two dates? Return two rows, one for each month, with the `date`, `cases` and `weekday_name` values for these two dates.


## Additional notes

While you are not asked to save the data file(s) to an actual cloud storage bucket or copy it from a cloud storage bucket into your database - you are encouraged to do so! Bonus points if you are able to connect and copy the data into a cloud-native relational database too (Snowflake, Redshift, AWS RDS, etc.). Feel free to use any cloud provider you wish and any relational database systems you’d like.



## CodeSubmit
Please organize, design, test and document your code as if it were going into production - then push your changes to the master branch.

All the best,

The CodeSubmit Team
