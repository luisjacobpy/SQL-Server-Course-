## SUM

```SQL
--<EJEMPLO DE SUM>
SELECT
 b.Name AS NombreProducto -- Alias
 ,SUM(a.Quantity) AS Cantidad 
FROM 
	Production.ProductInventory AS a
	INNER JOIN Production.Product AS b
		ON a.ProductID=b.ProductID
GROUP BY 
	b.Name

```
```SQL
--<EJEMPLO DE SUM usando WHERE>
SELECT
 b.Name AS NombreProducto -- Alias
 ,SUM(a.Quantity) AS Cantidad 
FROM 
	Production.ProductInventory AS a
	INNER JOIN Production.Product AS b
		ON a.ProductID=b.ProductID
WHERE
	b.name='Headset Ball Bearings'
GROUP BY 
	b.Name
```
En lenguaje natural: Selecciona la columna Name de la Tabla b

## COUNT 
COUNT Retorna el número de valores encontrados

```SQL
-- Vamos a investigar el numero de valores que hay en la columna EmailPromotion
-- Se utiliza COUNT
-- Importante es agrupar el valor
SELECT
	a.EmailPromotion -- Columna de la tabla a
	,COUNT(a.EmailPromotion) AS Cantidad
FROM
	person.Person AS a
GROUP  BY
	a.EmailPromotion
```
### En qué caso no voy a utilizar el GROUP BY

```SQL
-- En este caso solo se está contando la cantidad de datos

SELECT
	COUNT(a.EmailPromotion) AS Cantidad
FROM
	person.Person AS a
```
### Conteo de valores Null

```SQL
--Para contar los valores Null dentro de una tabla
SELECT 
	a.Title
	,COUNT(*) AS Cantidad
FROM 
	person.person as a

GROUP BY
	a.Title
```
//

```SQL
-- Saber por Lastname ¿Cuántos hay?
SELECT
	a.LastName
	,COUNT(a.LastName) AS Cantidad
FROM
	person.Person AS a
GROUP BY
	a.LastName
```

```SQL
-- Saber por Lastname ¿Cuántos valores unicos hay?
– Usamos DISTINCT dentro de la funcion de agragacion
SELECT
	COUNT( DISTINCT a.LastName) AS Cantidad
FROM
	person.Person AS a

```


## AVG

```SQL

-- AVG Retorna el promedio de valores
-- Quiero saber el promedio de precio por color

SELECT
	a.Color -- Columna
	,AVG(a.ListPrice) AS Promedio
FROM
	Production.Product AS a
GROUP BY
	a.Color
```


## Funcion / Function MAX() y MIN()
```SQL

-- Funcion Max
-- Necesito saber la fecha de la contraseña mínima y la fecha de la contraseña maxima
SELECT
	MIN(a.ModifiedDate) AS Minimo
	,MAX(a.ModifiedDate) AS Maximo
FROM
	person.Password AS a
```
***En este caso no requerimos colocar GROUP BY debido a que las columnas que estamos operando están inmersas en la función de agregación.***


