# Disparadores

Los disparadores o triggers al igual que los procedimientos almacenados, consisten en un conjunto de instrucciones que
se almacenan en el servidor mysql con la diferencia de que los disparadores se disparan de forma automática después de
que un evento ocurre en la base de datos, a continuación se muestra la lista de eventos en mysql

## Before insert

Se dispara antes de realizar una inserción de registros en una tabla.

``` sql
delimiter //
CREATE TRIGGER ins_sum BEFORE INSERT ON account
       FOR EACH ROW SET @sum = @sum + NEW.amount;
delimiter ;
```

## After insert

Se dispara después de realizar una inserción de registros en una tabla.


``` sql
delimiter //
CREATE TRIGGER ins_sum AFTER INSERT ON account
       FOR EACH ROW SET @sum = @sum + NEW.amount;
delimiter ;
```

## Before update

Se dispara antes de realizar una actualización de uno o varios registros en una tabla.

``` sql
delimiter //
CREATE TRIGGER upd_check BEFORE UPDATE ON account
       FOR EACH ROW
       BEGIN
           IF NEW.amount < 0 THEN
               SET NEW.amount = 0;
           ELSEIF NEW.amount > 100 THEN
               SET NEW.amount = 100;
           END IF;
       END;//
delimiter ;
```

## After update

Se dispara después de realizar una actualización de uno o varios registros en una tabla.
``` sql
delimiter //
CREATE TRIGGER upd_check AFTER UPDATE ON account
       FOR EACH ROW
       BEGIN
           IF NEW.amount < 0 THEN
               SET NEW.amount = 0;
           ELSEIF NEW.amount > 100 THEN
               SET NEW.amount = 100;
           END IF;
       END;//
delimiter ;
```

## Before delete

Se dispara antes de eliminar uno o varios registros en una tabla.

``` sql
delimiter //
CREATE TRIGGER add_register BEFORE DELETE ON users for each row
BEGIN
    DELETE FROM seats where id = 1;
END;//
delimiter ;
```

## After Delete

Se dispara después eliminar uno o varios registros en una tabla.

``` sql
delimiter //
CREATE TRIGGER add_register AFTER DELETE ON users for each row
BEGIN
    DELETE FROM seats where id = 1;
END;//
delimiter ;
```

