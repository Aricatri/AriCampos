#Algunas definiciones
<aside>
💡

> Herramientas de visualización de datos como plataformas de (**Tableau, Power BI o QlikView**) nos permitirán crear visualizaciones creativas.
</aside>

# Tipo de bases de datos

- [ ] MySQL
- [ ] PostgreSQL
- [ ] SQL Server
- [ ] Oracle

## Hablemos sobre los roles que podemos encontrar en el trabajo

Un **administrador de base de datos** determina el proceso de modelamiento y nos ayuda a buscar la base de datos, nos ayuda a determinar la base de información, crea backups y se asegura de que los datos funcionen siempre eficientemente.

Un **analista de datos** suele estar trabajando de la mano con las personas del negocio y tiene un impacto directo en el mismo.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/866ddf2c-d17e-43d0-91f2-85999a2b5b9c/a2c85aa5-95c9-49cd-9659-9b3fcde9f846/image.png)

### Hablemos de las entidades

> Representa el concepto de negocio en el cual debemos almacenar información.

Si deseas usar un nombre descriptivo más largo, considera descomponerlo en segmentos más cortos y significativos. Aquí tienes un par de sugerencias:

- Usa una abreviatura: `Dep_Origen` en lugar de `departamento de origen` para el atributo.

### Hablemos de la relación

Vínculos que tendremos entre las entidades de nuestro modelo de datos, comparten una llave foránea.

### Hablemos sobre el modelo conceptual

Se construye a partir del análisis de requerimientos; busca la lógica para poder trabajar y es una representación gráfica con mayor detalle de las entidades.

## Hablemos sobre la llave primaria (PK)

Es nuestro único identificador de nuestra entidad principal.

## Hablemos sobre nuestra llave foránea (FK)

La llave foránea es la referencia de nuestra llave primaria.

## Hablemos sobre la normalización de bases de datos

1. **Primera Forma Normal (1FN)**

    Se eliminan las columnas repetidas y se colocan las tablas separadas. Si se puede crear una tabla adicional, se recomienda. Tus atributos deben buscar ser atómicos.

    > ¿Los datos que se me van a brindar los puedo seguir dividiendo?

2. **Segunda Forma Normal (2FN)**

    Las columnas que no dependen exclusivamente de la PK se tienen que separar en otra tabla (no dependencias parciales).

    Todas las tablas deben tener una llave primaria.

    > ¿Este campo depende de nuestra llave primaria?

    Si no se cumple esta sentencia, se puede separar una tabla adicional.

3. **Tercera Forma Normal (3FN)**

    Los valores de la columna de la tabla no dependerán de otras columnas. Se refiere a que si se cambia una variable de una entidad, no debería variar el sentido de manera general.

## ¿Cómo hacemos nuestro análisis de requerimientos?

1. Diseñamos las entidades independientes (mientras más entidades, más fácil de poder trabajarlo después).

# Tipo de datos

[Data types (Transact-SQL) - SQL Server](https://learn.microsoft.com/en-us/sql/t-sql/data-types/data-types-transact-sql?view=sql-server-ver16)

| Tipo de dato     | Descripción |
|-------------------|-------------|
| char              |             |
| varchar           |             |
| text              |             |
| int               |             |
| decimal           |             |
| numeric           |             |
| float             |             |
| date              |             |
| datetime          |             |
| smalldatetime     |             |

# Constraints

| Constraint       | Significado |
|-------------------|-------------|
| primary key       | Permite identificar de manera única el registro de una base de datos. |
| foreign key       | Permite definir una relación de referencia (FK). |
| not null          | En la columna nos aseguramos que no se permitan ingresar datos NULOS. |
| unique            | Nos aseguramos que no exista un dato igual. |
| check             | Nos aseguramos que se cumpla una específica condición previamente planeada. |
| default           | Ingresa un dato por defecto cuando no hay dato para registrar. |
| index             | Se usa para realizar búsquedas más rápidas. |

# Cómo creamos las tablas

```sql
CREATE TABLE agente (
    id_agente INT PRIMARY KEY,
    nombre VARCHAR(20),
    especialidad VARCHAR(30)
);

CREATE TABLE agente_poliza (
    id_agente_poliza INT PRIMARY KEY,
    id_agente INT,
    num_poliza INT,
    por_comision DECIMAL(5,3),
    FOREIGN KEY (id_agente) REFERENCES agente(id_agente),
    FOREIGN KEY (num_poliza) REFERENCES poliza(num_poliza)
);
