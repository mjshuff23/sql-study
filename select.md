# SELECT

**SELECT** is used to grab data from one or more of our tables in our database.  There are many **clauses** that we can use with SELECT to be specific about what we're trying to get

1. **CLAUSES**
   1. **WHERE** - The **WHERE** clause is used to grab certain rows and also to do mathematical comparisons:
       1. `SELECT population FROM world WHERE name = 'Germany';`
       2. `SELECT name FROM world WHERE population > 1000000;`
   2. **IN** -  The **IN** clause allows us to check if an item is in a list:
       1. `SELECT name, population FROM world WHERE name IN ('Brazil', 'Russia', 'India', 'China');`
       2. `SELECT name, population, area FROM world WHERE name IN ('Japan', 'United States');`
   3. **BETWEEN** - The **BETWEEN** clause is used to get data that is within a certain range:
       1. `SELECT name, area FROM world WHERE area BETWEEN 250000 and 300000;`
   4. **LIKE** - The **LIKE** clause is used to grab data that matches a certain pattern or set of wild-cards.  A `%` may be used to match and string, `_` will match any single character. 
      1. The example shows countries beginning with Z. The country Zambia matches because ambia matches with the `%`:
         1. `SELECT name FROM bbc WHERE name LIKE 'Z%';`
      2. Select the code which shows the countries that end in A or L:
         1. `SELECT name FROM world WHERE name LIKE '%a' OR name LIKE '%l';`
2. **FUNCTIONS**
   1. **LENGTH** - LENGTH(s) returns the number of characters in string s.
      1. `SELECT LENGTH(name), name FROM bbc;`
      2. `LENGTH('Hello')` -> `5`
      3. `SELECT name, length(name) FROM world WHERE length(name)=5 and region='Europe';`
   2. **ROUND** - `ROUND(f,p)` returns `f` rounded to `p` decimal places
      1. `SELECT name, ROUND(population/1000000,1) FROM bbc;`
      2. `SELECT name, ROUND(population/1000000, 2), ROUND(GDP/1000000000, 2) FROM world WHERE continent = 'South America';`
3. **LOGICAL OPERATORS** 
   1. **AND** - used if BOTH comparisons must be true
      1. `SELECT name, area, population FROM world WHERE area > 50000 AND population < 1000000;`
   2. **OR** - used if ONE comparison must be true
      1. `SELECT name FROM world WHERE name LIKE '%a' OR name LIKE '%l';`
   3. **XOR** - used if ONE comparison must be true *BUT NOT BOTH*
      1. `SELECT name, population, area FROM world WHERE area > 3000000 XOR population > 250000000;`
4. **OTHER**
   1. Mathematical operations can also be done in your queries:
      1. `SELECT name, area*2 FROM world WHERE population = 64000;`
      2. `SELECT name, population/area FROM world WHERE name IN ('China', 'Nigeria', 'France', 'Australia');`
   2. We can also combine conditionals:
      1. `SELECT name, area, population FROM world WHERE area > 50000 AND population < 1000000;`