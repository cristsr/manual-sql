# Lenguaje de manipulacion de datos

El lenguaje dml nos Permite recuperar, almacenar, modificar, eliminar, insertar y actualizar datos de una base de datos.


Sentencias de DML:

- SELECT
- INSERT
- UPDATE
- DELETE

## Select
Se utiliza para consultar registros de la base de datos

- Seleccionar el nombre y la direccion de los edificios que se encuentran en el pais dado
``` sql
select name, address
from buildings
where seat in (
    select seats.id
    from seats
             left join (
        select id
        from cities
        where country = 'CO') c on c.id = seats.city
    where c.id is not null); 
``` 

## Insert 
Sentencia utilizada para agregar uno o varios registros a las tablas de una base de datos.

``` sql
insert into seats (address, name, city)
values ('new york street 41', 'New york seat', 3),
       ('Bogota street 12', 'Bogota seat', 8),
       ('Rio de janeiro street', 'Rio de janeiro seat', 6);
```

## Update
Sentencia utilizada para modificar uno o varios registros que cumplan la condición dada.

``` sql
update users set name = 'jhon 2' where dni = 435645;

```

## Delete 
Sentencia que permite eliminar uno o varios registros de una tabla que cumplan la condicion dada.

``` sql
delete from users where dni = 435645
```
