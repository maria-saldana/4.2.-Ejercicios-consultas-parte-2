4.2. Ejercicios consultas parte 2
📘 Prácticas de MongoDB
Este repositorio contiene una colección de ejercicios prácticos realizados con MongoDB como parte de mi formación en bases de datos NoSQL. Cada carpeta o archivo representa un conjunto de desafíos resueltos usando inserciones, consultas, actualizaciones y operaciones de agregación sobre diferentes estructuras de datos.

🧠 Temas trabajados
Inserción de documentos con insertMany()
Consultas con find(), expresiones regulares y filtros lógicos
Proyección de datos con project, concat, size, etc.
Agregaciones con group, avg, sum, sort
Unión de colecciones con $lookup y desanidado con $unwind
Actualizaciones condicionales con updateMany(), $set, $unset, $push, $inc
Eliminación con deleteMany()
Trabajo con estructuras complejas: arrays, objetos embebidos y campos anidados
🧰 Tecnologías
MongoDB (usado desde la shell interactiva)
JavaScript para scripts de base de datos
OBJETIVO: Utilizar correctamente los operadores de agrupación datos para  realizar cálculos sobre éstos
 
MARCO TEÓRICO
a) 	framework de agregación


 
I.  Completa la siguiente tabla
 
Comando 
Descripción general
Ejemplo de comandos
Operadores de agrupación
Operadores de Conteo Grupal en el Framework de Agregación de MongoDB
El operador $group en el framework de agregación de MongoDB permite implementar funcionalidad similar a SELECT COUNT GROUP BY de SQL. Este operador agrupa documentos con la misma clave de grupo en un solo documento, utilizando el campo _id como clave de grupo. Para contar documentos en cada grupo, se utiliza la expresión {$sum:1} como acumulador. La sintaxis básica para el operador $group es: $group: {_id: $clave_de_grupo, campo: $campo_de_agrupación, acumulador: $acumulador}. Este operador es fundamental para realizar conteos grupales y es una de las etapas centrales en la pipeline de agregación de MongoDB. 



Operadores aritméticos
Los operadores aritméticos en MongoDB son herramientas que permiten realizar operaciones matemáticas en los datos de la base de datos. Aquí hay algunos ejemplos de operadores aritméticos:
$add: Suma dos números o suma una fecha y números.
$subtract: Resta dos números y devuelve el resultado.
$abs: Devuelve el valor absoluto de un número.
$divide: Divide dos números y devuelve el cociente.
$pow: Eleva un número a la potencia de un exponente especificado.
Estos operadores son fundamentales para realizar cálculos y manipular datos de manera eficiente en MongoDB. 



Operadores booleanos
Los operadores booleanos son herramientas fundamentales en programación que permiten combinar y evaluar expresiones lógicas, devolviendo valores verdadero o falso según la condición evaluada.
Qué son los operadores booleanos
Los operadores booleanos son símbolos o palabras clave que permiten realizar operaciones lógicas entre expresiones que pueden ser verdaderas (True) o falsas (False). Se basan en la lógica booleana, desarrollada por George Boole, y son esenciales para la toma de decisiones en algoritmos y el control del flujo de ejecución de un programa



Operadores condicionales
Los operadores condicionales en MongoDB son utilizados para filtrar documentos en las consultas. Estos operadores permiten comparar valores en los documentos y seleccionar aquellos que cumplen con ciertas condiciones. Algunos de los operadores condicionales más comunes son:
$eq: Compara si un campo es igual a un valor específico.
$ne: Compara si un campo no es igual a un valor específico.
$gt: Compara si un campo es mayor que un valor específico.
$lt: Compara si un campo es menor que un valor específico.
$gte: Compara si un campo es mayor o igual a un valor específico.
$lte: Compara si un campo es menor o igual a un valor específico. 
1

Estos operadores son esenciales para realizar consultas precisas y eficientes en MongoDB, permitiendo a los desarrolladores filtrar y manipular datos de manera efectiva



Operadores de cadena 
Los operadores de cadena permiten manipular y combinar texto en programación, siendo el más común la concatenación mediante el operador +.
Qué son los operadores de cadena
Los operadores de cadena son símbolos o palabras reservadas que permiten realizar operaciones sobre cadenas de caracteres (strings), como unirlas, compararlas o modificar su contenido. Una cadena de caracteres es una secuencia de letras, números o símbolos encerrados entre comillas simples o dobles, y se utiliza para representar texto en los programas. 

 
 
Operadores de fecha
Los operadores de fecha en programación son símbolos que se utilizan para manipular y combinar valores relacionados con fechas. Aquí hay algunos puntos clave sobre los operadores de fecha:
Operadores de fecha: Devuelven valores exactos, teniendo en cuenta los cambios de años y los años bisiestos. 
1
Tipos de operadores: Incluyen operadores aritméticos, de comparación, lógicos y de pertenencia.  
 
Map Reduce
MapReduce es un modelo de programación que utiliza la computación paralela para procesar grandes conjuntos de datos. Consiste en dos tareas principales: Map y Reduce.
Map convierte un conjunto de datos en otro conjunto de datos formateado como pares clave/valor.
Reduce agrega los valores de pares clave/valor similares para producir un resultado final.
Este modelo es fundamental en la infraestructura de software de código abierto Hadoop y se utiliza para escalar el procesamiento de datos a gran escala en un clúster de servidores.
 


Operaciones de propósito único
Las operaciones de propósito único en MongoDB son simples y se utilizan para realizar tareas específicas sin necesidad de un pipeline de agregación. Estas operaciones son útiles para obtener conteos, sumas, mínimos y máximos de un conjunto de datos. Por ejemplo, para contar el número de documentos en una colección o vista, se puede utilizar la operación count(). Para calcular la suma de un campo específico, se puede usar la operación sum(). Estas operaciones son ideales para situaciones donde no se requiere un análisis más complejo y se busca obtener resultados rápidos y precisos




 
PROCEDIMIENTOS Y RESULTADOS

Genera las sentencias necesarias y  muestra evidencia de ellas:

Considerar una colección con documentos de MongoDB que representan información multimedia de la forma:


 { “tipo”: “CD”, “Artista”: “Los piratas”,
“TituloCanción”: “Recuerdos”,
“canciones”: [ {“cancion”:1,
“titulo”: “Adiós mi barco”, “longitud”: “3:20”
},
{“cancion”:2,
“titulo”: “Pajaritos”, “longitud”: “4:15” }
]
}


{ “tipo”: “DVD”, “Titulo”: “Matrix”, “estreno”: 1999, “actores”: [
“Keanu Reeves”, “Carry-Anne Moss”, “Laurence Fishburne”, “Hugo Weaving”, “Gloria Foster”,
“Joe Pantoliano”
] }









1) Seleccionar los documentos de tipo «CD», de manera que solo se muestre en dichos documentos los campos «Artista», «TituloCanción», y un nuevo campo «TitulosCanciones», que contenga un array con las canciones del disco.
2) Añadir las siguientes películas:
{“tipo”: “DVD”, {“tipo”: “DVD”, {“tipo”: “DVD”, “Titulo”: “Blade Runner”, “Titulo”: “Batman”, “Titulo”:
“Superman”,
“estreno”:1982 “estreno”: 1999 “estreno”: 1999
}}}
Seleccionar todos los documentos de tipo «DVD» y calcular cuántas películas hay de cada año de estreno, mostrando el año de estreno y el número de películas de cada año.
3) Seleccionar el documento sobre la película «Matrix» y crear un documento por cada uno de los actores que intervienen. En los documentos resultantes solo se mostrará el título y el actor.
4) Igual que la consulta anterior, pero se mostrará solo los tres últimos resultados ordenados por el nombre del actor.
5) Obtener las películas distintas que hay con respecto al título, los diferentes años de estrenos, y los diferentes tipos de documentos. Se realizará en tres consultas diferentes.
6) Agrupar los documentos por «Título», mostrando el título y el total que hay de cada grupo.
7) Añadir las siguientes películas:

{“tipo”: “DVD”, {“tipo”: “DVD”, {“tipo”: “DVD”,
“Titulo”: “Blade Runner”, “Titulo”: “Batman”, “Titulo”: “Superman”,
“estreno”:1967 “estreno”: 1989 “estreno”: 1996 }}}
Repetir el caso anterior pero solo con los documentos que
pertenecen a películas.
8) Obtener usando MapReduce la suma de los años de los
estrenos de cada película. Es decir, debe obtenerse documentos de la forma: {“_id”: “Batman”, “value”:{“TotalPeliculas”:3988 }}.



CONCLUSIÓN:

REFERENCIAS:
https://www.mongodb.com/es/docs/manual/aggregation/?msockid=39eae6057c6c63893681f0e27d9d62c5 
https://www.mongodb.com/es/docs/manual/reference/mql/expressions/?msockid=39eae6057c6c63893681f0e27d9d62c5
https://www.bing.com/ck/a?!&&p=013f6303d3bb4c9d6e39ab8a5aeccf79450e587e254a29e42815c8392dc5ea3eJmltdHM9MTc3OTQ5NDQwMA&ptn=3&ver=2&hsh=4&fclid=39eae605-7c6c-6389-3681-f0e27d9d62c5&psq=operadores+booleanos+en+programaci%c3%b3n&u=a1aHR0cHM6Ly9rZWVwY29kaW5nLmlvL2Jsb2cvbG9naWNhLWJvb2xlYW5hLw
https://www.alldevstack.com/es/mongodb-tutorial/mongodb-query-operators.html
https://saberpunto.com/programacion/simbolos-aritmeticos/
https://www.bing.com/search?q=Operadores%20de%20fecha%20%20programaci%C3%B3n&qs=n&form=QBRE&sp=-1&lq=0&pq=operadores%20de%20fecha%20programaci%C3%B3n&sc=12-34&sk=&cvid=B65449917F1C4F0B92D2EB2037062C6C#:~:text=Aproximadamente%209.950%20resultados-,Los%20operadores%20de%20fecha%20en%20programaci%C3%B3n%20son%20s%C3%ADmbolos%20que%20se%20utilizan,operadores%3A%20Incluyen%20operadores%20aritm%C3%A9ticos%2C%20de%20comparaci%C3%B3n%2C%20l%C3%B3gicos%20y%20de%20pertenencia.,-1
https://elpythonista.com/map-filter-y-reduce-en-python-programacion-funcional-completa-2025
https://www.mongodb.com/es/docs/manual/aggregation/?msockid=39eae6057c6c63893681f0e27d9d62c5
