## DROP TABLE

Permite no solo borrar la tabla sino toda subestructura.
Esta sentencia es la única que elimina la estructura de esa tabla
También se pueden eliminar tablas temporales 

```SQL
-- Vamos a eliminar con DROP TABLE las tablas que Creamos en las clases pasadas.

SELECT
	*
FROM
	[dbo].[Table_Personal]

SELECT
	*
FROM	
	[dbo].[Table_Telefono]

DROP TABLE [dbo].[Table_Personal]
DROP TABLE [dbo].[Table_Telefono]

```

```SQL
-- Eliminar tablas temporales locales y globales


DROP TABLE #Tabla1 -- Tabla temporal local
DROP TABLE ##TablaGlobal -- Tabla temporal global

```

## TRUNCATE TABLE
A diferencia de la DROP TABLE, la TRUNCATE TABLE mantiene la estructura de la tabla. PK, FK, índices. El archivo existe pero no existe la información contenida. 
Cuando uso el truncate table estoy eliminando de forma automática toda su información.

El TRUNCATE elimina toda la información es más rápido y consume menos recursos que un DELETE, por ende es recomendable usar TRUNCATE cuando vas a eliminar la información que contenga una tabla.
**TIP/Expereincia:** Al correr el Query con TRUNCATE TABLE (adjunto debajo) arrojo un mensaje de error, debido a que no se puede eliminar la información porque hace referencia a una FK.
```SQL
-- Error

TRUNCATE TABLE [Table_Telefono]
```

```SQL
-- Sin error
TRUNCATE TABLE [Table_Personal]
```
```SQL
-- Crreamos las tablas y agregamos información
CREATE TABLE Table_Telefono (Id_Tel	INT PRIMARY KEY, Nombre VARCHAR(100))
CREATE TABLE Table_Personal (Id INT PRIMARY KEY, Nombre VARCHAR(100), Cedula INT NOT NULL, Id_Tel INT FOREIGN KEY REFERENCES Table_Telefono (Id_Tel))

INSERT INTO [dbo].[Table_Telefono] VALUES (1, 'Celular')
INSERT INTO [dbo].[Table_Telefono] VALUES (2, 'Casa')
INSERT INTO [dbo].[Table_Telefono] VALUES (3, 'Oficina')

INSERT INTO [dbo].[Table_Personal] VALUES (1, 'Alex', 123 , 1)
INSERT INTO [dbo].[Table_Personal] VALUES (2, 'Diana', 124 , 2)
INSERT INTO [dbo].[Table_Personal] VALUES (3, 'Cristian', 125 , 3)

```

```SQL
SELECT
	*
FROM
	[dbo].[Table_Personal]

SELECT
	*
FROM
	[Table_Telefono]

-- TRUNCATE TABLE
	TRUNCATE TABLE [Table_Personal]

```


## DELETE
Permite eliminar una o más filas de una tabla.
Está diseñado a eliminar por medio de un WHERE
Si ejecuto la sentencia sin colocar el WHERE trabaja como un TRUNCATE, sin embargo es mejor usar el TRUNCATE en este último caso ya que mejora el PERFORMANCE. 
Dentro del DELETE no puedo colocar ALIAS

```SQL
---------------
-- Ejercicio
-- Eliminar de la tabla el registro de 'Diana' cuyo 'Id' es '2'

DELETE
FROM
	[Table_Personal]
WHERE 
	Id=2
```
