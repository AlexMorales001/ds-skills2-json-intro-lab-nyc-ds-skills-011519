
# Working with Known JSON Schemas - Lab

Here you'll get a little more practice working with JSON files before moving on to playing with APIs all on your own where you'll synthesize reading documentation, making get requests and then parsing JSON data.

## Reading a JSON Schema

Here's the JSON schema provided for a section of the NY Times API:
<img src="nytimes_movie_schema.png" width=500>

or a fully expanded view:

<img src="nytimes_movie_schema_detailed.png" width=500>

You can see this yourself here:
https://developer.nytimes.com/movie_reviews_v2.json#/Documentation/GET/critics/%7Bresource-type%7D.json

You can see that the master structure is a dictionary and has a key named 'response'. This is also a dictionary and has two keys: 'data' and 'meta'. As you continue to examine the schema hierarchy, you'll notice the vast majority in this case are dictionaries. 

## Loading the Data File

Start by importing the json file. The sample response from the api is stored in a file **ny_times_movies.json**


```python
#Your code here
```


```python
import json
```


```python
f = open('ny_times_movies.json', 'r')
data = json.load(f)
```

## Loading Specific Data

Create a DataFrame of the major data container within the json file, listed under the 'results' heading in the schema above.


```python
#Your code here
import pandas as pd
df = pd.DataFrame(data['results'])
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>byline</th>
      <th>critics_pick</th>
      <th>date_updated</th>
      <th>display_title</th>
      <th>headline</th>
      <th>link</th>
      <th>mpaa_rating</th>
      <th>multimedia</th>
      <th>opening_date</th>
      <th>publication_date</th>
      <th>summary_short</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A.O. SCOTT</td>
      <td>1</td>
      <td>2018-10-17 02:44:23</td>
      <td>Can You Ever Forgive Me</td>
      <td>Review: Melissa McCarthy Is Criminally Good in...</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td>R</td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
      <td>2018-10-19</td>
      <td>2018-10-16</td>
      <td>Marielle Heller directs a true story of litera...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>BEN KENIGSBERG</td>
      <td>1</td>
      <td>2018-10-16 11:04:03</td>
      <td>Charm City</td>
      <td>Review: ‘Charm City’ Vividly Captures the Stre...</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td></td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
      <td>2018-04-22</td>
      <td>2018-10-16</td>
      <td>Marilyn Ness’s documentary is dedicated to the...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>GLENN KENNY</td>
      <td>1</td>
      <td>2018-10-16 11:04:04</td>
      <td>Horn from the Heart: The Paul Butterfield Story</td>
      <td>Review: Paul Butterfield’s Story Is Told in ‘H...</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td></td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
      <td>2018-10-19</td>
      <td>2018-10-16</td>
      <td>A documentary explores the life of the blues m...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>A. O. SCOTT</td>
      <td>0</td>
      <td>2018-10-16 16:08:03</td>
      <td>The Price of Everything</td>
      <td>Review: ‘The Price of Everything’ Asks $56 Bil...</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td></td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
      <td>2018-10-19</td>
      <td>2018-10-16</td>
      <td>This documentary examines the global art marke...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>BEN KENIGSBERG</td>
      <td>0</td>
      <td>2018-10-16 11:04:03</td>
      <td>Impulso</td>
      <td>Review: ‘Impulso’ Goes Backstage With a Flamen...</td>
      <td>{'type': 'article', 'url': 'http://www.nytimes...</td>
      <td></td>
      <td>{'type': 'mediumThreeByTwo210', 'src': 'https:...</td>
      <td>None</td>
      <td>2018-10-16</td>
      <td>This documentary follows Rocío Molina, a cutti...</td>
    </tr>
  </tbody>
</table>
</div>



## How many unique critics are there?


```python
#Your code here
df.byline.nunique()
```




    8



## Create a new column for the review's url. Title the column 'review_url'


```python
#Your code here
df['url'] = df.link.map(lambda x: x['type'])
```

## How many results are in the file?


```python
#Your code here
data['num_results']

#alternative solution:
#len(df)
```




    20



## Summary
Well done! Here you continued to gather practice extracting data from JSON files and transforming them into our standard tool of Pandas DataFrames.
