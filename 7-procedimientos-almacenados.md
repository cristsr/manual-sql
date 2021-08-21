# Procedimientos almacenados

Los procedimientos almacenados consisten en un conjunto de instrucciones empaquetadas que se almacenan en el servidor de
mysql, nos permiten establecer condiciones y ciclos para la manipulación de los datos, aplicar transformaciones,
seleccionar o actualizar datos.

Muchas consultas complejas se pueden empaquetar en un procedimiento almacenado, esto permite que los clientes se olviden
de los detalles de implementación y puedan acceder a los datos mediante invocaciones de procedimientos almacenados.

## Definición en sql

Cada programa almacenado contiene un cuerpo que consta de una declaración SQL. Esta declaración puede ser una
declaración compuesta formada por varias declaraciones separadas por caracteres de punto y coma (;).

``` sql
delimiter //
CREATE PROCEDURE citycount (IN country CHAR(2), OUT cities INT)
   BEGIN
     SELECT COUNT(*) INTO cities FROM inventory.city
     WHERE CountryCode = country;
   END//
delimiter ;
```

## Invocación
La sentencia CALL permite iniciar la ejecución de un procedimiento almacenado

``` sql
CALL citycount('CO', @cities);
select @cities;
```


## Eliminación
Los procedimientos se pueden eliminar con la sentencia DROP.

``` sql
drop procedure if EXISTS citycount;
```
