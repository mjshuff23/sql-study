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