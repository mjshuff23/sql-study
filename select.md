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
   5. **NOT LIKE** - Compare characters, spaces, etcetera using `%`
      1. Opposite of `LIKE`
   6. **AS** - Used to rename a column when querying
      1. `SELECT name, CONCAT(ROUND(100*population/(SELECT population FROM world WHERE name='Germany'), 0), '%') AS percentage FROM world WHERE continent='Europe';`
   7. **GROUP BY**
   8. **DISTINCT** - Removes duplicates
2. **FUNCTIONS**
   1. **AGGREGATE FUNCTIONS** - An aggregate function takes many values and delivers just one value. For example the function SUM would aggregate the values 2, 4 and 5 to deliver the single value 11.
   2. **LENGTH** - `LENGTH(s)` returns the number of characters in string s.
      1. `SELECT LENGTH(name), name FROM bbc;`
      2. `LENGTH('Hello')` -> `5`
      3. `SELECT name, length(name) FROM world WHERE length(name)=5 and region='Europe';`
      4. `SELECT name, capital FROM world WHERE LENGTH(name) = LENGTH(capital)`
   3. **ROUND** - `ROUND(f,p)` returns `f` rounded to `p` decimal places
      1. `SELECT name, ROUND(population/1000000,1) FROM bbc;`
      2. `SELECT name, ROUND(population/1000000, 2), ROUND(GDP/1000000000, 2) FROM world WHERE continent = 'South America';`
      3. `SELECT name, ROUND(gdp/population, -3) FROM world WHERE gdp > 1000000000000`
   4. **LEFT** - `LEFT(s, n)` allows you to extract `n` characters from the start of the string `s`
       1. `SELECT name, LEFT(name, 3) FROM bbc;`
       2. `SELECT name, capital FROM world WHERE LEFT(name, 1) = LEFT(capital, 1) AND name <> capital;`
   5. **CONCAT** - `CONCAT(s1, s2, ...)` is used to concatenate(add) 2 or more strings together
      1. `SELECT CONCAT(region,name) FROM bbc`
   6. **MAX** - Finds the highest values in a column or part of a column
   7. **ALL** - ALL is used to select all records of a SELECT STATEMENT. It compares a value to every value in a list or results from a query. The ALL must be preceded by the comparison operators and evaluates to TRUE if the query returns no rows. For example, ALL means greater than every value, means greater than the maximum value. Suppose ALL (1, 2, 3) means greater than 3.
   8. **COUNT** - Total count of rows
   9. **COALESCE** - takes any number of arguments and returns the first value that is not null.
3. **COMPARISON OPERATORS**
   1. `=` - Compare equality
   2. `<` - Less than
   3. `>` - Greater than
   4. `<=` - Less than or equal to
   5. `>=` - Greater than or equal to
   6. `<>` OR `!=` - Compare inequality
   7. `LIKE` - Compare characters, spaces, etcetera using `%`
      1. If it starts with `%` and has characters after, it means "ENDS WITH"
      2. If it ends with `%` after characters, it means "STARTS WITH"
      3. If it has a `%` before AND after a character (`%a%`) it means "ANYWHERE IN"
   8. `NOT LIKE` - Compare characters, spaces, etcetera using `%`
      1. Opposite of `LIKE` 
4. **LOGICAL OPERATORS**
   1. **AND** - used if BOTH comparisons must be true
      1. `SELECT name, area, population FROM world WHERE area > 50000 AND population < 1000000;`
   2. **OR** - used if ONE comparison must be true
      1. `SELECT name FROM world WHERE name LIKE '%a' OR name LIKE '%l';`
   3. **XOR** - used if ONE comparison must be true *BUT NOT BOTH*
      1. `SELECT name, population, area FROM world WHERE area > 3000000 XOR population > 250000000;` 
5. **OTHER**
   1. Mathematical operations can also be done in your queries:
      1. `SELECT name, area*2 FROM world WHERE population = 64000;`
      2. `SELECT name, population/area FROM world WHERE name IN ('China', 'Nigeria', 'France', 'Australia');`
   2. We can also combine conditionals:
      1. `SELECT name, area, population FROM world WHERE area > 50000 AND population < 1000000;`
   3. **SELECT WITHIN SELECT** - We can use SELECT within another SELECT to be more precise:
      1. `SELECT name FROM world WHERE population > (SELECT population FROM world WHERE name='Russia');`
   4. **NULL** - Sometimes NULL values are given in tables, maybe because the data is unknown or inappropriate
      1. We can use the phrase `IS NULL` to pick out fields. We can use `IS NOT NULL` similarly.