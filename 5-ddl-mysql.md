# Lenguaje de definición de datos

El lenguaje de definición de datos permite crear y modificar la estructura de una base de datos.

Sentencias de DDL: 

- CREATE
- ALTER
- DROP
- TRUNCATE
- RENAME

## Create
Utilizado para crear nuevas tablas, campos e índices.

``` sql
create table countries
(
    code     char(2)     not null unique,
    name     varchar(80) not null,
    capital  varchar(80) null,
    currency char(4)     null,
    region   varchar(20) null,
    primary key (code)
);

create table cities
(
    id      int         not null auto_increment,
    name    varchar(80) not null,
    country char(2)     not null,
    primary key (id),
    constraint fk_country_city
        foreign key (country)
            references countries (code)
            on delete cascade
);
```

## Alter
Utilizado para modificar las tablas agregando campos o cambiando la definición de los campos.

``` sql
alter table countries add column active boolean null;
```

## Drop
Utilizado para eliminar tablas e índices.

``` sql
drop table workstations;
```

## Truncate
Utilizado para eliminar todos los registros de una tabla.

``` sql
truncate workstations;
```

## Rename
Tal como su nombre lo indica es utilizado para renombrar objetos
``` sql
rename table cities to cities2;
```






