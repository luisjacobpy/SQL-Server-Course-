# OPERADORES LÓGICOS
Nos permiten validar un resultado por medio del cumplimiento de una función.
Los operadores tienen una prioridad de ejecución.


## AND
Será verdadero  cuando todas las condiciones se cumplan.

```sql
-- AND
-- Se requieren validar los productos que cumplan las siguientes condiciones
-- Color = Black
-- Size = 58
-- standarcost menor a 350

SELECT
	*
FROM
	Production.Product AS a
WHERE
	a.Color='Black'
	AND a.Size='58' -- Se coloca ya que el valor es un VARCHAR.
	AND a.StandardCost<350

-- Notas es importante revisar que los valores de numero no sean VARCHART o tratarlos como tal.

```

## OR
Requeire que al menos una condición se cumpla.

```SQL
-- OR
-- Se requiere validar todos los productos de color
-- color=Grey
-- OR Color=Red 
-- AND que el campo makeflag = 1

------------
SELECT
	*
FROM
	Production.Product AS a
WHERE
	(a.Color='Grey'
	OR a.Color='Red')
	AND a.MakeFlag=1

--Debemos tener en cuenta la prioridad de operadores.
-- El AND se ejecuta de primera en comparaci'on con el OR
-- Las CONDICIONES deben de ir en parentesis

```

## BETWEEN
```SQL
--<>
--BETWEEN
-- Se requiere validar los productos que cuenten con el campo
-- reorderpoint entre 300 y 500
-- adiconal el campo: sellstardate entre la fecha de hoy y un año atras.
-- Si el rango de fechas no arroja informacion cambiarlo por: 2008-04-30 y 2012-12-31

SELECT
	*
FROM
	Production.Product AS a
WHERE
	a.ReorderPoint BETWEEN 300 AND 500
	--AND CAST(a.SellStartDate AS DATE) BETWEEN CAST(GETDATE() AS DATE) AND DATEADD(YEAR, -1,CAST(GETDATE() AS DATE)) -- Debemos usar CAST para trabajar con los rangos de fecha
	AND CAST(a.SellStartDate AS DATE) BETWEEN '2008-04-30' AND '2012-12-31'
  
  -- Se manejan dos lineas de AND ya que uno aes probable que no genere resultados debido al GETDATE es a la fecha actual
  
```

## LIKE

Es el que me permite validar que una cadena de caracteres coincide con una cadena que se le está especificando.
Tiene diferentes agregaciones.

```SQL
--<>
-- LIKE
SELECT 
*
FROM
 Person.Person AS a
WHERE	
 a.FirstName LIKE 'Terri'

-- Cuando trabajamos el like de manera simple, la cadena debe de ser exacta para que tengamos resultados.

```


### %% Que contengan / LIKE
```SQL
--<>
-- LIKE
SELECT *
FROM Production.Product AS a
WHERE a.Name LIKE '%Hex Nut%' -- Que contengan

-- '% %'
-- Permite indicarle al Query que contenga la información.

```
### Que inicie con
```SQL
--<>
-- LIKE
SELECT *
FROM Production.Product AS a
WHERE a.Name LIKE 'Hex Nut%' -- Que inicie, con esa palabra

-- '% %'
-- Permite indicarle al Query que contenga la información.
```
### Que finalice con
```SQL
--<>
-- LIKE
SELECT *
FROM Production.Product AS a
WHERE a.Name LIKE '%Hex Nut' -- Que finalicen con
```

```SQL
-- Búsqueda de letras 
SELECT *
FROM Production.Product AS a
WHERE
	a.Name LIKE '%_ace' --Finalice con una letra 'ace'. Deja el primer valor en blanco

```

```SQL
-- Uso de []
SELECT
	*
FROM(
	SELECT 
	'Race' AS Name
	UNION ALL
	SELECT 
	'Gace' AS Name
	UNION ALL
	SELECT 
	'Gase' AS Name) AS a
WHERE
	a.Name LIKE '[R_G]a[s_c]e' --Quiere decir que la primera letra puede ser R o G, después dice que después de la 'a', la  letra puede ser s o c.

```

## NOT
```SQL
-- Uso NOT []
SELECT
	*
FROM(
	SELECT 
	'Race' AS Name
	UNION ALL
	SELECT 
	'Gace' AS Name
	UNION ALL
	SELECT 
	'Gase' AS Name) AS a
WHERE
	a.Name NOT LIKE '[R_G]a[s_c]e' --Quiere decir que la primera letra puede ser R o G, después dice que después de la 'a', la letra puede ser s o c.

--------------------------
--NOT
-- Negar el valor o la condición que estoy indicando

```




