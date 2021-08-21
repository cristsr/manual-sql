# Usuarios y privilegios

Mysql provee un sistema completo para realizar la gestión de usuarios y permisos, mediante la ejecucion de instrucciones
sencillas y declarativas se puede controlar absolutamente todos los aspectos de un usuario.

## Gestión de usuarios

Mysql permite que varios usuarios puedan interactuar con los recursos del servidor

#### Creación de usuarios*

Para crear usuarios en mysql existe la sentencia create user

``` sql
create user 'admin'@'localhost' identified by 'admin';
create user 'auditor'@'localhost' identified by 'auditor';
create user 'temp'@'localhost' identified by 'temp';
```

#### Listar usuarios

Listar usuarios disponibles en mysql

``` sql
SELECT user FROM mysql.user;

SELECT user, host FROM mysql.user;
```

#### Actualizar usuarios

Para actualizar uno o varios usuarios en mysql se utiliza la sentencia update

``` sql
UPDATE mysql.user SET Password=PASSWORD('NuevaContraseña') 
WHERE USER='nombreUsuario' AND Host='NombreHost';
```

#### Eliminar usuarios en mysql

La sentencia drop user nos permite eliminar un usuario del registro

``` sql
drop user if exists 'admin'@'localhost';
```

## Privilegios

##### Asignación de privilegios

Los privilegios concedidos a una cuenta de MySQL determinan las operaciones que la cuenta puede realizar. Los
privilegios de MySQL difieren en los contextos en los que se aplican y en los diferentes niveles de operación:

- Los privilegios administrativos permiten a los usuarios gestionar el funcionamiento del servidor MySQL. Estos
  privilegios son globales porque no son específicos de una base de datos en particular.

``` sql
grant all privileges on *.* to admin@localhost;
```

- Los privilegios de base de datos se aplican a una base de datos y a todos los objetos que contiene. Estos privilegios
  se pueden conceder para bases de datos específicas, o globalmente para que se apliquen a todas las bases de datos.

``` sql
grant SELECT, INSERT, UPDATE, DELETE on inventory.* 
to 'auditor'@'localhost';
```

- Los privilegios para objetos de bases de datos como tablas, índices, vistas y rutinas almacenadas pueden concederse
  para objetos específicos dentro de una base de datos, para todos los objetos de un tipo determinado dentro de una base
  de datos (por ejemplo, todas las tablas de una base de datos) o globalmente para todos los objetos de un tipo
  determinado en todas las bases de datos.

``` sql
grant SELECT, INSERT, UPDATE, DELETE on inventory.workstations 
to 'temp'@'localhost';
```

##### Listar privilegios de un usuario

La sentencia show grants nos permite listar todos los privilegios que tiene un usuario dado.

``` sql
show grants for current_user;
show grants for 'admin'@'localhost';
show grants for 'auditor'@'localhost';
show grants for 'temp'@'localhost';
```

##### Revocar privilegios de un usuario

La sentencia revoke es utilizada para eliminar uno o varios privilegios de un usuario.

``` sql
REVOKE SELECT ON inventory.workstations FROM 'temp'@'localhost';
```
