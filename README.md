> El siguiente contenido fue elaborado por [@_nhsz](https://twitter.com/_nhsz) como guía para las clases de [undefined school](https://twitter.com/undefinedSchool)
> Son bienvenidos los _issues_ y _PRs_ para mejorar el contenido, corregir errores, etc. 

> 👉 Si te resultó útil, **se agradece que lo compartas para que le llegue a más gente!**

# ![Notas sobre Bases de Datos Relacionales](https://i.imgur.com/g9S0eWn.png)

## Contenido

- [Base de Datos](https://github.com/undefinedschool/notes-dbs#base-de-datos)
- [Qué problema resuelven las bases de datos](https://github.com/undefinedschool/notes-dbs#qu%C3%A9-problema-resuelven-las-bases-de-datos)
- [Conceptos](https://github.com/undefinedschool/notes-dbs#conceptos)
  - [Base de datos relacional](https://github.com/undefinedschool/notes-dbs#base-de-datos-relacional)
    - [Tabla](https://github.com/undefinedschool/notes-dbs#tabla)
      - [Registro](https://github.com/undefinedschool/notes-dbs#registro)
    - [Schema](https://github.com/undefinedschool/notes-dbs#schema)
    - [Tipos de datos](https://github.com/undefinedschool/notes-dbs#tipos-de-datos)
    - [Características](https://github.com/undefinedschool/notes-dbs#caracter%C3%ADsticas)
  - [DBMS](https://github.com/undefinedschool/notes-dbs#dbms)
  - [Server](https://github.com/undefinedschool/notes-dbs#server)
  - [Primary Key](https://github.com/undefinedschool/notes-dbs#primary-key)
    - [Natural keys](https://github.com/undefinedschool/notes-dbs#natural-keys)
    - [Synthetic keys](https://github.com/undefinedschool/notes-dbs#synthetic-keys)
  - [Foreign Key](https://github.com/undefinedschool/notes-dbs#foreign-key)
  - [Relaciones](https://github.com/undefinedschool/notes-dbs#relaciones)
  - [Índices](https://github.com/undefinedschool/notes-dbs#%C3%ADndices)
  - [Transacciones](https://github.com/undefinedschool/notes-dbs#transacciones)
  - [ACID](https://github.com/undefinedschool/notes-dbs#acid)
- [SQL](https://github.com/undefinedschool/notes-dbs#sql)
- [PostgreSQL](https://github.com/undefinedschool/notes-dbs#postgresql)
  - [Instalación](https://github.com/undefinedschool/notes-dbs#instalaci%C3%B3n)
- [Ejercicios](https://github.com/undefinedschool/notes-dbs#ejercicios)

---

## Base de Datos

Una base de datos es un **conjunto de datos relacionados entre si y almacenados sistemáticamente (agrupados o estructurados de cierta forma) para su posterior uso**.

Nos permiten guardar grandes cantidades de información de forma organizada, para que luego podamos encontrarla y utilizarla más fácilmente.

> Para más detalles, ver [Base de datos - Wikipedia](https://es.wikipedia.org/wiki/Base_de_datos)

## Qué problema resuelven las bases de datos

**Tenemos datos que necesitamos almacenar**, que pueden ser de diferentes tipos (como datos de clientes, información sobre un producto, nombres, fechas de nacimiento, cantidades, etc). **Pero el problema no pasa por tener datos en si**, este no es un motivo suficiente para necesitar usar una base de datos. Los problemas que enfrentamos son los siguientes:

- **tamaño**: la cantidad de datos que tenemos que manejar puede ir creciendo con el tiempo
- facilidad de **actualización de los datos**: qué pasaría si, por ejemplo, 2 personas quieren editar datos a la vez?
- **precisión:** hay algo que prevenga que ingresemos datos con el formato incorrecto?
- **seguridad**: quién puede acceder a estos datos? cómo controlamos el acceso y diferentes permisos o privilegios?
- **redundancia**: la duplicación de datos genera conflictos, cómo sabemos cuál es el correcto?
- **importancia**: no queremos perder datos ni el trabajo realizado frente a imprevistos

[![What are databases?](https://img.youtube.com/vi/Ls_LzOZ7x0c/0.jpg)](https://www.youtube.com/watch?v=Ls_LzOZ7x0c)
> Ver [What are databases? | Simon Allardice](https://www.youtube.com/watch?v=Ls_LzOZ7x0c)

> 👉 Una base de datos nos da una **estructura** y nos permite setear un conjunto de **reglas** sobre los datos que guardamos.
> A través de una base de datos, podemos **almacenar, manipular y obtener** datos.

## Conceptos

### Base de datos relacional

Una base de datos **_relacional_** es una **colección** de 1 o más [**_tablas_**]() (de 2 dimensiones), relacionadas entre sí. 

#### Tabla

**Organizamos los datos en tablas**. Las tablas forman los _bloques fundamentales_ de los que se compone una DB.

> 👉 Para una guía visual, ver [A Shelfish Starter Guide to Databases](https://illustrated.dev/databases).

Cada tabla contiene **_filas_** y **_columnas_**, que a su vez contienen **datos**. En las tablas definimos la estructura y los [_tipos de datos_]() que estas van a almacenar, al definir las columnas de las mismas.

**Cada columna le da un nombre y un [tipo]() (texto, numérico, fecha, etc.) al dato almacenado** y cada fila ([_registro_](https://github.com/undefinedschool/notes-dbs#registro)) debe seguir esta estructura.

![](https://miro.medium.com/max/736/0*kBYg1f1lVSFE5cY6.PNG)

> 👉 **Al definir las columnas de una tabla, estamos estableciendo reglas sobre los datos que contiene una tabla**, que el [DBMS](https://github.com/undefinedschool/notes-dbs#dbms) se encargará de hacer cumplir.

Los datos de las diferentes tablas pueden estar, como dijimos antes, _relacionados entre sí_ (de ahí el nombre de bases de datos _relacionales_).

> 👉 **Las tablas y sus columnas deben definirse de antemano, antes de poder cargar datos en la DB.**

##### Registro

Vamos a llamar **_registro_** (_record_) a cada una de las filas de una [tabla](), que representan una unidad de información.

#### Schema

La colección de tablas de una base de datos se conoce como **_schema_**.

👉 En una _base de datos relacional_, **el _schema_ debe definirse antes de poder interactuar con la misma**. Todos los _registros_ de una base de datos relacional deben seguir el esquema definido.

#### Tipos de datos

#### Características

- datos organizados en tablas, relacionadas entre sí
- _schema_ estricto, definido al comienzo

### DBMS

Oracle, MySQL, PostgreSQL, MongoDB, etc. _no son bases de datos en si, sino **Database Management Systems** (DBMS)_. Un _DBMS_ es un software que utilizamos para crear y administrar bases de datos, permitiéndonos acceder a los datos de forma rápida y estructurada.

> 👉 **Un _DBMS_ puede administrar 1 o varias bases de datos**.

En el caso de las bases de datos relacionales, utilizamos más específicamente, **Relational Database Management Systems** o _RDBMS_ (subcategoría dentro de los DBMS). Los principios y conceptos que usaremos aplican para las diferentes variantes mencionadas anteriormente.

### Server

La mayoría de las **bases de datos** siguen la **arquitectura _cliente-servidor_**.

Es en el _server_ donde se encuentran alojados los datos.

El **_server_ de la base de datos** además, **se encarga de correr el _DBMS_ (Database Management System)**. A través de un _cliente_, nos conectamos al _server_ de la DB, para crear nuestra base de datos e interactuar con ella.

### Primary Key

Es un valor de una columna (o conjunto de columnas) que identifica **unívocamente** (1 y sólo 1) cada registro (o fila) de una tabla. Generalmente se corresponde con el campo `id` de la tabla.

> 👉 **Toda tabla de una base de datos relacional debe tener definida una Primary Key**.

#### Natural keys

Se conocen como _natural keys_ (claves naturales) a las _Primary Keys_ que **se generan a partir de los datos de una tabla**.

Son valores de columnas que tienen relación col el resto de las columnas de un registro dado. Por ejemplo, email, número de seguridad social, número de pasaporte, ISBN, etc.

#### Synthetic keys

Se conocen como _synthetic keys_ o _surrogate keys_ (claves sustitutas) a las _Primary Keys_ **generadas por la base de datos al insertar un nuevo registro**: estas no derivan de los datos de la tabla, es decir, es una columna extra que agregamos sólo con este propósito.

Se trata generalmente de valores numéricos, como pueden ser `product_id` o `customer_id`, etc. 

> Para más detalles, ver [Natural Key vs Surrogate Key](https://www.databasejournal.com/features/mssql/article.php/3922066/SQL-Server-Natural-Key-Verses-Surrogate-Key.htm)

### Foreign Key

Es un valor o campo (o grupo de campos) que identifica **unívocamente** un registro (fila) de otra tabla, es decir, hace referencia a una [**Primary Key**](https://github.com/undefinedschool/notes-dbs#primary-key) de otra tabla.

El tipo de dato es indistinto, lo importante es que la columna que elijamos como _Primary Key_ no contenga valores repetidos.

> 👉 **Una tabla puede contener múltiples Foreign Keys**, dependiendo de sus relaciones con otras tablas.

### Relaciones

(WIP)

- 1 to 1
- 1 to many
- many to many

### Índices

Cuando buscamos datos en una tabla (`SELECT, WHERE`), la base de datos tiene que mirar registro por registro para encontrar aquellos que coincidan con los criterios especificados. Si tenemos un gran volumen de datos, esta operación puede ser _muy lenta_.

Para solucionar este problema existen los **índices**, que permiten que nuestras _queries_ sean rápidas y eficientes, mejorando en consecuencia la _performance_.

Podemos _indexar_ tablas por 1 o más columnas. **Una DB puede tener más de un índice**.

> ⚠️ **Agregar índices a una DB requiere espacio extra de almacenamiento (espacio en disco), aparte del espacio necesario para almacenar los datos**. Además, cada vez que agreguemos un nuevo registro a una tabla, se actualizarán los índices correspondientes, haciendo esta operación más costosa. Por lo tanto, hay que utilizarlos con la precaución y planificación necesaria.

### Transacciones

(WIP)

### ACID

(WIP)

## SQL

Es el lenguaje que vamos a utilizar para hacer consultas e interactuar con una _base de datos relacional_.

👉 Ver [notas de SQL](https://github.com/undefinedschool/notes-sql/).

## PostgreSQL

[PostgreSQL](https://www.postgresql.org), también conocido como _Postgres_ a secas, es un [_RDBMS_](https://www.codecademy.com/articles/what-is-rdbms-sql) para bases de datos relacionales, de propósito general, open-source y gratuito, tanto para uso personal como comercial. Se trata también de una de las bases de datos relacionales más avanzadas y populares que existen.

Provee soporte para la mayor parte del _standard SQL_ y agrega algunas features propias (incluso [podemos utilizar JavaScript para crear funciones _custom_](https://blog.heroku.com/javascript_in_your_postgres)).

Al tratarse de una _base de datos relacional_, vamos a urilizar SQL para realizar _queries_ con los datos almacenados en esta.

### Instalación

Lo más fácil es ir a la [sección de descargas de PostgreSQL](https://www.postgresql.org/download/) y descargar el [instalador interactivo](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads) correspondiente a nuestro Sistema Operativo.

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

👉 Para más detalles, ver [PostgreSQL (Postgres) - Installation & Overview](https://www.youtube.com/watch?v=fZQI7nBu32M).

## Ejercicios

1. Instalar [PostgreSQL](https://www.postgresql.org/) (Ver [PostgreSQL - Instalación](https://github.com/undefinedschool/notes-dbs#instalaci%C3%B3n)).
2. Práctica con [SQLBolt](https://sqlbolt.com/).
3. Práctica en [Codewars - SQL for Beginners](https://www.codewars.com/collections/sql-for-beginners).
4. Práctica en [PostgreSQL Exercises](https://pgexercises.com/gettingstarted.html).
