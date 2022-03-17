# Bases de datos

## Introducción a las bases de datos

### ¿Qué es una base de datos?

Es un conjunto de datos almacenados que pertenecen a un mismo contexto y que están organizados con algún propósito particular. Nos permiten, entre otras cosas:

- Almacenar datos
- Acceder a los datos
- Manipularlos y combinarlos
- Analizar datos
- Evitan la redudancia de datos*
- Conservan la integridad de los datos*

### Tipos de bases de datos

Existen dos tipos: relacionales y no relaciones.

### ¿Base de datos o archivos planos?

Las bases de datos son una mejor opción por encima de los archivos planos debido a dos razones principales.

1. **Redundancia**. Al manejar archivos diferentes es normal repetir campos en común para múltiples archivos lo que deriva en la repetición de una porción de la información en cada archivo.
   
2. **Consistencia e integridad de datos**. Cuadno se actualiza un dato en un archivo, dicho cambio no se refleja en los otros archivos, la información queda inconsistente y se pierde la integridad de los datos.

### Motores de bases de datos

Sistema de gestión de base de datos. Capa de software que almacena los datos y los protege. Poseen distintas capacidades: consistencia de datos, integridad, seguridad, respaldo, acceso concurrente, tiempo de respuesta.

Todos manejan un estándar en común: **SQL**. Con este lenuaje podemos:
- Crear bases de datos
- Modificar
- Escribir datos
- Consultar datos

_Saber usar SQL garantiza poder trabajar con todos los motores de bases de datos._

### Modelos de bases de datos

#### Modelado de datos

Es una manera de estructurar y organizar los datos para que se puedan utilizar fácilmente por las bases de datos.

Entre sus beneficios están:
- Registrar los requerimientos del negocio
- Descomponer un proceso complejo
- Observación de patrones
- Condiciona la comunicación dentro y entre organizaciones

Existen 3 tipos de modelos:

#### Modelo Conceptual

Identifica las relaciones de más alto nivel entre las diferentes entidades.Las características del modelo conceptual de datos incluyen. En este se basa el **modelo Entidad-Relación**:
- Incluye las entidades importantes y las relaciones entre ellas. [1] 
- No se especifica ningún atributo.
- No se especifica ninguna clave principal.

#### Modelo lógico

Describe los datos con el mayor detalle posible, independientemente de cómo se implementarán físicamente en la base de datos. Las características de un modelo de datos lógicos incluyen [1]:

- Incluye todas las entidades y relaciones entre ellos.
- Todos los atributos para cada entidad están especificados.
- La clave principal para cada entidad está especificada.
- Se especifican las claves externas (claves que identifican la relación entre diferentes entidades).

Explica el negocio y describe el _qué_. Es independiente de la implementación.

#### Modelo físico

Un modelo de datos físico introduce el contexto específico de la base de datos que falta en los modelos de datos lógicos y conceptuales. Representa las tablas, las columnas, los tipos de datos, las vistas, las restricciones, los índices y los procedimientos dentro de la base de datos o la información comunicada durante los procesos informáticos. Los modelos de datos físicos deben armarse en relación con un sistema de administración de bases de datos (DBMS) específico, así como con los requisitos específicos de los procesos que operan sobre la base de los datos [2].

Explica técnicamente cómo se van a almacenar los datos. Explica la implementación en el sistema de bases de datos. Describe el _cómo_.

*Arquitectura cliente-servidor: MySQL Server - MySQL Workbench*

## Modelado de bases de datos

Como vimos es el primer paso dentro de una implementación de una base de datos. Es importante porque no solo vamos a plasmar los requerimientos de aplicaciones sino que también vamos a traducir las reglas o restricciones que deben cumplir los datos.

### Modelo entidad-relación

El modelo de datos entidad-relación se basa en una percepción del mundo real, que consiste en un conjunto de objetos básicos llamados entidades y de relaciones entre ellos. Se emplea para interpretar, especificar y documentar los requerimientos para los sistemas de bases de datos.

#### Entidades

Una entidad es un objeto, real o abstracto, acerca del cual se recoge información de interés para la base de datos. Se representan usando **rectángulos**.

- Entidades fuertes: existen por sí mismas (ej: empleados).
- Entidades débiles: su existencia depende de otra entidad (ej: hijos de empleados).

**Ocurrencia de entidad**: es una _instancia_ de la entidad. Por ejemplo: si tenemos la entidad persona, una ocurrencia puede ser Pepe Pérez.

#### Atributos

Los atributos describen las características de una entidad.  Por ejemplo: para la entidad Cliente existirían atributos como nombre, domicilio, teléfono. Para representarlos **se listan dentro del rectángulo** de la entidad.

Tipos:
- Atributo con simple valor: es un valor simple.
- Atributo multivalor: corresponde a una serie de valores.
- Atributo derivado: su valor se puede derivar otro atributo afin.
- Atributo clave: identifica una ocurrencia en particular, diferencia los ítems entre sí.
- Atributo nulo: cuando el valor es desconocido o no tiene valor.

**Datos**: son los posibles valores que pueden tener los atributos. 

#### Convención de nombres

Para nombrar entidades y atributos se debe utilizar sustantivos en singular o plural. No se puede utilizar eñes, espacios o acentos. Si el nombre lleva más de una palabra se debe usar snake case o camel case.

#### Claves

- Clave candidata

Aquella que identifica de forma unívoca a cada ocurrencia. Dichas claves son candidatas a ser clave primaria. Se pueden definir varias y luego seleccionar la más adecuada.

- Clave primaria

Se compone de uno o más atributos cuyos valores identifican unívocamente a cada ocurrencia. No tiene valores nulos ni repetidos. Identifica cada fila de una tabla de forma única. Se representa escribiéndola en negrita seguido de las iniciales PK (Primary Key) entre paréntesis.

- Superclave

Conjunto de uno o más atributos que, tomados colectivamente, permiten identificar de forma unívoca a la ocurrencia de una entidad. Se utiliza generalmente en las tablas de relación.

### Caso de ejemplo: UBER

![Caso-uber-modelo-e-r](https://user-images.githubusercontent.com/75231007/157333739-fe592d7a-1ee1-4fbf-a933-3c758eefb29a.png)

### Caso de ejemplo: Playground


![Caso-estudio-Playground-diagrama-e-r](https://user-images.githubusercontent.com/75231007/157337296-04f7dec0-baec-40f4-8205-9adf5135a3a7.png)
_**Versión 1**: se definen entidades y atributos._

![Caso-estudio-Playground-diagrama-e-r (1)](https://user-images.githubusercontent.com/75231007/157719740-e3ebdc43-d63e-4a54-af90-10d4682562d2.png)

_**Versión 2**: se agregaron los tipos de datos._

### Tipos de datos [MySQL]

Los atributos de la base de datos deben tener un tipo de dato en específico. Cuanto más precisos seamos en su selección, mejor performance tendrá MySQL.


- Datos de tipo texto: almacenan alfanuméricos y símbolos
- Datos de tipo numérico: existen enteros y decimales.
- Datos de tipo fecha: MySQL no comprueba de forma estricta si una fecha es válida. 👀
- Datos de tipo boolean: MySQL guarda los booleanos como 0 o como 1, por performance no se recomienda su uso:skull:. Es preferible usar _TINYINT_ para su representación.  


| Tipo        | Nombre      | Uso         | [Min,Máx]    |
| ----------- | ----------- | ----------- | ---------- |
| Texto       | CHAR(n)     | Cadenas de texto de longitud poco variable | [1, 255]
| Texto   | VARCHAR(n) | Cadenas de texto de longitud muy variable | [1, 21.845]
| Texto   | TINYTEXT |  | [0, 255]
| Texto   | MEDIUMTEXT |  | [0, 16.777.215]
| Texto   | TEXT |  | [0, 4.294.967.295]
| Texto   | LONGTEXT |  | [0, 18.446.744.073.709.551.615]
| Numérico   | TINYINT |  | [0, 255]
| Numérico   | SMALLINT |  | [0, 65.535]
| Numérico   | MEDIUMINT |  | [0, 16.777.215]
| Numérico   | INT |  | [0, 4.294.967.295]
| Numérico   | BIGINT |  | [0, 18.446.744.073.709.551.615]
| Numérico   | FLOAT(n,d) | Almacenan números de coma flotante pequeño | n[1,24]; d[0,7]
| Numérico   | DOUBLE(n,d) | Almacenan números de coma flotante grande | n[25,53]; d[0,15]
| Fecha   | DATE | Almacena solo la fecha en formato YYYY-MM-DD | ['0001-01-01', '9999-12-31']
| Fecha   | TIME | Almacena solamente la hora en formato HH:MM:SS | ['00:00:00', '23:59:59']
| Fecha   | DATETIME | Almacena la fecha y la hora en formato YYYY-MM-DD HH:MM:SS | ['0001-01-01 00:00:00', '9999-12-31 23:59:59']

### Relaciones

Las relaciones indican cómo se van a relacionar dos tablas. Existen tres tipos de relaciones. Para identificar correctamente las relaciones sirve plantear ejemplos concretos para ver cómo interactuan las dos entidades. Es decir, podemos preguntarnos _¿cuántas entidad1 puede tener la entidad2? y viceversa_.

La **cardinalidad** se refiere al tipo de relación (1:1, 1:M, N:M).

- Uno a uno (1:1): Se coloca la clave primaria de una entidad en la tabla de la otra entidad y se indica que es una clave foránea (FK). 

- Uno a muchos (1:N): Se coloca la clave primaria de la entidad _del lado 1_ en la tabla de _muchos_. 

- Muchos a muchos (N:M): Se crea una nueva tabla (intermedia) que se suele nombrar componiendo los nombres de las dos tablas iniciales a relacionar; como atributos se le agrega un identificador (PK) y como llaves foráneas se pasarán las llaves primarias de las entidades iniciales.

Tipo de flechas
![image](https://user-images.githubusercontent.com/75231007/158664782-cf322004-4886-4a9c-82d9-6837989be3fa.png)

## SQL 

Las sentencias SQL se agrupan en dos categorías según su funcionalidad o propósito:

- Lenguaje de definición de datos (DDL): son sentencias para la creación de tablas y registros. Es decir, se utilizan para realizar modificaciones sobre la estructura de la base de datos.

- Lenguaje de manipulación de datos (DML): son sentencias para la consulta, actualización y borrado de datos. Es decir, se utilizan para realizar consultas y modificaciones sobre los registros almacenados dentro de cada una de las tablas.

### Create, Drop, Alter

- Crear una base de datos:

```
CREATE DATABASE miprimerabasededatos;
USE miprimerabasededatos;
```

- Crear una tabla:

```
CREATE TABLE nombre_de_la_tabla (
    nombre_de_la_columna_1 TIPO_DE_DATO CONSTRAINT,
    nombre_de_la_columna_2 TIPO_DE_DATO CONSTRAINT
)
```
**Llaves foráneas**: Cuando creemos una columna que contenga una id foránea, será necesario usar la sentencia FOREIGN KEY para aclarar a qué tabla y a qué columna hace referencia aquel dato.

- Borrar tabla (DROP table):

```
DROP TABLE IF EXIST nombreTabla;
```

- Alterar una tabla existente (ALTER table), maneja 3 comandos:
   - ADD: para agregar una columna. 
   
      ```
      ALTER TABLE peliculas
      ADD rating DECIMAL(3,1) NOT NULL;
      ```
   
   - MODIFY: para modificar una columna.
      
      ```
      ALTER TABLE peliculas
      MODIFY rating DECIMAL(4,1) NOT NULL;
      ```
   
   - DROP: para borrar una columna.
      
      ```
      ALTER TABLE peliculas
      DROP rating;
      ```
     
### Insert, update, delete

- Insertar datos a una tabla (INSERT). Existen dos formas:
   - Insertando datos en todas las columnas: Si estamos insertando datos en todas las columnas, no hace falta aclarar los nombres de cada columna. Sin embargo, el orden en el  que insertemos los valores, deberá ser el mismo orden que tengan asignadas las columnas en la tabla. 
      
      ```
      INSERT INTO table_name (columna_1, columna_2, columna_3, ...)
      VALUES (valor_1, valor_2, valor_3, ...);
      ```
      
   - Insertando datos en las columnas que especifiquemos.

      ```
      INSERT INTO table_name (columnaX, columnaY) 
      VALUES (valor_x, valor_y);
      ```

- Modificar datos existentes en una tabla (UPDATE), al igual que con DELETE, es importante no olvidar el WHERE cuando escribimos la sentencia, aclarando la condición. 

```
UPDATE nombre_tabla
SET columna_1 = valor_1, columna_2 = valor_2, ...
WHERE condición;
```

- Eliminar datos de una tabla (DELETE):

```
DELETE FROM nombre_tabla WHERE condición;
```

## Referencias

[1] - [Tecnologías-información:link:](https://www.tecnologias-informacion.com/modelos-datos.html)

[2] - [Erwin:link:](https://www.erwin.com/mx-es/solutions/data-modeling/physical.aspx)

