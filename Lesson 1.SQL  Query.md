## ORDER PROCESS SENTENCES

1. FROM
2. ON
3. JOIN
4. WHERE
5. GROUP BY
6. WHIT
7. HAVING 
8. SELECT
9. DISTINCT
10. ORDER BY
11. TOP

### SELECT
```SQL

SELECT
  * -- ALL
  FROM
    [Person].[Person] -- Table

```

Key concept: Alias
Alias is asigned by AS

#### Alias example
```SQL
SELECT
  a.BusinessEntitiID
  ,a.PersonTYPE 
  ,a.NameStyle
 FROM 
  [Person].[Person] AS a -- This is the Alias

```
### WHERE
WHERE is a condition

```SQL
SELECT
  *
 FROM
  [Person].[Person] AS a
 WHERE 
  a.BusnessEntityID=4
  
```
int numbers your are not write ('')

```SQL
SELECT
  *
 FROM
  [Person].[Person] AS a
 WHERE 
  a.LastName='Sanchéz'
  
```
