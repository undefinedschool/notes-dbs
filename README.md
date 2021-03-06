# ![Notas sobre Bases de Datos Relacionales](https://i.imgur.com/g9S0eWn.png)

### 👉 Ver [todas las notas](https://github.com/undefinedschool/notes)

## Contenido

- [Base de Datos](https://github.com/undefinedschool/notes-dbs#base-de-datos)
- [Qué problema resuelven las bases de datos](https://github.com/undefinedschool/notes-dbs#qu%C3%A9-problema-resuelven-las-bases-de-datos)
- [Conceptos](https://github.com/undefinedschool/notes-dbs#conceptos)
  - [Base de datos relacional](https://github.com/undefinedschool/notes-dbs#base-de-datos-relacional)
    - [Tabla](https://github.com/undefinedschool/notes-dbs#tabla)
      - [Registro](https://github.com/undefinedschool/notes-dbs#registro)
    - [Schema](https://github.com/undefinedschool/notes-dbs#schema)
    - [Tipos de datos](https://github.com/undefinedschool/notes-dbs#tipos-de-datos)
    - [Constraints](https://github.com/undefinedschool/notes-dbs#constraints)
      - [`NOT NULL`](https://github.com/undefinedschool/notes-dbs#not-null)
      - [`UNIQUE`](https://github.com/undefinedschool/notes-dbs#unique)
      - [`PRIMARY KEY`](https://github.com/undefinedschool/notes-dbs#primary-key)
      - [`FOREIGN KEY`](https://github.com/undefinedschool/notes-dbs#foreign-key)
      - [`CHECK`](https://github.com/undefinedschool/notes-dbs#check)
    - [Características](https://github.com/undefinedschool/notes-dbs#caracter%C3%ADsticas)
  - [DBMS](https://github.com/undefinedschool/notes-dbs#dbms)
  - [Server](https://github.com/undefinedschool/notes-dbs#server)
  - [Primary Key](https://github.com/undefinedschool/notes-dbs#primary-key-1)
    - [Natural keys](https://github.com/undefinedschool/notes-dbs#natural-keys)
    - [Synthetic keys](https://github.com/undefinedschool/notes-dbs#synthetic-keys)
  - [Foreign Key](https://github.com/undefinedschool/notes-dbs#foreign-key-1)
  - [Relaciones](https://github.com/undefinedschool/notes-dbs#relaciones)
  - [Join](https://github.com/undefinedschool/notes-dbs#join)
    - [`INNER JOIN`](https://github.com/undefinedschool/notes-dbs#inner-join)
    - [`LEFT JOIN`](https://github.com/undefinedschool/notes-dbs#left-join)
    - [`RIGHT JOIN`](https://github.com/undefinedschool/notes-dbs#right-join)
    - [`FULL (OUTER) JOIN`](https://github.com/undefinedschool/notes-dbs#full-outer-join)
    - [`SELF JOIN`](https://github.com/undefinedschool/notes-dbs#self-join)
    - [`CROSS JOIN`](https://github.com/undefinedschool/notes-dbs#cross-join)
  - [Union](https://github.com/undefinedschool/notes-dbs#union)
  - [Índices](https://github.com/undefinedschool/notes-dbs#%C3%ADndices)
    - [Cuándo usar índices](https://github.com/undefinedschool/notes-dbs#cu%C3%A1ndo-usar-%C3%ADndices)
  - [Transacciones](https://github.com/undefinedschool/notes-dbs#transacciones)
    - [ACID](https://github.com/undefinedschool/notes-dbs#acid)
  - [Normalización](https://github.com/undefinedschool/notes-dbs#normalizaci%C3%B3n)
- [Bases de Datos Relacionales (SQL) vs No Relacionales (NoSQL)](https://github.com/undefinedschool/notes-dbs#bases-de-datos-relacionales-sql-vs-no-relacionales-nosql)
- [ORMs](https://github.com/undefinedschool/notes-dbs#orms)
- [SQL](https://github.com/undefinedschool/notes-dbs#sql)
- [PostgreSQL](https://github.com/undefinedschool/notes-dbs#postgresql)
  - [Instalación](https://github.com/undefinedschool/notes-dbs#instalaci%C3%B3n)

---

## Base de Datos

Una base de datos es un **conjunto de datos relacionados entre si y almacenados sistemáticamente (agrupados o estructurados de cierta forma) para facilitar su posterior uso**.

Nos permiten guardar grandes cantidades de información de forma organizada, para que luego podamos encontrarla y utilizarla más fácilmente.

Una base de datos nos permite tener [_persistencia_](https://en.wikipedia.org/wiki/Persistence_(computer_science)) en los datos.

> Para más detalles, ver [Database - Wikipedia](https://en.wikipedia.org/wiki/Database)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

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

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

## Conceptos

### Base de datos relacional

Una base de datos **_relacional_** es una **colección** de 1 o más [**_tablas_**](https://github.com/undefinedschool/notes-dbs#tabla) (de 2 dimensiones), relacionadas entre sí.

**También se conoce a las bases de datos relacionales, más coloquialmente, como _Bases de Datos SQL_**, aunque es más correcto llamarlas _relacionales_, dado que hay DBs que utilizan otros lenguajes aparte de [_SQL_](https://github.com/undefinedschool/notes-sql/) para realizar consultas.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### Tabla

**Organizamos los datos en tablas**. Las tablas forman los _bloques fundamentales_ de los que se compone una DB.

> 👉 Para una guía visual, ver [A Shelfish Starter Guide to Databases](https://illustrated.dev/databases).

Cada tabla contiene **_filas_** y **_columnas_**, que a su vez contienen **datos**. En las tablas definimos la estructura y los [_tipos de datos_](https://github.com/undefinedschool/notes-dbs#tipos-de-datos) que estas van a almacenar, al definir las columnas de las mismas.

**Cada columna le da un nombre y un [tipo](https://github.com/undefinedschool/notes-dbs#tipos-de-datos) (texto, numérico, fecha, etc.) al dato almacenado** y cada fila ([_registro_](https://github.com/undefinedschool/notes-dbs#registro)) debe seguir esta estructura.

![](https://miro.medium.com/max/736/0*kBYg1f1lVSFE5cY6.PNG)

> 👉 **Al definir las columnas de una tabla, estamos estableciendo reglas sobre los datos que contiene una tabla**, que el [DBMS](https://github.com/undefinedschool/notes-dbs#dbms) se encargará de hacer cumplir.

Los datos de las diferentes tablas pueden estar, como dijimos antes, _relacionados entre sí_ (de ahí el nombre de bases de datos _relacionales_).

> 👉 **Las tablas y sus columnas deben definirse de antemano, antes de poder cargar datos en la DB.**

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

##### Registro

Vamos a llamar **_registro_** (_record_) a cada una de las filas de una [tabla](https://github.com/undefinedschool/notes-dbs#tabla), que representan una unidad de información.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### Schema

La forma y organización de los datos dentro de una base de datos, se conoce como **_schema_**. Representa la colección y asociación de [tablas](https://github.com/undefinedschool/notes-dbs#tabla).

👉 En una _base de datos relacional_, **el _schema_ debe definirse antes de poder interactuar con la misma**. Todos los _registros_ de una base de datos relacional deben seguir el esquema definido.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### Tipos de datos

**En bases de datos relacionales** como Postgres, **tenemos que especificar el tipo de datos que vamos a almacenar en un determinado campo**. Algunos de los tipos de datos que nos provee Postgres son:

- `SERIAL`: entero _auto-incrementable_, usualmente utilizado para IDs.
- `TEXT`: fragmentos de texto (muy similar a `VARCHAR`).
- `VARCHAR`: caracteres de longitud variable.
- `CHAR`: caracteres de longitud fija.
- `BOOLEAN`: un booleano.
- `INTEGER`: un entero.
- `REAL`: un número de punto flotante (por ejemplo, `3.141593`).
- `DECIMAL, NUMERIC`: valores numéricos de punto flotante con una precisión definida.
- `DATE`: para almacenar fechas.
- `MONEY`: valores numéricos de punto flotante para representar dinero.
- `ARRAY`: un array de otros datos (poco usual).

Para leer sobre la diferencia entre los tipos `TEXT`, `VARCHAR` y `CHAR`, ver [este post de _StackOverflow_](https://stackoverflow.com/questions/4848964/postgresql-difference-between-text-and-varchar-character-varying).

Para más detalles, ver [_PostgreSQL Data Types_](https://www.postgresql.org/docs/12/datatype.html)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### Constraints

Las _constraints_ son ciertas restricciones aplicadas sobre una tabla, creadas implícita o explícitamente por el [_schema_](https://github.com/undefinedschool/notes-dbs#schema). _Constraints_ son una parte clave del [_DDL_](https://github.com/undefinedschool/notes-sql/blob/master/README.md#ddl-comandos-para-modificar-el-schema). 

> 👉 **Violar una _constraint_ va a generar un error de parte de la base de datos y (generalmente) abortar la operación**.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

##### `NOT NULL`

Establece que al crear o actualizar un registro, el valor de un campo **no puede ser `NULL`**.

```SQL
CREATE TABLE college_students (
  id SERIAL PRIMARY KEY,
  last_name VARCHAR(50),
  first_name VARCHAR(50),
  major VARCHAR(50) NOT NULL
);
```

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

##### `UNIQUE`

Establece que **el valor de un campo para un registro debe ser único en la tabla**.

```SQL
CREATE TABLE phonebook (
  id SERIAL PRIMARY KEY,
  last_name VARCHAR(50),
  first_name VARCHAR(50),
  phone_number VARCHAR(7) UNIQUE
);
```

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

##### `PRIMARY KEY`

Una [_Primary Key_](https://github.com/undefinedschool/notes-dbs#primary-key-1) identifica un registro, el cual tiene a su vez, la propiedad de ser tanto [`UNIQUE`](https://github.com/undefinedschool/notes-dbs#unique) como [`NOT NULL`](https://github.com/undefinedschool/notes-dbs#not-null).

```SQL
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  first_name TEXT,
  last_name TEXT
);
```

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

##### `FOREIGN KEY`

Asocia los datos de una columna a los de otra columna, en una tabla diferente. 

> 👉 **La base de datos se asegura de que los datos de la [_Foreign key_](https://github.com/undefinedschool/notes-dbs#foreign-key-1) existan en la tabla que la _Foreign Key_ referencia**. 

```SQL
CREATE TABLE people (
  id SERIAL PRIMARY KEY,
  first_name TEXT,
  last_name TEXT
);

CREATE TABLE interests (
  id SERIAL PRIMARY KEY,
  interest TEXT,
  people_id INTEGER REFERENCES people
);
```

En el ejemplo anterior, los valores de la columna `people_id` referencian al `id` de la tabla `people`.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

##### `CHECK`

Recibe una expresión que debe evaluar a `true` para que la operación se concrete.

```SQL
CREATE TABLE products (
  product_no SERIAL PRIMARY KEY,
  name TEXT,
  price NUMERIC CHECK (price > 0)
);
```

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### Características

- datos organizados en tablas, relacionadas entre sí
- _schema_ estricto, definido al comienzo
- las columnas de cada tabla tienen [tipos de datos](https://github.com/undefinedschool/notes-dbs#tipos-de-datos) definidos

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### DBMS

Oracle, MySQL, PostgreSQL, MongoDB, etc. _no son bases de datos en si, sino **Database Management Systems** (DBMS)_. Un _DBMS_ es un software que utilizamos para crear y administrar bases de datos, permitiéndonos acceder a los datos de forma rápida y estructurada.

> 👉 **Un _DBMS_ puede administrar 1 o varias bases de datos**.

En el caso de las bases de datos relacionales, utilizamos más específicamente, **Relational Database Management Systems** o _RDBMS_ (subcategoría dentro de los DBMS). Los principios y conceptos que usaremos aplican para las diferentes variantes mencionadas anteriormente.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### Server

La mayoría de las **bases de datos** siguen la **arquitectura _cliente-servidor_**.

Es en el _server_ donde se encuentran alojados los datos.

El **_server_ de la base de datos** además, **se encarga de correr el _DBMS_ (Database Management System)**. A través de un _cliente_, nos conectamos al _server_ de la DB, para crear nuestra base de datos e interactuar con ella.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### Primary Key

Es un valor de una columna (o conjunto de columnas) que identifica **unívocamente** (1 y sólo 1) cada registro (o fila) de una tabla. Generalmente se corresponde con el campo `id` de la tabla.

> 👉 **Toda tabla de una base de datos relacional debería tener definida una Primary Key**.

[![Primary Key](https://img.youtube.com/vi/E3Bs3H14C8Y/0.jpg)](https://www.youtube.com/watch?v=E3Bs3H14C8Y)
> Ver [Primary Key](https://www.youtube.com/watch?v=E3Bs3H14C8Y)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### Natural keys

Se conocen como _natural keys_ (claves naturales) a las _Primary Keys_ que **se generan a partir de los datos de una tabla**.

Son **valores de columnas _naturalmente_ únicos**, que tienen relación con el resto de las columnas de un registro dado. Por ejemplo, el email, número de seguridad social, número de pasaporte, ISBN, etc.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### Synthetic keys

Se conocen como _synthetic keys_ o _surrogate keys_ (claves sustitutas) a las _Primary Keys_ **generadas por la base de datos al insertar un nuevo registro**: estas no derivan de los datos de la tabla, es decir, es una columna extra que agregamos sólo con este propósito.

Se trata generalmente de valores numéricos, como pueden ser `product_id` o `customer_id`, etc. 

> Para más detalles, ver [Natural Key vs Surrogate Key](https://www.databasejournal.com/features/mssql/article.php/3922066/SQL-Server-Natural-Key-Verses-Surrogate-Key.htm).

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### Foreign Key

Es un valor o campo (o grupo de campos) que identifica **unívocamente** un registro (fila) de otra tabla, es decir, hace referencia a una columna de otra tabla que tenga la _constraint_ [`UNIQUE`](https://github.com/undefinedschool/notes-dbs#unique) (generalmente será una [**Primary Key**](https://github.com/undefinedschool/notes-dbs#primary-key-1)).

El tipo de dato es indistinto, lo importante es que la columna que elijamos como _Primary Key_ no contenga valores repetidos.

> 👉 **Una tabla puede contener múltiples Foreign Keys**, dependiendo de sus relaciones con otras tablas.

[![Foreign Key](https://img.youtube.com/vi/5HQzigiRb5c/0.jpg)](https://www.youtube.com/watch?v=5HQzigiRb5c)
> Ver [Foreign Key](https://www.youtube.com/watch?v=5HQzigiRb5c)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### Relaciones

> 👉 **Ver [_Bases de Datos - Relaciones_](https://github.com/undefinedschool/notes-dbs-relationships/)**.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### Join

Cuando necesitamos combinar datos de una (_self join_) o más tablas, utilizamos `JOIN`, basándonos en las columnas en común entre las tablas. Las columnas en común suelen ser la [_Primary Key_](https://github.com/undefinedschool/notes-dbs#primary-key-1) de la primer tabla y la [_Foreign Key_](https://github.com/undefinedschool/notes-dbs#foreign-key-1) de la segunda tabla.

[![SQL Joins Explained](https://img.youtube.com/vi/9yeOJ0ZMUYw/0.jpg)](https://www.youtube.com/watch?v=9yeOJ0ZMUYw)
> Ver [SQL Joins Explained](https://www.youtube.com/watch?v=9yeOJ0ZMUYw)

![Joins](https://i.imgur.com/TXBDSyI.png)

> 👉 Para ver la sintaxis y cómo escribir los diferentes tipos de joins, **ver [_Bases de Datos - SQL (Joins)_](https://github.com/undefinedschool/notes-sql/#join)**.

> 👉 Para un resumen de los diferentes tipos de Joins, **ver [_PostgreSQL Joins_](https://www.postgresqltutorial.com/postgresql-joins/)**.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### `INNER JOIN`

![Inner Join](https://upload.wikimedia.org/wikipedia/commons/thumb/1/18/SQL_Join_-_07_A_Inner_Join_B.svg/440px-SQL_Join_-_07_A_Inner_Join_B.svg.png)

> 👉 Ver [**PostgreSQL INNER JOIN**](https://www.postgresqltutorial.com/postgresql-inner-join/)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### `LEFT JOIN`

![Left Join](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/SQL_Join_-_01_A_Left_Join_B.svg/440px-SQL_Join_-_01_A_Left_Join_B.svg.png)

> 👉 Ver [**PostgreSQL LEFT JOIN**](https://www.postgresqltutorial.com/postgresql-left-join/)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### `RIGHT JOIN`

![Right Join](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5f/SQL_Join_-_03_A_Right_Join_B.svg/468px-SQL_Join_-_03_A_Right_Join_B.svg.png)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### `FULL (OUTER) JOIN`

![Full Join](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3d/SQL_Join_-_05b_A_Full_Join_B.svg/440px-SQL_Join_-_05b_A_Full_Join_B.svg.png)

> 👉 Ver [**PostgreSQL FULL (OUTER) JOIN**](https://www.postgresqltutorial.com/postgresql-full-outer-join/)

> **Nota:** no confundir con [`UNION`](https://www.quora.com/What-is-the-difference-between-full-outer-join-and-union-in-SQL/answer/Ashutosh-Tripathy-10) <sup id="cite_ref-1"><a href="#cite_note-1">[1]</a></sup>.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### `SELF JOIN`

> 👉 Ver [**PostgreSQL SELF JOIN**](https://www.postgresqltutorial.com/postgresql-self-join/)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### `CROSS JOIN`

> 👉 Ver [**PostgreSQL CROSS JOIN**](https://www.postgresqltutorial.com/postgresql-cross-join/)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### Union

> 👉 Ver [**PostgreSQL UNION**](https://www.postgresqltutorial.com/postgresql-union/)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### Índices

Cuando buscamos datos en una tabla (`SELECT, WHERE`), la base de datos tiene que mirar registro por registro para encontrar aquellos que coincidan con los criterios especificados. Si tenemos un gran volumen de datos, esta operación puede ser _muy lenta_.

Para solucionar este problema existen los **índices**, que permiten que nuestras _queries_ sean rápidas y eficientes, mejorando en consecuencia la _performance_.

Podemos _indexar_ tablas por 1 o más columnas. **Una tabla puede tener más de un índice**.

> ⚠️ **Agregar índices a una DB requiere espacio extra de almacenamiento (espacio en disco), aparte del espacio necesario para almacenar los datos**. Además, cada vez que agreguemos un nuevo registro a una tabla, se actualizarán los índices correspondientes, haciendo esta operación más costosa. Por lo tanto, hay que utilizarlos con la precaución y planificación necesaria.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### Cuándo usar índices

- cuando tenemos más operaciones de lectura que de escritura
- espacio en disco suficiente
- alta cardinalidad de un atributo (como PKs)
- alta frecuencia de búsqueda/filtrado/ordenamiento

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### Transacciones

Una _transacción_ es una **unidad combinada de trabajo**, una **serie de pasos que debemos ejecutar en cierto orden y que se considera exitosa si y sólo si todos los pasos se ejecutan correctamente**. Si algún paso falla, la transacción entera se cancela y se revierten todos los pasos individuales, volviendo al estado original, previo a la operación.

> 👉 Ver [**PostgreSQL Transaction**](https://www.postgresqltutorial.com/postgresql-transaction/) y más detalles en la [documentación de Postgres](https://www.postgresql.org/docs/current/tutorial-transactions.html)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

#### ACID

Es un acrónimo que define qué características debe cumplir una transacción, para garantizar la integridad, consistencia y seguridad de los datos durante una operación.

- **A**: Atómica (atomic). Se refiere a que es una unidad de trabajo _indivisible_ (aunque hoy en día sabemos que los átomos pueden dividirse pero quedó el nombre), la transacción se realiza completa o se revierte.
- **C**: Consistente (consistent). Significa que cualquier transacción debe llevar a la db de un estado válido a otro estado válido (los estados intermedios no son visibles), según las reglas definidas por el DBMS.
- **I**: Aislada (isolated). Durante una transacción, los datos involucrados se encuentran aislados, no pudiendo ser accedidos y/o modificados por otra operación.
- **D**: Persistente (durable). Si la transacción se realiza de forma exitosa, debe estar garantizada su persistencia en la db (por ejemplo, si inmediatamente ocurre algún error después).

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

### Normalización

(WIP)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

## Bases de Datos Relacionales (SQL) vs No Relacionales (NoSQL)

(WIP)

Para un resumen de las diferencias, ver [_SQL vs NoSQL or MySQL vs MongoDB_](https://www.youtube.com/watch?v=ZS_kXvOeQ5Y)

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

## ORMs

Los ORMs (Object Relational Mapping) nos permiten _mapear_ entidades de bases de datos (relacionales) a objetos nativos del lenguaje que estemos utilizando en el backend (por ejemplo JS con Node).

Introducen una capa intermedia entre la db y el código del backend (_data layer_), que se encarga de realizar esta conversión por nosotros y nos permite interactuar con la DB a través de los objetos y métodos que nos provee.

### Pros

- Siempre trabajamos con objetos nativos del lenguaje
- Reduce la cantidad de código que tenemos que escribir (principalmente las queries)
- Ahorra trabajo repetitivo
- Facilita el testing

### Cons

- Es una capa más de abstracción
- Agrega más conceptos para aprender
- Tenemos menos control
- Algunas queries se complejizan bastante
- Dificulta entender la lógica detrás de las operaciones que estamos realizando
- Dificulta el mantenimiento (por ejemplo compatibilidad con diferentes DMBS) y debugging
- Impacto en la performance de las operaciones vs _raw SQL_

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

## SQL

Es el lenguaje que vamos a utilizar para hacer consultas e interactuar con una _base de datos relacional_.

👉 Ver [notas de SQL](https://github.com/undefinedschool/notes-sql/).

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

## PostgreSQL

[PostgreSQL](https://www.postgresql.org), también conocido como _Postgres_ a secas, es un [_RDBMS_](https://www.codecademy.com/articles/what-is-rdbms-sql) para bases de datos relacionales, de propósito general, open-source y gratuito, tanto para uso personal como comercial. Se trata también de una de las bases de datos relacionales más avanzadas y populares que existen.

Provee soporte para la mayor parte del _standard SQL_ y agrega algunas features propias (incluso [podemos utilizar JavaScript para crear funciones _custom_](https://blog.heroku.com/javascript_in_your_postgres)).

Al tratarse de una _base de datos relacional_, vamos a urilizar SQL para realizar _queries_ con los datos almacenados en esta.

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

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

[↑ Ir al inicio](https://github.com/undefinedschool/notes-dbs#contenido)

---

<sup id="cite_note-1"><a href="#cite_ref-1">1</a></sup> Ver [Cuándo usar `UNION`](https://www.quora.com/When-would-you-use-UNION-in-SQL).
