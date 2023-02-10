# SELECT BASICS

## Ejercicio 1

Comando **WHEN**, Mostrar una columna y una fila: Show the population of Germany

```sql
SELECT population 
FROM world
WHERE name = 'Germany'
```
Ejemplo

| Raza | Pelo | Tamaño | Personalidad |
| --- | --- | --- | --- |
| Labrador Retriever | Corto | Grande | Amigable |
| Bulldog Francés | Corto | Mediano | Leal |
| Golden Retriever | Largo | Grande | Juguetón |
| Chihuahua | Corto | Pequeño | Vivaz |
| Pastor Alemán | Medio | Mediano a Grande | Inteligente |



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

Comando **BETWEEN** (Rangos): Show the country and the area for countries with an area between 200,000 and 250,000.

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



















![Aprendiendo](https://cdn-icons-png.flaticon.com/512/2306/2306173.png)











