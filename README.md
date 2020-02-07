> El siguiente contenido fue elaborado por [@_nhsz](https://twitter.com/_nhsz) como guía para las clases de [undefined school](https://twitter.com/undefinedSchool)

> Son bienvenidos los _issues_ y _PRs_ para mejorar el contenido, corregir errores, etc

# [WIP] Notas sobre DBs relacionales

## Contenido

- []()

---

## Bases de Datos

### Qué problema resuelven

Tenemos datos que necesitamos almacenar, que pueden ser de diferentes tipos (como datos de clientes, información sobre un producto, nombres, fechas de nacimiento, cantidades, etc). Pero **el problema no pasa por tener datos en si**, este no es un motivo suficiente para necesitar usar una base de datos. Los problemas son los siguientes

- **tamaño**: la cantidad de datos que tenemos que manejar puede ir creciendo con el tiempo
- facilidad de **actualización de los datos**: qué pasaría si, por ejemplo, 2 personas quieren editar datos a la vez?
- **precisión:** hay algo que prevenga que ingresemos datos con el formato incorrecto?
- **seguridad**: quién puede acceder a estos datos? cómo controlamos el acceso y diferentes permisos o privilegios?
- **redundancia**: la duplicación de datos genera conflictos, cómo sabemos cuál es el correcto?
- **importancia**: no queremos perder datos ni el trabajo realizado frente a imprevistos

## SQL

**SQL** (**S**tructured **Q**uery **L**anguage), es un lenguaje que utilizamos para interactuar con una base de datos relacional y realizar operaciones de tipo _CRUD_ (**C**reate, **R**ead, **U**pdate, **D**elete), como crear bases de datos, crear tablas, insertar datos en estas tablas, seleccionar datos específicos que cumplan con ciertos criterios, combinar datos, eliminar datos, etc.

### Instalación

Ver [PostgreSQL (Postgres) - Installation & Overview](https://www.youtube.com/watch?v=fZQI7nBu32M)

## Base de datos relacional

Una base de datos **_relacional_** es una colección de **_tablas_**, relacionadas entre sí. Cada table contiene **_filas_** y **_columnas_**, que a su vez contienen **datos**. Vamos a llamar **_registro_** (_record_) a cada una de las filas.

![](https://miro.medium.com/max/736/0*kBYg1f1lVSFE5cY6.PNG)

Los datos de las diferentes tablas pueden estar, como dijimos antes, _relacionados entre sí_ (de ahí el nombre de bases de datos _relacionales_).

La colección de tablas de una base de datos se conoce como **_schema_**.

### Server

La mayoría de las bases de datos siguen la arquitectura _cliente-servidor_.

El _server_ de la base de datos se encarga de correr el _DBMS_ (Database Management System). A través de un _cliente_, nos conectamos al _server_ de la DB, para crear nuestra base de datos.

## Ejercicios

1. Instalar [PostgreSQL](https://www.postgresql.org/) (Ver [PostgreSQL (Postgres) - Installation & Overview](https://www.youtube.com/watch?v=fZQI7nBu32M))
