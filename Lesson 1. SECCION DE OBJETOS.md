<h1> SECCION DE OBJETOS <h1/>
	
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
### GROUP BY
```SQL

SELECT 
 A.Color
 ,SUM(a.ListPrice) AS Suma --agregamos un alias para la nueva seccion
FROM
	Production.Product AS a
GROUP BY
	a.Color

```
### Funciones de agregación / Adding functions
```SQL
-- Funciones de agregación 
COUNT 
SUM
MIN
MAX 
AVG
```

#### Adding more columns
```
SELECT 
 A.Color
 ,a.Name -- Add to SELECT and remember add to GROUP BY Selection
 ,SUM(a.ListPrice) AS Suma --agregamos un alias para la nueva seccion
FROM
	Production.Product AS a
GROUP BY
	a.Color
	,a.Name 
```
### HAVING
***HAVING**** is a condition or conditional
 ```SQL
--<>
SELECT
	a.Color
	,SUM(a.ListPrice) as Total
FROM 
	Production.Product AS a
GROUP BY
	a.Color
	HAVING SUM(a.ListPrice)>10000 -- CONDITIONAL

-- Cuando estamos generando una agrupación no podemos colocar el valor en el WHERE.
-- EL valor debe ir incluido en el HAVING

```
### ORDER BY
 ```SQL
--<>
SELECT
	a.Color
	,SUM(a.ListPrice) as Total
FROM 
	Production.Product AS a
GROUP BY
	a.Color
	HAVING SUM(a.ListPrice)>10000
ORDER BY
	SUM(a.ListPrice) DESC -- Descnedente, en el caso de que no coloqumos nada lo toma por default ascedente.
-- Cuando estoy usando valores de agragación (SUM, MAX, MIN) simpre debere llevar todo el valor por medio de la agregacion.
### TOP
 
 #### Example N1
 ```SQL
SELECT TOP 10
	*
FROM
	Production.Product AS a

```
#### Example in percent
 ```SQL
SELECT TOP 2 PERCENT
	*
FROM
	Production.Product AS a

```

 ### DISTINCT

 #### Example / Correct
 ```SQL

SELECT DISTINCT
	a.JobTitle
FROM
	HumanResources.Employee AS a
ORDER BY
	a.JobTitle	
-- Nos puede arrojar un resultado similar si utilizamos en GROUP BY
-- DISTINCT fue creado para ester uso en especifico por lo que se recomienda utilizarlo

```
 
 Example with GROUP BY / Incorrect, cause the perfermance of system

```SQL
SELECT 
	a.JobTitle
FROM
	HumanResources.Employee AS a

GROUP BY 
	a.JobTitle
ORDER BY

```

```SQL

SELECT DISTINCT
	a.JobTitle
	,a.Gender
FROM
	HumanResources.Employee AS a

ORDER BY
	a.JobTitle	


```


 
 
