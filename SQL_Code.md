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

| name       | GDP         |
| ---------- | ----------- |
| Brazil     | 11115.265   |
| China      | 6121.711    |
| India      | 1504.793    |
| Indonesia  | 3482.020    |
| United States | 51032.295 |




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
FROM world
WHERE (area > 3000000) IS NOT (population > 250000000);


*En SQL Server*
SELECT name, population, area
FROM world
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

name             | population_mil | GDP_bill |
|------------------|----------------|----------|
| Argentina        | 42.67          | 477.03   |
| Bolivia         | 10.03          | 27.04    |
| Brazil          | 202.79         | 2254.11  |
| Chile           | 17.77          | 268.31   |
| Colombia        | 47.66          | 369.81   |
| Ecuador         | 15.77          | 87.5     |
| Guyana          | 0.78           | 2.85     |
| Paraguay        | 6.78           | 25.94    |
| Peru            | 30.48          | 204.68   |
| Saint Vincent and the Grenadines | 0.11      | 0.69     |
| Suriname        | 0.53           | 5.01     |
| Uruguay         | 3.29           | 49.92    |
| Venezuela       | 28.95          | 382.42   |



## Ejercicio 10


Usar **ROUND**, para redondear a las miles, es decir con número **negativo**, cuando los número son muy grandes.


Ejemplo: Show the name and per-capita GDP for those countries with a GDP of at least one trillion (1000000000000; that is 12 zeros). Round this value to the nearest 1000.

Show per-capita GDP for the trillion dollar countries to the nearest $1000.

```sql
SELECT name, ROUND(gdp/population,-3) AS GDP_percapita_trill
FROM world
WHERE GDP>=1000000000000
```

| Name | GDP per capita (in USD) |
| ---- | ----------------------- |
| Australia | 66,000 |
| Brazil | 11,000 |
| Canada | 45,000 |
| China | 6,000 |
| France | 40,000 |
| Germany | 42,000 |
| India | 2,000 |
| Italy | 33,000 |
| Japan | 47,000 |
| Mexico | 10,000 |
| Russia | 14,000 |
| South Korea | 22,000 |
| Spain | 28,000 |
| United Kingdom | 39,000 |
| United States | 51,000 |



>Nota: En esta consulta, primero se divide el valor de GDP por population para calcular el PIB per cápita. Luego, se usa la función ROUND para redondear el resultado a la milésima más cercana, utilizando el -3 para especificar que se quiere redondear a las miles. Finalmente, se filtran solo aquellos países con un PIB igual o superior a 1000000000000 utilizando la cláusula WHERE.


## Ejercicio 11


Usar **LENGHT** o **LEN** para **contar carácteres** de una cádena de **texto**.


Ejemplo: Greece has capital Athens.

Each of the strings 'Greece', and 'Athens' has 6 characters.

Show the name and capital where the name and the capital have the same number of characters.

You can use the LENGTH function to find the number of characters in a string
For Microsoft SQL Server the function LENGTH is LEN


Código general:

SELECT name, LENGTH(name), continent, LENGTH(continent), capital, LENGTH(capital)
  FROM world
 WHERE name LIKE 'G%'
 
Pero este código seleccionará el nombre, la longitud del nombre, el continente, la longitud del continente, la capital y la longitud de la capital para aquellos países cuyo nombre comience con la letra "G", por tanto no aplica.
 
 
 El Código correcto para el ejemplo es:
 
 ´´´sql
SELECT name, LEN(name) AS num_país, capital, LEN(capital) AS num_Capital
FROM world
WHERE LEN(name) = LEN(capital)
´´´

| name        | capital       |
|-------------|---------------|
| Algeria     | Algiers       |
| Angola      | Luanda        |
| Armenia     | Yerevan       |
| Botswana    | Gaborone      |
| Canada      | Ottawa        |
| Djibouti    | Djibouti      |
| Egypt       | Cairo         |
| Estonia     | Tallinn       |
| Fiji        | Suva          |
| Gambia      | Banjul        |
| Georgia     | Tbilisi       |
| Ghana       | Accra         |
| Greece      | Athens        |
| Luxembourg  | Luxembourg    |
| Mauritania  | Nouakchott    |
| Paraguay    | Asunción      |
| Peru        | Lima          |
| Poland      | Warsaw        |
| Russia      | Moscow        |
| Rwanda      | Kigali        |
| San Marino  | San Marino    |
| Singapore   | Singapore     |
| Taiwan      | Taipei        |
| Togo        | Lomé          |
| Turkey      | Ankara        |
| Zambia      | Lusaka        |


El lenght se utiliza en`WHERE` para filtrar los registros basados en la condición de que la longitud de `name` sea igual a la longitud de `capital`. La función `LENGTH` se utiliza para calcular el número de caracteres en cada columna. 




## Ejercicio 12

Usar **LEFT** para aislar el **primer** carácter de una palabra. EN el where pueden ir varias funciones.

Ejemplo: The capital of Sweden is Stockholm. Both words start with the letter 'S'.

Show the name and the capital where the first letters of each match. Don't include countries where the name and the capital are the same word.
You can use the function LEFT to isolate the first character.
You can use <> as the NOT EQUALS operator.

```sql
SELECT name, capital
FROM world
WHERE LEFT(name,1) = LEFT(capital,1) AND name<>capital
````

| name       | capital         |
|------------|-----------------|
| Algeria    | Algiers        |
| Andorra    | Andorra la Vella |
| Barbados   | Bridgetown      |
| Belize     | Belmopan        |
| Brazil     | Brasília        |
| Brunei     | Bandar Seri Begawan |
| Burundi    | Bujumbura       |
| Guatemala  | Guatemala City  |
| Guyana     | Georgetown      |
| Kuwait     | Kuwait City     |
| Maldives   | Malé            |
| Marshall Islands | Majuro   |
| Mexico     | Mexico City     |
| Monaco     | Monaco-Ville    |
| Mozambique | Maputo          |
| Niger      | Niamey          |
| Panama     | Panama City     |
| Papua New Guinea | Port Moresby |
| Sao Tomé and Príncipe | São Tomé |
| South Korea | Seoul          |
| Sri Lanka  | Sri Jayawardenepura Kotte |
| Sweden     | Stockholm       |
| Taiwan     | Taipei          |
| Tunisia    | Tunis           |



## Ejercicio 13

Usar **LIKE** para buscar varias letras sin importar el orden en un registro.

Ejemplo: Equatorial Guinea and Dominican Republic have all of the vowels (a e i o u) in the name. They don't count because they have more than one word in the name.
Find the country that has all the vowels and no spaces in its name.
You can use the phrase name NOT LIKE '%a%' to exclude characters from your results.
The query shown misses countries like Bahamas and Belarus because they contain at least one 'a'


```sql
SELECT name
   FROM world
WHERE name LIKE '%a%'
   AND name LIKE '%e%'
   AND name LIKE '%i%'
   AND name LIKE '%o%'
   AND name LIKE '%u%'
  AND name NOT LIKE  '% %' ESCAPE '\'
  ```
  
  
|name|
| -- | 
|Mozambique|

La siguiente consulta selecciona todas las filas de la tabla table_name en las que el campo field_name contiene exactamente dos palabras separadas por un espacio.

El patrón '% %' coincide con una cadena que tenga dos secuencias de caracteres separadas por un espacio, y el carácter de escape '\' indica que el siguiente carácter ("%") no es un comodín.

Ten en cuenta que esta consulta puede ser limitada y puede no funcionar correctamente en todos los casos, ya que no se está tomando en cuenta la longitud de las palabras o si hay más de un espacio en blanco entre ellas. En estos casos, puede ser necesario utilizar una solución más compleja, como una expresión regular o una función de manipulación de cadenas.







![Aprendiendo](https://cdn-icons-png.flaticon.com/512/2306/2306173.png)











