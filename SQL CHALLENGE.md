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
