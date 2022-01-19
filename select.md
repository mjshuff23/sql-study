# SELECT

**SELECT** is used to grab data from one or more of our tables in our database.  There are many **clauses** that we can use with SELECT to be specific about what we're trying to get

1. **CLAUSES**
   1. **WHERE** - The **WHERE** clause is used to grab certain rows and also to do mathematical comparisons:
       1. `SELECT population FROM world WHERE name = 'Germany';`
       2. `SELECT name FROM world WHERE population > 1000000;`
   2. **IN** -  The **IN** clause allows us to check if an item is in a list:
       1. `SELECT name, population FROM world WHERE name IN ('Brazil', 'Russia', 'India', 'China');`
       2. `SELECT name, population, area FROM world WHERE name IN ('Japan', 'United States');`