## INNER JOIN

Los Joins son palabras reservadas que me permiten recuperar datos de dos o más tablas basadas en relaciones. 
Me permite conectar múltiples tablas para traer información.

Debo especificar la columna de cada tabla que voy a unir por medio de las claves 
PK o FK


```SQL
SELECT
	*
FROM
	[Person].[Person] AS a
	INNER JOIN [Person].[PersonPhone] AS b
		ON a.BusinessEntityID=b.BusinessEntityID   -- Clave de tabla

	-- El INNER JOIN me permite seleccionar los registros que tienen valores que conincidan en ambas tablas.
	-- El INNER JOIN me va a traer lo que coincida entre la tabla A y la tabal B

``

```SQL
SELECT
	a.FirstName
	,b.PhoneNumber
FROM
	[Person].[Person] AS a
	INNER JOIN [Person].[PersonPhone] AS b
		ON a.BusinessEntityID=b.BusinessEntityID   -- Clave de tabla

```

```SQL

--<Realizamos la conexión con tres tablas en este QUERY>

SELECT
	a.FirstName
	,b.PhoneNumber
	,c.Name
FROM
	[Person].[Person] AS a
	INNER JOIN [Person].[PersonPhone] AS b
		ON a.BusinessEntityID=b.BusinessEntityID   -- Clave de tabla
	INNER JOIN [Person].[PhoneNumberType] AS c 
		ON b.PhoneNumberTypeID=c.PhoneNumberTypeID -- Establecemos la conexión 

	-- IMPORTANTE DARLE SEGUIMIENTO AL NUMERO DE VALORES, ASI NOS DAMOS CUENTA SI ESTAMOS PERDIENDO INFORMACION.
```

