# Python map(), reduce(), filter()
## map()
```python
# What we have
scores = [5, 7, 22, 97, 54, 62, 77, 23, 73, 61]
# We want to get an array of each score doubled
[10, 14, 44, 194, 108, 124, 154, 46, 146, 122]
```
```python
doubled_scores = list(map(lambda score: score*2 , scores))
```
## reduce()
```python
# What we have
scores = [5, 8, 10, 20, 50, 100]
# We want to get the sum of all scores
193
```
```python
from functools import reduce

sum_scores = reduce((lambda accumulator, score: accumulator + score), scores)
```
## filter()
```python
# What we have
scores = [5, 7, 22, 97, 54, 62, 77, 23, 73, 61] 
# We want an array of odd scores only
```
```python
odd_scores = list(filter(lambda score: (score%2 != 0) , scores)) 
```

>source: https://www.geeksforgeeks.org/python-lambda-anonymous-functions-filter-map-reduce/