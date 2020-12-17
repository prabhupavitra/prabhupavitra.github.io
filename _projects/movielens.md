

```python
# Basic Libraries
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn import ensemble, linear_model, model_selection, preprocessing, svm
from sklearn.metrics import mean_squared_error, r2_score
from yellowbrick.regressor import PredictionError, ResidualsPlot

import requests, zipfile
from urllib.request import urlopen
from io import BytesIO

url = "http://files.grouplens.org/datasets/movielens/ml-10m.zip"
remote_zf = urlopen(url)
local_zf = BytesIO(remote_zf.read())
zf = zipfile.ZipFile(local_zf)

# Extract files 
ratings = pd.read_table(zf.open('ml-10M100K/ratings.dat'), 
                        sep="::", 
                        usecols = [0,1,2,3],
                        names=["userId", "movieId", "rating", "timestamp"])

movies = pd.read_table(zf.open('ml-10M100K/movies.dat'), 
                       sep="::", 
                       usecols=[0,1,2],
                       names=["movieId", "title", "genres"])

movielens = ratings.merge(movies,how="left",on="movieId")

# Train-test split
from sklearn.model_selection import train_test_split
X = movielens.drop('rating', axis=1)
y = movielens.rating
validation_size = 0.1
seed = 1
X_train, X_validation, Y_train, Y_validation =\
train_test_split(X, y, test_size=validation_size, random_state=seed)

## Data visualizations

(
    
)

```

The first 6 rows of dataset
```python
X_train.head()
```