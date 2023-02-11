# `SELECT BASICS`


## Ejercicio 1

Comando **WHEN**, Mostrar una columna y una fila: Show the population of Germany

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



## Ejercicio 6


Usar **WHERE, LIKE**, **%** para filtros de nombres en columnas. El **LIKE** es utilizado para **comparar patrones de cadenas de texto.

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



![Aprendiendo](https://cdn-icons-png.flaticon.com/512/2306/2306173.png)











