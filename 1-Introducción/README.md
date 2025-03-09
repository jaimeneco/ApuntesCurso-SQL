# ----------------
# INTRODUCCIÓN:
# ----------------
## ¿Qué es SQL?
- Es álgebra relacional y nos permite guardar y manipular bien la información.
- Structured Query Language (Lenguaje de consultas estructuradas)
- Lenguaje de programación que nos permite trabajar con bases de datos relacionales.
- Lenguaje estandarizado(lo aprendemos una sola vez y lo podemos utilizar para todo lo demás) y el mayor utilizado en todo el mundo para manejar bases de datos.
- Sabiendo SQL vas a poder saber cualquier gestor de bases de datos: PostgreSQL, MySQL, Oracle database... 

## ¿Qué podemos hacer con SQL?
- Podemos crear, modificar, actualizar, eliminar, administrar bases de datos.
- Podemos consultar datos concretos y trabajar con ellos.

## Fundamentos de las bases de datos:
Iremos de los conceptos más abstractos a los más tangibles.

- Entidad: es una representación de algo.
    *Ejemplo: CASA
        -Atributos de CASA: tamaño, dirección, ambientes, ubicación, precio, propietario...
        -Atributos Simples: compuestos por datos únicos.(Precio: 100.000€)
        -Atributos Compuestos: compuestos por atributos más pequeños.(Ambiente: un comedor y una cocina tienen diferentes atributos simples que los componen.)
        -Atributos Multivalor: son más de uno. (En una casa hay más de una ventana, más de una puerta y, por ejemplo, más de un ambiente).
        -Atributos Derivados: los que conocemos y sabemos por otros atributos. (La antigüedad de una casa se puede saber por el año de construcción de la casa).

- KEY: es un atributo que es la forma única de poder identificar algo. (Siguiendo el ejemplo: Una casa tiene un id de vivienda en el registro)

- Ejemplo con otra entidad: PERSONA
    -Atributos: altura, edad, DNI (key), nombre, hobbies.

## ¿Qué es una base de datos?
- No podemos operar con un código SQL sin un gestor de bases de datos.
- Es un conjunto de información  organizada y estructurada para que la podamos manipular e interactuar de forma eficaz y eficiente.
- Si guardamos los datos de una PERSONA:
        - Info básica (Nombre, apellido, edad, DNI(key))
        - Citas médicas (Turno, motivo, horario DNI(key))

