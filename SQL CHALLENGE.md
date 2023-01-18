## PREGUNTA 1

```SQL
-- PREGUNTA 1
-- Genere un SELECT a la tabla [Person]. [Person].
--------------------------------
SELECT
	*
FROM
	Person.Person
```
## PREGUNTA 2
```SQL
-- PREGUNTA 2
-- Genere un SELECT a la tabla [Person]. [Person], 
-- únicamente de los campos BusinessEntityID, PersonType, FirstName y LastName.

---------------------
SELECT
a.BusinessEntityID
,a.PersonType
,a.FirstNameX`
,a.LastName

FROM
	Person.Person AS a -- Assingned alias

```
## PREGUNTA 3

```SQL
-- PREGUNTA 3
-- Genere un query con los mismos campos del punto número 2 donde PersonType sea igual a EM.
SELECT
a.BusinessEntityID
,a.PersonType
,a.FirstName
,a.LastName

FROM
	Person.Person AS a -- Assingned alias

WHERE 
	a.PersonType='EM'

```
## PREGUNTA 4
```SQL
-- PREGUNTA 4
-- Genere una consulta sobre la tabla [HumanResources]. [Employee] que 
-- muestre BusinessEntityID, NationalIDNumber y JobTitle, ordene los registros de mayor a menor por el campo BusinessEntityID..
SELECT
	a.BusinessEntityID
	,a.NationalIDNumber
	,a.JobTitle

FROM
	HumanResources.Employee AS a -- Assingned alias
ORDER BY 
	a.BusinessEntityID DESC

```
### PREGUNTA 5

```SQL
-- PROBLEMA 5
-- Genere una consulta sobre la tabla [HumanResources].[Employee]
-- Muestre las JobTitle únicos, el campo JobTitle debe registrar en la consulta como Unicos.

SELECT DISTINCT
 a.JobTitle AS Unicos 

FROM 
	HumanResources.Employee AS a

```

### PREGUNTA 6
```SQL
– PREGUNTA 6
-- Genere una consulta para todos los campos de la tabla [HumanResources]. [Employee] 
-- Donde el BusinessEntityID sea mayor a 10.

SELECT
	a.BusinessEntityID
FROM
	HumanResources.Employee AS a
WHERE
	a.BusinessEntityID>10	

```

### PREGUNTA 7
```SQL
-- Problema 7
-- Genere una consulta de todos los campos para la tabla [HumanResources]. [Employee] donde el 
-- JobTitle sea Sales Representative y el Gender F.

SELECT
	*
FROM
	HumanResources.Employee AS a
WHERE
	a.JobTitle='Sales Representative' AND a.Gender='F'

```

### PREGUNTA 8
```SQL
-- PREGUNTA 8
-- Genere una consulta que permita obtener la cantidad por JobTitle. 
-- La consulta debe mostrar el campo JobTitle seguido de la cantidad que hay por dicho JobTitle, ordene de mayor a menor.	
SELECT
	a.JobTitle-- Columna de la tabla
	,COUNT(a.JobTitle) AS Cantidad-- Uso de COUNT

FROM
	HumanResources.Employee AS a
GROUP BY
	a.JobTitle
ORDER BY
	Cantidad DESC -- utilizo el alias de la nueva columna

```

### PREGUNTA 9
```SQL
-- PREGUNTA 9
--Realice una consulta de la tabla [HumanResources]. [Employee] 
-- la cual indique el promedio del campo VacationHours 
-- donde el JobTitle sea Production Technician - WC50, el campo resultante del promedio debe llamarse Promedio.
SELECT
	a.JobTitle-- Columna de la tabla
	,AVG(a.VacationHours) AS Promedio-- Uso de Promedio
FROM
	HumanResources.Employee AS a

WHERE
	a.JobTitle='Production Technician - WC50'
GROUP BY
	a.JobTitle
-- ** Importante al utilizar WHERE en funciones de adición recordar agregar GROUP BY
```

### PREGUNTA 10
```SQL
-- PREGUNTA 10
-- Realice una consulta de la tabla [Sales]. [SalesPerson] 
-- la cual indique la suma total del campo SalesYTD, el nuevo campo resultante debe llamarse SumaTotal.
SELECT
	SUM(a.SalesYTD) AS SumaTotal	
FROM
	Sales.SalesPerson AS a	
```

### PREGUNTA 11
```SQL

-- PREGUNTA 11
-- Realice una consulta de la tabla [Sales]. [SalesPerson] 
-- la cual indique la suma total del campo SalesYTD donde el campo TerritoryID no sea NULL, 
-- el nuevo campo resultante debe llamarse SumaTotal.
SELECT
	SUM(a.SalesYTD) AS SumaTotal	
FROM
	Sales.SalesPerson AS a
WHERE 
	a.TerritoryID IS NOT NUll

```

### PREGUNTA 12
```SQL
-- PREGUNTA 12
-- Genere una consulta a la tabla [Sales]. [SalesPerson] 
-- que indique el valor máximo y el valor mínimo del campo Bonus, 
-- los nuevos campos deben llamarse maximo y minimo respectivamente.
SELECT
	MAX(a.Bonus) AS maximo
	,MIN(a.Bonus) AS minimo
FROM
	Sales.SalesPerson AS a

```
