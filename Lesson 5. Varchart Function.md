## CONCAT
Si el concat encuentra valores nulos los va a dejar con valor de 1

```SQL
-- Requiero agrupar cadenas de caracteres

SELECT
	a.Title
	,a.FirstName
	,a.MiddleName
	,a.LastName
	,CONCAT(a.Title,' ',a.FirstName,' ',a.MiddleName,' ',a.LastName) AS FullName
FROM
	Person.Person AS a

```
## CONCAT_WS
A diferrncia de **CONCAT**, la funcion CONCAT_WS Permite agregar un caracter determinado (puede ser un espacio) entre la concatencaión de caracteres.

```SQL
-- Requiero agrupar cadenas de caracteres
-- CONCAT_WS; Nos sirve para colocar los espacios entre textos, sin tener que integrarlos de manera manual.
SELECT
	a.Title
	,a.FirstName
	,a.MiddleName
	,a.LastName
	,CONCAT(a.Title,' ',a.FirstName,' ',a.MiddleName,' ',a.LastName) AS FullName
	,CONCAT_WS(' ',a.Title,a.FirstName,a.MiddleName,a.LastName) AS FullName2 -- Toma el primer valor como el separador
FROM
	
## LEN

```SQL

-- LEN
-- Nos permite conocer el numero de valores que componen una cadena de carateres
-- No tiene en cueenta los valores en blanco finales

SELECT
	CONCAT(a.Title,' ',a.FirstName,' ',a.MiddleName,' ',a.LastName) AS FullName
	,CONCAT_WS(' ',a.Title,a.FirstName,a.MiddleName,a.LastName) AS FullName2 -- Toma el primer valor como el separador
	,LEN(CONCAT_WS(' ',a.Title,a.FirstName,a.MiddleName,a.LastName)) AS Cantidad

FROM
	Person.Person AS a
```

## LEFT()
Nos permite extraer una cadena de caracteres determinada por el valor que designemos
```SQL
-- LEFT
SELECT
	LEFT(a.EmailAddress, 2) AS NuevaColumna -- Dentro de la funcion el numero designa el numero de caracteres a devolver
FROM
	Person.EmailAddress AS a

```

## RIGTH

```SQL
-- RIGHT
-- Queremos saber cuantos dominios unicos extisten en la tabla
SELECT RIGHT(a.EmailAddress, 20) AS Nueva

FROM Person.EmailAddress AS a
```
```SQL
-- RIGHT
-- Queremos saber cuantos dominios unicos extisten en la tabla
SELECT DISTINCT 
	RIGHT(EmailAddress, 20) AS Nueva

FROM 
	Person.EmailAddress

```
## LTRIM
Nos permite quitar los espacios iniciales desde la izquierda.

```SQL
-- LTRIM  y RTRIM
-- Cundo del origen de los datos nos llega la información con espacios al inicio y/o al final
SELECT
	RTRIM(LTRIM(a.Nombre)) AS NombreSinEspacios  -- Se ejecutan juntas RTRIM y LTRIM
FROM(
	
	SELECT
		CONCAT('   ',a.Title,' ',a.FirstName,' ',a.MiddleName,' ',a.LastName,'  ') AS Nombre
	FROM
		Person.Person AS a) AS a

```
## REPLACE
Permite reemplazar todas las apariciones de la cadena de caracteres 
```SQL
-- REPLACE
-- No tiene en cuenta si son mayusculas o minusculas

SELECT
	a.EmailAddress
	,REPLACE(a.EmailAddress, '@adventure-works.com', '@nuevo_correo.com')
FROM
	Person.EmailAddress AS a
-- SELECT REPLACE('Hola Mundo mundo', 'mundo', 'Nuevo')

```
## STUFF
```SQL
-- STUFF
-- Nos permite eliminar una parte de la columna e insertar una nueva información

SELECT ('Hola mundo')
SELECT STUFF('Hola mundo',6, 5, 'Nuevo curso') 
-- Parametros [1: Desde donde va a comenzar 5]; [2: Cantidad de caracteres que va a eliminar 6];3 Nueva cadena

```




