# CREATE TABLE
Creación de tablas fisicas

**CREATE** Me permite crear:
* Table
* Vistas
* Procedimientos almacenados 
* Triggers

**TIP:** Si yo creo una tabla, debo apuntar a la base de datos donde quiero crearlo. 

## CREATE TABLE
```SQL
-- Creando tablas con CREATE TABLE

CREATE TABLE Table_Telefono (Id_Tel INT PRIMARY KEY, Numero INT NULL) -- Null permite que reciba valores nulos
CREATE TABLE Table_Personal (Id INT PRIMARY KEY, Nombre VARCHAR(100), Cedula INT NOT NULL, Id_Tel INT FOREIGN KEY REFERENCES Table_Telefono (Id_Tel))

-- DEBO REFERENCIAR LA TABLA QUE CONTIENE EL VALOR FK 'REFERENCES'
-- Debemos ejecutar primero la creacion de la tabla que guarda la referencia en este caso Table_Telefono

```

**TIP:** Para comprobar la creacion, nos colocamos sobre el nombre de la tabla y presionamos ALT + F1

## TEMPORAL TABLE
Creación de tablas temporales locales y tablas temporales locales
El uso de estas tablas ayudan al performance de la tabla de datos.
Son tablas que por lo general se eliminan al cerrar una instancia.
Yo consulto si hacer mayor uso del motor de la base de datos.
 
La tabla temporal al momento de ser creada queda  almacenada en la  ‘tempdb’ (es una db del sistema la encontramos en ‘System Databases’) al igual que la global. 

Las tablas temporales no se pueden indexar.

### LOCAL VS GLOBAL
```SQL
-- TABLA TEMPORAL LOCAL
-- Uso del simbolo # = Local
-- Uso de ## = Global
-- Creando tablas con CREATE TABLE

--Temporal local
CREATE TABLE #Table_Telefono (Id_Tel INT PRIMARY KEY, Numero INT NULL) -- Null permite que reciba valores nulos
--Temporal global
CREATE TABLE ##Table_Personal (Id INT PRIMARY KEY, Nombre VARCHAR(100), Cedula INT NOT NULL, Id_Tel INT FOREIGN KEY REFERENCES Table_Telefono (Id_Tel))

--Vamos a traer la información de la tabla local
SELECT	
	*
FROM
	#Table_Telefono

-- En el momento de la creación pasan a estar almacenadas en la 'tempdb'
-- La 'tempdb' suele colapsar al no cerrar las instancias en las organizaciones. No hay que dejar instancias abiertas

```
Solo la tabla Global (Blobal Table), se puede consultar desde otra instancia.
```SQL
-- Consultando TABLE GLOBAL
SELECT	
	*
FROM
	##Table_Personal

```

## Accedder a los objetos de la BDD

```SQL

SELECT	
	*
FROM
	tempdb..sysobjects AS a -- Accediendo a una base de datos del sistema para observar sus objetos
WHERE
	a.name LIKE '%Table_Telefono%' -- cuando contengan
	OR a.name LIKE '%Table_Personal%'
```

