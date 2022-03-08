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

-Superclave

Conjunto de uno o más atributos que, tomados colectivamente, permiten identificar de forma unívoca a la ocurrencia de una entidad. Se utiliza generalmente en las tablas de relación.

### Caso de ejemplo: UBER

![Caso-uber-modelo-e-r](https://user-images.githubusercontent.com/75231007/157333739-fe592d7a-1ee1-4fbf-a933-3c758eefb29a.png)

### Caso de ejemplo: UBER

![Caso-estudio-Playground-diagrama-e-r](https://user-images.githubusercontent.com/75231007/157337296-04f7dec0-baec-40f4-8205-9adf5135a3a7.png)

## Referencias

[1] - [Tecnologías-información:link:](https://www.tecnologias-informacion.com/modelos-datos.html)

[2] - [Erwin:link:](https://www.erwin.com/mx-es/solutions/data-modeling/physical.aspx)

