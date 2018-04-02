Apuntes Curso de introducción a Python Coursera

Descarga de Python
https://www.python.org/
Descarga de IDE pycharm
http://www.jetbrains.com/pycharm/download/#section=mac

###Tipos de datos básicos o primitivos

int		tipo numérico
float	tipo numérico
str		tipo de texto
bool 	tipo lógico o booleano

int representa números enteros positivos o negativos

```
para saber el tipo de datos en python
>>>type (23) 
```

float representa números con puntos decimales

str representa secuencias o cadenas de caracteres (string) normalmente se indica el comienzo y el final del string con comillas dobles o simples.

Atencion....
si escribimos un número entre comillas ya no sería de tipo int sino de tipo string.

bool representa valores booleano o de lógica binaria : verdadero o falso : True o False

Atención 
Si escribimos True o False sin la primera letra en mayúscula phyton no lo reconocerá.

###Operadores y Expresiones

+ suma
- resta
* Multiplicación
/ División
- inverso aditivo
** exponenciación
// división entera
% Módulo

Cuando tenemos operaciones con más de un operador estos se resuelven dependiendo de la prioridad de cada uno o precedencia, cuando varias operaciones con igual precedencia se resuelven por orden de asociatividad.

>>> (3+5//4-2)-2**4+3*(7-2)
Resultado es 1

Dentro de cada paréntesis se evalúa


| Operador | Precedencia | Asociatividad | Ejemplo | Resultado | 
|----------|-------------|---------------|---------|-----------|
| **| 1|Derecha a Izquierda |2**3**2 | 512 |
| +, - (unarios) | 2| | -2**2 | -4
| *,/,//,% | 3| izquierda a derecha | 15/3*2 |10
| +, - (binarios) | 4 |izquierda a derecha | 3-4+5 | 4|

#### Operadores de igualdad

Menor <
Mayor o igual >=
Distinto !
igualdad ==

Siempre se aplican a tipos numéricos y su salida siempre es de tipo booleano True o False.

#### Operadores de tipo lógico

se aplican a bool y siempre entregan una salida bool

not  ( invierte el resultado de un valor lógico
and  ( conjunción lógica entrega True solo cuando ambos valores son verdaderos )
or   ( Disyunción lógica entrega True cuando al menos uno de los valores es verdadero )

>>> not 3>5       True
>>> 3>5 and 2<6   False
>>> 3>5 or 2<6 	 True

### Operaciones con varios tipos de operadores

| Operador | Precedencia | Asociatividad | Ejemplo | Resultado | 
|----------|-------------|---------------|---------|-----------|
| **| 1|Derecha a Izquierda |2**3**2 | 512 |
| +, - (unarios) | 2| | -2**2 | -4
| *,/,//,% | 3| izquierda a derecha | 15/3*2 |10
| +, - (binarios) | 4 |izquierda a derecha | 3-4+5 | 4|
| <. <=,>,>= , !=,== |5 |izquierda a derecha | 3<4<=4<5 | True|
| not | 6 | | not not 5>2 | True |
| and | 7 | izquierda a derecha | not True and False | False |
| or | 8 | izquierda a derecha | True or True and False | True |

### Operadores para texto o strings

Operadores de concatenación +  
```
"Yo soy " + " Tu Padre"
salida = Yo soy Tu Padre
```
Operadores de Repetición * 

```
"Ja" * 4
salida = JaJaJaJa
```
### Operando con disntintos tipos de valores

convertir valores enteros a un string

" son las " + 3 + 12 = nos devolverá un error
" son las " + str (3+12) = nos devolverá = " son las 15 "

lo que estamos diciendole a python es que los valores entre paréntesis son string y no int o float.

Conversiones a int

>>> int (3.56545)
>>> 3

>>> int ("3") + 12
>>> 15

conversiones a float

>>> float(3)
>>> 3.0

>>> float("3.5") + 12
>>> 15.5

conversiones en bool

0 o "" es False , el resto es true

bool (0) 			False
bool ("")			False
bool (15.5)		True
bool ("False")	True
bool ("True")		True
bool ("0")		True

conversiones a str

str(3.0) 			"3.0"
str( 8 + 1-76) + segundos		"9.76 segundos"
str (3<5 and 9.76 < 10) 		"True"

## Almacenando valores. Variables y asignación.


= asigna un valor a una variable
Recuperamos el valor usando el nombre de la variable

por Ejemplo

pesos_por_hora = 200
llegada = 20
salida = 22
( salida - llegada ) * pesos_por_hora
Resultado es 400

las reglas para nombrar nombres de variables es que 
deben epmpezar con una letra o _ y puede seguir con letras, números o _

no se pueden usar variables con palabras reservadas.
tipo and , as , break etc........

## Escribiendo en pantalla

print ("Hola Mundo")  --> Hola Mundo

mensaje = "Hola Mundo"
print (mensaje) 			--> Hola Mundo

cambiando el fin de línea (end)

nombre = "Cristian"
edad = 38
print("Soy", nombre, end=" ")
print("y tengo", edad, "años")
print("cumplidos")

Soy Cristian y tengo 38 años
cumplidos

cambiando el separador de expresiones (sep)

print("-El tesoro", "está", "en", sep="...")
- El tesoro...está...en

## Recibiendo datos del usuario input

variable = input(texto)

```
nombre= input("Cual es tu nombre?")
saludo= "Hola,"
pregunta= "¿Como estás hoy ?"
print( saludo, nombre, pregunta)

Salida

¿Cual es tu nombre? ....
Hola, ... ¿Como estás hoy?
```
input siempre entrega un str

si hacemos un programa que nos diga cuantas lecciones nos faltan por terminar y queremos hacer operaciones numéricas con el input hay que pasarlo a int 

```
lec= int(input("¿Cuantas lecciones has visto?"))
total = 15
faltan = total - lec
print ("Te faltan ", faltan, "lecciones. !animo!")

salida

¿ Cuantas lecciones has visto? 10
te faltan 5 lecciones !animo!
```

## Condiciones if - else

Si la ```condición``` es verdadera se realiza la acción
Si la ```condición``` es falsa realizará otra acción

Para realizar este tipo de condiciones se utiliza valores booleanos para ello podemos utilizar 

- operadores de comparación:
	< <= > >= != ==
- operadores apra tipos lógicos
	not and or
Ejemplos:

not 3>5 		true  ( ya que lo opuesto de not es true )
3>5 and 2<6	false ( Entrega verdadero cuando ambos valores son verdaderos)
3>5 or 2<6	true  ( Entrega verdadero cuando al menos uno de los valores es verdadero)

En el código esta sería la manera de hacerlo

```
if condición:
	instrucción1
else:
	instrucción2
```
ejemplo

```
llueve = true
if llueve == true:
	print("llevaré paraguas")
else:
	print("no llevaré paraguas")
print("ahora saldré a la calle")
```

Tenemos que tener cuidado con la identación al crear nuestras condiciones, ya que todo lo que esté identando dentro del if es lo que se ejecutará, en el ejemplo anterior si el último print estuviera identado dentro del else este se ejecutaría solo si la condición es falsa, pero como no está identado este se ejecuta cuando termina la condición.

condiciones mas complejas añadiendo más condiciones.

```
llueve = true
temperatura = 12
if llueve == true and temperatura <20
	print("llevare paraguas y abrigo")
else:
	print("no necesito paraguas o abrigo")
```

## Condición IF ( sin else )

Esta condición se cumple si aparece el condicionante de lo contrario el programa sigue ejecutandose normalmente.

Ejemplo:
```
charco = true
print("Comienza la caminata")
if charco == true:
	print(" a saltar ")
print("Fin de la caminata")
```
Nota: No puede haber ```else``` sin ```if```

## Condiciones: Elif

Para evitar condiciones if-else anidadas podemos usar condiciones elif, podemos usar tantas condiciones elif como queramos.

Ejemplo:
```
if condición1:
	instrucción1
elif condición2:
	instrucción2
elif condición3:
	instrucción3
...
else:
	instrucciónN
```
En este caso al igual que con la condición IF sola no es necesario terminar con un else ( es opcional )

## Flujo Cíclico: While

Lograr que el programa realice un ciclo, repitiendo un conjunto de instrucciones.

![](file:///Users/kapi_tan//SynologyDrive/Escritorio/apuntes/img/python/while_loop.jpg)

Mientras la condición sea verdadera pasarán al código correspondiente, cuando la condición sea falsa se saldrá del ciclo.

Ejemplo: programa para convertir temperatura de Farenheit a Celsius.

El Pseudocódigo sería el siguiente
```
temp = 32
print("fº    cº")
while	temp sea menor a 73:
	imprimir temp y su conversion a Cº
	sumar 1 a temp
```
Código Real

```
temp = 32
print("fº			cº")
while temp < 73:
	print(temp,"     ",int((temp-32)*5/9))
	temp = temp + 1
```
## Instrucción for

Repetir un conjunto de instrucciones un número definido de veces.

sintaxis
```
for variable in secuencia
	instrucciones
```

Programa anterior implemetando for:
```
print("fº			cº")
for temp in range (21):
	print(temp,"     ",int((temp-32)*5/9))
```
la expresion: range(fin), crea una secuencia de números, que parte desde 0 y llega hasta fin -1

podríamos probar con este ejemplo:
```
for i in range (7):
	print(i)
```
la salida de consola sería la siguiente:

```
0
1
2
3
4
5
6
```
se imprime i desde 0 hasta el final que le hayamos asignado -1 que en este caso al ser 7 es 6.

Creando secuencias de números sobre las cuales iterar

si a range le pasamos 2 datos range(inicio, fin) crea una secuencia de números, que parte desde inicio hasta fin -1.

```
for i in range(8,14):
	print(i)
```
La salida será 
```
8
9
10
11
12
13
```
Si a range le pasamos 3 parámetros: range(inicio,fin,paso) crea una secuencia de números, que parte desde inicio y llegas hasta fin -1 saltando en lo que definamos en paso.

```
for i in range(4,101,3):
	print(i)
```
salida

```
4
7
10
13
eliminados numeros intermedios, para simplificar.
91
94
97
100
```

### Funciones

Básicamente sirven para reutilizar código

Fragmento de código que recibe parámetros, ejecuta acciones y retornan un resultado.

funciones que ya hemos utilizado

print y input

Una vez que el programa llega al retorno, se termina la ejecución de la función.

Ejemplo de función:
```
def calculo(numero):
	resultado = (numero -3) ** 3
	return resultado
```
Para ver el resultado de la función:

```
print(calculo(8))
salida = calculo(5)
print(salida + 100)
```
la salida de estas llamadas son
```
125
108
```
Ejemplo de una función que retorna si un número es par o no

```
def es_par(numero)
	if numero % 2 == 0:
		return True
	else:
		return False

#probando la función
print(es_par(8))
print(es_par(7))

#salida
True
False
```
* parámetros son aquello que la función recibe para poder trabajar dentro de la función.
* Retorno es aquello que la función entrega para terminar la ejecución de la función.

## Importación de módulos y llamada a funciones

Existen muchas librerías o módulos ya programados.

por ejemplo las librerías random o math

primer método para importar 

```
import <nombre módulo>

por ejemplo

import math

para llamar a la función:

import modulo
modulo.funcion(argumentos)

ejemplo

import math
math.sin(0)
```
Segundo método

```
from <nombre módulo> import
<elemento1>,<elemento2>

ejemplo

from math import pow, sqrt

para usar las funciones:

from modulo import funcion
funcion(argumentos)

ejemplo:

from random import uniform
uniform(0,1)

```
Tercer método
```
from <nombre módulo> import
<elemento1> as <alias>

ejemplo

from math import e as euler

para llamar a la función:

from random import randint as rnd
rnd(5,10)

```
Cuarto Método (no recomendado)
```
from <nombre módulo> import *

ejemplo:

from math import *
```
* La función random permite generar números pseudoaleatorios.
* La función math permite realizar cálculos complejos y acceder a constantes conocidas.

ejemplo de usar las librerías random y math

```
from random import randint as rnd
from math import pi, e

lanzamiento = rnd(1,6)
if lanzamiento < 4:
	print (pi * lanzamiento)
else:
	print (e * lanzamiento)
```
## Definición de las funciones

Se debe tener en cuenta lo siguiente

1. Comienza con def.
2. Nombre.
3. Paréntesis, que pueden llevar los parámetros dentro.
4. Se tienen que indicar los dos puntos.
5. El código y los retornos identados.

estructura básica

```
def nombre(parametro1,parametro2,parametroN):
# aquí va el código de la función
# y todo lo relacionado
# variables, retornos, etc...
valor = 0
return valor
```
ejemplo

```
def max_divisor(n):
	maximo_actual = 0
	i = 1
	while i < n:
		if n % i == 0:
			maximo_actual = i
		i + = 1
	return maximo_actual
```
ejemplo con más de un parámetro

```
def potencia_positiva(base, exponente):
	if exponente == 0:
		return 1
	else
		resultado = 1
		while exponente > 0:
			resultado *= base
			exponente -= 1
		return resultado
```
Las funciones se definen una sola vez, para llamarla es necesario que anteriormente esté definida.

## Invocación y Scope de funciones

 * La invocación o llamado se reliza cuando se quiere ejecutar la función definida.
 * Sin invocación, el código nunca se ejecuta.
 * Las llamadas a la función hay que hacerlas despues de definir la función.
 * Se puede, opcionalmente, igualar  la llamada a una función a una variable.

 Ejemplo
 
 ```
 def calculo(numero):
 	resultado = (numero - 3) ** 3
 	return resultado
 
 salida = calculo(5)  # el valor de la operación calculo(5) lo metemos dentro      
 						  # de salida.
 ```
 * El scope tambien llamado alcance de una función corresponde al manejo de las variables dentro de la misma.
 * Las variables definidas dentro de una función no existen fuera de ellla.

 Ejemplo:
 
 ```
 def es_par(numero):
 	divisor = 2
 	if numero % divisor = 0
 		return True
 	else:
 		return False
 
 print(divisor) # cuando intentameos mostrar esta variable nos dará error ya que esta variable solo está definida dentro de la función.
 
 ```
 * Que las variables "mueran" al terminar la función evita errores.
 * Se les llama **variables locales**, y solo existen dentro de la función que las define.
 * Las variables fuera del scope de la función, se pueden utilizar pero no modificar.
 * Fuera del scope: variables que no fuerón definidas en la función.
 
 Ejemplo:
 
 ```
 def fx(numero):
 	print(numero * factor)
 
 factor = 0.5
 fx(3)
 print(factor)
 
 la salida de este código será 
 
 1,5  # lo que imrime la función fx(3)
 0,5  # el resultado de print(factor)
 ```
En este ejemplo para usar la función estamos leyendo una variable externa llamada factor que vale 0.5

```
def fx2(numero):
	factor += 0.1
	print(numero * factor)

factor = 0.5
fx2(3)
```

en este caso el código genera un error porque se está intentando modificar una variable que está en un scope superior dentro de la función añadiendole 0.1 y esto no es posible.

```
def fx3(numero):
	factor = 0.9
	print(numero * factor)

factor = 0.5
fx3(3)
print(factor)

salida:

2.7   # resultado de la función con la variable factor 0.9
0.5   # valor de la variable factor fuera de la función
```
En este caso se observa la diferencia de las 2 variables fuera y dentro de la función cada una con un valor distinto.

* Las variables definidas en una función son locales.
* Dentro de una función se pueden leer variables de un scope mayor o externo, pero no modificarlas.

## Funciones como módulos.

* Un archivo Python con la extensión .py es un módulo.
* Los módulos tienen conjuntos de funciones y constantes importables desde cualquier otro programa.

para importar un módulo podemos usar:

- from modulo import elementos 
- import mofulo

* De igual forma si creamos un archivo con extensión .py, podrá ser importado de la misma forma. Basta con tener en ese archivo las funciones y constantes deseadas.

Ejemplo

En el archivo modulo_fumciones.py agregamos el siguiente código.

```
def es_par(numero):
	if numero % 2 == 0:
		return True
	else:
		return False
```
En el archivo programa.py agregamos el siguiente módulo.

```
from modulo_funciones import es_par

numero = int(input("Ingrese nº: "))
if es_par(numero):
	print("Su número es par!")
else:
	print("Su número es impar!")
```
De esta manera el progama lo que hace es llamar al módulo modulo_funciones e importar la función es_par despues pide un número al usuario e indica al usuario si el número es par o impar.

* Existen muchos módulos preexistentes como los módulo random o math.

## Manipulación de Strings

* Usamos ```+```para concatenar Strings por ejemplo: "hola" + " a todos " = "hola a todos.
* Usamos ```*```para repetir Strings por ejemplo: "hola "*3 = "hola hola hola"

### Acceso a los elementos mediante Indices
* Es posible seleccionar ciertos elementos de un string según su posición en él.
* Los índice comienzan en 0.

Ejemplo
```
print("Martes"[0]) # El resultado es "M"
```
Otro Ejemplo
```
a = "La casa es verde"
print(a[5])		# El resultado es "s"
```
* Se pueden seleccionar los símbolos del final con números negativos ( posición -1 es la última letra, decrecen hacia la izquierda)
```
print("Martes"[5])
print("Martes"[-1])
# "s"
# "s"
```
* Podemos también seleccionar un cierto intervalo de símbolos del string indicandolo como string[inicio:final+1], esto es conocido como **slicing**

```
print("Martes"[1:4])
# "art"
```
* Existen ciertos símbolos que no pueden escribirse directamente con el teclado (como una línea nueva), para esto se ocupa el símbolo "\" también llamada Backslash en conjunto con alguna letra para indicarlos.

"\n": indica una nueva línea
```
print("Un párrafo. \n Otro párrafo.")

# "Un párrafo.
# Otro párrafo"
```
* Para escribier un backslash ```\``` y que no lo tome como un salto de línea o cualquier otra cosa hay que colocarlo doble ```\\```

### Métodos propios de Strings

* Unos de los métodos más útiles y comunes es ```len```( abreviado de lenght, longitud) lo que hace es devolver el largo del string que se le pase como parámetro.

Ejmplo:
```
len(martes) # 6
```
* Para pasar todo un string a mayusculas o minúsculas, se puede invocar los métodos:

string.upper()
string.lower()

Ejemplo:

```
print("Martes".upper())  # "MARTES"
print("MArtes".lower())  # "martes"

```
* Para eliminar algún símbolo de **extremos** del string, existe el método strip, se debe indicar con un parámetro el símbolo a eliminar.

Ejemplo:
```
a= "Bien. Martes a las 5."
print(a.strip("."))    

# "Bien. Martes a las 5"
```
* Para reemplzar algún símbolo del strin, existe el método replace, con el símbolo antiguo y el nuevo como parámetros.

Ejemplo:

```
a = "Hola!!1!"
print(a.replace("1", "!"))

# "Hola!!!!"
```
### Archivos

* Para abrir un archivo se ocupará la función open, a la que se le debe de dar como parámetro el nombre del archivo (incluyendo la terminación después del punto)

a= open("archivo.txt")

* La función open toma un segundo parámetro: el modo es el que indica si se quiere leer o escribir el archivo.

"r": solo lectura
"w": solo escritura

open("archivo","modo")

















## Programación orientada a objetos
https://www.youtube.com/watch?v=AAKoccH230Y

Bases de la programación (I)

* Abstracción: proceso mental de extracción de las características esenciales de algo, ignorando los detalles superfluos.
* Encapsulación: proceso por el que se ocultan los detalles del soporte de las características de una abstracción
* Modularización: proceso de descomposición de un sistema en un conjunto de módulos("piezas") poco acoplados( independientes) y cohesivos ( con significado propio).
* Jerarquización: Proceso de estructuración por el que se produce una organización (jerarquia) de un conjunto de elementos en grados o niveles de responsabilidad, de incumbencia o de composición 



* sistema : Un conjunto de elementos que colaboran entre si para un objetivo en común. Por Ejemplo Cuerpo Humano.
* MVC: Modelo Vista Controlador 





















Para poder utilizar caracteres extendidos en Python es necesario indicarle que estamos haciendo tal cosa, ya que sino, por defecto únicamente contempla que estamos utilizando ASCII de 7bits, en los que no se contemplan ni eñes ni acentos ni ningún otro carácter que no esté en el teclado americano.
Para indicarle pues que estamos utilizando otro tipo de codificación, y eso lo podemos hacer de la siguiente manera:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
```
print "¡Hola papá!\nYa puedo escribir bien.\nÑañañaña"
Incluyendo la línea de la codificación como se puede apreciar en el código anterior.

```

#print sys.stdout.encoding  --> Para mostrar la codificación que estás usando

#!/usr/bin/python
# -*- coding: iso-8859-1 -*-
import os, sys

```
