## CAST()
Para conocer el tipo de dato, seleccionamos el nombre de la tabla y presionamos ALT + F1


```SQL
-- uso de CAST()
-- Requiero traer inofromación de una columna date and time, \
-- solo necesito 'date'
SELECT
	a.ModifiedDate
	,CAST(a.ModifiedDate AS DATE) AS NuevaFecha -- Coloco el origen de los datos y despues coloco al tipo de dato que se va a modificar.
	,a.MakeFlag
	,CAST(a.MakeFlag AS FLOAT) AS NuevoValor
	,a.StandardCost
	,CAST(a.StandardCost AS INT) AS NuevoStandarCost
FROM
	Production.Product AS a

	-- Para ver el tipo de dato de la columna: seleccionamos y ALT + F1 

```
**Comentarios rapidos**
Con SHIFT + ALT, hacia abajo se muestra una linea y despues puedo comentar

```SQL
SELECT
	*

FROM
	Production.Product AS a

WHERE
	CAST(a.ModifiedDate AS DATE)='2014-02-08' -- No se modifica la informacion, solo se modifica al momento de la busqueda.

	-- Para ver el tipo de dato de la columna: seleccionamos y ALT + F1 

```

## CONVERT()
Permite convertir una expresion de un tipo de dato a otro. Es mas comun trabajar con CAST() por su forma simple de hacerlo.
```SQL
-- Ejemplo con CAST()
SELECT
*
FROM
	Production.Product AS a
WHERE
	CAST(a.ModifiedDate AS DATE)='2014-02-08' -- No se modifica la informacion, solo se modifica al momento de la busqueda.
---------------
-- Ejemplo con CONVERT()
SELECT
	a.ModifiedDate
	,CONVERT(DATE, a.ModifiedDate) AS Fecha
	,a.MakeFlag
	,CONVERT(VARCHAR, a.MakeFlag) AS NuevoValor
	,a
FROM
	Production.Product AS a
```

```SQL
-- Ejemplo con CONVERT()
SELECT
	a.ModifiedDate
	,CONVERT(DATE, a.ModifiedDate) AS Fecha
	,a.MakeFlag
	,CONVERT(VARCHAR, a.MakeFlag) AS NuevoValor
	,a.StandardCost
	,CONVERT(BIGINT, a.StandardCost) AS BigInt -- BIGINT significa gran entero
FROM
	Production.Product AS a

```
## PARSE()
Modifica una fecha que está en cadena de texto a un formato de DATE
```SQL
SELECT PARSE('Friday, 14 December 2018' AS DATE)
```

