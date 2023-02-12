# Revisar Datos Tabla

1. Contenido de Filas

```sql
SELECT COUNT(*) AS Num_Filas
FROM world
```

Resultado: 195 filas (rowns)

2. Contenido de Columnas

```sql
SELECT COUNT(*) AS Num_Colum
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'world'
```
Resultado: 8 Columnas (columns)

>Nota: Esta consulta utiliza la vista **INFORMATION_SCHEMA.COLUMNS** para obtener información sobre las columnas en las tablas de una base de datos



3. Número de Paises por Continente

```sql
SELECT continent, COUNT(name) AS Num_paises
FROM world
GROUP BY continent
ORDER BY Num_paises DESC
```

Resultado:

Continent | Num_paises
----------|-----------
Africa    | 53
Asia      | 47
Europe    | 44
Oceania   | 14
South America | 13
North America | 11
Caribbean | 11
Eurasia   | 2


4. Pasar información por continente

Debido a que en SQLZOO solo muestran 50 filas, se deben pasar por grupos al formato text edit de la MAC

4.1 Para ello agrupo los más pequeños (que tienen entre 2 y 13 filas), así:

```sql
SELECT *
FROM world
WHERE Continent IN ('Eurasia', 'Caribbean', 'North America', 'South America')
````
Y luego voy generando y copiando la información de los continentess restantes, así:

```sql
SELECT *
FROM world
WHERE Continent = 'Asia'
```
...

Luego, para copiar la información de 






