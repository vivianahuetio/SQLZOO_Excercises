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


Comando WHERE para filtrar registros. Show the name for the countries that have a population of at least 200 millions


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



## Ejercicio 3


Hacer **Calculos en Columnas con otra columna**. Calculate per capita GDP[^1] for those countries with a population of at least 200 million.

[^1]: My Per Capita GDP is the GDP divided by the population GDP/population


```sql
SSELECT name, gdp/population AS GDP
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


## Ejercicio 5


Hacer Calculos en Columnas. Dividir con números direcamente en la columna. Divide the population by 1000000 to get population in millions.







![Aprendiendo](https://cdn-icons-png.flaticon.com/512/2306/2306173.png)











