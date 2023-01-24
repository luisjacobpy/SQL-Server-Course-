## GETDATE
Es una función no determinista, cada vez que yo la ejecuto va a traer un valor distinto.

```SQL
SELECT GETDATE()
```

## DATEADD
Es la encargada de agregar un número el cual nosotros le indicamos a una parte de la fecha. Estas funciones por lo general trabajan con semanas, meses años

```SQL
-- Vamos a QUITAR un mes a la fecha que arroja el sistema
-- Recordamos que el GETDATE sera el valor del campo

SELECT DATEADD(MONTH, -1,GETDATE())
SELECT DATEADD(YEAR, 1, GETDATE())  -- Agrega 1 año
SELECT DATEADD(MINUTE, 10, GETDATE() -- Agrega 10 minutos


```
### DATEADD utilizando WHERE
```SQL
-- Necesitamos traer información desde la tabla `Production.product`
-- Desde la fecha x hasta un año despues.

SELECT *
FROM Production.Product AS a
WHERE
	CAST(a.SellStartDate AS DATE) BETWEEN '2012-05-30' AND DATEADD(YEAR, 1, '2012-05-30')

-- Colocamos el CAST para traer solo la fecha

```
## DATENAME
-- Es la encargada de devolver una parte específica de la fecha 
-- EL valor devuelto será una cadena de carácter y por ende un VARCHART
```SQL

-- Funcion DATENAME
-- Es la encargada de devolver una parte específica de la fecha 
-- EL valor devuelto será una cadena de carácter y por ende un VARCHART
-- La fecha que arroja esta en ingles, para cambiar a español yo selecciono SET LANGUAGE SPANISH
SELECT DATENAME(YEAR, GETDATE())
SELECT DATENAME(MONTH, GETDATE())
SELECT DATENAME(DAY, GETDATE())
SELECT DATENAME(HOUR, GETDATE())
SELECT DATENAME(WEEKDAY, GETDATE())

```
## DAYPART
```SQL
-- Es el encargado de retornar una parte especifica de la fecha
-- El DATEPART es lo mismo que el DATENAME pero me retorna solo valores enteros.
SELECT DATEPART(YEAR, GETDATE())
SELECT DATEPART(MONTH, GETDATE())
SELECT DATEPART(DAY, GETDATE())
SELECT DATEPART(HOUR, GETDATE())
SELECT DATEPART(WEEKDAY, GETDATE())

```
## DAY / MONTH / YEAR

```SQL
SELECT DAY(GETDATE())
SELECT MONTH(GETDATE())
SELECT YEAR(GETDATE())

```
