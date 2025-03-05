# -OPERADORES-

## OPERADOR BETWEEN y NOT BETWEEN: (se pueden juntar con los operadores de AND, OR y NOT)
- Para comparar rangos numéricos. Devolver productos entre 20 y 40 euros. Además que sea de la categoría 6.
- Incluye los valores límite (BETWEEN 2 AND 4, incluye 2, 3 y 4). 
- El primer valor siempre debe ser el menor.
- Se debe usar con valores que sean compatibles, no puedes comparar una fecha con un nombre.
```SQL
select * FROM Products WHERE Price BETWEEN 20 AND 40

select * FROM Products WHERE Price BETWEEN 20 AND 40 AND CategoryID = 6

select * FROM Products WHERE Price NOT BETWEEN 20 AND 40 AND CategoryID = 6   // Obtenemos resultado diferente al anterior.

select * FROM Employees WHERE BirthDate BETWEEN "1950-0-1" AND "1960-0-1" // Empleados que hayan nacido entre los años 1950 y los 1960, ambos incluídos.
```

## OPERADOR LIKE y NOT LIKE:(se pueden juntar con los operadores de AND, OR y NOT)
- Es un operador de comparación. Se utiliza para buscar y filtrar registros en función de ciertos patrones de cadenas de texto.
- Funciona parecido a poner un igual (=), pero tienen algunas diferencias.

- El LIKE tiene comodines:
    - % : que contenga alguna letra, al principio, al final o en el medio.
    - _ : si buscamos Fuller pero sin buscarlo al completo. Se que se llama Full...algo pero no recuerdo completo. Busco LIKE "Full_ _"

```SQL
Select * FROM Employees WHERE LastName LIKE "Fuller"

Select * FROM Employees WHERE LastName LIKE "F%"    /// Que tenga la F al princiopio LastName.
Select * FROM Employees WHERE LastName LIKE "%r"    /// Que tenga la r al final del LastName.
Select * FROM Employees WHERE LastName LIKE "%r%"   /// Que tenga la r en cualquier lado del LastName.

Select * FROM Employees WHERE LastName LIKE "F_ _ _ _ R"    /// Cuando sé que empieza y acaba por F y R pero sin saber qué hay en el medio.
Select * FROM Employees WHERE LastName LIKE "_ AIM _"    /// Cuando quiero filtrar por LastName que contentan AIM en el centro y tengan una letra a cada lado. Nos podría devolver si los hay por ejemplo: Jaime, Jaima, Saima...
```

## OPERADOR IS NULL o IS NOT NULL:
```SQL
select * FROM Products Order by ProductName Asc  /// Te muestra ordenados primero los nulos y luego de pequeño a mayor

select * FROM Products
WHERE ProductName IS NULL  ///Te devuelve solo los nulos.
Order by ProductName Asc

select * FROM Products
WHERE ProductName IS NOT NULL /// Te devuelve todos los valores NO NULLS
Order by ProductName Asc
```


## OPERADOR IN y NOT IN: es la introducción a las subconsultas.
- Es un operador lógico.
- Opera sobre un conjunto de datos

Vamos a pedirle que nos muestre los productos de los proveedores 3, 4, 5 y 6.
```SQL
// Poco eficiente:
select * FROM Products
WHERE SupplierID = 3
OR SupplierID = 4
OR SupplierID = 5
OR SupplierID = 6

//Más eficiente: Se puede usar en la clausula select, update y delete.
select * FROM Products
WHERE SupplierID IN (3, 4, 5, 6)
```

Quiero seleccionar los empleados que sean Fuller o King:
```SQL
// Poco eficiente:
select * FROM Employees
WHERE LastName = "Fuller"
OR LastName = "King"

// Más eficiente:
select * FROM Employees
WHERE LastName IN ("Fuller", "King")

// Para negarlo o que nos devuelva lo contrario. Todo lo que no sea Fuller o King:
select * FROM Employees
WHERE LastName NOT IN ("Fuller", "King")
```