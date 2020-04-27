# map(), reduce(), filter()
## map()
Run a callback for each element in an array and append each new value in the resulting array.
<!-- tabs:start -->
#### ** Javascript **
```javascript
// What you have
const officers = [
  { id: 20, name: 'Captain Piett' },
  { id: 24, name: 'General Veers' },
  { id: 56, name: 'Admiral Ozzel' },
  { id: 88, name: 'Commander Jerjerrod' }
];
// We want an array of ids only
[20, 24, 56, 88]
```
```javascript
const officersIds = officers.map(officer => officer.id);
```
#### ** Python **
```python
# What we have
scores = [5, 7, 22, 97, 54, 62, 77, 23, 73, 61]
# We want to get an array of each score doubled
[10, 14, 44, 194, 108, 124, 154, 46, 146, 122]
```
```python
doubled_scores = list(map(lambda score: score*2 , scores))
```
<!-- tabs:end -->
## reduce()
Run a callback for each element in an array but pass the result in argument of the next callback.
<!-- tabs:start -->
#### ** Javascript **
```javascript
// What you have
const pilots = [
  { id: 10, name: "Poe Dameron", years: 14 },
  { id: 2, name: "Temmin 'Snap' Wexley", years: 30 },
  { id: 41, name: "Tallissan Lintra", years: 16 },
  { id: 99, name: "Ello Asty", years: 22 }
];
// What you need (the total of ages of all of them)
82
// Or the most experienced pilot
{ id: 2, name: "Temmin 'Snap' Wexley", years: 30 }
```
```javascript
const totalYears = pilots.reduce((accumulator, pilot) => accumulator + pilot.years, 0);
```
```javascript
var mostExpPilot = pilots.reduce((oldest, pilot) => {
  return (oldest.years || 0) > pilot.years ? oldest : pilot;
}, {});
```
#### ** Python **
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
<!-- tabs:end -->
## filter()
Filter an array by conditionnal instructions.
<!-- tabs:start -->
#### ** Javascript **
```javascript
// What we have
var pilots = [
  { id: 2, name: "Wedge Antilles", faction: "Rebels" },
  { id: 8, name: "Ciena Ree", faction: "Empire" },
  { id: 40, name: "Iden Versio", faction: "Empire" },
  { id: 66, name: "Thane Kyrell", faction: "Rebels" }
];
// We want to filter rebels and empire pilots
```
```javascript
const rebels = pilots.filter(pilot => pilot.faction === "Rebels");
const empire = pilots.filter(pilot => pilot.faction === "Empire");
```
#### ** Python **
```python
# What we have
scores = [5, 7, 22, 97, 54, 62, 77, 23, 73, 61]
# We want an array of odd scores only
[5, 7, 97, 77, 23, 73, 61]
```
```python
odd_scores = list(filter(lambda score: (score%2 != 0) , scores))
```
<!-- tabs:end -->
## Combining .map(), .reduce() and .filter()
<!-- tabs:start -->
#### ** Javascript **
```javascript
// What we have
var personnel = [
  { id: 5, name: "Luke Skywalker", pilotingScore: 98, shootingScore: 56, isForceUser: true },
  { id: 82, name: "Sabine Wren", pilotingScore: 73, shootingScore: 99, isForceUser: false },
  { id: 22, name: "Zeb Orellios", pilotingScore: 20, shootingScore: 59, isForceUser: false },
  { id: 15, name: "Ezra Bridger", pilotingScore: 43, shootingScore: 67, isForceUser: true },
  { id: 11, name: "Caleb Dume", pilotingScore: 71, shootingScore: 85, isForceUser: true },
];
// We want to get the total score of force users only
```
```javascript
const totalJediScore = personnel
  .filter(person => person.isForceUser)
  .map(jedi => jedi.pilotingScore + jedi.shootingScore)
  .reduce((acc, score) => acc + score, 0);
```
#### ** Python **
TODO
<!-- tabs:end -->
## Sources
<!-- tabs:start -->
#### ** Javascript **
>Source: https://medium.com/poka-techblog/simplify-your-javascript-use-map-reduce-and-filter-bd02c593cc2d
#### ** Python **
>source: https://www.geeksforgeeks.org/python-lambda-anonymous-functions-filter-map-reduce/
<!-- tabs:end -->