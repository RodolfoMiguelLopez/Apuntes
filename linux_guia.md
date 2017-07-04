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
cd| Para ir a un directorio  ejemplo : cd home --> /home$
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






























