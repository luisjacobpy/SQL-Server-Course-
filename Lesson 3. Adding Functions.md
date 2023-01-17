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
