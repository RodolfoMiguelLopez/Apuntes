#Apuntes linux
===================================

##Indice:
- Directorios.
- Información básica.
- Comando para moverse. 
- Ayuda del sistema.
- Información del usuario.


###DIRECTORIOS

Directorio | Descripción
---|---
/: | raiz
/BIN/ 	| Comandos básicos todos los usuarios
/BOOT/ | Archivos de arranque
/DEV/ 	| Dispositivos del sistema
/ETC/ 	| Configuración del sistema y aplicaciones
/HOME/	| Directorio home de usuarios
/LIB/	| Librerías Núcleo del sistema y Módulos
/MNT/	| Punto de montaje temporal para dispositivos
/PROC/	| Procesos y variables del núcleo
/ROOT/ | Directorio home de Root
/SBIN/ | Comandos especiales para root
/TMP/	| Archivos Temporales
/USR/	| Segunda estructura jerárquica software
/VAR/	| Directorio para varias cosas, spoolers, logs, informacion variable.
/MEDIA/| Punto de Montaje
/OPT/	| **Sin Descripción**
/RUN/ | **Sin Descripción**
/SBIN/ | **Sin Descripción**
/srv/ | **Sin Descripción**
/sys/ | **Sin Descripción**
/tmp/ | **Sin Descripción**

###INFORMACION BASICA VITAL

Uso de la consola : explicacion prompt

```
usuario@equipo:directorio$ --> usuario en equipo no siendo root
root@equipo:directorio#  --> usuario en equipo siendo root
```


###COMANDOS PARA MOVERSE

Comando | Descripción
---|---
ls| listar archivos como el dir de windows
ls -a| lista todos los archivos tambien los  ocultos
ls -l| lista los archivos en columna + info ```ls -l -a = ls -la```
history|listado de comandos ejecutados en consola
!74 | ejecuta el comando de la lista de history nº74
pwd| Para saber directorio actual
cd ~ | Para ir al directorio HOME del usuario
cd | Directorio HOME del usuario
cd + xxx| Para ir a un directorio  ejemplo : cd home --> /home$
cd /| Directorio raiz
.| Directorio Actual
..|	 Directorio Superior
cd ..|	 Subir al directorio superior
ln| Para crear Accesos Directos
ls -s /ruta/nombrearchivo.extension nombre_link | crea un link
Tree| programa para ver directorios como arbol hay que instalarlo
apt-get tree | Instala Tree
more| al comienzo de un comando tabula la salida por pantalla
more cat /etc/group | para ver mas ir pulsando barra espaciadora
less| al comienzo de un comando tabula la salida por pantalla

###MANIPULACION DE ARCHIVOS

rm 			--> elimina archivos
rmdir		--> elimina directorios vacios
rm -r 		--> elinina directorios con contenido
cp 			--> copiar archivos
mv 			--> mover archivos , renombrar archivos
cat 		--> ver contenido de un archivo por terminal

###AYUDA DEL SISTEMA

man				--> Ayuda del sistema. Uso: man comando_a_buscar ENTER
					moverte dentro de man --> avpag y repag
					/palabra--> para buscar palabra
						n --> siguiente coincidencia
						N --> anterior coincidencia
						h --> ayuda
						q --> para salir de man
mandb			--> Actualizar Base de Datos de man
man -k	palabra	--> busca manuales o descripcion con esa palabra. No dentro del manual
apropos 		--> igual que [ man -k ]
whatis			--> informacion basica
info comando    --> informacion extendida

###PERMISOS

r read lectura
w write escritura
x execution ejecucion

- fichero
d directorio
l enlace

drwxrwxrwx ( d = directorio ) - ( 1º rwx = Permisos Propietario) - ( 2º rwx = Permisos grupo ) - ( 3º rwx = Permiso usuarios del sistema )

Con la siguiente tabla se puede ver las opciones disponibles para asignar permisos

Decimal		Binario		Significa
0			000			---
1			001			--x 	solo ejecucion
2			010			-w- 	solo escritura
3			011			-wx 	escritura y ejecucion
4			100			r-- 	solo lectura
5			101			r-x  	lectura y ejecucion
6			110			rw- 	lectura y escritura
7			111			rwx 	lectura , escritura y ejecucion

chmod		--> para cambiar permisos de un directorio, archivo o enlace
				chmod xxx nombre_fichero
				chmod 777 prueba.txt = frwxrwxrwx
				chmod 755 prueba.txt = frwxr-xr-x
chmod 		--> modo alternativo de usar chmod
				chmod [a,u,g,o](+,-)(r,w,x) nombre_fichero
				-a todos		+ poner	
				-u usuario 		- quitar
				-g grupo
				-o todos
chown 		--> para cambiar propietario del fichero
chgrp		--> para cambiar propietario del grupo
touch		--> para manipular fechas del fichero



###VARIOS COMANDOS

cal 		--> nuestra el calendario del mes
				cal -y --> muestra calendario anual
daate		--> muestra hora y fecha sistema

###INFO_USUARIO

whoami 		--> saber usuario actual
groups		--> saber en que grupos esta el usuario actual
id 			--> id usuario y grupos
su 			--> cambiar usuario sin cambiar shell
				su test --> cambia al usuario test si tiene pass lo pedira
sudo su 	--> cambia a usuario superadministrador normalmente root siempre pedira pass
newgrp		--> cambia a un nuevo grupo dentro de la sesion abierta.
who  		--> saber quien esta conectado en la misma maquina
w 			--> igual que comando anterior con + info
write		--> manda un mensaje por terminal a otro usuario
				write user tty --> puedes usar [w] para ver usuarios y tty
wall		--> manda un mensaje por terminal a todos los usuarios
mesg	 	--> activa o desactiva recibir mensajes

###USUARIOS Y GRUPOS

gnome_system_tools --> herramienta para gestionar usuarios y grupos hay que instalar
					gui ( graphic user intereface ) para administracion de usuarios

adduser		--> añadir usuario al sistema
useradd		--> añadir usuario al sistema
usermod		--> cambia opciones de passwd y shadow
chfn 		--> cambiar nommbre e informacion usuario
chsh		--> cambia shell del usuario
userdel 	--> borra usuario
deluser 	--> borra usuario
passwd 		--> cambia contraseñas y relacionados
addgroup	--> añadir grupo
groupadd	--> añadir grupo
delgroup	--> eliminar grupo
groupdel	--> eliminar grupo
gpasswd		--> cambia contraseña grupo

archivos donde se guarda la configuracion de los usuarios y grupos

/etc/passwd --> usuarios
/etc/shadow --> contraseñas usuarios
/etc/group 	--> grupos

###PATRONES Y BUSQUEDAS

* 			--> cero (0) o mas caracteres
? 			--> comodin por cualquier caracter pero solo 1
[]			--> uno de los caracteres del conjunto
[!]			--> uno de los caracteres que no existe en el conjunto

[:clase:] 	--> buscar clase de caracteres

[CLASE]	[SIGNIFICADO]
alnum	[A-Za-z0-9]
blank 	[\]
digit	[0-9A-Fa-f]
lower	[a-z]
punct	[.,¡!¿?:;]...
upper	[A-Z]
alpha	[A-Z a-z]
cntrl	[caracter de control]
graph 	[caracteres imprimibles sin espacios]
print	[caracteres imprimibles con espacios]
space 	[ ]
xdigit	[0-9A-Fa-f]

A-F 	caracteres de la A a la Z
\t 		es un tabulador
\n 		es un salto de linea


grep 	busca un cierto patrón en el contenido de los ficheros
cut 	separar en campos el contenido
head 	coger un determinado numero de lineas al principio
tail 	igual que el anterior pero al final
wc 		contar lineas 
diff 	compara ficheros
sdiff	mezcla archivos
updatedb	actualiza base de datos interna que usa el comando locate

##APUNTES DE CURSO DE YOUTUBE UBUNTU

###INSTALAR Y DESINSTALAR PROGRAMAS

Para instalar programas en linux hay 2 formas principales o por interfaz gráfica ( Centro de software, synaptic)
o a través de linea de comandos (aptitude, apt, dpkg)

Un paquete de software es un fichero único que incluye además del software.
- nombre y descripción
- nº de versión y distribuidor
- la suma de verificación (para comprobar su autenticidad)
- paquetes requeridos para que funcione llamados **dependencias**

hay varios tipos dependiendo del sistema para el que han sido diseñados.

.deb		(debian y derivados)
.rpm		(redhat, fedora, mandriva, suse)
.package	(paquetes autoejecutables)

alien aplicación para convertir .rpm a .deb

dentro de esos paquetes nos podemos encontrar con:

.bin 	el programa	
.run 	asistente gráfico

la lista de repositorios en ubuntu está en:
 en etc/apt/sources.list
y tiene la siguiente nomenclatura

deb_direccion_etiquetas

###USO DE APT INSTALAR Y DESISNTALAR PROGRAMAS

- sudo su 				(es necesario para poder usar la mayoria de comandos APT)
- apt-get update 		(Ver Actualizaciones) -- ¿actualiza las actualizaciones de los distintos repositorios?
- apt-get upgrade		(Actualizar paquetes)
- apt-cache search		(Busca paquetes con las palabras a buscar)
- - -

Ejemplo: busca programas con las palabras editor y html.
	
```bash
usuario#apt-cache search editor html
```

Mas información del paquete

```bash
Usuario#apt-cache search nombre_paquete
```

Ejemplo: nos dá información del paquete manpages_es

```bash
usuario#apt-cache search manpages_es
```


###Instalar las VirtualBox Guest Addition en UBUNTU 16.04

```bash
sudo apt-get install virtualbox-guest-dkms
```
## apuntes Introduccion a terminal y línea de comando ... organizar despues.

pwd
cd ~ ( Para hacer este símbolo en MAC es necesario pulsar ALT + Ñ
cd /
cd

archivos, directorios, links

para ver los archivos del sistema 
ls
para ver los tipos de archivo
ls -l

si en la columna de la izquierda los perisos empieza por:

- Es un archivo
d Es un directorio
l es un link

Estos son los tipo de inodo
https://es.wikipedia.org/wiki/Inodo


ls -lt --> para mostrar directorio por tipo y del mas actual al más antiguo
ls -lh --> para mostrar directorios por tipo y que el tamaño sea de fácil lectura

du --> disk usage 
du -h -d=1 --> Listado del peso de disco con 1 de profundidad y human readable

cd . --> Referencia al directorio actual
cd .. --> Directorio anterior

mkdir --> crear directorio
mv --> mover archivos

mv -flags [origin] [destino]
mv DSVC94.jpg fotos/
podemos hacer lo mismo estando dentro de directorio fotos
mv ../DSVC94.jpg ./ --> lo que hacemos es traer la foto del directorio anterior al directorio donde me encuentro ahora mismo

podemos mover archivos desde cualquier punto a cualquier otro siempre y cuando los referenciemos correctamente.

por ejemplo queremos mover todos los archivos con extensión .mp3 de nuestra carpeta de música a la carpeta donde me encuentro ahora

mv ~/Musica/*.mp3 . --> el . del final del archivo indica el directorio actual , si lo quisiera mover a otra carpeta distinta podría usar:

mv ~/Musica/*.mp3 ~/Escritorio/mp3/

el asterisco * se le denomina wildcard o comodines.

cp --> comando para copiar , usa la misma estructura que mv

para renombrar archivos se usa el mismo comando mv pero dentro del mismo directorio:

mv archivo_origina.txt archivo_renombrado.txt

touch :Actualiza los registros de fecha y hora, con la fecha y hora actual de los ficheros indicados como argumento. Si el fichero no existe, el comando touch lo crea. Su uso más frecuente es para crear archivos.

touch archivo.txt -->si existe lo abre y lo cierra
touch archivo.txt -->si no existe lo crea

links-->enlace simbólico a un archivo o directorio

ln -S archivo_original.txt archivo_link.txt

Comando rm

rm -r / --> Borra todo el sistema operativo
rm archivo_para_borrar --> borra un archivo (no pregunta)

para borrar un directorio es necesario tambien eliminar los archivos que contiene, nos podemos saltar esta limitación con 

rm -rf directorio/

para eliminar links es igual que un archivo , en este caso al ser un link no borra el archivo original solo el link.

--

bc -->calculadora 
bc -q --> sin los creditos
bc calculos --> para pasarle calculos en un archivo de texto
bc -q calculos --> igual que anterior pero sin creditos
quit para salir

--

*Extra* crear un archivo y abrirlo con un programa específico

touch calculos
open -a textedit calculos
--
md5 --> para que nos dé una huella digital del archivo
md5 archivo.xxx --> nos dá el Hash del archivo en md5
--
more o less --> son los mismos
sirve para mostrar contenido de archivos paginandoslo 
espacio --> avanzo
b--> vuelvo para atrás
q--> salgo
--
tail --> muestra por defecto las ultimas 10 lineas de un archivo
tail -f --> para estar escuchando un archivo y ver la salida en tiempo real
head --> muestra por defecto las primeras 10 lineas de un archivo
cat -->imprime un archivo por pantalla
man + comando que quieres saber como funciona--> manual
	- q salir
	- espacio -->avanza

path variable del sistema donde el sistema tiene permitido leer los ejecutables, separados por dos puntos.

eco $PATH

si queremos saber de donde se lee una app

which bc
which cat

la forma de ejecutar comandos pueden ser muy distintas a continuación os dejo unos ejemplos, hay que tener en cuenta que parámetro no es lo mismo que bandera, las banderas son opciones de ejecución de un programa, se podría decír que son como opciones del programa y parámetros son información que le pasamos al programa.

```
comando
comando -f 1 --banderas=1
comando parametro.txt
comando parametro_1.txt parametro_2.txt
comando -b -h 1 parametro.txt
```

Comando top : sirve para ver los procesos actuales del sistema, cada proceso tiene un PID que es un identificador único.

Una vez ejecutado top si pulsamos ```o```podemos ingresar un filtro por ejemplo CPU, MEM.

para ejecutar scripts por ejemplo de php pero es igual para cualquier otro lenguage:

se ejecuta el proceso normalmente
php ../scripts/ejemplo.php
se ejecuta el proceso y lo mando a background
devuelve valor PID para poder recuperarlo o matarlo
php ../scripts/ejemplo.php &
Matar procesos
kill -9 12547

process status muestra todos los procesos que se están ejecutando
ps -wA

El exit status es la forma que tiene el sistema de decirnos como ha terminado ese programa si por ejemplo ejecutamos ls que nos lista el arbol de directorio despues podemos usar el comando ```echo $?```y nos devolverá el valor del exit en este caso 0 significa que se ha ejecutado correctamente. si por el contrario ejecutamos ```lsdf```al no existir nos dice que no existe el comando si ejecutamos ```echo $?``` nos saldrá 1 que es terminado con errores o cualquier otro motivo.

Flujos

A modo de canales, conectan la entrada y salida (I/O) de un comando/aplicación con la terminal/consola cuando se ejecuta, son los siguientes:

standard input (stdin) 0
standard output (stdout) 1
standard error (stderr) 2

los numeros despues de los canales son identificadores

Usos que podemos dar estos tres canales para enviar y recoger los datos que surgen de la ejecución de un script, comando o aplicación.

standard input (stdin)0
Stdin, o standard input son los datos que son enviados al programa, normalmente stdin es texto enviado por el usuario.

standard output (stdout)1
A través de la salida estándar, “stdout” se reciben los datos que vuelca el comando o programa durante su ejecución, ejemplos sencillos de stdout serían por ejemplo el resultado de un “ls”,”cat” o cualquier otro comando de terminal. En cambio, hay otros comandos o programas que no muestran salida (a no ser que se especifique), como por ejemplo mover o copiar ficheros.

standard error (stderr)2
A través del canal stderr los programas o comandos suelen enviar el informe de error de la ejecución de un comando en caso de fallar. En nuestros scripts o comandos podemos combinar el uso de stdout y stderr para separar la salida estándar de los errores, almacenarlos en registros independientes o manipularlos por separado.

podemos enviar los datos que salen por standart input y standart error a un archivo para ello usamos el simbolo ```>```para crear un archivo y empezar desde cero ```>>``` con dos concatenamos y empieza al final del archivo si ya existe si no lo crea.

si ejecutamos un script podemos especificar que sale por cada salida pero si queremos que tanto el stdout y el stderr se mande a un archivo podemos hacerlo con ```2>&1```si solo queremos que mande los errores ```2>```si solo queremos que mande el stdout ```1>```

Tambien podemos usar ```|```tuberías comunmente llamados pipes son como concatenadores, la salida de un comando la une con la entrada de otro comando y si sucesivamente si hubiera más.

por ejemplo tenemos un archivo con operaciones que se llama calculo
```
1+2
3-4
5*6
2+H /* esto va a dar error */
7/8
```
para hacer los calculos con la calculadora podemos usar 

bc -q calculos

el stdout de cat va al stdin del bc

cat calculos | bc -q

el stdout de cat va al stdin del bc el stdout de bc va a un archivo 

cat calculos | bc -q > resultados

el stdout de cat va al stdin del bc el stdout de bc va a wc y la salida del wc va a un archivo 

cat calculos | bc -q | wc -l > numero de líneas



































