```
 ____    ____       _       _______     ___  ____   ______      ___   ____      ____  ____  _____  
|_   \  /   _|     / \     |_   __ \   |_  ||_  _| |_   _ `.  .'   `.|_  _|    |_  _||_   \|_   _| 
  |   \/   |      / _ \      | |__) |    | |_/ /     | | `. \/  .-.  \ \ \  /\  / /    |   \ | |   
  | |\  /| |     / ___ \     |  __ /     |  __'.     | |  | || |   | |  \ \/  \/ /     | |\ \| |   
 _| |_\/_| |_  _/ /   \ \_  _| |  \ \_  _| |  \ \_  _| |_.' /\  `-'  /   \  /\  /     _| |_\   |_  
|_____||_____||____| |____||____| |___||____||____||______.'  `.___.'     \/  \/     |_____|\____| 
                                                                       
```                                                                                                 


#Guia Rápida Markdown
--------------------------------------
<a id="indice"></a>
###Indice:

1.  [Que es markdown](#quees)
2.  [Párrafos](#parrafos)
3.  [Encabezados](#encabezados)
4.  [Separadores](#separadores)
5.  [Énfasis](#enfasis)
6.  [Tachado](#tachado)
7.  [Citas](#citas)
8.  [Listas](#listas)
9.  [Imagenes](#imagenes)
10. [Enlaces](#enlaces)
11. [Tablas](#tablas)
12. [Código](#codigo)
13. [Videos / Iframe´s](#videos)
14. [Comentarios](#comentarios)
15. [Extras en GitHub](#extrasgh)
16. [Teclas](#teclas)
17. [Escape](#escape)
18. [Fuentes](#fuentes)

<a id="quees"></a>
##1)  ¿Qué es Markdown? 

Markdown ( Abreviado MD ) es un lenguaje de marcado ligero creado por John Gruber que trata de conseguir la máxima legibilidad y facilidad de publicación tanto en su forma de entrada como de salida, inspirándose en muchas convenciones existentes para marcar mensajes de correo electrónico usando texto plano. Se distribuye bajo licencia BSD y se distribuye como plugin (o al menos está disponible) en diferentes sistemas de gestión de contenidos (CMS). Markdown convierte el texto marcado en documentos XHTML utlizando html2text creado por Aaron Swartz. Markdown fue implementado originariamente en Perl por Gruber, pero desde entonces ha sido traducido a multitud de lenguajes de programación, incluyendo PHP, Python, Ruby, Java y Common Lisp.

[Subir](#indice)
<a id="parrafos"></a>
##2)  Párrafos 

Si estuviéramos escribiendo normalmente en un editor común, para definir un párrafo simplemente presionaríamos un par de Enter y veremos nuestro cursor ir un par de líneas más abajo para escribir en un párrafo nuevo.

En HTML se le conoce como ```<p>``` de párrafo o paragraph.<p>
En Markdown es tan fácil como en un editor normal.

Adicionalmente tenemos la ventaja de que un único salto de línea, no separa el texto en múltiples líneas, si escribimos algo así:

    Un texto.
    Otro texto.

Se verá así:

    Un texto. Otro texto.

Utilizar múltiples líneas de separación se reduce igualmente a un único espacio de separación entre los párrafos.

[Subir](#indice)
<a id="encabezados"></a>
##3)  Encabezados 

En un editor normal necesitaríamos de la barra de herramientas para definir un estilo de encabezado para un texto, o si te sientes un poco desordenado bastaría con subirle al tamaño de la fuente y ponerlo en negrita.
En Markdown es muy sencillo, simplemente debes colocar el caracter numeral (#) de prefijo al encabezado, mientras más de estos tenga de menor grado será el encabezado (hasta 6).

Serían  el equivalente de ```<h1>```, ```<h2>```, ```<h3>``` de HTML


```
# <h1> Gran encabezado
## <h2> Mediano
### <h3> Pequeño
#### <h4> Mas pequeño
##### <h5> Aún más pequeño
###### <h6> muy pequeño
```
--------- Ejemplo en MD -----------
# <h1> Gran encabezado
## <h2> Mediano
### <h3> Pequeño
#### <h4> Mas pequeño
##### <h5> Aún más pequeño
###### <h6> muy pequeño
--------- Ejemplo en MD -----------

Adicionalmente, solo para ```<h1>``` y ```<h2>``` puedes utilizar la sintaxis setex, la cual te permite "subrayar" con 3 o más símbolos de igual (=) para producir un encabezado ```<h1>``` o con guiones (-) para ```<h2>```

```
Hola
===
Hola
---
```
--------- Ejemplo en MD -----------
Hola
====
Hola
----
--------- Ejemplo en MD -----------

<a id="separadores"></a>
##4)  Separadores 

Se delimitan al escribir 3 o más asteriscos o guiones. Pueden estar seguidos o separados por un espacio, no importa. Sería el equivalente al ```<hr>``` en HTML.

```
* * *
***
- - -
---
```
--------- Ejemplo en MD -----------
* * *
***
- - -
--------- Ejemplo en MD -----------

[Subir](#indice)
<a id="enfasis"></a>
##5)  Énfasis 
Content for chapter one.


Este formateado es el conocido como itálico y negrita.

En HTML sería ```<em>``` y ```<strong>```.
Para crear texto con formato itálico tan solo debes rodear el texto entre simples asteriscos o subguiones, y para negrita entre dobles:


| Sintáxis   | Resultado  |
|-----------------|---------------------------------- |
| ```*texto italico.*``` 	 | *texto italico.*        |
| ```_texto italico._```| _texto italico._           |
| ```**texto negrita.**``` 	 | **texto negrita.**  |
| ```__texto negrita.__```| __texto negrita.__       |


[Subir](#indice)
<a id="tachado"></a>
##6)  Tachado 

Este permite colocar texto como si lo estuviésemos tachando, utilizado mucho noticias que fueron corregidas o actualizadas.

EN HTML sería ```<strike>``` de strikethrough.
Basta con rodear el texto entre doble virgulillas o tildes de eñe:

```
~~texto tachado.~~
```
~~texto tachado.~~

[Subir](#indice)
<a id="citas"></a>
##7)  Citas 
(#anchors-in-markdown)
En HTML sería ```<blockquote>```.
Solo debemos colocar el carácter de "mayor que" (>) como prefijo al texto que le sigue:

```
> Esta es una cita.
```
> Esta es una cita.<p>
>> Esto es otra cita dentro de la primera.
>>> Esto es otra cita dentro de la segunda.
>
> Vuelta al primer nivel de cita.

Tambien se pueden incluir otros elementos markdown en las citas.

> ***Codigo en cita:***
> 
>     return shell_exec("echo $input | $markdown_script");

[Subir](#indice)
<a id="listas"></a>
##8)  Listas 

Para definir una lista de objetivos solemos utilizar la funcionalidad de viñetas para listas sin orden especifico y listas numeradas.

En HTML sería ```<ul>``` para listas sin orden, ```<ol>``` para listas ordenadas y ```<li>`` para definir cada item de la lista.<p>
En Markdown las definimos simplemente prefijando cada ítem con un asterisco (*), guión (-) o símbolo de más (+) para listas sin orden. Para listas ordenadas prefijamos con el número que le corresponde y un punto:

```
* Compra leche.
* Comprar pan.

1. Primero ir al mercado.
      * esto es otra lista
        * esto es otra lista
2. De último ir a la casa.
3. Luego pasar por la oficina.
```
* Compra leche.
* Comprar pan.

1. Primero ir al mercado.
      * esto es otra lista
        * esto es otra lista
2. De último ir a la casa.
3. Luego pasar por la oficina.

[Subir](#indice)
<a id="imagenes"></a>
##9)  Imágenes 

¿Qué son muchas palabras sin imágenes de prueba que lo demuestren? Una imagen vale más que mil palabras, llaman la atención al momento y en muchas ocasiones nos permiten expresar cosas que con solo texto no serían lo mismo. Afortunadamente es igual de sencillo de escribir que los enlaces, solo debes preceder con el símbolo !:

```
![texto alterno](url-de-imagen)
```
![Taken by J T Darling while on service in Macedonia, Bulgaria and Greece in 1918](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Soldier_1918.jpg/107px-Soldier_1918.jpg?uselang=es)

Fuente:[wikipedia][1] 

<!--Este enlace aparecerá al final del documento-->

De igual manera puedes utilizar la sintaxis alternativa que mostramos en los enlaces para tener tu texto más organizado.

[Subir](#indice)
<a id="enlaces"></a>
##10)  Enlaces 

Colocar enlaces o links es sumamente útil e importante ya que permite referenciar contenido ubicado en un lugar diferente a la página en la que estamos. De hecho al principio de esta entrada pasaste por uno, veamos como lo hacemos:


En la [entrada pasada](http://codehero.co/como-escribir-markdown-parte-i/)...
Colocamos entre corchetes [] el texto que queremos tenga el enlace y seguidamente colocamos entre paréntesis () el enlace de destino.

Si prefieres hacerlo de una manera más ordenada que tener las referencias en el medio de tu texto puedes hacerlo también de la siguiente manera:

```
[soy un link en linea](https://www.google.com)

[Soy un link en linea con titulo](https://www.google.com "Google's Homepage")

[soy un link de referencia][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

Existe una manera adicional de crear enlaces automáticos para direcciones URL,
 simplemente encerrarla entre los caracteres menor < que y mayor que >:

Some text to show that the reference links can follow later.

\[arbitrary case-insensitive reference text]: https://www.mozilla.org
\[1]: http://slashdot.org
\[link text itself]: http://www.reddit.com
```
Para crear referencias tambien se puede usar 

    [^enlace]
    
al final del documento se crea la correspodiente referencia con el contenido minimo de 

    [^enlace]:
    
De esta manera donde pongamos el codigo ```[^enlace]``` aparecerá una referencia representada por un numero y el enlace nos llevará a su descripción al final del texto.

Para ir al final pincha en el numero [^Fin]

[Subir](#indice)
<a id="tablas"></a>
##11)  Tablas 

Para Crear tablas dibujamos las líneas de la tabla con pipes (|) para delimitar las columnas y guiones (-) para separar el encabezado del resto de las filas:

```
| Encabezado 1    | Encabezado 2 |
|-----------------|--------------|
| probemos        | algo         |
| probemos alguna | otra cosa    |

```
Se vería así:

| Encabezado 1    | Encabezado 2 |
|-----------------|--------------|
| probemos        | algo         |
| probemos alguna | otra cosa    |


No es necesario que los pipes estén alineados, y los "bordes" son opcionales, por ejemplo:

```
Encabezado 1 | Encabezado 2
---|---
probemos | algo
probemos alguna | otra cosa

```
Esto generaría la misma tabla.

También puedes alinear el texto de tus columnas colocando el símbolo de dos puntos (:) en el separador hecho con guiones del lado que deseas que esté alineado:

```
| Alineado a la izq. | Centrado | Alineado a la der. |
|:-------------------|:--------:|-------------------:|
| prueba             | prueba   | prueba             |
```
Se vería así:

| Alineado a la izq. | Centrado | Alineado a la der. |
|:-------------------|:--------:|-------------------:|
| prueba             | prueba   | prueba             |

[Subir](#indice)
<a id="codigo"></a>
##12)  Código 

###Sintaxis de triple backtick *
Colocar este tipo de bloques es muy fácil, solo debemos encerrar el bloque de código que deseamos entre 3 backticks (\```) seguido del nombre del lenguaje al que pertenece el código que deseas colocar:

```lenguaje
x = y
...
```
Un ejemplo de código en JavaScript sería algo así:

```js
<script type="text/javascript">
  document.write("¡Hola, mundo!");
</script>
```

Para los diferentes lenguajes estas serían las abreviaturas que habría que colocar, si alguno no está en la lista puedes buscarlo en: <http://pygments.org/>

Abreviatura | Lenguaje
---|---
apache | configuración Apache
bash y console | Bash y Shell
bat | Fichero Batch DOS/Windows
boo | Boo
c | C
cpp | C++
csharp | C
css | Cascade Style Sheet (CSS)
diff ó udiff | Diff
erlang | Erlang
go | Go
haskell | Haskell
html | HTML
java | Java
js | javascript
latex | LaTeX
cl | Common Lisp
lua | Lua
mysql | MySQL
pascal y delphi | Pascal y Delphi
perl | Perl
php | PHP
python ó py ó pycon ó pytb ó python3 ó cython | Python
ruby | Ruby
scala | Scala
scheme | Scheme
smalltalk | Smalltalk
sql | SQL
sqlite3 | sqlite3
text | Texto simple monoespaciado
vala | Vala
vbnet | Visual Basic .NET
vim | Vim Script
xml |	 XML

Esto generaría un agradable bloque de código con syntax highlighting:

También podemos colocar bloques de texto pre-formateado sin especificar lenguaje alguno tan solo obviando la especificación del lenguaje de lo que colocaremos dentro de los backticks.


###Sintaxis de pre-espaciado

Otra manera de colocar texto o código pre-formateado pero sin lenguaje especificado es "indentando" nuestro texto con 4 espacios, lo escribiríamos así:

    hola esto es código tambien pero sin poner las comillas
    
ahora esto es texto normal

[Subir](#indice)
<a id="videos"></a>
##13)  Video / Iframe´s 


Podemos insertar en el documento con un codigo de iframe como el siguiente directamente de un video de youtube.

```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/6A5EpqqDOdk" frameborder="0"
 allowfullscreen></iframe>
```
El resultado sería el siguiente:

<iframe width="560" height="315" src="https://www.youtube.com/embed/6A5EpqqDOdk" frameborder="0" allowfullscreen></iframe>

[Subir](#indice)
<a id="comentarios"></a>
##14) Comentarios

Para insertar comentarios en MD y que solo sean visible en el código.

```
<!--Aquí va el comentario-->
```

<!--Este comentario no se ve en el documento HTML-->

[Subir](#indice)
<a id="extrasgh"></a>
##15) Extras en Github

Lista de tareas

    - [ x ] Tarea Completada
    - [   ] Tarea sin Completar

Mención al perfil de github

    @rmlp1024

Emojis:

    :boom: :camel:

[Subir](#indice)
<a id="teclas"></a>
##16) Teclas

Para introducir caracteres que hacen alusión a la pulsación de teclas, muy útil para manuales y guias  se pueden usar el siguiente código:

     <kbd>Cmd</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>
Quedando como resultado esto:

 <kbd>Cmd</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>
 
 En consecuencia cambia el tipo de letra y hace mas legible la guía.

[Subir](#indice)
 <a id="escape"></a>
##17) Escape

ESCAPE

Para conseguir poner caracteres reservados de markdown en un texto se utiliza el simbolo ```\``` contrabarra.

Esto se logra escribiendo:

```
\*Texto entre con asterisk\*

\_Texto entre con underscore\_
```
El resultado es este 

\*Texto entre con asterisk\*

\_Texto entre con underscore\_

Se pueden hacer escape de todos estos simbolos reservados de markdown

simbolo | nombre
---|---
\ |  backslash
` |  backtick
* |  asterisk
_ |  underscore
{}|  curly braces
[]|  square brackets
()|  parentheses
#|  hash mark
+ |  plus sign
- |  minus sign (hyphen)
. |  dot
! |  exclamation mark

      
[Subir](#indice)
 <a id="fuentes"></a>
##18) Fuentes:


* <http://codehero.co/como-escribir-markdown-parte-i/>
* <http://codehero.co/como-escribir-markdown-parte-ii/>
* <http://markdown.es/>
* <http://macdown.uranusjr.com/>
* <http://dillinger.io/>
* <https://stackedit.io/editor> EL BUENO
* <http://daringfireball.net/projects/markdown/>
* <https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet>
* <http://code.tutsplus.com/tutorials/markdown-the-ins-and-outs--net-25482>
* <http://joedicastro.com/pages/markdown.html>
* <https://es.wikipedia.org/wiki/Markdown>
* [wikipedia](https://commons.wikimedia.org/wiki/Category:Historical_images?uselang=es)

[^Fin]: Descripción del enlace

[Subir](#indice)