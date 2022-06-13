# test_technical_discussion
This is a technical discussion demo.


## Heading 2

* bullet 1
* bullet 2

regular text

This is a good example of [my code](https://gist.github.com/robptrck/ff4b3b4bbdb1ff52dbc750a0e816)

Code for writing SQL queries inside Python using sqlite3 and pandas [my code](https://gist.github.com/robptrck/4aed3cef8c8b49e4f5454f78954c7597)

Test inputting table

|index|team|country|season|total\_goals|
|---|---|---|---|---|
|0|Real Madrid|Spain|2019|53|
|1|Barcelona|Spain|2019|47|

```
# Average goal by team

conn = sqlite3.connect('test.db')

cursor = conn.execute(''' SELECT team,
                            AVG(total_goals) AS avg_goals
                          FROM team_data
                          GROUP BY team;''')

for row in cursor:
  print(row)
```

---
### Steps to create table, import data and make a query
```
# Create the table

import sqlite3

conn = sqlite3.connect('test.db') '''

conn.execute('''
CREATE TABLE IF NOT EXISTS team_data(team text, 
                      country text, 
                      season integer, 
                      total_goals integer);''')

# Insert data

conn.execute("INSERT INTO team_data VALUES('Real Madrid', 'Spain', 2019, 53);")
conn.execute("INSERT INTO team_data VALUES('Barcelona', 'Spain', 2019, 47);")
conn.execute("INSERT INTO team_data VALUES('Arsenal', 'UK', 2019, 52);")
conn.execute("INSERT INTO team_data VALUES('Real Madrid', 'Spain', 2018, 49);")
conn.execute("INSERT INTO team_data VALUES('Barcelona', 'Spain', 2018, 45);")
conn.execute("INSERT INTO team_data VALUES('Arsenal', 'UK', 2018, 50 );")

# Average goal by team

conn = sqlite3.connect('test.db')

cursor = conn.execute(''' SELECT team,
                            AVG(total_goals) AS avg_goals
                          FROM team_data
                          GROUP BY team;''')

for row in cursor:
  print(row)
  
# select team data

cursor = conn.execute('''Select *
                         From team_data''')

for row in cursor:
  print(row)

# create df

import pandas as pd

df = pd.read_sql_query("SELECT * FROM team_data", conn)
df
```
|index|team|country|season|total\_goals|
|---|---|---|---|---|
|0|Real Madrid|Spain|2019|53|
|1|Barcelona|Spain|2019|47|
|2|Arsenal|UK|2019|52|
|3|Real Madrid|Spain|2018|49|
|4|Barcelona|Spain|2018|45|
|5|Arsenal|UK|2018|50|
|6|Real Madrid|Spain|2019|53|
|7|Barcelona|Spain|2019|47|
|8|Arsenal|UK|2019|52|
|9|Real Madrid|Spain|2018|49|
|10|Barcelona|Spain|2018|45|
|11|Arsenal|UK|2018|50|
