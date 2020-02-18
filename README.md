> El siguiente contenido fue elaborado por [@_nhsz](https://twitter.com/_nhsz) como guía para las clases de [undefined school](https://twitter.com/undefinedSchool)
> Son bienvenidos los _issues_ y _PRs_ para mejorar el contenido, corregir errores, etc. 

> 👉 Si te resultó útil, **se agradece que lo compartas para que le llegue a más gente!**

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

[![What are databases?](https://img.youtube.com/vi/Ls_LzOZ7x0c/0.jpg)](https://www.youtube.com/watch?v=Ls_LzOZ7x0c)

Una base de datos nos da una **estructura** y nos permite setear un conjunto de **reglas** sobre los datos que guardamos.

## Características

- _schema_ estricto
- datos organizados en tablas, relacionadas entre sí

## Conceptos

### Base de datos relacional

Una base de datos **_relacional_** es una **colección** de **_tablas_** (de 2 dimensiones), relacionadas entre sí. 

Para una guía visual, ver [A Shelfish Starter Guide to Databases](https://illustrated.dev/databases)

**Organizamos los datos en tablas**.

Cada tabla contiene **_filas_** y **_columnas_**, que a su vez contienen **datos**. 

Vamos a llamar **_registro_** (_record_) a cada una de las filas.

![](https://miro.medium.com/max/736/0*kBYg1f1lVSFE5cY6.PNG)

Los datos de las diferentes tablas pueden estar, como dijimos antes, _relacionados entre sí_ (de ahí el nombre de bases de datos _relacionales_).

La colección de tablas de una base de datos se conoce como **_schema_**.

👉 En una _base de datos relacional_, **el _schema_ debe definirse antes de poder interactuar con la misma**. Todos los _registros_ de una base de datos relacional deben seguir el esquema definido.

### Server

La mayoría de las bases de datos siguen la arquitectura _cliente-servidor_.

El _server_ de la base de datos se encarga de correr el _DBMS_ (Database Management System). A través de un _cliente_, nos conectamos al _server_ de la DB, para crear nuestra base de datos e interactuar con ella.

### Primary Key

Es un valor que identifica **unívocamente** cada registro (fila) de una tabla. Generalmente se corresponde con el campo `id` de la tabla.

### Relaciones

- 1 to 1
- 1 to many
- many to many

### Index

Cuando buscamos datos en una tabla (`SELECT, WHERE`), la base de datos tiene que mirar registro por registro para encontrar aquellos que matcheen con los criterios especificados. Si tenemos un gran volumen de datos, esta operación puede ser muy lenta.

Para solucionar este problema existen los **índices**, que permiten que nuestras _queries_ sean rápidas y eficientes.

## SQL

Es el lenguaje que vamos a utilizar para hacer consultas e interactuar con una _base de datos relacional_.

👉 Ver [notas de SQL](https://github.com/undefinedschool/notes-sql/)

## PostgreSQL

[PostgreSQL](https://www.postgresql.org), también conocido como _Postgres_ a secas, es un [_RDBMS_](https://www.codecademy.com/articles/what-is-rdbms-sql) para bases de datos relacionales, de propósito general, open-source y gratuito, tanto para uso personal como comercial. Se trata también de una de las bases de datos relacionales más avanzadas y populares que existen.

Provee soporte para la mayor parte del _standard SQL_ y agrega algunas features propias (incluso [podemos utilizar JavaScript para crear funciones _custom_](https://blog.heroku.com/javascript_in_your_postgres)).

Al tratarse de una _base de datos relacional_, vamos a urilizar SQL para realizar _queries_ con los datos almacenados en esta.

### Instalación

Lo más fácil es ir a la [sección de descargas de PostgreSQL](https://www.postgresql.org/download/) y descargar el [instalador interactivo](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads) correspondiente a nuestro SO.

En el caso de OS X, podemos usar [`homebrew`](https://brew.sh/) para instalarlo:

```bash
brew install postgresql
```

y luego iniciar el servicio como _daemon_, es decir, que se quede corriendo de fondo, escuchando en el puerto default

```bash
brew services start postgresql
```

Para actualizar, hacemos

```bash
brew upgrade postgresql
brew postgresql-upgrade-database
brew services restart postgresql
```

👉 Para más detalles, ver [PostgreSQL (Postgres) - Installation & Overview](https://www.youtube.com/watch?v=fZQI7nBu32M)

## Ejercicios

1. Instalar [PostgreSQL](https://www.postgresql.org/) (Ver [PostgreSQL - Instalación](https://github.com/undefinedschool/notes-dbs#instalaci%C3%B3n))
2. Práctica con [SQLBolt](https://sqlbolt.com/)
3. Práctica en [Codewars - SQL for Beginners](https://www.codewars.com/collections/sql-for-beginners)
4. Práctica en [PostgreSQL Exercises](https://pgexercises.com/gettingstarted.html)
