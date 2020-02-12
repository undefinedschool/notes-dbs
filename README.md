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

Una base de datos nos da una **estructura** y nos permite setear un conjunto de **reglas** sobre los datos que guardamos.

## Conceptos

### Base de datos relacional

Una base de datos **_relacional_** es una colección de **_tablas_** (de 2 dimensiones), relacionadas entre sí. Organizamos los datos en tablas.

Cada tabla contiene **_filas_** y **_columnas_**, que a su vez contienen **datos**. 

Vamos a llamar **_registro_** (_record_) a cada una de las filas.

![](https://miro.medium.com/max/736/0*kBYg1f1lVSFE5cY6.PNG)

Los datos de las diferentes tablas pueden estar, como dijimos antes, _relacionados entre sí_ (de ahí el nombre de bases de datos _relacionales_).

La colección de tablas de una base de datos se conoce como **_schema_**.

### Server

La mayoría de las bases de datos siguen la arquitectura _cliente-servidor_.

El _server_ de la base de datos se encarga de correr el _DBMS_ (Database Management System). A través de un _cliente_, nos conectamos al _server_ de la DB, para crear nuestra base de datos e interactuar con ella.

### Primary Key

Es un valor que identifica **unívocamente** cada registro (fila) de una tabla. Generalmente se corresponde con el campo `id` de la tabla.

### Index

Cuando buscamos datos en una tabla (`SELECT, WHERE`), la base de datos tiene que mirar registro por registro para encontrar aquellos que matcheen con los criterios especificados. Si tenemos un gran volumen de datos, esta operación puede ser muy lenta.

Para solucionar este problema existen los **índices**, que permiten que nuestras _queries_ sean rápidas y eficientes.

## SQL

**SQL** (**S**tructured **Q**uery **L**anguage), es un lenguaje que utilizamos para interactuar con una base de datos relacional y realizar operaciones de tipo _CRUD_ (**C**reate, **R**ead, **U**pdate, **D**elete), como crear bases de datos, crear tablas, insertar datos en estas tablas, seleccionar datos específicos que cumplan con ciertos criterios, combinar datos, eliminar datos, etc, es decir, _consultar, manipular y transformar datos de una base de datos relacional_.

👉 **SQL nos permite entonces, responder preguntas específicas sobre los datos almacenados en la DB**.

> A las _bases de datos relacionales_ también se las conoce coloquialmente como _bases de datos SQL_. Existen muchas,     SQLite, MySQL, Postgres, Oracle, Microsoft SQL Server, etc. Todas estas tienen soporte para el **standard SQL** (que es lo que  vamos   a utilizar) y además, cada implementación o _engine_ agrega sus propias features y tipos de datos (no standard).

⚠️ **Nota:** las instrucciones deben siempre terminar con `;`. Es indiferente si las escribimos en una sola línea o en varias, utilizando indentación para que resulte más legible.

Vamos a llamar _consulta_ o **_query_** a cada instrucción que termina con `;`. 

Una _query_ está compuesta por _comandos_ y _cláusulas_. 

- **Comandos:** son los que utilizamos para crear y definir nuevas bases de datos, campos e índices. También para seleccionar, insertar, eliminar y actualizar datos, generar consultas para ordenar, filtrar y extraer datos de la base de datos.
- **Cláusulas:** son condiciones de modificación utilizadas para definir los datos que desea seleccionar o manipular.

## Comandos para modificar el _schema_

### `CREATE DATABASE`

Es el _comando_ que utilizamos para crear una nueva base de datos.

```sql
CREATE DATABASE testingdb;
```

También podríamos escribir la instrucción en 2 líneas, porque lo importante es el `;`.

```sql
CREATE DATABASE 
  testingdb;
```

### `CREATE TABLE`

Es el _comando_ que utilizamos para crear una nueva tabla.

```sql
CREATE TABLE movies (
  id SERIAL PRIMARY KEY,
  title VARCHAR(100),
  overview VARCHAR,
  release_date DATE,
  remove_this CHAR(1)
);
```

### `ALTER`

Es un _comando_ que nos permite modificar una tabla.

Para **agregar una nueva columna**, usamos `ALTER` con `ADD`

```sql
ALTER TABLE
  movies
ADD
  rate DECIMAL(4, 2);
```

Para **eliminar una columna**, usamos `ALTER` con `DROP COLUMN`

```sql
ALTER TABLE
  movies
DROP COLUMN
  remove_this;
```

### `DROP`

Es un _comando_ que nos permite eliminar tablas o la base de datos entera.

Para **eliminar una tabla**, usamos `DROP TABLE`

```sql
DROP TABLE movies;
```

Para **eliminar una db**, usamos `DROP DATABASE`

```sql
DROP DATABASE testingdb;
```

## Comandos para trabajar y manipular datos

### `INSERT`

Es el _comando_ que utilizamos para insertar valores en una tabla. 

```sql
INSERT INTO 
  movies (title, overview, release_date, rate)
VALUES 
  ('Gattaca', 'In a future society in the era of indefinite eugenics, humans are set on a life course depending on their DNA. Young Vincent Freeman is born with a condition that would prevent him from space travel, yet is determined to infiltrate the GATTACA space program.', '1997-10-24', 7.50);
```

### `SELECT`

Es el _comando_ que utilizamos para **seleccionar valores de una tabla**.

Si queremos traer todas las columnas de una tabla, usamos el `*`

```sql
SELECT * FROM movies;
```

Si queremos ver sólo los títulos, tenemos que especificar la columna

```sql
SELECT title FROM movies;
```

También podemos traer varias columnas

```sql
SELECT title, rate FROM movies;
```

### `ORDER BY`

Es la _cláusula_ que utilizamos para ordenar valores por cierto campo.

Especificamos por qué campo ordenar. **Por default, ordena de forma ascendente**.

```sql
SELECT title, rate FROM movies ORDER BY rate;
```

Podemos especificar el orden agregando `ASC|DESC`

```sql
SELECT 
  title, rate 
FROM 
  movies 
ORDER BY 
  rate DESC;
```

### `WHERE`

Es la _cláusula_ que utilizamos para setear las condiciones que deben cumplir los campos que queremos seleccionar

```sql
SELECT 
  title, rate 
FROM 
  movies
WHERE
  rate > 7;
```

### `UPDATE`

Es el _comando_ que utilizamos para actualizar el valor de un campo. Se usa junto con `SET`, para especificar los valores nuevos y `WHERE`, para especificar qué campo queremos modificar.

```sql
UPDATE
  movies
SET
  rate = 8.00
WHERE
  title = 'Gattaca';
```

### `DELETE`

Es el _comando_ que utilizamos para eliminar registros de una tabla.

```sql
DELETE FROM
  movies
WHERE
  title = 'Gattaca';
```

:warning: **No te olvides de poner el `WHERE` en el `DELETE FROM`!**

[![](https://img.youtube.com/vi/i_cVJgIz_Cs/0.jpg)](https://www.youtube.com/watch?v=i_cVJgIz_Cs)

## PostgreSQL

[PostgreSQL](https://www.postgresql.org), también conocido como _Postgres_ a secas, es una base de datos relacional de propósito general, open-source y gratuita (tanto para uso personal como comercial). Se trata también de una de las bases de datos relacionales más avanzadas y populares que existen.

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
