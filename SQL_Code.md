# `SELECT BASICS`


## Ejercicio 1

Comando **WHERE**, Mostrar una columna y una fila: Show the population of Germany

```sql
SELECT population 
FROM world
WHERE name = 'Germany'
```
Ejemplo

| population |
| --- | 
| 80716000|



## Ejercicio 2

Comando **IN** (comprobar si esta una palabra): Show the name and the population for 'Sweden', 'Norway' and 'Denmark'.

```sql
SELECT name, population
FROM world
WHERE name IN ('Sweden', 'Norway', 'Denmark')
```



| Name | Population |
|---|---|
|Denmark| 5634437 |
|Norway |	5124383 |
|Sweden |	9675885 |



## Ejercicio 3

Comando **BETWEEN**, **AND** (para rangos): Show the country and the area for countries with an area between 200,000 and 250,000.

```sql
SELECT name, area
FROM World
WHERE area BETWEEN 200000 AND 250000
````

| Name | area |
|--|--|
|Belarus|	207600|
|hana	|238533|
|Guinea |	245857 |
|Guyana |	214969|
|Laos |	236800 |
|Romania|	238391|
|Uganda	|241550|
|United Kingdom	|242900|




# `SELECT FROM WORLD`


## Ejercicio 1

Comando SELECT Mostrar columnas de la tabla

```sql
SELECT name, continent, population 
FROM world
````



## Ejercicio 2


Comando WHERE **para comparaciones númericas**. Show the name for the countries that have a population of at least 200 millions

```sql
SELECT name 
FROM world
WHERE population >= 200000000
```

|name|
|--|
|Brazil|
|China|
|India|
|Indonesia|
|United States|

> Nota: Para comparaciones numéricas, se pueden utilizar los operadores de comparación estándar, como > (mayor que), < (menor que), >= (mayor o igual que), <= (menor o igual que), = (igual a), y <> (diferente a)


## Ejercicio 3


Hacer **Calculos en Columnas con otra columna**. Calculate per capita GDP[^1] for those countries with a population of at least 200 million.

[^1]: My Per Capita GDP is the GDP divided by the population GDP/population


```sql
SELECT name, gdp/population AS GDP
FROM world
WHERE population >= 200000000
````


## Ejercicio 4


Hacer **Calculos en Columnas con números externos**. Dividir con números direcamente en la columna. Divide the population by 1000000 to get population in millions.

```sql
SELECT name, population/1000000
FROM world
WHERE continent ='South America'
````

| name                | population_mi |
| ------------------- | -------------- |
| Argentina           | 42.6695        |
| Bolivia            | 10.027254      |
| Brazil             | 202.794        |
| Chile              | 17.773         |
| Colombia           | 47.662         |
| Ecuador            | 15.7742        |
| Guyana             | 0.784894       |
| Paraguay           | 6.783374       |
| Peru               | 30.475144      |
| Saint Vincent and the Grenadines | 0.109 |
| Suriname           | 0.534189       |
| Uruguay            | 3.286314       |
| Venezuela          | 28.946101      |



## Ejercicio 5


Usar **WHERE, IN** con varias ordenes. Show the name and population for France, Germany, Italy

```sql
SELECT name, population
FROM world
WHERE name IN ('France', 'Germany', 'Italy')
```

|name|pupulation|
|--|--|
|France|65906000|
|Germany|80716000|
|Italy|	60782668|

> Nota:  el **IN** filtra las filas donde el valor en la columna seleccionada en WHERE, es igual a alguno de los valores en la lista entre paréntesis


## Ejercicio 6


Usar **WHERE, LIKE**, **%** para filtros de nombres en columnas. El **LIKE** es utilizado para **comparar patrones de cadenas de texto**.

Ejemplo: Show the name and population for France, Germany, Italy

```sql
SELECT name
FROM world
WHERE name LIKE '%United%'
````

|name|
|--|
|United Arab Emirates|
|United Kingdom|
|United States|


> Nota: Este código selecciona la columna name de la tabla countries y filtra solo aquellas filas cuyo valor en la columna name incluye la palabra "United". La cláusula LIKE es utilizada para comparar un patrón de búsqueda con los valores en la columna, y el signo de porcentaje (%) se utiliza como comodín para representar cualquier número de caracteres. Por lo tanto, el patrón '%United%' significa que se debo seleccionar todas las filas donde la palabra "United" aparezca en cualquier parte del valor en la columna name.




## Ejercicio 7


Usar **WHERE, OR**, para condicionales. El operador lógico **OR** permite combinar varios criterios en una cláusula WHERE, y se utiliza para seleccionar aquellas **filas que cumplen con al menos uno de los criterioso**.

Ejemplo: Two ways to be big: A country is big if it has an area of more than 3 million sq km or it has a population of more than 250 million. Show the countries that are big by area or big by population. Show name, population and area.


```sql
SELECT name, population, area
FROM world
WHERE area >= 3000000 OR population >=250000000
````

| name           | population      | area       |
| -------------- | --------------- | ---------- |
| Australia      | 23,545,500      | 7,692,024 km² |
| Brazil         | 202,794,000     | 8,515,767 km² |
| Canada         | 35,427,524      | 9,984,670 km² |
| China          | 1,365,370,000   | 9,596,961 km² |
| India          | 1,246,160,000   | 3,166,414 km² |
| Indonesia      | 252,164,800     | 1,904,569 km² |
| Russia         | 146,000,000     | 17,125,242 km² |
| United States  | 318,320,000     | 9,826,675 km² |



> Nota: En este caso, se seleccionarán aquellas filas donde la superficie es mayor a 3 millones de km^2 OR la población es mayor a 250 millones.



## Ejercicio 8


Usar **WHERE, **XOR**, Condicional Excluyente. El operador XOR es un operador lógico que se evalúa como verdadero cuando una de las expresiones es verdadera y la otra es falsa.

Ejemplo: Exclusive OR (XOR). Show the countries that are big by area (more than 3 million) or big by population (more than 250 million) but not both. Show name, population and area.

Australia has a big area but a small population, it should be included.
Indonesia has a big population but a small area, it should be included.
China has a big population and big area, it should be excluded.
United Kingdom has a small population and a small area, it should be excluded


```sql
SELECT name, population, area
FROM world
WHERE ((area > 3000000) AND (population <= 250000000))
   OR ((area <= 3000000) AND (population > 250000000))
```

| name         | population   | area        |
| ------------ | ------------ | ----------- |
| Australia    | 23545500     | 7692024     |
| Brazil       | 202794000    | 8515767     |
| Canada       | 35427524     | 9984670     |
| Indonesia    | 252164800    | 1904569     |
| Russia       | 146000000    | 17125242    |


>Nota: En este caso, la consulta selecciona todas las filas de la tabla de países que cumplen con la condición de que la superficie sea mayor a 3 millones de km² o la población sea mayor a 250 millones de habitantes, pero no ambos.

En diferentes bases de datos:

*En MySQL*
SELECT name, population, area
FROM world
WHERE (area > 3000000 XOR population > 250000000);

*En PostgreSQL*
SELECT name, population, area
FROM countries
WHERE (area > 3000000) IS NOT (population > 250000000);


*En SQL Server*
SELECT name, population, area
FROM countries
WHERE ((area > 3000000) AND (population <= 250000000))
   OR ((area <= 3000000) AND (population > 250000000));



## Ejercicio 9


Usar **ROUND**, para redondear un número en determinado número de decimales.

Show the name and population in millions and the GDP in billions for the countries of the continent 'South America'. Use the ROUND function to show the values to two decimal places.

For South America show population in millions and GDP in billions both to 2 decimal places.
Millions and billions
Divide by 1000000 (6 zeros) for millions. Divide by 1000000000 (9 zeros) for billions.

```sql
SELECT name, ROUND(population/1000000,2) AS population_mill, ROUND(GDP/1000000000,2) AS GDP_bill
FROM world
WHERE continent = 'South America'
```









![Aprendiendo](https://cdn-icons-png.flaticon.com/512/2306/2306173.png)











