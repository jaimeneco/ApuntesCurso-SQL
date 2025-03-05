# LAS CONDICIONES:
Sirven para seleccionar y filtrar datos concretos, para evitar hacer una cagada y borrarlo todo. Verifican condiciones y devuelven cosas.

## Cláusula WHERE: es la condición más común de SQL. Diferentes formas de filtrar con WHERE:
```SQL
select ProductName FROM Products /// o para saber toda la info ponemos: select * FROM Products
WHERE ProductID = 14  ///Buscamos por ID
WHERE ProductName = "Tofu"  ////Buscamos por nombre

select * FROM Products
WHERE Price > 40 /////  Te muestra todos los productos de menos de 40 euros. Se pueden usar estos:( >, <, <=, >= ).

select FROM turnos_medicos /// Para ver todo
Delete FROM turnos_medicos 
WHERE id_turno = 3        /// Para eliminar el turno con id=3
```

## Con esto le estamos diciendo: Actualízame en la tabla turnos_medicos, los campos horario y motivo y que este cambio solo aplique a los registros que tengan el id de turno 2.
```SQL
Update turnos_medicos 
SET horario = "10:30", motivo = "Dolor de muelas"
WHERE id_turno = 2;
select * FROM turnos_medicos
```


# OPERADORES AND, OR y NOT:

### Quiero obtener los Customers que tengan ID mayor o igual que 50 y menor que 55.
```SQL
select * FROM Customers
WHERE CustomerID >=50 AND CustomerID <55  /// Se deben cumplir ambas
```

### Quiero obtener los empleados que han ganado un premio: 
```SQL
select * FROM Employees
WHERE FirstName = "Nancy" OR FirstName = "Ana"  Se cumple una condición o la otra condición. Te muestra los dos registros que cumplen la primera o la segunda condición, es decir, Ana y Nancy con toda su información.
```

### Filtrado juntando AND y OR: Cuando quiero un producto que valga menos de 20, o que si vale más de 20 sean de la categoría del producto 6. Además tiene que ser un producto del proveedor que yo quiero, que es el SupplierID = 7.
```SQL
select * FROM Products
WHERE Price < 20 OR CategoryID = 6 AND SupplierID = 7 // De esta forma estamos comparando primero el precio y luego los otros dos juntos. Para hacer las dos primeras juntas y la tercera por separado lo ponemos entre paréntesis:
WHERE (Price < 20 OR CategoryID = 6) AND SupplierID = 7
```

### Para filtrar negando una condición:
```SQL
Select * FROM Products
WHERE NOT Price > 40 /// Te niega una condición, es decir, hace lo contrario


Quiero enviar un mail a todos los clientes que NO vivan en USA:
select * FROM Customers
WHERE NOT Country = "USA"
```

### Mezclar NOT con el AND: quiero enviar un mail a todos los clientes que NO vivan ni en USA ni en Francia:
```SQL
select * FROM Customers
WHERE NOT Country = "USA" AND NOT Country = "France"
```

### Dar un premio entre el cliente 50 y el 55 de nuestra base de datos. De estos 5 clientes, hay uno que vive en un Germany que es un país en que no llegan los envíos. Debemos excluir ese país u otros :
///No es la forma más eficiente:
```SQL
Select * FROM Customers
WHERE CustomerID >= 50
AND CustomerID <55
AND NOT Country = "Germany"
```
///Esta sí es la más eficiente, además usamos la CLÁUSULA LIMIT.
```SQL
Select * FROM Customers
WHERE CustomerID >= 50
AND NOT Country = "Germany"
AND NOT Country = "UK"
AND NOT Country = "Argentina"
LIMIT 5  //Limita la cantidad de resultados que queremos recibir
```

### Un cliente nos pide que no quiere productos de la categoría 6 y que quiere sólo recibir los productos de mayor calidad del proveedor. Además solo tiene 30 euros para gastar y quiere ver sólo 3 productos. Esos primeros tres productos no le gustaron, así que quería ver 3 más pero de forma aleatoria (Random()).
```SQL
Select * FROM Products
WHERE NOT CategoryID = 6
AND NOT SupplierID = 1
AND Price <= 30
Order by Random()
LIMIT 3
```

# DISTINTO DE VS NOT, diferencias: captura 6.png
- La diferencia es prácticamente mínima entre ambos conceptos, pero la hay y el funcionamiento es diferente.
- 'Distinto de' es un operador de <b>COMPARACIÓN</b>. Los operadores de comparación comparan dos valores y nos devuelven True o False.
- 'NOT' es un operador <b>LÓGICO</b> o <b>Booleano</b>. Estos operadores ya trabajan con Booleanos (true y false)

```SQL
Select * FROM Customers WHERE Country != "USA"
```














