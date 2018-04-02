# Apuntes Curso NDG Linux Essentials

## capitulo 1 (Tipos de comandos)

* Comandos integrados en el shell: Un buen ejemplo es el comando cd ya que es parte del bash shell. Cuando un usuario escribe el comando cd, el bash shell ya se está ejecutando y sabe cómo interpretar ese comando, sin requerir de ningún programa adicional para iniciarse.
* Comandos que se almacenan en archivos que son buscados por el shell: Si escribes un comando ls, entonces shell busca en los directorios que aparecen en la variable RUTA DE ACCESO (PATH) para tratar de encontrar un archivo llamado ls que puede ejecutar. Estos comandos se pueden ejecutar también escribiendo la ruta de acceso completa del comando.
* Alias: Un alias puede reemplazar un comando integrado, la función o un comando que se encuentra en un archivo. Los alias pueden ser útiles para la creación de nuevos comandos de funciones y comandos existentes.
* Funciones: Las funciones también pueden ser construidas usando los comandos existentes o crear nuevos comandos, reemplazar los comandos integrados en el shell o comandos almacenados en archivos. Los alias y las funciones normalmente se cargan desde los archivos de inicialización cuando se inicia el shell por primera vez, que veremos más adelante.

**Ejemplo de alias:**
supongamos que usamos mucho nuestro calendario, para hacerlo tenemos que ejecutar cada vez cal 2018 si queremos hacer una abreviatura podemos decirle que usaremos un alias de esta manera:  alias mical="cal2018", cada vez que ejecutemos mical verás tu calendario de 2018.

* **EOL** End of Life (Fin de ciclo de vida de soporte de aplicaciones)

* **LTS** Long Term Support (Largo periodo de soporte)


## capitulo 2 (Aplicaciones de código abierto y Licencias)


### El software de Linux cae generalmente en una de tres categorías:

* Software de servidor – software que no tiene ninguna interacción directa con el monitor y el teclado de la máquina en la que se ejecuta. Su propósito es servir de información a otras computadoras llamados clientes. A veces el software de servidor puede no interactuar con otros equipos, sin embrago, va a estar ahí sentado y "procesando" datos.
* Software de escritorio – un navegador web, editor de texto, reproductor de música u otro software con el que tú interactúas. En muchos casos, como un navegador web, el software consultará a un servidor en el otro extremo e interpretará los datos para ti. Aquí, el software de escritorio es el cliente.
* Herramientas – una categoría adicional de software que existe para que sea más fácil gestionar el sistema. Puedes tener una herramienta que te ayude a configurar la pantalla o algo que proporcione un shell de Linux o incluso herramientas más sofisticadas que convierten el código fuente en algo que la computadora pueda ejecutar.

### Aplicaciones de servidor

* Servidores web
	* Contenido estático: Paginas html estáticas
	* Contenido dinámico: Wordpress
usan el protocolo HTTP o HTTPS
El servidor web dominante es Apache, otro tambien muy usado es nginx se centra mas en el rendimiento.

* Correo Electrónico Cuando se habla de servidores de correo electrónico siempre es útil considerar las 3 funciones diferentes para recibir correo electrónico entre personas:

	* **Agente de transferencia de correo** _(MTA- Mail Transfer Agent)_ Decide qué servidor debe recibir el correo electrónico y utiliza el Protocolo simple de transferencia de correo _(SMTP- Simple Mail Transfer Protocol)_ para mover el correo electrónico hacia tal servidor. No es inusual que un correo electrónico tome varios "saltos" para llegar a su destino final, ya que una organización puede tener varios MTAs.
	* **Agente de entrega de correo** _(MDA- Mail Delivery Agent, también llamado el Agente de entrega local)_ se encarga de almacenar el correo electrónico en el buzón del usuario. Generalmente se invoca desde el MTA al final de la cadena.
	* **Servidor POP/IMAP** _(Post Office Protocol e Internet Message Access Protocol)_ son dos protocolos de comunicación que permiten a un cliente de correo funcionando en tu computadora actuar con un servidor remoto para recoger el correo electrónico.

A veces un software implementará varios componentes. En el mundo de código cerrado, Microsoft Exchange implementa todos los componentes
El MTA más conocido es sendmail. Postfix es otro MDA popular y pretende ser más simple y más seguro que sendmail.
Si utilizas formatos de archivo estándar para guardar mensajes de correo electrónico, tu MTA también puede entregar el correo. Como alternativa, puedes usar algo como procmail que te permite definir filtros personalizados para procesar el correo y filtrarlo.

Dovecot es un servidor POP/IMAP popular gracias a su facilidad de uso y bajo mantenimiento. Cyrus IMAP es otra opción.

- Compartir Archivos

Para compartir archivos, Samba es el ganador sin duda. Samba permite que una máquina Linux se parezca a una máquina Windows para que pueda compartir archivos y participar en un dominio de Windows.

Para compartir archivos, Samba es el ganador sin duda. Samba permite que una máquina Linux se parezca a una máquina Windows para que pueda compartir archivos y participar en un dominio de Windows.

- Directorio o DNS ( sistema de nombres de dominio)

DNS contiene también información global como la dirección de la MTA para un nombre de dominio proporcionado.
El Consorcio de Software de Internet (Internet Software Consortium), mantiene el servidor DNS más popular, llamado simplemente bind
El DNS se centra en gran parte en nombres de equipos y direcciones IP y no es fácilmente accesible. Han surgido otros directorios para almacenar información distinta tales como cuentas de usuario y roles de seguridad. El Protocolo ligero de acceso a directorios (LDAP- Lightweight Directory Access Protocol) es el directorio más común que alimenta también el Active Directory de Microsoft. En el LDAP, un objeto se almacena en una forma de árbol (ramificada), y la posición de tal objeto en el árbol se puede utilizar para obtener información sobre el objeto, además de lo que se almacena en el objeto en sí. Por ejemplo, un administrador de Linux puede almacenarse en una rama del árbol llamado "Departamento TI", que está debajo de una rama llamada "Operaciones". Así uno puede encontrar personal técnico buscando bajo la rama del Departamento TI. OpenLDAP es aquí el jugador dominante.

- DHCP
El trabajo de DHCP sirve para identificar las solicitudes y asignar una dirección disponible del grupo DHCP. La entidad Internet Software Consortium también mantiene el servidor ISC DHCP que es el jugador más común.

- Bases de datos
Las bases de datos más populares son MySQL y PostgreSQL. En la base de datos podrías ingresar datos de venta totales y luego usar un lenguaje llamado Lenguaje de consulta estructurado (SQL- Structured Query Language) para agregar ventas por producto y fecha con el fin de producir un informe.

ESCRITORIO

Antes de considerar las aplicaciones individuales, es útil conocer el entorno de escritorio. Un escritorio de Linux ejecuta un sistema llamado X Window, también conocido como X11. Un servidor Linux X11 es un X.org que hace que el software opere en un modo gráfico y acepte la entrada de un teclado y un ratón. Otro software controla a las ventanas y a los iconos, y se llama administrador de ventanas o entorno de escritorio. 

El administrador de ventanas es una versión más simple del entorno de escritorio, ya que sólo proporciona el código para dibujar menús y gestionar las ventanas de las aplicaciones en la pantalla

Los administradores de ventanas incluyen: Compiz, FVWM y Enlightenment, aunque hay muchos más. Los entornos de escritorio principalmente son KDE y GNOME, los cuales tienen sus propios administradores de ventanas

Herramientas ofimáticas: OpenOffice y LibreOffice
Navegadores web: Chrome y Firefox
Clientes de correo electrónico: Thunderbird, Evolution y Kmail
Herramientas creativas: Blender, Gimpl, Audacity

HERRAMIENTAS DE CONSOLA

El usuario recibe un mensaje, que normalmente termina en un signo de dólar ```$``` para indicar una cuenta sin privilegios. Cualquier cosa antes del símbolo, en este caso sysadmin@localhost:~, es un indicador configurable que proporciona información extra al usuario. En la imagen anterior, sysadmin es el nombre del usuario actual, localhost es el nombre del servidor, y ~ es el directorio actual (en UNIX, el símbolo de tilde es una forma corta para el directorio home del usuario).

Linux ofrece una variedad de shells para elegir, en su mayoría difieren en cómo y qué se puede modificar para requisitos particulares y la sintaxis del lenguaje “script” incorporado. Las dos familias principales son Bourne shell y C shell. Bourne shell recibió su nombre de su creador y C shell porque la sintaxis viene prestada del lenguaje C. Como ambos de estos shells fueron inventados en la década de 1970 existen versiones más modernas, el Bourne Again Shell (Bash) y tcsh (tee-cee-shell). Bash es el shell por defecto en la mayoría de los sistemas, aunque casi puedes estar seguro de que tcsh es disponible si lo prefieres.

Editores de texto por consola : Vim / emacs / pico / nanoç

Administradores de paquetes:

Si tienes un sistema Linux necesitarás agregar, quitar y actualizar el software. En cierto momento esto significaba descargar el código fuente, configurarlo, construirlo y copiar los archivos en cada sistema. Afortunadamente, las distribuciones crearon paquetes, es decir copias comprimidas de la aplicación. Un administrador de paquetes se encarga de hacer el seguimiento de que archivos que pertenecen a que paquete, y aun descargando las actualizaciones desde un servidor remoto llamado repositorio. En los sistemas Debian las herramientas incluyen dpkg, apt-get y apt-cache. En los sistemas derivados de Red Hat utilizas rpm y yum.

HERRAMIENTAS DE DESARROLLO

Los lenguajes informáticos proporcionan una manera para que un programador ingrese instrucciones en un formato más legible por el ser humano y que tales instrucciones sean eventualmente traducidas en algo que la computadora entiende. Los lenguajes pertenecen a uno de los dos campos: interpretado o compilado. Un lenguaje interpretado traduce el código escrito en código de computación mientras se ejecuta el programa, y el lenguaje compilado se traduce todo a la vez.

Ejemplos de lenguajes compilados
- C
- Java (Java Virtual Machine)
Ejemplos de lenguages interpretado
- Perl
- PHP
- Ruby (Framework: Ruby on Rails)
- Python

Un lenguaje es una herramienta que te ayuda a decirle al equipo lo que quieres hacer. Una librería empaqueta las tareas comunes en un paquete distinto que puede ser utilizado por el desarrollador. 

Ejemplos de librerías:

- ImageMagick es una librería o biblioteca que permite a los programadores manipular las imágenes en código. ImageMagick también incluye algunas herramientas de línea de comandos que le permiten procesar las imágenes desde un shell y aprovechan las capacidades de scripting.

- OpenSSL es una librería criptográfica que se utiliza en todo, desde servidores web hasta la línea de comandos. 
Proporciona un interfaz estándar para que puedas agregar criptografía en tu programa de Perl, por ejemplo.
-  librería de C

LICENCIAS

Microsoft Corporation posee la propiedad intelectual de Microsoft Windows. La licencia, el CLUF-Contrato de Licencia de Usuario Final (EULA-End User License Agreement) es un documento legal personalizado que debes leer e indicando su aceptación con un clic para que puedas instalar el software. Microsoft posee el código fuente y distribuye sólo copias de binarios a través de canales autorizados. La mayoría de los productos de consumo se les autoriza una instalación de software en una computadora y no se permite hacer otras copias del disco que no sea una copia de seguridad. No puedes revertir el software a código fuente utilizando ingeniería inversa. Pagas por una copia del software con la que obtienes actualizaciones menores, pero no las actualizaciones mayores.

Linux pertenece a Linus Torvalds. Él ha colocado el código bajo una licencia GNU Public License versión 2 (GPLv2). Esta licencia, entre otras cosas, dice que el código fuente debe hacerse disponible a quien lo pida y que puedes hacer cualquier cambio que desees. Una salvedad a esto es que si haces cambios y los distribuyes, debes poner tus cambios bajo la misma licencia para que otros puedan beneficiarse. GPLv2 dice también que no puedes cobrar por distribuir el código fuente a menos que sean tus costos reales de hacerlo (por ejemplo, copiar a medios extraíbles).

La FSF ha desarrollado su propio sistema de licencias, como la GPLv2 y GPLv3 y las versiones de licencias Lesser2 y 3 GPL (LGPLv2 y LGPLv3). Las licencias menores (lesser) son muy similares a las licencias regulares excepto que tienen disposiciones para enlazarlos contra un software no libre. Por ejemplo, bajo la licencia GPLv2 no puedes redistribuir el software que utiliza una librería de código cerrado (como un controlador de hardware) pero la variante menor permite tal acción.

La Open Source Initiative fue fundada en 1998 por Bruce Perens y Eric Raymond (ESR). Creen que el software libre también fue políticamente acusado y que eran necesarias licencias menos extremas, particularmente alrededor de los aspectos de copyleft de las licencias de la FSF. OSI cree que no sólo la fuente debe ser disponible libremente, pero también cero restricciones se deben aplicar sobre el uso del software sin importar el uso previsto.

Las licencias de la FSF, como la GPLv2, también son licencias de código abierto. Sin embargo, muchas licencias de software libre como BSD y la MIT no contienen las disposiciones de copyleft y por lo tanto no son aceptables para la FSF. Estas licencias se llaman licencias de software libre permisiva porque son permisivas en cómo puedes redistribuir el software. Puedes tomar un software bajo la licencia BSD e incluirla en un producto de software cerrado siempre que le des atribución adecuada.

FOSS

En lugar de afligirse por puntos más sensibles del código abierto frente al Software Libre, la comunidad ha comenzado a referirse a este concepto como Software Libre y de Código Abierto (FOSS). La palabra "libre" puede significar "gratuito como un almuerzo" (sin costo) o "libre como un discurso" (sin restricciones). Esta ambigüedad ha llevado a la inclusión de la palabra libre para referirse a la definición de este último concepto. De esta manera tenemos los términos de software gratuito/libre/de código abierto (FLOSS- Free/Libre/Open Source Software ).

Tales términos son convenientes, pero esconden las diferencias entre las dos escuelas de pensamiento. Por lo menos, si utilizas software FOSS sabes que no tienes que pagar por él y puedes redistribuirlo como quieres.

La organización de Creative Commons (CC) ha creado las Licencias de Creative Commons que tratan de satisfacer las intenciones detrás de las licencias de software libre para entidades no de software. Las licencias CC también pueden utilizarse para restringir el uso comercial si tal es el deseo del titular de los derechos de autor. Las licencias CC son:

•Attribution (CC BY) – al igual que la licencia BSD, puedes utilizar el contenido de la CC para cualquier uso, pero debes acreditar al titular los derechos de autor


•Attribution ShareAlike (CC BY-SA) – una versión copyleft de la licencia de atribución. Los trabajos derivadas deben compartirse bajo la misma licencia, mucho como en los ideales del Software Libre


•Attribution No-Derivs (CC BY-ND) – puedes redistribuir el contenido bajo las mismas condiciones como CC-BY, pero no lo puedes cambiar


•Attribution-NonCommercial (CC BY-NC) – al igual que CC BY, pero no lo puedes utilizar para los fines comerciales


•Attribution-NonCommercial-ShareAlike (CC-BY-NC-SA) – se basa en la licencia CC BY-NC, pero requiere que los cambios se compartan bajo la misma licencia.


•Attribution-NonCommercial-No-Derivs (CC-BY-NC-ND) – compartes el contenido para que se utilice con fines no comerciales, pero la gente no puede cambiar el contenido.


•No Rights Reservados (CC0) – esta es la versión de Creative Commons en el dominio público.

---capitulo 3

gufw es una interfaz gráfica para "Uncomplicated firewall" de Ubuntu.
Bajo el capó estás usando iptables que es el sistema firewall integrado. En lugar de introducir comandos iptables complicados, usas un GUI. Mientras que este GUI te permite construir una política efectiva de un escritorio, éste apenas araña la superficie de lo que se puede hacer con iptables.

---capitulo 4

La Interfaz de Línea de Comandos (CLI), es una interfaz basada en texto para la computadora, donde el usuario introduce un comando y la computadora lo ejecuta. El entorno de la CLI es proporcionado por una aplicación en la computadora conocida como un terminal.

El terminal acepta lo que el usuario escribe y lo pasa a un shell. El shell interpreta lo que el usuario ha introducido en las instrucciones que se pueden ejecutar con el sistema operativo. Si el comando produce una salida, entonces se muestra este texto en el terminal. Si surgen problemas con el comando, se muestra un mensaje de error.

prompt

La estructura del prompt puede variar entre las distribuciones, pero por lo general contiene información sobre el usuario y el sistema. A continuación te mostramos una estructura común de un prompt:

```
sysadmin@localhost:~$
```

El prompt anterior proporciona el nombre del usuario registrado en (sysadmin), el nombre del sistema (localhost) y el directorio actual (~). El símbolo ~ se utiliza como abreviación para el directorio principal del usuario (el directorio principal del usuario viene bajo el directorio /home (o «inicio» en español) y con el nombre de la cuenta de usuario, por ejemplo: /home/sysadmin).


El shell

El BASH shell tiene también otras funciones populares:
• Scripting: La capacidad de colocar los comandos en un archivo y ejecutar el archivo, resultando en todos los comandos siendo ejecutados. Esta función también tiene algunas características de programación, tales como las instrucciones condicionales y la habilidad de crear funciones (AKA, subrutinas). 
• Los Alias: La habilidad de crear "nicknames" (o «sobrenombres» en español) cortos para más comandos más largos. 
• Las Variables: Las Variables se utilizan para almacenar información para el BASH shell. Estas variables pueden utilizarse para modificar cómo las funciones y los comandos trabajan y proporcionan información vital sobre el sistema. 

Los comandos

El formato típico de un comando es el siguiente:
comando [opciones] [argumentos]

Las opciones se utilizan para modificar el comportamiento básico de un comando y los argumentos se utilizan para proporcionar información adicional (tal como un nombre de archivo o un nombre de usuario). Cada opción y argumento vienen normalmente separados por un espacio, aunque las opciones pueden a menudo ser combinadas

El comando ls proporciona ejemplos útiles. Por sí mismo, el comando ls listará los archivos y directorios contenidos en el directorio de trabajo actual:

```
sysadmin@localhost:~$ ls                                           
Desktop  Documents  Downloads  Music  Pictures  Public  Templates   Videos    
sysadmin@localhost:~$
```
Un argumento lo puedes pasar también al comando ls para especificar contenido de qué directorio hay que listar. Por ejemplo, el comando  ls /etc/ppp listará el contenido del directorio /etc/ppp en lugar del directorio actual:

```
sysadmin@localhost:~$ ls /etc/ppp                                 
ip-down.d  ip-up.d                                                
sysadmin@localhost:~$
```

Puesto que el comando ls acepta múltiples argumentos, puede listar el contenido de varios directorios a la vez, introduciendo el comando ls /etc/ppp /etc/ssh:

```
sysadmin@localhost:~$ ls /etc/ppp /etc/ssh         
/etc/ppp:                       
ip-down.d  ip-up.d                                  
/etc/ssh:                                                         
moduli               ssh_host_dsa_key.pub     ssh_host_rsa_key      sshd_configssh_config
ssh_host_ecdsa_key   ssh_host_rsa_key.pub         
ssh_host_dsa_key     ssh_host_ecdsa_key.pub   ssh_import_id            
sysadmin@localhost:~$
```
las opciones

Las opciones pueden utilizarse con comandos para ampliar o modificar el comportamiento de un comando. Las opciones son a menudo de una letra; sin embargo, a veces serán "palabras". Por lo general, los comandos viejos utilizan una letra, mientras los comandos nuevos utilizan palabras completas para las opciones. Opciones de una letra son precedidas por un único guión -. Opciones de palabra completa son precedidas por dos guiones --.

Por ejemplo, puedes utilizar la opción -l con el comando ls para ver más información sobre los archivos que se listan. El comando ls -l lista los archivos contenidos dentro del directorio actual y proporciona información adicional, tal como los permisos, el tamaño del archivo y otra información:

```
sysadmin@localhost:~$ ls -l                                       
total 0                                                           
drwxr-xr-x 1 sysadmin sysadmin 0 Jan 29  2015 Desktop             
drwxr-xr-x 1 sysadmin sysadmin 0 Jan 29  2015 Documents           
drwxr-xr-x 1 sysadmin sysadmin 0 Jan 29  2015 Downloads           
drwxr-xr-x 1 sysadmin sysadmin 0 Jan 29  2015 Music               
drwxr-xr-x 1 sysadmin sysadmin 0 Jan 29  2015 Pictures            
drwxr-xr-x 1 sysadmin sysadmin 0 Jan 29  2015 Public               
drwxr-xr-x 1 sysadmin sysadmin 0 Jan 29  2015 Templates           
drwxr-xr-x 1 sysadmin sysadmin 0 Jan 29  2015 Videos              
sysadmin@localhost:~$
```

En la mayoría de los casos, las opciones pueden utilizarse conjuntamente con otras opciones. Por ejemplo, los comandos ls -l -h o ls -lh listarán los archivos con sus detalles, pero se mostrará el tamaño de los archivos en formato de legibilidad humana en lugar del valor predeterminado (bytes):

```
sysadmin@localhost:~$ ls -l /usr/bin/perl                         
-rwxr-xr-x 2 root root 10376 Feb  4  2014 /usr/bin/perl         
sysadmin@localhost:~$ ls -lh /usr/bin/perl                        
-rwxr-xr-x 2 root root 11K Feb  4  2014 /usr/bin/perl            
sysadmin@localhost:~$
```

Nota que el ejemplo anterior también demostró cómo se pueden combinar opciones de una letra: -lh . El orden de las opciones combinadas no es importante.

La opción -h también tiene la forma de una palabra completa: --human-readable (--legibilidad-humana).

Las opciones a menudo pueden utilizarse con un argumento. De hecho, algunas de las opciones requieren sus propios argumentos. Puedes utilizar los argumentos y las opciones con el comando ls para listar el contenido de otro directorio al ejecutar el comando ls -l/etc/ppp:
```
sysadmin@localhost:~$ ls -l /etc/ppp   
total 0                                                            
drwxr-xr-x 1 root root 10 Jan 29  2015 ip-down.d                  
drwxr-xr-x 1 root root 10 Jan 29  2015 ip-up.d          
sysadmin@localhost:~$
```
Historial de Comandos
Al ejecutar un comando en una terminal, el comando se almacena en "history list" (o «lista de historial» en español). Esto está diseñado para que más adelante puedas ejecutar el mismo comando más fácilmente puesto que no necesitarás volver a introducir el comando entero.

Para ver la lista de historial de una terminal, utiliza el comando history (o «historial» en español):
```
sysadmin@localhost:~$ date                                       
Sun Nov  1 00:40:28 UTC 2015                                      
sysadmin@localhost:~$ ls                                           
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  
Videos       
sysadmin@localhost:~$ cal 5 2015                                  
    May 2015                                                      
Su Mo Tu We Th Fr Sa                                              
                1  2                                               
 3  4  5  6  7  8  9                                           
10 11 12 13 14 15 16                                              
17 18 19 20 21 22 23                                              
24 25 26 27 28 29 30                                               
31                                                                
sysadmin@localhost:~$ history                                   
    1  date                                                       
    2  ls                                                      
    3  cal 5 2015                                             
    4  history                                                 
sysadmin@localhost:~$
```
Pulsando la tecla de Flecha Hacia Arriba ↑ se mostrará el comando anterior en tu línea de prompt. Puedes presionar arriba repetidas veces para moverte a través del historial de comandos que hayas ejecutado. Presionando la tecla Entrar se ejecutará de nuevo el comando visualizado.

Cuando encuentres el comando que quieres ejecutar, puedes utilizar las teclas de Flecha Hacia Izquierda ← y Flecha Hacia Derecha → para colocar el cursor para edición. Otras teclas útiles para edición incluyen Inicio, Fin, Retroceso y Suprimir.

Si ves un comando que quieres ejecutar en la lista que haya generado el comando history, puedes ejecutar este comando introduciendo el signo de exclamación y luego el número al lado del comando, por ejemplo:
!3
```
sysadmin@localhost:~$ history                                     
    1  date                                                      
    2  ls                                                         
    3  cal 5 2015                                                 
    4  history                                                    
sysadmin@localhost:~$ !3                                        
cal 5 2015                                                        
     May 2015                                                     
Su Mo Tu We Th Fr Sa                                              
                1  2                                              
 3  4  5  6  7  8  9                                             
10 11 12 13 14 15 16                                              
17 18 19 20 21 22 23                                            
24 25 26 27 28 29 30                                               
                  31                                              
sysadmin@localhost:~$
```
Algunos ejemplos adicionales del history:


Ejemplo

Significado


history 5 Muestra los últimos cinco comandos de la lista del historial 
!! Ejecuta el último comando otra vez 
!-5 Ejecuta el quinto comando desde la parte inferior de la lista de historial 
!ls Ejecuta el comando ls más reciente 

4.5 Introduciendo las variables del BASH shell

Una variable del shell BASH es una función que te permite a ti o al shell almacenar los datos. Esta información puede utilizarse para proporcionar información crítica del sistema o para cambiar el comportamiento del funcionamiento del shell BASH (u otros comandos).

Las variables reciben nombres y se almacenan temporalmente en la memoria. Al cerrar una ventana de la terminal o shell, todas las variables se pierden. Sin embargo, el sistema automáticamente recrea muchas de estas variables cuando se abre un nuevo shell.

Para mostrar el valor de una variable, puedes utilizar el comando echo (o «eco» en español). El comando echo se utiliza para mostrar la salida en la terminal; en el ejemplo siguiente, el comando mostrará el valor de la variable HISTSIZE:

```
sysadmin@localhost:~$ echo $HISTSIZE                     
1000                                                             
sysadmin@localhost:~$
```

La variable HISTSIZE define cuántos comandos anteriores se pueden almacenar en la lista del historial. Para mostrar el valor de la variable debes utilizar un carácter del signo de dólar $ antes del nombre de la variable. Para modificar el valor de la variable, no se utiliza el carácter $:
```
sysadmin@localhost:~$ HISTSIZE=500                                            
sysadmin@localhost:~$ echo $HISTSIZE                              
500                                                             
sysadmin@localhost:~$
```
4.6 La Variable PATH

Una de las variables del shell BASH más importante que hay que entender es la variable PATH.

El término path (o «ruta» en español) se refiere a una lista que define en qué directorios el shell buscará los comandos. Si introduces un comando y recibes el error "command not found" (o «comando no encontrado» en español), es porque el shell BASH no pudo localizar un comando por ese nombre en cualquiera de los directorios en la ruta. El comando siguiente muestra la ruta del shell actual:
```
sysadmin@localhost:~$ echo $PATH                                        
/home/sysadmin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:
/usr/games                                                              
sysadmin@localhost:~$
```
Basado en la anterior salida, cuando intentas ejecutar un comando, el shell primero busca el comando en el directorio /home/sysadmin/bin. Si el comando se encuentra en ese directorio, entonces se ejecuta. Si no es encontrado, el shell buscará en el directorio /usr/local/sbin.

Si el comando no se encuentra en ningún directorio listado en la variable PATH, entonces recibirás un error, command not found:
```
sysadmin@localhost:~$ zed                                              
-bash: zed: command not found                                           
sysadmin@localhost:~$
```
Si en tu sistema tienes instalado un software personalizado, puede que necesites modificar la ruta PATH para que sea más fácil ejecutar estos comandos. Por ejemplo, el siguiente comando agregará el directorio /usr/bin/custom a la variable PATH:
```
sysadmin@localhost:~$ PATH=/usr/bin/custom:$PATH                        
sysadmin@localhost:~$ echo $PATH                                       
/usr/bin/custom:/home/sysadmin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games                                              
sysadmin@localhost:~$
```
4.7 Comando export

Hay dos tipos de variables utilizadas en el shell BASH, la local y la de entorno. Las variables de entorno, como PATH y HOME, las utiliza el BASH al interpretar los comandos y realizar las tareas. Las variables locales son a menudo asociadas con las tareas del usuario y son minúsculas por convención. Para crear una variable local, simplemente introduce:
```
sysadmin@localhost:~$ variable1='Something'
```

Para ver el contenido de la variable, te puedes referir a ella iniciando con el signo de ```$```:

```
sysadmin@localhost:~$ echo $variable1                                   
Something
```
Para ver las variables de entorno, utiliza el comando env (la búsqueda a través de la salida usando grep, tal como se muestra aquí, se tratará en los capítulos posteriores). En este caso, la búsqueda para variable1 en las variables de entorno resultará en una salida nula:
```
sysadmin@localhost:~$ env | grep variable1                              
sysadmin@localhost:~$
```
Después de exportar variable1 llegará a ser una variable de entorno. Observa que esta vez, se encuentra en la búsqueda a través de las variables de entorno:
```
sysadmin@localhost:~$ export variable1                                  
sysadmin@localhost:~$ env | grep variable1                             
variable1=Something
```
El comando export también puede utilizarse para hacer una variable de entorno en el momento de su creación:
```
sysadmin@localhost:~$ export variable2='Else'                           
sysadmin@localhost:~$ env | grep variable2                             
variable2=Else
```
Para cambiar el valor de una variable de entorno, simplemente omite el ```$``` al hacer referencia a tal valor:

```
sysadmin@localhost:~$ variable1=$variable1' '$variable2                
sysadmin@localhost:~$ echo $variable1                                   
Something Else
```
Las variables exportadas pueden eliminarse con el comando unset:
```
sysadmin@localhost:~$ unset variable2
```
> (hay que eliminar el símbolo ```$``` para poder eliminar la variable)

4.8 Comando which

Puede haber situaciones donde diferentes versiones del mismo comando se instalan en un sistema o donde los comandos son accesibles para algunos usuarios y a otros no. Si un comando no se comporta como se esperaba o si un comando no está accesible pero debería estarlo, puede ser beneficioso saber donde el shell encuentra tal comando o que versión está utilizando.

Sería tedioso tener que buscar manualmente en cada directorio que se muestra en la variable PATH. En su lugar, puedes utilizar el comando which (o «cuál» en español) para mostrar la ruta completa del comando en cuestión:
```
sysadmin@localhost:~$ which date                                       
/bin/date                                                               
sysadmin@localhost:~$ which cal                                        
/usr/bin/cal                                                            
sysadmin@localhost:~$
```
El comando which busca la ubicación de un comando buscando en la variable PATH.

4.9 Comando type

El comando type puede utilizarse para determinar la información acerca de varios comandos. Algunos comandos se originan de un archivo específico:

```
sysadmin@localhost:~$ type which                                       
which is hashed (/usr/bin/which)
```
Esta salida sería similar a la salida del comando which (tal como se explica en el apartado anterior, que muestra la ruta completa del comando):
```
sysadmin@localhost:~$ which which                         
/usr/bin/which
```
El comando type también puede identificar comandos integrados en el bash (u otro) shell:
```
sysadmin@localhost:~$ type echo                                     
echo is a shell builtin
```
En este caso, la salida es significativamente diferente de la salida del comando which:

```
sysadmin@localhost:~$ which echo                                        
/bin/echo
```
Usando la opción -a, el comando type también puede revelar la ruta de otro comando:
```
sysadmin@localhost:~$ type -a echo                                      
echo is a shell builtin                                                
echo is /bin/echo
```
El comando type también puede identificar a los aliases para otros comandos:
```
sysadmin@localhost:~$ type ll                                          
ll is aliased to `ls -alF'                                              
sysadmin@localhost:~$ type ls                                          
ls is aliased to `ls --color=auto'
```
La salida de estos comandos indican que ll es un alias para ls - alF, incluso ls es un alias para ls --color=auto. Una vez más, la salida es significativamente diferente del comando which:
```
sysadmin@localhost:~$ which ll                                          
sysadmin@localhost:~$ which ls                                         
/bin/ls
```
El comando type soporta otras opciones y puede buscar varios comandos al mismo tiempo. Para mostrar sólo una sola palabra que describe al echo, ll, y a los comandos which, utiliza la opción -t:
```
sysadmin@localhost:~$ type -t echo ll which                  
builtin                                                                
alias                                                             
file
```
4.10 Los Alias

Un alias puede utilizarse para asignar comandos más largos a secuencias más cortas. Cuando el shell ve un alias ejecutado, sustituye la secuencia más larga antes de proceder a interpretar los comandos.

Por ejemplo, el comando ls -l comúnmente tiene un alias l o ll. Ya que estos comandos más pequeñas son más fáciles de introducir, también es más rápido ejecutar la línea de comandos ls -l.

Puedes determinar qué alias se definen en el shell con el comando alias:
```
sysadmin@localhost:~$ alias   
alias alert='notify-send —urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'                                          
alias egrep='egrep --color=auto'                                       
alias fgrep='fgrep --color=auto'                                        
alias grep='grep --color=auto'                                          
alias l='ls -CF'                                                       
alias la='ls -A'                                                       
alias ll='ls -alF'                                                     
alias ls='ls --color=auto'
```
Los alias que ves en los ejemplos anteriores fueron creados por los archivos de inicialización. Estos archivos están diseñados para hacer automático el proceso de creación de los alias. Hablaremos sobre ellos con más detalle en un capítulo posterior.

Los nuevos alias se pueden crear introduciendo alias name=command (o «alias nombre=comando» en español), donde nombre es el nombre que quieres dar a el alias y comando es el comando que quieres que se ejecute cuando se ejecuta el alias.

Por ejemplo, puedes crear un alias de tal manera que lh muestre una lista larga de archivos, ordenados por tamaño con un tamaño "human friendly" (o «amigable para el usuario» en español) con el comando alias lh='ls -Shl'. Introduciendo lh debe ahora dar lugar a la misma salida que introduciendo el comando ls -Shl:
```
sysadmin@localhost:~$ alias lh='ls -Shl'                                      
sysadmin@localhost:~$ lh /etc/ppp                                          
total 0                                                                 
drwxr-xr-x 1 root root 10 Jan 29  2015 ip-down.d            
drwxr-xr-x 1 root root 10 Jan 29  2015 ip-up.d 
```

Los alias creados de esta manera sólo persistirán mientras el shell esté abierto. Una vez que el shell es cerrado, los nuevos alias que hayas creado, se perderán. Además, cada shell posee sus propios alias, así que si creas un alias en un shell y luego lo abres en otro shell, no verás el alias en el nuevo shell.

4.11 Globbing

Los caracteres de globbing se denominan a menudo como "comodines". Estos son símbolos que tienen un significado especial para el shell.

A diferencia de los comandos que ejecutará el shell, u opciones y argumentos que el shell pasará a los comandos, los comodines son interpretados por el mismo shell antes de que intente ejecutar cualquier comando. Esto significa que los comodines pueden utilizarse con cualquier comando.

4.11.1 Asterisco (*)

El asterisco se utiliza para representar cero o más de cualquier carácter en un nombre de archivo. Por ejemplo, supongamos que quieres visualizar todos los archivos en el directorio /etc que empiecen con la letra t:
```
sysadmin@localhost:~$ echo /etc/t*                              
/etc/terminfo /etc/timezone                                      
sysadmin@localhost:~$
```
El patrón t* significa "cualquier archivo que comienza con el carácter t y tiene cero o más de cualquier carácter después de la letra t".

Puedes usar el asterisco en cualquier lugar dentro del patrón del nombre de archivo. El siguiente ejemplo coincidirá con cualquier nombre de archivo en el directorio /etc que termina con .d:
```
sysadmin@localhost:~$ echo /etc/*.d                                 
/etc/apparmor.d /etc/bash_completion.d  /etc/cron.d /etc/depmod.d   /etc/fstab.d /etc/init.d /etc/insserv.conf.d /etc/ld.so.conf.d /etc/logrotate.d /etc/modprobe.d /etc/pam.d /etc/profile.d /etc/rc0.d /etc/rc1.d /etc/rc2.d /etc/rc3.d /etc/rc4.d /etc/rc5.d /etc/rc6.d /etc/rcS.d /etc/rsyslog.d /etc/sudoers.d /etc/sysctl.d  /etc/update-motd.d
```
En el ejemplo siguiente se mostrarán todos los archivos en el directorio /etc que comienzan con la letra r y terminan con .conf:
```
sysadmin@localhost:~$ echo /etc/r*.conf                             
/etc/resolv.conf /etc/rsyslog.conf
```
4.11.2 Signo de Interrogación (?)

El signo de interrogación representa cualquier carácter único. Cada carácter de signo de interrogación coincide con exactamente un carácter, nada más y nada menos.

Supongamos que quieres visualizar todos los archivos en el directorio /etc que comienzan con la letra t y que tienen exactamente 7 caracteres después del carácter de t:
```
sysadmin@localhost:~$ echo /etc/t???????      
/etc/terminfo /etc/timezone                                  
sysadmin@localhost:~$
```
Los comodines pueden utilizarse juntos para encontrar patrones más complejos. El comando ```echo /etc/*????????????????????``` imprimirá sólo los archivos del directorio /etc con veinte o más caracteres en el nombre del archivo:
```
sysadmin@localhost:~$ echo /etc/*????????????????????            
/etc/bindresvport.blacklist /etc/ca-certificates.conf            
sysadmin@localhost:~$
```
El asterisco y el signo de interrogación también podrían usarse juntos para buscar archivos con extensiones de tres letras ejecutando el comando ```echo /etc/*.???```:
```
sysadmin@localhost:~$ echo /etc/*.???                
/etc/blkid.tab /etc/issue.net                                
sysadmin@localhost:~$
```
4.11.3 Corchetes [ ]

Los corchetes se utilizan para coincidir con un carácter único representando un intervalo de caracteres que pueden coincidir con los caracteres. Por ejemplo, echo /etc/[gu]* imprimirá cualquier archivo que comienza con el carácter g o u y contiene cero o más caracteres adicionales:
```
sysadmin@localhost:~$ echo /etc/[gu]*                              
/etc/gai.conf /etc/groff /etc/group /etc/group- /etc/gshadow /etc/gshadow- /etc/ucf.conf /etc/udev /etc/ufw /etc/update-motd.d /etc/updatedb.conf            
sysadmin@localhost:~$
```
Los corchetes también pueden ser utilizados para representar un intervalo de caracteres. Por ejemplo, el comando echo /etc/[a-d]* mostrará todos los archivos que comiencen con cualquier letra entre e incluyendo a y d:
```
sysadmin@localhost:~$ echo /etc/[a-d]*                             
/etc/adduser.conf /etc/adjtime /etc/alternatives /etc/apparmor.d 
/etc/apt /etc/bash.bashrc /etc/bash_completion.d /etc/bind /etc/bindresvport.blacklist /etc/blkid.conf /etc/blkid.tab /etc/ca-certificates /etc/ca-certificates.conf /etc/calendar /etc/cron.d /etc/cron.daily /etc/cron.hourly /etc/cron.monthly /etc/cron.weekly /etc/crontab /etc/dbus-1 /etc/debconf.conf /etc/debian_version /etc/default 
/etc/deluser.conf /etc/depmod.d /etc/dpkg                          
sysadmin@localhost:~$
```
El comando ```echo /etc/*[0-9]*``` mostrará todos los archivos que contienen al menos un número:
```
sysadmien@localhost:~$ echo /etc/*[0-9]*                            
/etc/dbus-1 /etc/iproute2 /etc/mke2fs.conf /etc/python2.7 /etc/rc0.d
/etc/rc1.d /etc/rc2.d /etc/rc3.d /etc/rc4.d /etc/rc5.d /etc/rc6.d   
sysadmin@localhost:~$
```
El intervalo se basa en el cuadro de texto de ASCII. Esta tabla define una lista de caracteres disponiéndolos en un orden estándar específico. Si proporcionas un orden inválido, no se registrará ninguna coincidencia:
```
sysadmin@localhost:~$ echo /etc/*[9-0]*                           
/etc/*[9-0]*                                                       
sysadmin@localhost:~$
```
4.11.4 Signo de Exclamación (!)

El signo de exclamación se utiliza en conjunto con los corchetes para negar un intervalo. Por ejemplo, el comando echo [!DP]* mostrará cualquier archivo que no comienza con D o P.

4.12 Las Comillas

Hay tres tipos de comillas que tienen significado especial para el shell Bash: comillas dobles ", comillas simples ' y comilla invertida `. Cada conjunto de comillas indica al shell que debe tratar el texto dentro de las comillas de una manera distinta a la normal.

4.12.1 Comillas Dobles

Las comillas dobles detendrán al shell de la interpretación de algunos metacaracteres, incluyendo los comodines. Dentro de las comillas dobles, el asterisco es sólo un asterisco, un signo de interrogación es sólo un signo de interrogación y así sucesivamente. Esto significa que cuando se utiliza el segundo comando echo más abajo, el shell BASH no convierte el patrón de globbing en nombres de archivos que coinciden con el patrón:
```
sysadmin@localhost:~$ echo /etc/[DP]*                                         
/etc/DIR_COLORS /etc/DIR_COLORS.256color /etc/DIR_COLORS.lightbgcolor /etc/PackageKit                                                                  
sysadmin@localhost:~$ echo "/etc/[DP]*"                                       
/etc/[DP]*                                                                    
sysadmin@localhost:~$
```
Esto es útil cuando quieres mostrar algo en la pantalla, lo que suele ser un carácter especial para el shell:
```
sysadmin@localhost:~$ echo "The glob characters are *, ? and [ ]"      
The glob characters are *, ? and [ ]                                   
sysadmin@localhost:~$
```

Las comillas dobles todavía permiten la sustitución de comando (se tratará más adelante en este capítulo), sustitución de variable y permiten algunos metacaracteres de shell sobre los que aún no hemos hablado. Por ejemplo, en la siguiente demostración, notarás que el valor de la variable PATH es desplegada:
```
sysadmin@localhost:~$ echo "The path is $PATH"                          
The path is /usr/bin/custom:/home/sysadmin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games                          
sysadmin@localhost:~$
```
4.12.2 Comillas Simples

Las comillas simples evitan que el shell interprete algunos caracteres especiales. Esto incluye comodines, variables, sustitución de comando y otro metacarácter que aún no hemos visto.

Por ejemplo, si quieres que el carácter $ simplemente signifique un $, en lugar de actuar como un indicador del shell para buscar el valor de una variable, puedes ejecutar el segundo comando que se muestra a continuación:
```
sysadmin@localhost:~$ echo The car costs $100                           
The car costs 00                                                        
sysadmin@localhost:~$ echo 'The car costs $100'                        
The car costs $100                                                      
sysadmin@localhost:~$
```
4.12.3 Barra Diagonal Inversa (\) Carácter de escape

Puedes utilizar una técnica alternativa para citar un carácter con comillas simples. Por ejemplo, supón que quieres imprimir lo siguiente: ```“The services costs $100 and the path is $PATH"```. Si pones esto entre las comillas dobles, ```$1 y $PATH``` se consideran variables. Si pones esto entre las comillas simples, ```$1 y $PATH``` no son variables. Pero ¿qué pasa si quieres tener ```$PATH tratado como una variable y no a $1```?

Si colocas una barra diagonal invertida \ antes del otro carácter, tratará al otro carácter como un carácter de "comillas simples". El tercer comando más abajo muestra cómo utilizar el carácter \, mientras que los otros dos muestran cómo las variables serían tratadas si las pones entre las comillas dobles y simples:
```
sysadmin@localhost:~$ echo "The service costs $100 and the path is $PATH"
The service costs 00 and the path is /usr/bin/custom:/home/sysadmin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games 
sysadmin@localhost:~$ echo 'The service costs $100 and the path is $PATH' 
The service costs $100 and the path is $PATH                         
sysadmin@localhost:~$ echo The service costs \$100 and the path is $PATH
The service costs $100 and the path is /usr/bin/custom:/home/sysadmin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games 
sysadmin@localhost:~$
```
4.12.4 Comilla Invertida

Las comillas invertidas se utilizan para especificar un comando dentro de un comando, un proceso de sustitución del comando. Esto permite un uso muy potente y sofisticado de los comandos.

Aunque puede sonar confuso, un ejemplo debe hacer las cosas más claras. Para empezar, fíjate en la salida del comando date:
```
sysadmin@localhost:~$ date                                           
Mon Nov  2 03:35:50 UTC 2015
```
Ahora fíjate en la salida de la línea de comandos echo Today is date (o «eco La fecha de hoy es» en español):
```
sysadmin@localhost:~$ echo Today is date                               
Today is date                                                           
sysadmin@localhost:~$
```
En el comando anterior la palabra date (o «fecha» en español) es tratada como texto normal y el shell simplemente pasa date al comando echo. Pero, probablemente quieras ejecutar el comando date y tener la salida de ese comando enviado al comando echo. Para lograr esto, deberás ejecutar la línea de comandos echo Today is `date`:
```
sysadmin@localhost:~$ echo Today is `date`                         
Today is Mon Nov 2 03:40:04 UTC 2015                         
sysadmin@localhost:~$
```
4.13 Instrucciones de Control

Las instrucciones de control te permiten utilizar varios comandos a la vez o ejecutar comandos adicionales, dependiendo del éxito de un comando anterior. Normalmente estas instrucciones de control se utilizan en scripts o secuencias de comandos, pero también pueden ser utilizadas en la línea de comandos.

4.13.1 Punto y Coma

El punto y coma puede utilizarse para ejecutar varios comandos, uno tras otro. Cada comando se ejecuta de forma independiente y consecutiva; no importa el resultado del primer comando, el segundo comando se ejecutará una vez que el primero haya terminado, luego el tercero y así sucesivamente.

Por ejemplo, si quieres imprimir los meses de enero, febrero y marzo de 2015, puedes ejecutar cal 1 2015; cal 2 2015; cal 3 2015 en la línea de comandos:
```
sysadmin@localhost:~$ cal 1 2015; cal 2 2015; cal 3 2015               
    January 2015                                                        
Su Mo Tu We Th Fr Sa                                 
             1  2  3                                            
 4  5  6  7  8  9 10                                            
11 12 13 14 15 16 17                                                 
18 19 20 21 22 23 24                                                    
25 26 27 28 29 30 31                                                            
                                                               
    February 2015                                                     
Su Mo Tu We Th Fr Sa                                                   
 1  2  3  4  5  6  7                                                   
 8  9 10 11 12 13 14                                                   
15 16 17 18 19 20 21                                                   
22 23 24 25 26 27 28                                                           

     March 2015                                                        
Su Mo Tu We Th Fr Sa                                                   
 1  2  3  4  5  6  7                                                   
 8  9 10 11 12 13 14                                                  
15 16 17 18 19 20 21                                                   
22 23 24 25 26 27 28                                                   
29 30 31 
```

4.13.2 Ampersand Doble (&&)

El símbolo de ampersand doble && actúa como un operador "y" lógico. Si el primer comando tiene éxito, entonces el segundo comando (a la derecha de la &&) también se ejecutará. Si el primer comando falla, entonces el segundo comando no se ejecutará.

Para entender mejor como funciona esto, consideremos primero el concepto de fracaso y éxito para los comandos. Los comandos tienen éxito cuando algo funciona bien y fallan cuando algo sale mal. Por ejemplo, considera la línea de comandos ls /etc/xml. El comando tendrá éxito si el directorio /etc/xml es accesible y fallará cuando no es accesible.

Por ejemplo, el primer comando tendrá éxito porque el directorio /etc/xml existe y es accesible mientras que el segundo comando fallará porque no hay un directorio /junk:
```
sysadmin@localhost:~$ ls /etc/xml                  
catalog  catalog.old  xml-core.xml  xml-core.xml.old           
sysadmin@localhost:~$ ls /etc/junk                             
ls: cannot access /etc/junk: No such file or directory
sysadmin@localhost:~$
```
La manera en que usarías el éxito o fracaso del comando ls junto con && sería ejecutando una línea de comandos como la siguiente:
```
sysadmin@localhost:~$ ls /etc/xml && echo success          
catalog  catalog.old  xml-core.xml  xml-core.xml.old        
success                                              
sysadmin@localhost:~$ ls /etc/junk && echo success          
ls: cannot access /etc/junk: No such file or directory           
sysadmin@localhost:~$
```
En el primer ejemplo arriba, el comando echo fue ejecutado, porque tuvo éxito el comando ls. En el segundo ejemplo, el comando echo no fue ejecutado debido a que el comando ls falló.

### 4.13.3 Línea Vertical Doble 

La línea vertical doble ```||``` es un operador lógico ```"o"```. Funciona de manera similar a ```&&```; dependiendo del resultado del primer comando, el segundo comando se ejecutará o será omitido.

Con la línea vertical doble, si el primer comando se ejecuta con éxito, el segundo comando es omitido. Si el primer comando falla, entonces se ejecutará el segundo comando. 

En otras palabras, esencialmente estás diciendo al shell, **"O bien ejecuta este primer comando o bien el segundo"**.

En el ejemplo siguiente, el comando echo se ejecutará sólo si falla el comando ls:

```
sysadmin@localhost:~$ ls /etc/xml || echo failed                 
catalog  catalog.old  xml-core.xml  xml-core.xml.old               
sysadmin@localhost:~$ ls /etc/junk || echo failed                  
ls: cannot access /etc/junk: No such file or directory             
failed                                                            
sysadmin@localhost:~$
```

### Practica Capítulo 3

**whoami**: muestra el nombre del usuario actual

**uname**: muestra información sobre el sistema que se está utilizando

**pwd**: directorio de trabajo actual   ( Print Working Directory) 

Linux utiliza la barra diagonal ```/``` para separar los directorios para crear lo que se denomina ruta. La barra diagonal inicial representa el directorio de nivel superior, conocido como el directorio **root** .

La tilde ```~```  que ves en el **prompt** también está indicando cuál es el directorio actual. Este carácter es una forma de _«acceso directo»_ para representar tu **home**.

**echo**: se puede utilizar para imprimir el texto, el valor de una variable y mostrar cómo el entorno del shell expande los metacaracteres.

```
echo $PATH
```
Muestra el valor de una variable

___


Comando | Descripción
---|---
```echo * ``` | Busca «cero o más» coincidencias de caracteres en un nombre de archivo
```echo P*``` | Muestra todos los archivos en el directorio actual que comienzan con la letra **P**
```echo *s```|Muestra todos los archivos en tu directorio actual que terminan en la letra **s**
```echo D*n*s```| Muestra los archivos que empiezen por **D** contengan **n** y terminen en **s**
```echo ??????```| Muestra los nombres de archivos que tienen exactamente 6 caracteres
```echo D????????```| Muestra los nombres de archivos que empiezan por **D** y que tienen 8 caracteres más
```echo ?????*s```| Muestra los nombres de archivo que tienen al menos seis caracteres y terminan en la letra **s**
```echo [DP]*```| el primer carácter del nombre de archivo puede ser o bien una **D** o una **P**
```echo [!DP]*```|el primer carácter puede ser cualquier carácter excepto una **D** o **P**
```echo [D-P]*```| El primer carácter del nombre de archivo puede ser cualquier carácter que comienze cualquier carácter entre la  **D** y la **P**
```echo [!D-P]*```| Cualquier carácter individual coincidirá, excepto si está entre la letra **D** y la **P**


Te podrías preguntar «¿quién decide qué letras haya entre la D y la P? ». En este caso la respuesta es bastante obvia (E, F, G, H, I, J, K, L, M, N y O), pero ¿qué tal que el rango fuese [1-A]?

Para determinar el rango de caracteres se utiliza la tabla de texto ASCII.

```
ascii
```

Por lo tanto, ¿con qué caracteres coincidirá el glob [1-A] ? De acuerdo con la tabla de texto ASCII: 1, 2, 3, 4, 5, 6, 7, 8, 9, :, ;, <, =, >, ?, @ y A.

___

El uso de las comillas


* Comillas invertidas:
Uso de las comillas invertidas para usar un comando dentro de un cadena de texto

```
sysadmin@localhost:~$ echo Today is `date`
Today is Tue Jan 19 15:48:57 UTC 2016

```
Colocar el comando entre comillas y simbolo dolar antes tiene el mismo efecto

```
sysadmin@localhost:~$ echo Today is $(date)
Today is Tue Jan 19 15:51:09 UTC 2016

```
* Comillas simples

Si no quieres que algo se ejecute puedes poner comillas simples alrededor del comando
```
sysadmin@localhost:~$ echo This is the command '`date`'
This is the command `date`


```
Tambien puedes usar la barra invertida **\** delante de las comillas.

```
sysadmin@localhost:~$ echo This is the command \`date\`
This is the command `date`

```
* Comillas dobles

Las comillas dobles no tienen ningún efecto sobre las comillas invertidas. El shell las seguirá utilizando como una sustitución del comando.

```
sysadmin@localhost:~$ echo This is the command "`date`"
This is the command Tue Jan 19 16:05:41 UTC 2016
```
Las comillas dobles tendrán efecto sobre los caracteres comodín de tal manera que deshabilitan su significado especial.

```
sysadmin@localhost:~$ echo D*
Desktop Documents Downloads
sysadmin@localhost:~$ echo "D*"
D*

```
___

**Las Instrucciones de Control**

Por lo general, introduces un solo comando y lo ejecutas presionando Entrar. El shell Bash ofrece tres estados diferentes que se pueden utilizar para separar varios comandos escritos juntos.

El separador más simple es el punto y coma **(;)**. El uso de punto y coma entre múltiples comandos les permite ejecutarse el uno tras el otro de forma secuencial de la izquierda a la derecha.

Los caraceters **&&** crean una lógica e instrucción. Los comandos separados por **&&** se ejecutan de manera condicional. Si el comando a la izquierda de **&&** tiene éxito, entonces el comando a la derecha de **&&** también será ejecutado. Si el comando a la izquierda de **&&** falla, entonces el comando a la derecha de la **&&** no se ejecuta.

Los caracteres **||** crean una lógica o una instrucción que también causa una ejecución condicional. Cuando los comandos están separados por **||**, entonces sólo si el comando a la izquierda falla, el comando a la derecha de **||** se ejecuta. Si el comando a la izquierda de **||** tiene éxito, entonces el comando a la derecha de la **||** no se ejecuta.

##### Ejemplo de uso de (;)

* Ejecutar tres comandos uno seguido de otro

```
sysadmin@localhost:~$ echo Hello; echo Linux; echo Student
Hello
Linux
Student
sysadmin@localhost:~$
```
Todos los comandos se ejecutan correctamente y de forma secuencia.

* Ejecutamos tres comandos pero hacemos que uno de ellos falle

```
sysadmin@localhost:~$ false; echo Not; echo Conditional          
Not
Conditional
sysadmin@localhost:~$
```
Ten en cuenta que en el ejemplo anterior, los tres comandos se ejecutan a pesar de que el primero falle. Aunque no lo puedes ver en la salida del comando false, éste se ejecutó. Sin embargo, cuando los comandos están separadas por el carácter **;**, son completamente independientes entre sí.

##### Ejemplo de uso de (&&)

* Ejecutamos tres comandos y utilizamos el separador & para separarlos.

```
sysadmin@localhost:~$ echo Start && echo Going && echo Gone          
Start
Going
Gone
sysadmin@localhost:~$
```
Todas las instrucciones se ha ejecutado correctamente.

* Ejecutamos tres comandos y provocamos que uno de ellos falle

```
sysadmin@localhost:~$ echo Success && false && echo Bye
Success
sysadmin@localhost:~$
```
Como vemos el primer comando se ha ejecutado correctamente y como el segundo ha fallado el tercero ya no se ha ejecutado.

##### Ejemplo de uso (||)

* Ejecutamos dos instrucciones con el separador ||

```
sysadmin@localhost:~$ false || echo Fail Or
Fail Or
sysadmin@localhost:~$ true || echo Nothing to see here
sysadmin@localhost:~$
```

Los carácteres or que separan los siguientes comandos muestra cómo el fracaso antes de la instrucción or provoca que el siguiente comando sea ejecutado; sin embargo, la primera instrucción exitosa hace que el comando no se ejecute

___

Comando | Descripción
---|---
history | Muestra un historial de los últimos comandos ejecutados en la shell.
history !2 | Ejecuta el comando de la lista que está en la posición 2.
history 5 | Muestra los 5 últimos comandos ejecutados.

## Capítulo 5 (Encontrar Ayuda)

Para ver la ayuda de un comando podemos ejecutar su manual.

Por ejemplo para ver el manual del comando calc ```man calc```

El comando man utiliza un __«localizador»_ para mostrar documentos. Este localizador es normalmente el comando less, pero en algunas distribuciones puede ser el comando **more**. Ambos son muy similares en cómo se ejecutan.

Si quieres ver los diferentes comandos de movimiento que están disponibles, puedes introducir la letra **h** mientras visualizas una página man. Esto mostrará una página de ayuda.

Resumen de teclas abreviadas ayuda de man

Comando | Función
---|---
Return (o Intro) | Bajar una línea 
Space (o Espacio) |  Bajar una página 
/term(o /término | Buscar un término  
n | Buscar el siguiente elemento de la búsqueda 
1G | Ir a Inicio 
G | Ir a la final 
h | Mostrar ayuda 
q | Cerrar página man 

##### Las Secciones de la Página man

Las páginas man se dividen en secciones.La siguiente tabla describe algunas de las secciones más comunes que encontrarás en las páginas del comando man:


Nombre de la Sección | Propósito
---|---
NAME (o Nombre en español) | Proporciona el nombre del comando y una breve descripción. 
SYNOPSIS (Sinopsis) | Proporciona ejemplos de cómo se ejecuta el comando. Información detallada a continuación. 
DESCRIPTION (Descripción) | Proporciona una descripción más detallada del comando. 
OPTIONS (Opciones) |Muestra las opciones para el comando, así como una descripción de cómo se utilizan. A menudo esta información se encontrará en la sección DESCRIPTION (o «DESCRIPCIÓN» en español) y no en una sección separada de OPTIONS (o «OPCIONES» en español). 
FILES | (Archivos) Muestra las opciones para el comando, así como una descripción de cómo se utilizan. Estos archivos pueden utilizarse para configurar las características más avanzadas del comando. A menudo esta información se encontrará en la sección de DESCRIPTION y no en una sección separada de OPTIONS. 
AUTHOR (Autor) | El nombre de la persona que creó la página man y (a veces) la manera de contactar a la persona.  
REPORTING BUGS | (Reportando Errores) Proporciona información sobre cómo reportar problemas con el comando. 
COPYRIGHT | (Derechos de Autor) Proporciona información básica de los derechos de autor. 
SEE ALSO (Ver También) | Proporciona una idea de dónde puedes encontrar información adicional. También suele incluir otros comandos que están relacionados con este comando. 

##### SYNOPSIS de la Página man

La sección de SYNOPSIS (o «SINOPSIS» en español) de una página man puede ser difícil de entender, pero es muy importante porque proporciona un ejemplo conciso de cómo utilizar el comando. Por ejemplo, considera la SYNOPSIS de la página man para el comando cal:

```
SYNOPSIS                                                              
     cal [-3hjy] [-A number] [-B number] [[[day] month] year]
```

Los corchetes [ ] se utilizan para indicar que esta característica no es necesaria para ejecutar el comando. Por ejemplo, [-3hjy] significa que puedes usar las opciones -h, -j, -y, 1 o 3, pero ninguna de estas opciones son necesarias para el correcto funcionamiento del comando **cal**.

El segundo conjunto de corchetes en la SYNOPSIS del comandocal ([[[day] month] year]) muestra otra característica. Esto significa que puedes especificar un año por sí mismo, pero si se especifica un mes también se debe especificar un año. Además, si especificas un día entonces también necesitarás especificar un mes y un año.

Otro componente de SYNOPSIS que puede causar cierta confusión puede verse en SYNOPSIS del comando date:

```
SYNOPSIS                                                              
       date [OPTION]... [+FORMAT]                                      
       date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]
```

En esta SYNOPSIS hay dos sintaxis para el comando date. El primero de ellos se utiliza para mostrar la fecha en el sistema mientras que el segundo se utiliza para fijar la fecha.

Las puntos suspensivos siguientes a [OPTION], ..., indican que uno o más ítems antes de la opción pueden usarse.

Además, la notación [-u|--utc|--universal] significa que puedes utilizar la opción -u , la opción --utc o la opción --universal . Normalmente esto significa que las tres opciones hacen lo mismo, pero a veces este formato (uso del carácter |) sirve para indicar que no se utilicen las opciones combinadas, tal como un operador lógico «o».

##### Buscando dentro de la Página man

Para buscar un término en la página man, pulsa / e introduce el término seguido por la tecla Enter. El programa buscará desde la ubicación actual hacia el final de la página para tratar de localizar y resaltar el término.

> Las búsquedas dentro de man no diferencian entre MAYUSCULAS Y minúsculas.

Si el término no se encuentra, o has llegado al final de las coincidencias, el programa reportará Pattern not found (press Return) (o «Patrón no encontrado (presiona Regresar)» en español). Si se encuentra una coincidencia y quieres pasar al siguiente término, pulsa n. Para volver al término anterior pulsa N.

##### Las Páginas man Categorizadas por Secciones

Hasta ahora, hemos estado visualizando las páginas man de comandos. Sin embargo, a veces los archivos de configuración también tienen sus páginas man. Los archivos de configuración (a veces llamados archivos de sistema) contienen datos que se utilizan para almacenar información sobre el Sistema Operativo o servicios, hay miles de páginas man en una distribución típica de Linux.

Por defecto, hay nueve secciones de las páginas man:

1. Programas ejecutables o comandos del shell
2. Llamadas del sistema (funciones proporcionados por el kernel)
3. Llamadas de la librería (funciones dentro de las librerías de los programas)
4. Archivos especiales (generalmente se encuentran en /dev)
5. Formatos de archivo y convenciones, por ejemplo /etc/passwd 
6. Juegos
7. Otros (incluyendo paquetes macro y convenciones), por ejemplo, man(7), groff(7) 
8. Comandos de administración de sistema (generalmente sólo para el root)
9. Rutinas del kernel [No estándar]

Cuando utilizas el comando **man**, éste busca cada una de estas secciones por orden hasta que encuentra al primer "match" o coincidencia.

Por ejemplo, si ejecutas el comando ```man cal```, en la primera sección (programas ejecutables o comandos del shell) se buscará la página **man** llamada **cal**. Si no lo encuentra, entonces se busca en la segunda sección. Si no se encuentra ninguna página **man** tras buscar en todas las secciones, recibirás un mensaje de error:

```
sysadmin@localhost:~$ man zed                                          
No manual entry for zed                                                
sysadmin@localhost:~$
```
##### Determinar la Sección de una página man

Para determinar a qué sección pertenece una página man específica tienes que ver el valor numérico de la primera línea de la salida de la página man. Por ejemplo, si ejecutas el comando **man cal**, verás que el comando **cal** pertenece a la primera sección de las páginas man:

```
CAL(1)                    BSD General Commands Manual             CAL(1)
```
##### Especificar una Sección

En algunos casos, necesitarás especificar la sección para visualizar la página **man** correcta. Esto es necesario porque a veces habrá páginas **man** con el mismo nombre en diferentes secciones.

Por ejemplo, hay un comando llamado **passwd** que permite cambiar tu contraseña. También hay un archivo llamado **passwd** que almacena la información de la cuenta. Ambos, el comando y el archivo tienen una página **man**.

El comando **passwd** es un comando de "user" (o «usuario» en español), por lo que el comando **man passwd** mostrará la página man para el comando passwd por defecto:

```
PASSWD(1)                        User Commands                 PASSWD(1)
```
Para especificar una sección diferente, proporciona el número de la sección como el primer argumento del comando **man**. Por ejemplo, el comando ```man 5 passwd``` buscará la página **man** de **passwd** sólo en la sección 5:

```
PASSWD(5)                File Formats and Conversions          PASSWD(5)
```

##### Buscar las secciones

A veces no es claro en qué sección se almacena una página man. En estos casos, puedes buscar una página man por nombre.

La opción **-f** para el comando **man** mostrará páginas que coinciden, o parcialmente coinciden, con un nombre específico y provee una breve descripción de cada página **man**:

```
sysadmin@localhost:~$ man -f passwd                                    
passwd (5)           - the password file                              
passwd (1)           - change user password                           
passwd (1ssl)        - compute password hashes                         
sysadmin@localhost:~$
```

Ten en cuenta que en la mayoría de las distribuciones de Linux, el comando **whatis** hace lo mismo que el comando **man -f**. En esas distribuciones, ambos comandos producen la misma salida.

##### Buscar Páginas man por una Palabra Clave

Desafortunadamente, no siempre te acordarás del nombre exacto de la página man que quieres ver. En estos casos puedes buscar páginas man que coincidan con una palabra clave mediante el uso de la opción **-k** del comando **man**.

Por ejemplo, ¿qué pasa si quieres ver una página que muestra cómo cambiar la contraseña, pero no recuerdas el nombre exacto? Puedes ejecutar el comando man **-k password**:

```
sysadmin@localhost:~$ man -k passwd                                    
chgpasswd (8)        - update group passwords in batch mode            
chpasswd (8)         - update passwords in batch mode                 
fgetpwent_r (3)      - get passwd file entry reentrantly               
getpwent_r (3)       - get passwd file entry reentrantly               
gpasswd (1)          - administer /etc/group and /etc/gshadow         
pam_localuser (8)    - require users to be listed in /etc/passwd      
passwd (1)           - change user password                           
passwd (1ssl)        - compute password hashes                        
passwd (5)           - the password file                               
passwd2des (3)       - RFS password encryption                         
update-passwd (8)    - safely update /etc/passwd, /etc/shadow and /etc/group    
```

Ten en cuenta que en la mayoría de las distribuciones de Linux, el comando **apropos** hace lo mismo que el comando **man -k**. En esas distribuciones, ambas producen la misma salida.

##### Comando info

Las páginas **man** son unas fuentes extensas de información, pero suelen tener algunas desventajas. Un ejemplo de una desventaja es que cada página **man** es un documento independiente y no está relacionado con ninguna otra página **man**. Aunque algunas páginas man tienen una sección SEE ALSO que puede hacer referencia a otras páginas **man**, en realidad tienden a ser relacionadas con las fuentes de documentación.

El comando **info** también proporciona documentación sobre funciones y comandos del sistema operativo. El objetivo de este comando es ligeramente diferente de las páginas **man**, proporcionan un recurso de documentación que provee una estructura lógica, facilitando la lectura de la documentación.

Para visualizar la documentación **info** de un comando, ejecuta el comando 
```info command``` (reemplaza command con el nombre del comando sobre cuál buscas la información) Por Ejemplo: ```info ls```

Observa que la primera línea proporciona información que te indica dónde dentro de la documentación info estás ubicado. Esta documentación se divide en nodes (o «nodos») y en el ejemplo anterior estás actualmente en el nodo **ls invocation**. Si pasaras al siguiente nodo (tal como ir al siguiente capítulo en un libro), estarías en el nodo **dir invocation**. Si te pasaras un nivel hacia arriba estarías en el nodo **Directory listing**.

> Una vez ejecutado el comando info para ver la información de ayuda pulsa la tecla **h** Para moverte por los nodos tienes que usar las teclas **<kbd>Alt</kbd>** + **<kbd>[</kbd>** y **<kbd>]</kbd>** para salir de la ayuda pulsa **<kbd>l</kbd>** 

Con el comando ```--help```también puedes conseguir ayuda rápida de un comando muy parecida a ```man```

##### Documentación Adicional del Sistema
En la mayoría de los sistemas, existe un directorio donde se encuentra la documentación adicional. Estos archivos de documentación se suelen llamar archivos **readme**. La ubicación de estos archivos puede variar según la distribución que estés utilizando. Ubicaciones típicas incluyen **/usr/share/doc** y **/usr/doc.**

Recuerda que el comando **whatis** o **man -f** te dirá en qué sección se almacena la página **man**. Si utilizas este comando con suficiente frecuencia, probablemente te topes con una salida inusual, como la siguiente:

```
sysadmin@localhost:~$ whatis ls                                              
ls (1)               - list directory contents 
ls (lp)              - list directory contents                                 
sysadmin@localhost:~$ 
```
Según esta salida, hay dos comandos que listan el contenido del directorio. La respuesta simple a la pregunta por qué hay dos comandos **ls** es que UNIX tuvo dos variantes principales, lo que dio lugar a que algunos comandos fueran desarrollados «en paralelo». Por lo tanto, algunos comandos se comportan diferentemente en diversas variantes de UNIX. Muchas distribuciones modernas de Linux incluyen comandos de ambas variantes de UNIX.

Esto, sin embargo, conlleva un pequeño problema: Cuando corres el comando ls, ¿Cuál de los comandos se ejecuta?

Para buscar la ubicación de un comando o de las páginas **man** para un comando, utiliza el comando **whereis**. Este comando busca los comandos, archivos de código fuente y las páginas **man** en las ubicaciones específicas donde estos archivos se almacenan normalmente:

```
sysadmin@localhost:~$ whereis ls                                              
ls: /bin/ls /usr/share/man/man1/ls.1.gz         
ls: /bin/ls /usr/share/man/man1/ls.2.gz                                       
sysadmin@localhost:~$
```
Las páginas man se suelen distinguir fácilmente entre los comandos ya que normalmente están comprimidos con un comando llamado **gzip**, dando por resultado un nombre de archivo que termina en **.gz**.

Lo interesante es que verás que hay dos paginas **man**, pero sólo un comando (/bin/ls). Esto es porque el comando ls puede utilizarse con las opciones/funciones que se describen por cualquiera de las páginas **man**.

##### Encontrar Cualquier Archivo o Directorio

El comando **whereis** está diseñado para encontrar de manera específica las páginas **man** y los comandos. Si bien esto es útil, hay veces en las que quieras encontrar un archivo o directorio, no sólo archivos de comandos.

Para encontrar cualquier archivo o directorio, puede utilizar el comando **locate** (o «localizar» en español). Este comando buscará en una base de datos de todos los archivos y directorios que estaban en el sistema cuando se creó la base de datos. Por lo general, el comando que genera tal base de datos se ejecuta por la noche.

```
sysadmin@localhost:~$ locate gshadow                                            
/etc/gshadow                                                                    
/etc/gshadow-                                                                   
/usr/share/man/cs/man5/gshadow.5.gz                                             
/usr/share/man/fr/man5/gshadow.5.gz                                             
/usr/share/man/man5/gshadow.5.gz                                                
/usr/share/man/ru/man5/gshadow.5.gz                                             
/usr/share/man/sv/man5/gshadow.5.gz                                             
sysadmin@localhost:~$                                                           
```
Los archivos que creaste hoy normalmente no los vas a poder buscar con el comando **locate**. Si tienes acceso al sistema como usuario **root** (con la cuenta del administrador de sistema), puede actualizar manualmente la base de datos **locate** ejecutando el comando ```updatedb```. Los usuarios regulares no pueden actualizar el archivo de base de datos.

Otra posible solución a la búsqueda de archivos "nuevos" es hacer uso del comando **find**. Este comando busca en el sistema de archivos en vivo en lugar de una base de datos estática

Comando | Descripción
---|---
locate -c passwd | Muestra por pantalla el número de resultados que ha encontrado con el comando locate
locate -b passwd | Muestra un listado de comandos donde la salida contiene el término de búsqueda en su _basename_ es la parte del nombre de archivo que no incluye los nombres de directorio.
locate -b "\passwd" | Para limitar la salida aún más, coloca un carácter \ delante del término de búsqueda. Este carácter limita la salida a los nombres de archivo que coincidan exactamente con el término:

## Capítulo 6: Gestión de los Archivos y Directorios

##### Comprender los Archivos y los Directorios


Los archivos se utilizan para almacenar datos tales como texto, gráficos y programas. Los directorios (También conocidos como «carpetas») se utilizan para proporcionar una estructura de organización jerárquica

Igual que Windows, la estructura de directorios de Linux tiene un nivel superior, sin embargo no se llama Este Equipo, sino directorio raíz y su símbolo es el carácter ```/``` . También, en Linux no hay unidades; cada dispositivo físico es accesible bajo un directorio, no una letra de unidad. 

> En realidad, los directorios son archivos también; los datos que contienen son los nombres de los archivos que han sido introducidos en ellos, junto con el número de **inode** _(un número identificador único asignado a cada archivo)_ para saber dónde existen los datos de ese archivo en el disco.

* Para ver el sistema de archivos raíz, introduce ```ls /```:

```
sysadmin@localhost:~$ ls /                                            
bin   dev  home  lib    media  opt   root  sbin     selinux  sys  usr  
boot  etc  init  lib64  mnt    proc  run   sbin???  srv   tmp  var
```

##### El Directorio Path

Una ruta de acceso te permite especificar la ubicación exacta de un directorio. Para el directorio sound la ruta de acceso sería **/etc/sound**. El primer carácter / representa el directorio root (o «raíz» en español), mientras que cada siguiente carácter / se utiliza para separar los nombres de directorio.

> Para considerar:
El directorio /etc originalmente significaba "etcetera" en la documentación temprana de Bell Labs y solía contener archivos que no pertenecían a ninguna ubicación. En las distribuciones modernas de Linux, el directorio /etc por lo general contiene los archivos de configuración estática como lo define por el Estándar de Jerarquía de Archivos (o «FHS», del inglés «Files Hierarchy Standard»)

##### El Directorio Home

El término home directory (o «directorio de inicio» en español) a menudo causa confusión a los usuarios principiantes de Linux. Para empezar, en la mayoría de las distribuciones de Linux hay un directorio llamado home bajo el directorio root: /home.

Bajo de este directorio /home hay un directorio para cada usuario del sistema. El nombre del directorio será el mismo que el nombre del usuario, por lo que un usuario llamado «bob» tendría un directorio home llamado /home/bob.

Tu directorio home es un directorio muy importante. Para empezar, cuando abres un shell automáticamente te ubicarás en tu directorio home, en donde harás la mayor parte de tu trabajo.

Además, el directorio home es uno de los pocos directorios donde tienes el control total para crear y eliminar los archivos adicionales.

Tu directorio tiene incluso un símbolo especial que puedes usar para representarlo: **~**. Si tu directorio home es **/home/sysadmin**, puedes simplemente introducir **~** en la línea de comandos en lugar de **/home/sysadmin**. También puedes referirte al directorio home de otro usuario usando la notación **~usuario**

Los entornos de Linux son sensibles a mayúsculas y minúsculas.

Par ver el directorio de trabajo actual hay que usar el comando **pwd**

```
sysadmin@localhost:~$ pwd                                             
/home/sysadmin                                                         
sysadmin@localhost:~$
```

##### Cambio de Directorios

Si te quieres cambiar a un directorio diferente, utiliza el comando **cd** (cambiar directorio). Por ejemplo, el siguiente comando cambiará el directorio actual a un directorio llamado **/etc/sound/events**:

```
sysadmin@localhost:~$ cd /etc/sound/events                                    
sysadmin@localhost:/etc/sound/events$
```
Si quieres volver a tu directorio home, puedes introducir el comando **cd** sin argumentos o usar el comando **cd** con el carácter **~** como argumento.

##### Nombres de Ruta Absoluta versus Relativa

Hay que recordar que una ruta de acceso es esencialmente una descripción de la ubicación de un archivo o un directorio en el sistema de archivos. Una ruta de acceso también se puede entender como las direcciones que indican al sistema donde se encuentra un archivo o un directorio. Por ejemplo, el comando ```cd /etc/perl/Net``` significa "cambiar al directorio Net, que encontrarás bajo el directorio ```perl```, que encontrarás bajo el directorio ```etc``` , que encontrarás bajo el directorio ```/```".

Cuando des un nombre de ruta que comienza en el directorio raíz, se llamará **ruta absoluta**. En muchos casos, proporcionar una ruta de acceso absoluta tiene sentido. Por ejemplo, si estás en tu directorio ```home``` y quieres ir al directorio ```/etc/perl/Net```, entonces proporcionar una ruta de acceso absoluta al comando ```cd``` tiene sentido:

```
sysadmin@localhost:~$ cd /etc/perl/Net                                 
sysadmin@localhost:/etc/perl/Net$ 
```
Sin embargo, ¿Qué pasa si estás en el directorio ```/etc/perl``` y quieres ir al directorio ```/etc/perl/Net```? Sería tedioso introducir la ruta completa para llegar a un directorio que es sólo un nivel más abajo de tu ubicación actual. En una situación como ésta, vas a utilizar una ruta relativa:

```
sysadmin@localhost:/etc/perl$ cd Net                                    
sysadmin@localhost:/etc/perl/Net$ 
```
> Una ruta de acceso relativa proporciona direcciones usando tu **ubicación actual** como un punto de referencia. Recuerda que esto es diferente de las rutas absolutas, que siempre requieren que utilices el **directorio raíz** como punto de referencia.

Existe una técnica útil de ruta de acceso relativa que se puede utilizar para subir un nivel en la estructura de directorios: el directorio **..** . Sin importar en qué directorio estás, el comando **..** siempre representa un directorio arriba que el directorio actual (con la excepción de cuando estás en el directorio ```/```):

```
sysadmin@localhost:/etc/perl/Net$ pwd                                 
/etc/perl/Net                                                          
sysadmin@localhost:/etc/perl/Net$ cd ..                                
sysadmin@localhost:/etc/perl$ pwd                                      
/etc/perl                                                              
sysadmin@localhost:/etc/perl$
```

A veces usar las rutas de acceso relativas es una mejor opción que rutas de acceso absolutas, sin embargo esto no siempre es el caso. ¿Qué pasa si estás en el directorio ```/etc/perl/Net``` y quieres ir al directorio ```/usr/share/doc```? Utilizando una ruta absoluta, se ejecutaría el comando ```cd /usr/share/doc```. Utilizando una ruta relativa, se ejecutaría el comando ```cd ../../../usr/share/doc```:

```
sysadmin@localhost:/etc/perl/Net$ cd                                   
sysadmin@localhost:~$ cd /etc/perl/Net                                 
sysadmin@localhost:/etc/perl/Net$ cd /../../../usr/share/doc           
sysadmin@localhost:/usr/share/doc$ pwd                                 
/usr/share/doc                                                         
sysadmin@localhost:/usr/share/doc$
```

>Las rutas relativas y absolutas no sólo sirven para el comando ```cd```. Siempre cuando especificas un archivo o un directorio, puedes utilizar las rutas de acceso relativas o absolutas.

Mientras que el doble punto (..) se utiliza para referirse al directorio arriba del directorio actual, el punto solo (.) se usa para referirse al directorio actual. No tendría sentido para un administrador moverse al directorio actual introduciendo ```cd``` . (aunque en realidad funciona). Es más útil referirse a un elemento en el directorio actual usando la notación ```./```. Por ejemplo:

```
sysadmin@localhost:~$ pwd                                              
/home/sysadmin                                                         
sysadmin@localhost:~$ cd ./Downloads/                                  
sysadmin@localhost:~/Downloads$ pwd                                    
/home/sysadmin/Downloads                                               
sysadmin@localhost:~/Downloads$ cd ..                                  
sysadmin@localhost:~$ pwd                                              
/home/sysadmin                                                         
sysadmin@localhost:~$
```

> Este uso del punto solo (.), como punto de referencia, no se debe confundir con su uso al principio de un nombre de archivo.

##### Listado de los Archivos en un Directorio

Esto se consigue con el comando ```ls```

```
sysadmin@localhost:~$ ls                                               
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  
Videos      
sysadmin@localhost:~$
```
##### Lista de Colores

Principales tipos de archivos en linux.

Tipo |	Descripción
---|---
plain file (o «archivo simple» en español) |	Un archivo que no es un tipo de archivo especial; también se llama un archivo normal
directory (o «directorio» en español)	| Un directorio de archivos (contiene otros archivos)
executable (o «ejecutable» en español)	|Un archivo que se puede ejecutar como un programa
symbolic link	 Un a|rchivo que apunta a otro archivo (o «enlace simbólico» en español)

En muchas distribuciones de Linux, las cuentas de usuario regulares son modificadas de tal manera que el comando ```ls``` muestre los nombres de archivo, codificados por colores según el tipo de archivo. 

Color |	Tipo de Archivo
---|---
Negro o blanco	| Archivo regular
Azul	| Archivo de directorio
Cian	| Archivo de enlace simbólico (un archivo que apunta a otro archivo)
Verde	| Archivo ejecutable (un programa)

Esto no es un comportamiento normal para el comando ls, sino algo que sucede cuando se utiliza la opción ```--color``` para el comando ```ls```. La razón por la que el comando ls parece realizar automáticamente estos colores, es que hay un alias para el comando ls para que se ejecute con la opción ```--color```:

```
sysadmin@localhost:~$ alias                                           
alias egrep='egrep --color=auto'                                       
alias fgrep='fgrep --color=auto'                                      
alias grep='grep --color=auto'                                         
alias l='ls -CF'                                                    
alias la='ls -A'                                                       
alias ll='ls -alF'                                                    
alias ls='ls --color=auto'                                             
sysadmin@localhost:~$
```

Como puedes ver en la salida anterior, cuando se ejecuta el comando ```ls```, en realidad se ejecuta el comando ```ls --color=auto```.

En algunos casos, puede que no quieras ver todos los colores (a veces te pueden distraer un poco). Para evitar el uso de los alias, coloca un carácter de barra invertida ```\``` antes de tu comando.

##### Archivos Ocultos (ls -a)

Cuando utilizas el comando ls para mostrar el contenido de un directorio, no todos los archivos se muestran automáticamente. El comando ls no muestra los archivos ocultos de manera predeterminada.

Para mostrar todos los archivos, incluyendo los archivos ocultos, utiliza la opción ```-a``` para el comando ```ls```.

```
sysadmin@localhost:~$ ls -a                                            
.             .bashrc   .selected_editor  Downloads  Public           
..            .cache    Desktop           Music      Templates         
.bash_logout  .profile  Documents         Pictures   Videos
```
##### Listado con visualización larga (ls -l)

Existe información sobre cada archivo, llamada metadata (o «metadatos» en español), y visualizarla a veces resulta útil. Esto puede incluir datos de quién es el dueño de un archivo, el tamaño de un archivo y la última vez que se modificó el contenido de un archivo. Puedes visualizar esta información mediante el uso de la opción ```-l``` para el comando ```ls```:

```
sysadmin@localhost:~$ ls -l                                           
total 0                                                                
drwxr-xr-x 1 sysadmin sysadmin 0 Jan 29  2015 Desktop                  
sysadmin@localhost:~$
```


1	Representa lo que se denomina un recuento de vínculo físico (explicado más adelante).
root	El usuario propietario del archivo.
root	El grupo propietario del archivo.
150	El tamaño del archivo en bytes.
	La fecha/hora en que la el archivo fue modificado por última vez.

Carácter | Descripción
---|---
- | **Tipo de archivo.** El primer carácter de cada línea de salida indica el tipo de archivo. Tipos de archivo comunes incluyen: **d= directorio, -= archivo simple, l= enlace simbólico**
rw-r--r-- | **Permisos.** Los próximos diez caracteres demostrarán los permisos del archivo. Los permisos se utilizan para determinar quién tiene acceso al archivo.
1 | **Conteo de enlaces físicos.** El conteo de enlaces físicos de un archivo se usa para demostrar cuantos enlaces físicos hacia este archivo existen.
root | **Usuario propietario.** Cada archivo es propiedad de una cuenta de usuario. Esto es importante porque el propietario tiene los derechos para establecer permisos en un archivo y el propietario tiene sus propios permisos en el archivo.
root | **Grupo propietario.** Cada archivo es propiedad de un grupo. Esto es importante porque cualquier miembro de este grupo tendrá acceso especial al archivo basado en los permisos de grupo del archivo.
150 | **Tamaño de archivo.** Este campo describe el tamaño de un archivo en bytes. Nota: En el caso de los directorios, este valor no describe el tamaño total del directorio, más bien, cuántos bytes están reservados para mantenerse al corriente con los nombres de archivo en el directorio (en otras palabras, ignora este campo en los directorios).»
Jan 22 15:18 | **Hora de modificación.** Este campo indica la última hora en la que el contenido del archivo fue modificado. En el caso de los directorios, indica la última vez que se agregó o eliminó un archivo dentro del directorio.
archivo.txt | **Nombre.** El último campo es el nombre del archivo o directorio.

##### Tamaños legibles (ls -lh)

Cuando visualizas los tamaños de los archivos con la opción ```-l``` del comando ```ls``` obtienes los tamaños de los archivo en bytes. Para archivos de texto, un byte es 1 carácter.

Para archivos más pequeños, los tamaños en byte están bien. Sin embargo, para los archivos más grandes es difícil comprender qué tan grande es el archivo.

Para mejorar esto usamos el comando ```ls -lh```:

```
sysadmin@localhost:~$ ls -lh /usr/bin/omshell                                 
-rwxr-xr-c 1 root root 1.5M Oct 9 2012 /usr/bin/omshell              
sysadmin@localhost:~$
```
> Se debe de utilizar el comando ```-h``` junto con la opción ```-l```

##### Lista de Directorios (ls -d)

Cuando se utiliza el comando ```ls -d```, se refiere al directorio actual y no al contenido dentro de él. Sin otras opciones, es algo sin sentido, aunque es importante tener en cuenta que al directorio actual siempre se refiere con un solo punto (.)

##### Listado Recursivo (ls -R)

Habrá momentos cuando quieras visualizar todos los archivos en un directorio, así como todos los archivos en todos los subdirectorios bajo un directorio. Esto se llama **listado recursivo**.

Para realizar un listado recursivo, utiliza la opción ```-R``` para el comando ```ls```:

##### Ordenando listas de archivos (ls -xxxx)

De forma predeterminada, el comando ```ls``` ordena los archivos alfabéticamente por nombre de archivo. A veces, puede ser útil ordenar los archivos utilizando diferentes criterios.

Comando | Descripción
---|---
ls -S | Ordena los archivos por tamaño
ls -lS | Ordena los archivos por tamaño y muestra metadatos
ls -lSh | Ordena los archivos por tamaño, muestra metadatos y el tamaño de los archivos son human readable
ls -tl | Ordena los archivos modificados mas recientes en primer lugar ```-t```
ls -t --fulltime | Ordena los archivos modificados mas recientes con formato de tiempo extendido.
ls -lrS | Ordena los archivos de forma inversa, por tamaño de menor a mayor tamaño.
ls -lrt | Ordena los archivos de forma inversa, por fecha de modificación de la mas antigua a la más reciente.
 
> La fecha de modificación de los directorios representa la última vez que un archivo se agrega o se elimina del directorio.

##### Listado con Globs

Al utilizar los argumentos glob con el comando ```ls```, utiliza siempre la opción ```-d```. Cuando utilizas la opción ```-d```, el comando ```ls``` no muestra el contenido de un directorio, sino más bien el nombre del directorio:
	
```
sysadmin@localhost:/etc$ ls -d a*                                               
adduser.conf  adjtime  alternatives  apparmor.d  apt                            
sysadmin@localhost:/etc$ 
```
Sin ```-d```

```
sysadmin@localhost:/etc$ ls a*                                                  
adduser.conf  adjtime                                                           
                                                                                
alternatives:                                                                   
README          ex.fr.1.gz        nawk         rmt               vi.pl.1.gz     
awk             ex.it.1.gz        nawk.1.gz    rmt.8.gz          vi.ru.1.gz     
awk.1.gz        ex.pl.1.gz        pager        rsh               view           
builtins.7.gz   ex.ru.1.gz        pager.1.gz   rsh.1.gz          view.1.gz      
editor          from              pico         rview             w              
editor.1.gz     from.1.gz         pico.1.gz    traceroute6       w.1.gz         
editor.fr.1.gz  infobrowser       rcp          traceroute6.8.gz  write          
editor.it.1.gz  infobrowser.1.gz  rcp.1.gz     updatedb          write.1.gz     
editor.pl.1.gz  locate            rename       vi                               
editor.ru.1.gz  locate.1.gz       rename.1.gz  vi.1.gz                          
ex              mt                rlogin       vi.fr.1.gz                       
ex.1.gz         mt.1.gz           rlogin.1.gz  vi.it.1.gz                       
                                                                                
apparmor.d:                                                                     
disable  force-complain  local  usr.sbin.named  usr.sbin.rsyslogd               
                                                                                
apt:                                                                            
apt.conf.d     sources.list    trustdb.gpg  trusted.gpg.d                       
preferences.d  sources.list.d  trusted.gpg 
```
Como puedes ver, cuando el comando ls ve un nombre de archivo como argumento, sólo muestra el nombre del archivo. Sin embargo, para cualquier directorio, mostrará el contenido del directorio, y no sólo el nombre del directorio.

##### Copiar los Archivos (cp )

El comando ```cp``` se utiliza para copiar los archivos. Requiere especificar un origen y un destino. La estructura del comando es la siguiente:

``` cp [fuente] [destino] ```

La fuente («source» en inglés) es el archivo que quieres copiar. El destino («destination» en inglés) es la ubicación en donde quieres poner la copia. Cuando el comando es exitoso, el comando cp no tendrá ninguna salida (ninguna noticia es buena noticia). El siguiente comando copiará el archivo /etc/hosts a tu directorio home:

```
sysadmin@localhost:~$ cp /etc/hosts ~                                     
sysadmin@localhost:~$ ls                                                  
Desktop    Downloads  Pictures  Templates  hosts                          
Documents  Music      Public    Videos                                    
sysadmin@localhost:~$
```

##### Modo Verbose (cp -v)

La opción ```-v``` hará que el comando ```cp``` produzca la salida en caso de ser exitoso. La opción ```-v``` se refiere al comando verbose:

```
sysadmin@localhost:~$ cp -v /etc/hosts ~                              
`/etc/hosts' -> `/home/sysadmin/hosts'                                 
sysadmin@localhost:~$
```
Cuando el destino es un directorio, el nuevo archivo resultante tendrá el mismo nombre que el archivo original. Si quieres que el nuevo archivo tenga un nombre diferente, debes proporcionar el nuevo nombre como parte del destino:

```
sysadmin@localhost:~$ cp /etc/hosts ~/hosts.copy                      
sysadmin@localhost:~$ ls                                               
Desktop    Downloads  Pictures  Templates  hosts                       
Documents  Music      Public    Videos     hosts.copy                  
sysadmin@localhost:~$
```

##### Evitar Sobrescribir los Datos (cp -i, -n)

El comando ```cp``` puede ser destructivo para los datos si el archivo de destino ya existe. En el caso donde el archivo de destino existe, el comando ```cp``` sobreescribe el contenido del archivo existente con el contenido del archivo fuente.

Con la opción ```-i``` (interactivo), el comando ```cp``` emitirá un prompt antes de sobrescribir un archivo, y tendremos que responder ```n``` o ```y``` antes de sobreescribir un archivo, cuando son bastantes archivos podemos usar la combinación de ```cp``` con ```-i``` y agregarle ```-n``` que significa sin sobreescribir.

##### Copiar los Directorios (cp -r)

En un ejemplo anterior se dieron mensajes de error cuando el comando ```cp``` intentó copiar los directorios:

```
sysadmin@localhost:~$ cp -i /etc/skel/.* ~                             
cp: omitting directory `/etc/skel/.'                                   
cp: omitting directory `/etc/skel/..'                                  
cp: overwrite `/home/sysadmin/.bash_logout'? n                         
cp: overwrite `/home/sysadmin/.bashrc'? n                              
cp: overwrite `/home/sysadmin/.profile'? n                            
cp: overwrite `/home/sysadmin/.selected_editor'? n                     
sysadmin@localhost:~$
```
Donde la salida dice ...omitting directory... (o «omitiendo directorio» en español), el comando ```cp``` está diciendo que no puede copiar este artículo porque el comando no copia los directorios por defecto. Sin embargo, la opción ```-r``` del comando cp copiará ambos, los archivos y los directorios.

##### Mover los Archivos (mv)

Para mover un archivo, utiliza el comando ```mv```. La sintaxis del comando mv es muy parecida al comando ```cp```:

```
mv [fuente] [destino]
```
>Cuando se mueve un archivo, el archivo se elimina de la ubicación original y se coloca en una ubicación nueva.

##### Mover los archivos mientras se cambia el nombre (mv)

Para cambiar el nombre del archivo destino con respecto al origen , lo especificamos a la hora de ejecutar el comando ```mv```

```
sysadmin@localhost:~$ ls                                               
Desktop    Downloads  Pictures  Templates  example.txt                 
Documents  Music      Public    Videos                    
sysadmin@localhost:~$ mv example.txt Videos/newexample.txt             
sysadmin@localhost:~$ ls                                               
Desktop    Downloads  Pictures  Templates                  
Documents  Music      Public    Videos                                 
sysadmin@localhost:~$ ls Videos                                       
hosts  newexample.txt                                                  
sysadmin@localhost:~$
```
##### Renombrar los Archivos (mv)

El comando ```mv``` no sólo se utiliza para mover un archivo, sino también cambiar el nombre de un archivo también conocido como renombrar. 

Por ejemplo, los siguientes comandos cambiarán el nombre del archivo newexample.txt a myexample.txt:

```
sysadmin@localhost:~$ cd Videos                                        
sysadmin@localhost:~/Videos$ ls                                        
hosts  newexample.txt                                                  
sysadmin@localhost:~/Videos$ mv newexample.txt myexample.txt           
sysadmin@localhost:~/Videos$ ls                                        
hosts  myexample.txt                                                   
sysadmin@localhost:~/Videos$
```
##### Opciones Adicionales del mv ( mv -i, -n, -v)

Igual al comando cp, el comando mv proporciona las siguientes opciones:

Opción	| Significado
---|---
-i	| Movimiento interactivo: pregunta si un archivo debe sobrescribirse.
-n	| No sobrescribir el contenido de los archivos de destino
-v	| Verbose: muestra el movimiento resultante

>Importante: Aquí no hay ninguna opción -r, ya que el comando mv moverá los directorios de forma predeterminada.

##### Crear Archivos (touch)

Para crear un archivo vacío, utiliza el comando ```touch``` (o «tocar» en español) como se muestra a continuación:

```
sysadmin@localhost:~$ ls                                                
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  
Videos 
sysadmin@localhost:~$ touch sample                                     
sysadmin@localhost:~$ ls -l sample                                     
-rw-rw-r-- 1 sysadmin sysadmin 0 Nov  9 16:48 sample                   
sysadmin@localhost:~$
```
Fíjate que el tamaño del archivo nuevo es 0 bytes, el comando ```touch``` no añade ningún dato en al archivo nuevo.

##### Eliminar los Archivos (rm ,-i)
Para borrar un archivo, se utiliza el comando ```rm```:

```
sysadmin@localhost:~$ ls                                               
Desktop    Downloads  Pictures  Templates  sample                      
Documents  Music      Public    Videos                                 
sysadmin@localhost:~$ rm sample                                        
sysadmin@localhost:~$ ls                                               
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  
Videos       
sysadmin@localhost:~$
```

Ten en cuenta que el archivo fue borrado sin hacer preguntas. Esto podría causar problemas al borrar varios archivos usando los caracteres glob, por ejemplo: ```rm *.txt```. Ya que estos archivos son borrados sin proporcionar una pregunta, un usuario podría llegar a borrar archivos que no quería eliminar.

Como precaución, los usuarios deben utilizar la opción ```-i``` al eliminar varios archivos.

##### Eliminar los Directorios (rm, -r, -i) 

Puedes borrar los directorios con el comando ```rm```. Sin embargo, si utilizas el comando ```rm``` por defecto (sin opciones), éste no eliminará un directorio:

```
sysadmin@localhost:~$ rm Videos                                        
rm: cannot remove `Videos': Is a directory                            
sysadmin@localhost:~$
```

Si quieres eliminar un directorio, utiliza la opción ```-r``` con el comando ```rm```:

```
sysadmin@localhost:~$ ls                                               
Desktop    Downloads  Pictures  Templates  sample.txt                  
Documents  Music      Public    Videos                                 
sysadmin@localhost:~$ rm -r Videos                                     
sysadmin@localhost:~$ ls                                               
Desktop  Documents  Downloads  Music  Pictures  Public  Templates 
sample.txt 
sysadmin@localhost:~$
```

>**Importante**: Cuando un usuario elimina un directorio, todos los archivos y subdirectorios se eliminan sin proporcionar pregunta interactiva. Lo mejor es utilizar la opción ```-i``` con el comando ```rm```.

También puedes borrar un directorio con el comando ```rmdir```, pero sólo si el directorio está **vacío**.

##### Crear Directorios

Para crear un directorio, utiliza el comando ```mkdir```:

```
sysadmin@localhost:~$ ls                                               
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  
sample.txt
sysadmin@localhost:~$ mkdir test                                       
sysadmin@localhost:~$ ls                                               
Desktop    Downloads  Pictures  Templates   test                       
Documents  Music      Public    sample.txt                             
sysadmin@localhost:~$
```
##### Apuntes de Prácticas capítulo 6

```echo $HOME``` --> para saber la variable de entorno que se refiere a nuestro directorio home
```cp -p``` --> para copiar desde el diectorio origen y perservar los atributos del archivo.

## Capítulo 7 (Empaquetamiento y Compresión)

* El Empaquetamiento - Combina varios archivos en uno solo, lo que elimina la sobrecarga en archivos individuales y los hace más fácil de transmitir
* Compresión – hace los archivos más pequeños mediante la eliminación de información redundante

##### Compresión (gzip, bzip2)

Cuando se habla de compresión, existen dos tipos:

* Lossless (o «sin pérdida» en español): No se elimina ninguna información del archivo. Comprimir un archivo y descomprimirlo deja algo idéntico al original.
* Lossy (o «con pérdida» en español): Información podría ser retirada del archivo cuando se comprime para que al descomprimir el archivo de lugar a un archivo que es un poco diferente que el original. 

Por ejemplo, una imagen con dos tonos de verde sutilmente diferentes podría hacerse más pequeña por tratar esos dos tonos como uno. De todos modos, el ojo no puede reconocer la diferencia.

Linux proporciona varias herramientas para comprimir los archivos, la más común es gzip. A continuación te mostraremos un archivo de registro antes y después de la compresión.

```
bob:tmp $ ls -l access_log*
-rw-r--r-- 1 sean sean 372063 Oct 11 21:24 access_log
bob:tmp $ gzip access_log
bob:tmp $ ls -l access_log*
-rw-r--r-- 1 sean sean 26080 Oct 11 21:24 access_log.gz
```

En el ejemplo anterior hay un archivo llamado access_log que tiene 372,063 bytes. El archivo se comprime invocando el comando ```gzip``` con el nombre del archivo como el único argumento. Al finalizar el comando su tarea, el archivo original desaparece y una versión comprimida con una extensión de archivo ```.gz``` se queda en su lugar.

```gzip -l``` --> info de la compresion
```gunzip o gzip -d``` --> descomprime los archivos
```bzip2 o bunzip2```  --> otro compresor usa diferente algoritmo

##### Empaquetado (tar, -c, -f, -z)

Tar tiene 3 modos que deberás conocer:

* **Crear**: hacer un archivo nuevo de una serie de archivos
* **Extraer**: sacar uno o más archivos de un archivo
* **Listar**: mostrar el contenido del archivo sin extraer

```
sysadmin@localhost:~/Downloads$ tar -cf acccess_log.tar acccess_log*     
sysadmin@localhost:~/Downloads$ ls -l acccess_log.tar                           
-rw-rw-r-- 1 sysadmin sysadmin 10240 Mar 30 14:54 acccess_log.tar 
```

La creación de un archivo requiere dos opciones de nombre. La primera, ```c```, especifica el modo. La segunda, ```f```, le dice a ```tar``` que espere un nombre de archivo como el siguiente argumento. El primer argumento en el ejemplo anterior crea un archivo llamado ```access_logs.tar```. El resto de los argumentos se toman para ser nombres de los archivo de entrada, ya sea un comodín, una lista de archivos o ambos. En este ejemplo, utilizamos la opción comodín para incluir todos los archivos que comienzan con ```access_log```.

El ejemplo anterior hace un listado largo de directorio del archivo creado. El tamaño final es 542,720 bytes que es ligeramente más grande que los archivos de entrada. Los tarballs pueden ser comprimidos para transporte más fácil, ya sea comprimiendo un archivo con ```gzip``` o diciéndole a ```tar``` que lo haga con la opción ```z``` tal como se muestra a continuación:

```
sysadmin@localhost:~/Downloads$ tar -czf acccess_log.tar.gz acccess_log*
sysadmin@localhost:~/Downloads$ ls -l acccess_log.tar.gz                        
-rw-rw-r-- 1 sysadmin sysadmin 181 Mar 30 14:59 acccess_log.tar.gz      
```
El ejemplo anterior muestra el mismo comando como en el ejemplo anterior, pero con la adición del parámetro ```z```. La salida es mucho menor que el tarball en sí mismo, y el archivo resultante es compatible con ```gzip```. Se puede ver en el último comando que el archivo descomprimido es del mismo tamaño, como si hubieras utilizado el tar en un paso separado.

Mientras que UNIX no trata las extensiones de archivo especialmente, la convención es usar ```.tar``` para los archivos ```tar``` y ```.tar.gz``` o ```.tgz``` para los archivos ```tar``` comprimidos. Puedes utilizar ```bzip2``` en vez de ```gzip``` sustituyendo la letra ```z``` con ```j``` y usando ```.tar.bz2```,```.tbz```, o ```.tbz2``` para una extensión de archivo (por ejemplo ```tar –cjf file.tbz access_log*```)

En el archivo ```tar```, comprimido o no, puedes ver lo que hay dentro utilizando el comando ```t```.

```
sysadmin@localhost:~/Downloads$ tar tzf acccess_log.tar.gz                      
acccess_log                                                                     
acccess_log2                                                                    
acccess_log3                                                                    
acccess_log4                                                                    
acccess_log5                        
```
Este ejemplo utiliza 3 opciones:

* **t**: listar documentos en el archivo en el archivo empaquetado
* **j o z**: descomprimir con bzip2 antes de la lectura / con z para descomprimir con bzip 
* **f**: operar en el nombre de archivo access_logs.tbz

##### Empaquetado con Zip

El modo predeterminado del ```zip``` es añadir documentos a un archivo y comprimir.

```
bob:tmp $ zip logs.zip logs/*
  adding: logs/access_log (deflated 93%)
  adding: logs/access_log.1 (deflated 62%)
  adding: logs/access_log.2 (deflated 88%)
  adding: logs/access_log.3 (deflated 73%)
  adding: logs/access_log.4 (deflated 72%)
```

El primer argumento en el ejemplo anterior es el nombre del archivo sobre el cual se trabajará, en este caso es el ```logs.zip```. Después de eso, hay que añadir una lista de archivos a ser agregados. La salida muestra los archivos y la relación de compresión. Debes notar que el ```tar``` requiere la opción ```–f``` para indicar que se está pasando un nombre de archivo, mientras que el zip y unzip requiere un nombre de archivo, por lo tanto no tienes que decir explícitamente que se está pasando un nombre de archivo.

```Zip``` no se efectuará de manera recursiva hacia los subdirectorios por defecto, lo que es un comportamiento diferente del ```tar```, para ello debes utilizar el comando ```–r``` para indicar que se debe usar la recursividad.

El listado de los archivos en el ```zip``` se realiza por el comando ```unzip``` y la opción ```–l``` (listar):

```
bob:tmp $ unzip -l logs.zip
Archive:  logs.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
        0  10-14-2013 14:07   logs/
     1136  10-14-2013 14:07   logs/access_log.3
      362  10-14-2013 14:07   logs/access_log.1
      784  10-14-2013 14:07   logs/access_log.4
    90703  10-14-2013 14:07   logs/access_log
   153813  10-14-2013 14:07   logs/access_log.2
---------                     -------
   246798                     6 files
```

Extraer los archivos es como crear el archivo, ya que la operación predeterminada es extraer.

##### Prácticas capitulo 7

* Utiliza el comando ```tar``` para crear un archivo empaquetado del directorio /etc/udev y guardalo en la carpeta /home/sysadmin/Backups.

```
sysadmin@localhost:~$ tar -cvf Backups/udev.tar /etc/udev                       
tar: Removing leading `/' from member names                                     
/etc/udev/                                                                      
/etc/udev/rules.d/                                                              
/etc/udev/rules.d/70-persistent-cd.rules                                        
/etc/udev/rules.d/README                                                        
/etc/udev/udev.conf                                                             
sysadmin@localhost:~$ ls Backups                                                
udev.tar                        
```
La opción ```-c``` le indica al comando ```tar``` que cree un archivo ```tar```. La opción ```-v``` significa "verbose", que le indica al comando ```tar``` para muestre lo que está haciendo. La opción ```-f``` se utiliza para especificar el nombre del archivo ```tar```.

> No tienes que utilizar la extensión .tar  con nombre de archivo empaquetado, sin embargo, es muy útil para determinar el tipo de archivo.

* Muestra el contenido del archivo ```tar``` (t = lista el contenido, v = verbose, f =nombre del archivo):

```
sysadmin@localhost:~$ tar -tvf Backups/udev.tar                                 
drwxr-xr-x root/root         0 2016-03-03 18:40 etc/udev/                       
drwxr-xr-x root/root         0 2016-03-03 18:40 etc/udev/rules.d/               
-rw-r--r-- root/root       306 2016-03-03 18:39 etc/udev/rules.d/70-persistent-c
d.rules                                                                         
-rw-r--r-- root/root      1157 2012-04-05 19:18 etc/udev/rules.d/README         
-rw-r--r-- root/root       218 2012-04-05 19:18 etc/udev/udev.conf              
```

* Para crear un archivo ```tar``` comprimido, utiliza la opción ```-z```

```
sysadmin@localhost:~$ tar -zcvf Backups/udev.tar.gz /etc/udev                   
tar: Removing leading `/' from member names                                     
/etc/udev/                                                                      
/etc/udev/rules.d/                                                              
/etc/udev/rules.d/70-persistent-cd.rules                                        
/etc/udev/rules.d/README                                                        
/etc/udev/udev.conf                                                             
sysadmin@localhost:~$ ls -lh Backups/                                           
total 16K                                                                       
-rw-rw-r-- 1 sysadmin sysadmin  10K Mar 30 18:56 udev.tar                       
-rw-rw-r-- 1 sysadmin sysadmin 1.2K Mar 30 19:05 udev.tar.gz 
```
> Aquí se pueden observar la diferencia de tamaño de un empaquetado a uno comprimido, del mismo archivo.

* Extraer el contenido de un archivo ```.tar.gz```

```
sysadmin@localhost:~/Backups$ tar -xvf udev.tar.gz                              
etc/udev/                                                                       
etc/udev/rules.d/                                                               
etc/udev/rules.d/70-persistent-cd.rules                                         
etc/udev/rules.d/README                                                         
etc/udev/udev.conf                                                              
sysadmin@localhost:~/Backups$ ls                                                
etc  udev.tar  udev.tar.gz        
```

* Añadir un archivo a un archivo empaquetado existente, utiliza la opción ```-r``` con el comando ```tar```.

Para ello vamos a utilizar estos dos comandos:

```
tar -rvf udev.tar /etc/hosts
tar –tvf udev.tar  // Para comprobar que ha funcionado
```

Resultado en consola

```
sysadmin@localhost:~/Backups$ ls                                                
etc  udev.tar  udev.tar.gz                                                      
sysadmin@localhost:~/Backups$ tar -rvf udev.tar /etc/hosts                      
tar: Removing leading `/' from member names                                     
/etc/hosts                                                                      
sysadmin@localhost:~/Backups$ tar -tvf udev.tar                                 
drwxr-xr-x root/root         0 2016-03-03 18:40 etc/udev/                       
drwxr-xr-x root/root         0 2016-03-03 18:40 etc/udev/rules.d/               
-rw-r--r-- root/root       306 2016-03-03 18:39 etc/udev/rules.d/70-persistent-c
d.rules                                                                         
-rw-r--r-- root/root      1157 2012-04-05 19:18 etc/udev/rules.d/README         
-rw-r--r-- root/root       218 2012-04-05 19:18 etc/udev/udev.conf              
-rw-r--r-- root/root       172 2018-03-30 18:52 etc/hosts                                             
```

* Utilizar el comando ```gzip``` para comprimir un archivo.

```
sysadmin@localhost:~$ ls                                                        
Backups  Documents  Music     Public     Videos                                 
Desktop  Downloads  Pictures  Templates  udev.conf                              
sysadmin@localhost:~$ gzip udev.conf                                            
sysadmin@localhost:~$ ls -l udev.conf.gz                                        
-rw-r--r-- 1 sysadmin sysadmin 193 Mar 30 19:26 udev.conf.gz 
```
>* Cuando utilizas el comando gzip, el archivo original se sustituye por el archivo comprimido. En el ejemplo anterior, el archivo words fue sustituido por words.gz.
* Al descomprimir el archivo, el archivo comprimido será reemplazado por el archivo original.

* Utliza el comando ```gunzip```para descomprimir un archivo

```
sysadmin@localhost:~$ ls -l udev.conf.gz                                        
-rw-r--r-- 1 sysadmin sysadmin 193 Mar 30 19:26 udev.conf.gz                    
sysadmin@localhost:~$ gunzip udev.conf.gz                                       
sysadmin@localhost:~$ ls -l udev.conf                                           
-rw-r--r-- 1 sysadmin sysadmin 218 Mar 30 19:26 udev.conf 
```

* Utiliza el comando ```bzip2``` para comprimir un archivo

```
sysadmin@localhost:~$ ls -l udev.conf                                           
-rw-r--r-- 1 sysadmin sysadmin 218 Mar 30 19:26 udev.conf                       
sysadmin@localhost:~$ bzip2 udev.conf                                           
sysadmin@localhost:~$ ls -l udev*                                               
-rw-r--r-- 1 sysadmin sysadmin 210 Mar 30 19:26 udev.conf.bz2
```

* Utiliza el comando ```bunzip2``` para descomprimir un archivo

```
sysadmin@localhost:~$ ls -l udev*                                               
-rw-r--r-- 1 sysadmin sysadmin 210 Mar 30 19:26 udev.conf.bz2                   
sysadmin@localhost:~$ bunzip2 udev.conf.bz2                                     
sysadmin@localhost:~$ ls -l udev*                                               
-rw-r--r-- 1 sysadmin sysadmin 218 Mar 30 19:26 udev.conf                       
```

* Utiliza el comando ```zip``` para comprimir un archivo

```
sysadmin@localhost:~$ ls -l udev*                                               
-rw-r--r-- 1 sysadmin sysadmin 218 Mar 30 19:26 udev.conf                       
sysadmin@localhost:~$ zip udev.conf.zip udev.conf                               
  adding: udev.conf (deflated 24%)                                              
sysadmin@localhost:~$ ls -l udev*                                               
-rw-r--r-- 1 sysadmin sysadmin 218 Mar 30 19:26 udev.conf                       
-rw-rw-r-- 1 sysadmin sysadmin 333 Mar 30 19:42 udev.conf.zip                   
```

* Comprimir un directorio con ```zip```

```
sysadmin@localhost:~$ zip -r udev.zip /etc/udev                                 
  adding: etc/udev/ (stored 0%)                                                 
  adding: etc/udev/rules.d/ (stored 0%)                                         
  adding: etc/udev/rules.d/70-persistent-cd.rules (deflated 29%)                
  adding: etc/udev/rules.d/README (deflated 50%)                                
  adding: etc/udev/udev.conf (deflated 24%)                                     
sysadmin@localhost:~$ ls -l udev.zip                                            
-rw-rw-r-- 1 sysadmin sysadmin 1840 Mar 30 19:45 udev.zip                       
```

* Mostrar el contenido de un archivo comprimido con ```zip```

```
sysadmin@localhost:~$ unzip -l udev.zip                                         
Archive:  udev.zip                                                              
  Length      Date    Time    Name                                              
---------  ---------- -----   ----                                              
        0  2016-03-03 18:40   etc/udev/                                         
        0  2016-03-03 18:40   etc/udev/rules.d/                                 
      306  2016-03-03 18:39   etc/udev/rules.d/70-persistent-cd.rules           
     1157  2012-04-05 19:18   etc/udev/rules.d/README                           
      218  2012-04-05 19:18   etc/udev/udev.conf                                
---------                     -------                                           
     1681                     5 files                                           
```

* Extraer el contenido de un archivo comprimido con ```.zip```

```
sysadmin@localhost:~/mybackups$ unzip udev.zip
Archive:  udev.zip
creating: etc/udev/
creating: etc/udev/rules.d/
inflating: etc/udev/rules.d/70-persistent-cd.rules
inflating: etc/udev/rules.d/README
inflating: etc/udev/udev.conf
sysadmin@localhost:~/mybackups$
```
## Capítulo 8: (Las Barras Verticales, Redirección y Las Expresiones Regulares)

##### Las Barras Verticales en la Línea de Comandos

* El carácter barra vertical ```|``` (o «pipe» en inglés) puede utilizarse para enviar la salida de un comando a otro. En lugar de que se imprima en la pantalla, **la salida de un comando** se convierte en una **entrada para el siguiente comando**.

* Los comandos ```head``` (o «cabeza» en español) y ```tail``` (o «cola» en español) se pueden utilizar para mostrar solamente algunas de las primeras o las últimas líneas de un archivo (o, cuando se utiliza con una barra vertical, la salida de un comando anterior)

* Por defecto, los comandos ```head``` y ```tail``` mostrarán diez líneas. Por ejemplo, el siguiente comando muestra las diez primeras líneas del archivo ```/etc/sysctl.conf```:

```bash
sysadmin@localhost:~$ head /etc/sysctl.conf                            
#                                                                     
# /etc/sysctl.conf - Configuration file for setting system variables  
# See /etc/sysctl.d/ for additional system variables                   
# See sysctl.conf (5) for information.                                 
#                                                                     

#kernel.domainname = example.com                                                
                                                               
# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3                                        
sysadmin@localhost:~$
```
En el ejemplo siguiente, se mostrarán las últimas diez líneas del archivo:

```bash
sysadmin@localhost:~$ tail /etc/sysctl.conf                            
# Do not send ICMP redirects (we are not a router)                    
#net.ipv4.conf.all.send_redirects = 0                                  
#                                                                      
# Do not accept IP source route packets (we are not a router)         
#net.ipv4.conf.all.accept_source_route = 0                             
#net.ipv6.conf.all.accept_source_route = 0                             
#                                                                      
# Log Martian Packets                                                  
#net.ipv4.conf.all.log_martians = 1                                    
#                                                                      
sysadmin@localhost:~$
```
En lugar de mostrar la salida del comando anterior, poner la barra vertical junto al comando head muestra sólo las primeras diez líneas:

```bash
sysadmin@localhost:~$ ls /etc | head                                   
adduser.conf                                                           
adjtime                                                               
alternatives                                                         
apparmor.d                                                             
apt                                                                    
bash.bashrc                                                           
bash_completion.d                                                     
bind                                                                  
bindresvport.blacklist                                                 
blkid.conf                                                             
sysadmin@localhost:~$
```
La salida del comando ```ls``` se pasa al comando ```head``` por el shell en vez de ser impreso a la pantalla. El comando ```head``` toma esta salida (del ```ls```) como "datos de entrada" y luego se imprime la salida del ```head``` a la pantalla.

##### Redirección de E/S

La Redirección de Entrada/Salida (E/S) permite que la información pase de la línea de comandos a las diferentes secuencias. Antes de hablar sobre la redirección, es importante entender las secuencias estándar.

* STDIN - La entrada estándar STDIN es la información normalmente introducida por el usuario mediante el teclado. Cuando un comando envía un prompt al shell esperando datos, el shell proporciona al usuario la capacidad de introducir los comandos, que a su vez, se envían al comando como STDIN.
* STDOUT - Salida estándar o STDOUT es la salida normal de los comandos. Cuando un comando funciona correctamente (sin errores), la salida que produce se llama STDOUT. De forma predeterminada, STDOUT se muestra en la ventana de la terminal (pantalla) donde se ejecuta el comando.
* STDERR - Error estándar o STDERR son mensajes de error generados por los comandos. De forma predeterminada, STDERR se muestra en la ventana de la terminal (pantalla) donde se ejecuta el comando.

La redirección de E/S permite al usuario redirigir STDIN para que los datos provengan de un archivo y la salida de STDOUT/STDERR vaya a un archivo. La redirección se logra mediante el uso de los caracteres de la flecha: ```<``` y ```>```.

##### STDOUT

**STDOUT** se puede dirigir a los archivos. Para empezar, observa la salida del siguiente comando que se mostrará en la pantalla:

```bash
sysadmin@localhost:~$ echo "Line 1"                                    
Line 1                                                                 
sysadmin@localhost:~$
```

Utilizando el carácter > , la salida puede ser redirigida a un archivo:

```bash
sysadmin@localhost:~$ echo "Line 1" > ejemplo.txt                               
sysadmin@localhost:~$ ls                                                        
Desktop    Downloads  Pictures  Templates  ejemplo.txt                          
Documents  Music      Public    Videos                                          
sysadmin@localhost:~$ cat ejemplo.txt                                           
Line 1  
```
> Es importante tener en cuenta que la flecha sola sobrescribe cualquier contenido de un archivo existente.

También es posible preservar el contenido de un archivo existente anexando al mismo. Utiliza la «doble flecha» >> para anexar a un archivo en vez de sobreescribirlo:

```bash
sysadmin@localhost:~$ echo "Line 2" >>ejemplo.txt                               
sysadmin@localhost:~$ cat ejemplo.txt                                           
Line 1                                                                          
Line 2                                                                          
```
##### Redirigir la STDERR

* Puedes redirigir el STDERR de una manera similar a la STDOUT. Al STDOUT  se le asigna la secuencia o canal («stream» o «channel» en inglés) #2.

* Al utilizar las flechas para redirigir, se asumirá la secuencia #1 mientras no venga especificada otra secuencia. Por lo tanto, la secuencia #2 debe especificarse al redirigir el STDERR.

* Para demostrar la redirección del STDERR, primero observa el siguiente comando que producirá un error porque el directorio especificado no existe:

```bash
sysadmin@localhost:~$ ls /fake                                 
ls: cannot access /fake: No such file or directory              
sysadmin@localhost:~$
```

Ten en cuenta que no hay nada en el ejemplo anterior lo que implica que la salida es STDERR. La salida es claramente un mensaje de error, pero ¿cómo podrías saber que se envía al STDERR? Una manera fácil de determinar esto es redirigir al STDOUT:

```shell
sysadmin@localhost:~$ ls /fake > output.txt                    
ls: cannot access /fake: No such file or directory              
sysadmin@localhost:~$
```

En el ejemplo anterior, el STDOUT fue redirigido al archivo output.txt. Por lo tanto, la salida que se muestra no puede ser STDOUT porque habría quedado en el archivo output.txt. Ya que todos los resultados del comando van a STDOUT o STDERR, la salida mostrada debe ser STDERR.

El STDERR de un comando puede enviarse a un archivo:

```
sysadmin@localhost:~$ ls /fake 2> error.txt                     
sysadmin@localhost:~$ more error.txt                            
ls: cannot access /fake: No such file or directory              
sysadmin@localhost:~$
```

En el comando de arriba, 2> indica que todos los mensajes de error deben enviarse al archivo error.txt.

##### Redireccionando Múltiples Secuencias

Es posible dirigir la salida STDOUT y STDERR de un comando a la vez.

Las salidas STDOUT y STDERR pueden enviarse a un archivo mediante el uso de &> un conjunto de caracteres que significan «ambos 1> y 2>»:

```
sysadmin@localhost:~$ ls /fake /etc/ppp &> all.txt          
sysadmin@localhost:~$ cat all.txt                               
ls: cannot access /fake: No such file or directory              
/etc/ppp:                                                       
chap-secrets         
ip-down
ip-down.ipv6to4      
ip-up  
ip-up.ipv6to4
ipv6-down
ipv6-up
options
pap-secrets
peers                                                            
sysadmin@localhost:~$
```
Si no quieres que las salidas STDERR y STDOUT vayan al mismo archivo, puede redirigirlas a diferentes archivos utilizando > and 2>. Por ejemplo:

```
sysadmin@localhost:~$ ls /fake /etc/ppp > example.txt 2> error.txt        
sysadmin@localhost:~$ ls                                        
Desktop    Downloads  Pictures  Templates  all.txt    example.txt
Documents  Music      Public    Videos     error.txt  
sysadmin@localhost:~$ cat error.txt                             
ls: cannot access /fake: No such file or directory              
sysadmin@localhost:~$ cat example.txt                           
/etc/ppp:                                                       
chap-secrets         
ip-down
ip-down.ipv6to4      
ip-up  
ip-up.ipv6to4
ipv6-down
ipv6-up
options
pap-secrets
peers                 
sysadmin@localhost:~$
```
##### Redirigir la entrada STDIN

La mayoría de los usuarios de Linux terminan redirigiendo rutinariamente la STDOUT, en ocasiones la STDERR y la STDIN... bien, muy raramente. Hay muy pocos comandos que requieren de que redirijas la STDIN.

Para entender esto, consideremos primero un nuevo comando llamado tr. Este comando tomará un conjunto de caracteres y los plasmará en otro conjunto de caracteres.

Por ejemplo, supongamos que quieres poner una línea de comandos en mayúsculas. Puede utilizar el comando ```tr``` de la siguiente manera:

```
sysadmin@localhost:~$ tr 'a-z' 'A-Z'                         
watch how this works                                            
WATCH HOW THIS WORKS                                            
sysadmin@localhost:~$
```

El comando ```tr``` tomó la entrada STDIN desde el teclado (watch how this works) (a ver cómo funciona esto) y convierte todas las letras en minúsculas antes de enviar la salida STDOUT a la pantalla (WATCH HOW THIS WORKS).

Parecería que el comando ```tr``` sirviera más para realizar la traducción en un archivo, no la entrada del teclado. Sin embargo, el comando ```tr``` no admite argumentos del nombre de archivo:

Sin embargo, puedes decirle al shell que obtenga la STDIN de un archivo en vez de desde el teclado mediante el uso del carácter <:

```
sysadmin@localhost:~$ tr 'a-z' 'A-Z' < example.txt 
/ETC/PPP:                   
CHAP-SECRETS                                             
IP-DOWN                                                               
IP-DOWN.IPV6TO4                                                      
IP-UP                                                                 
IP-UP.IPV6TO4                                                         
IPV6-DOWN                                                             
IPV6-UP                                                               
OPTIONS                                                               
PAP-SECRETS                                                     
sysadmin@localhost:~$
```

Esto es bastante raro porque la mayoría de los comandos aceptan a los nombres de archivo como argumentos. Sin embargo, para los que no, este método podría utilizarse para que el shell lea desde el archivo en lugar de confiar en el comando que tienen esta capacidad.

Una última nota: En la mayoría de los casos probablemente quieras tomar la salida resultante y colocarla en otro archivo:

```
sysadmin@localhost:~$ tr 'a-z' 'A-Z' < example.txt > newexample.txt 
sysadmin@localhost:~$ more newexample.txt
/ETC/PPP:           
CHAP-SECRETS                                             
IP-DOWN                                                               
IP-DOWN.IPV6TO4                                                      
IP-UP                                                                 
IP-UP.IPV6TO4                                                         
IPV6-DOWN                                                             
IPV6-UP                                                               
OPTIONS                                                               
PAP-SECRETS                                                          
sysadmin@localhost:~$
```
##### Comando (find)

El comando find es una herramienta muy poderosa que puedes utilizar para buscar archivos en el sistema de archivos. Este comando puede buscar archivos por nombre, incluso usando los caracteres comodín cuando no estás seguro del nombre exacto del archivo. Además, puedes buscar los archivos en función de los metadatos de archivos, tales como tipo de archivo, tamaño de archivo y propiedad de archivo.

Component	| Description
---|---
[directorio de inicio]| 	Aquí el usuario especifica dónde comenzar la búsqueda. El comando find buscará en este directorio y todos sus subdirectorios. Si no hay directorio de partida, el directorio actual se utiliza para el punto de partida
[opción de búsqueda]|	Aquí el usuario especifica una opción para determinar qué tipo de metadatos hay que buscar; hay opciones para el nombre de archivo, tamaño de archivo y muchos otros atributos de archivo.
[criterio de búsqueda]|	Es un argumento que complementa la opción de búsqueda. Por ejemplo, si el usuario utiliza la opción para buscar un nombre de archivo, el criterio de búsqueda sería el nombre del archivo.
[opción de resultado]|	Esta opción se utiliza para especificar qué acción se debe tomar al encontrar el archivo. Si no se proporciona ninguna opción, se imprimirá el nombre del archivo a STDOUT.

##### Buscar por Nombre de Archivo (find -name)

Para buscar un archivo por nombre, utiliza la opción ```-name``` (o «nombre» en español) del comando ```find``` (o «buscar» en español):

```
sysadmin@localhost:~$ find /etc -name hosts                           
find: `/etc/dhcp': Permission denied
find: `/etc/cups/ssl': Permission denied  
find: `/etc/pki/CA/private': Permission denied  
find: `/etc/pki/rsyslog': Permission denied
find: `/etc/audisp': Permission denied 
find: `/etc/named': Permission denied
find: `/etc/lvm/cache': Permission denied 
find: `/etc/lvm/backup': Permission denied
find: `/etc/lvm/archive': Permission denied                           
/etc/hosts
find: `/etc/ntp/crypto': Permission denied
find: `/etc/polkit-l/localauthority': Permission denied   
find: `/etc/sudoers.d': Permission denied  
find: `/etc/sssd': Permission denied 
/etc/avahi/hosts
find: `/etc/selinux/targeted/modules/active': Permission denied  
find: `/etc/audit': Permission denied                                
sysadmin@localhost:~$
```

Observa que se encontraron dos archivos: ```/etc/hosts``` y ```/etc/avahi/hosts```. El resto de la salida eran los mensajes STDERR porque el usuario que ejecutó el comando no tiene permiso para acceder a ciertos subdirectorios.

Recuerda que puedes redirigir el STDERR a un archivo por lo que no necesitarás ver estos mensajes de error en la pantalla:

```
sysadmin@localhost:~$ find /etc -name hosts 2> errors.txt             
/etc/hosts 
/etc/avahi.hosts                                                      
sysadmin@localhost:~$
```

Mientras que la salida es más fácil de leer, realmente no hay ningún propósito para almacenar los mensajes de error en el archivo error.txt. Los desarrolladores de Linux se dieron cuenta de que sería bueno tener un archivo de «basura» (o «junk» en inglés) para enviar los datos innecesarios; se descarta cualquier archivo que envíes al archivo ```/dev/null```:

```
sysadmin@localhost:~$ find /etc -name hosts 2> /dev/null              
/etc/hosts
/etc/avahi/hosts                                                      
sysadmin@localhost:~$
```
##### Mostrando los Detalles del Archivo (find -name -ls)

Puede ser útil obtener información sobre el archivo al utilizar el comando ```find```, porque solo el nombre del archivo en sí mismo podría no proporcionar información suficiente para que puedas encontrar el archivo correcto.

Por ejemplo, puede haber siete archivos llamados hosts; si supieras que el archivo host que necesitas se había modificado recientemente, entonces sería útil ver la hora de modificación del archivo.

Para ver estos detalles del archivo, utiliza la opción ```-ls``` para el comando find:

```
sysadmin@localhost:~$ find /etc -name hosts -ls 2> /dev/null
    41   4 -rw-r--r--   1 root     root      158 Jan 12 2010 /etc/hosts
  6549   4 -rw-r--r--   1 root     root      1130 Jul 19 2011 /etc/avahi/hosts 
sysadmin@localhost:~$
```

> Las dos primeras columnas de la salida anterior son el número inodo del archivo y el número de bloques que el archivo utiliza para el almacenamiento. El resto de las columnas son la salida típica del comando ls -l: tipo de archivo, permisos, cuenta de enlaces físico, usuario propietario, grupo propietario, tamaño del archivo, hora de modificación del archivo y el nombre de archivo.

##### Buscar los Archivos por Tamaño

Una de las muchas opciones útiles de la búsqueda es la opción que le permite buscar archivos por tamaño. La opción ```-size``` (o «tamaño» en español) te permite buscar los archivos que son mayores o menores que un tamaño especificado, así como buscar un tamaño de archivo exacto.

Cuando se especifica un tamaño de archivo, puedes proporcionar el tamaño en **bytes (c), kilobytes (k), megabytes (M) o gigabytes (G)**. Por ejemplo, la siguiente será una búsqueda de archivos en la estructura de directorios ```/etc``` con el tamaño exacto de 10 bytes:

```
sysadmin@localhost:~$ find /etc -size 10c -ls 2>/dev/null    
   432    4 -rw-r--r--   1 root     root           10 Jan 28  2015 /etc/adjtime
 8814    0 drwxr-xr-x   1 root     root           10 Jan 29  2015 /etc/ppp/ip-d
own.d                                                           
8816    0 drwxr-xr-x   1 root     root           10 Jan 29  2015 /etc/ppp/ip-u
p.d                                                            
 8921    0 lrwxrwxrwx   1 root     root           10 Jan 29  2015 /etc/ssl/cert
s/349f2832.0 -> EC-ACC.pem                                    
  9234    0 lrwxrwxrwx   1 root     root           10 Jan 29  2015 /etc/ssl/cert
s/aeb67534.0 -> EC-ACC.pem                                     
 73468    4 -rw-r--r--   1 root     root           10 Nov 16 20:42 /etc/hostname
sysadmin@localhost:~$
```

Si quieres buscar los archivos que son más grandes que un tamaño especificado, puedes usar el carácter ```+``` antes que el tamaño. Por ejemplo, el siguiente ejemplo buscará todos los archivos en la estructura de directorio /usr que su tamaño sea mayor a 100 megabytes:

```
sysadmin@localhost:~$ find /usr -size +100M -ls 2> /dev/null
574683 104652 -rw-r--r--   1 root      root      107158256 Aug  7 11:06 /usr/share/icons/oxygen/icon-theme.cache                    
sysadmin@localhost:~$
```

Si quieres buscar los archivos que son más pequeños que un tamaño especificado, puedes usar el carácter ```-``` antes que el tamaño.

##### Opciones de Búsqueda Útiles Adicionales

Hay muchas opciones de búsqueda. La siguiente tabla muestra algunas:

Opción	| Significado
---|---
```-maxdepth```|	Permite al usuario especificar la profundidad en la estructura de los directorios a buscar. Por ejemplo, -maxdepth 1 significaría sólo buscar en el directorio especificado y en sus subdirectorios inmediatos.
```-group```	|Devuelve los archivos que son propiedad de un grupo especificado. Por ejemplo, -group payrolldevolvería los archivos que son propiedad del grupo payroll (o «nómina» en español).
```-iname```	|Devuelve los archivos especificados que coinciden con el nombre de archivo, pero a diferencia del -name, -iname no es sensible a las mayúsculas y minúsculas. Por ejemplo, -iname hosts coincidiría con los archivos llamados hosts, Hosts, HOSTS, etc.
```-mmin```	|Devuelve los archivos que fueron modificados según el tiempo de modificación en minutos. Por ejemplo, -mmin 10 coincidirá con los archivos que fueron modificados hace 10 minutos.
```-type```	|Devuelve los archivos que coinciden con el tipo de archivo. Por ejemplo, -type f devuelve los archivos que son archivos regulares.
```-user```	|Devuelve los archivos que son propiedad de un usuario especificado. Por ejemplo, -user bob devuelve los archivos que son propiedad del usuario bob.

##### Usar Múltiples Opciones

Si utilizas múltiples opciones, éstas actúan como un operador lógico "y", lo que significa que para que se dé una coincidencia, todos los criterios deben coincidir, no sólo uno. 

Por ejemplo, el siguiente comando muestra todos los archivos en la estructura de directorio ```/etc``` con el tamaño de 10 bytes y que son archivos simples:

```
sysadmin@localhost:~$ find /etc -size 10c -type f -ls 2>/dev/null       
432    4 -rw-r--r--   1 root     root           10 Jan 28  2015 /etc/adjtime
73468    4 -rw-r--r--   1 root     root           10 Nov 16 20:42 /etc/hostname
sysadmin@localhost:~$
```
##### Visualización de los Archivos Utilizando el Comando less

* Mientras que visualizar pequeños archivos con el comando ```cat``` no plantea ningún problema.
* Para archivos más grandes, querrás usar el comando pager que permite ver el contenido permiténdote moverte hacia adelante y hacia atrás en el archivo utilizando las teclas de movimiento.

**Hay dos comandos pager comúnmente utilizados:**

* El comando less: Este comando proporciona una capacidad de paginación muy avanzada. Normalmente es el pager predeterminado utilizado por comandos como el comando man.
* El comando more: Este comando ha existido desde los primeros días de UNIX. Aunque tenga menos funciones que el comando less, tiene una ventaja importante: El comando less no viene siempre incluido en todas las distribuciones de Linux (y en algunas distribuciones, no viene instalado por defecto). El comando more siempre está disponible.

##### La Pantalla de Ayuda con el Comando less

Al ver un archivo con el comando less, puedes utilizar la tecla ```h``` para mostrar una pantalla de ayuda.

Movimiento	|Tecla
---|---
Ventana hacia adelante |	Barra espaciadora
Ventana hacia atrás	|b
Línea hacia adelante|	Entrar
Salir|	q
Ayuda|	h

##### Comandos de Búsqueda less

Hay dos formas de buscar con el comando ```less```, puedes buscar hacia adelante o hacia atrás desde tu posición actual usando patrones llamados expresiones regulares.

Para iniciar una búsqueda hacia adelante desde tu posición actual, utiliza la tecla ```/```. A continuación, escribe el texto o el patrón y presiona la tecla **Enter**.

Para iniciar una búsqueda hacia atrás desde tu posición actual, pulsa la tecla ```?```, después introduce el texto o el patrón y presiona la tecla **Enter**

Si la búsqueda encuentra más de una coincidencia, entonces con la tecla **n** te puedes mover a la siguiente coincidencia y la tecla **N** te permitirá ir a la coincidencia anterior.

##### Revisando los Comandos head y tail

Recordemos que los comandos ```head``` y ```tail``` se utilizan para filtrar los archivos y mostrar un número limitado de líneas. Si quieres ver un número de líneas seleccionadas desde la parte superior del archivo, utiliza el comando ```head``` y si quieres ver un número de líneas seleccionadas en la parte inferior de un archivo, utiliza el comando ```tail```.

Ejemplos:

Comando de Ejemplo	|Explicación del texto visualizado
---|---
```head /etc/passwd```	|Las primeras diez líneas del archivo /etc/passwd
```head -3 /etc/group```	|Las primeras tres líneas del archivo/etc/group
```head -n 3 /etc/group	```|Las primeras tres líneas del archivo /etc/group
```help | head```	|Las primeras diez líneas de la salida del comando help redirigidas por la barra vertical
```tail /etc/group	```|Las últimas diez líneas del archivo /etc/group
```tail -5 /etc/passwd```	|Las últimas cinco líneas del archivo /etc/passwd
```tail -n 5 /etc/passwd```	|Las últimas cinco líneas del archivo /etc/passwd
```help | tail```	|Las últimas diez líneas de la salida del comando help redirigidas por la barra vertical

##### El Valor Negativo de la Opción -n

Tradicionalmente en UNIX, se especifica el número de líneas a mostrar como una opción con cualquiera de los comandos, así pues ```-3``` significa mostrar tres líneas. Para el comando ```tail```, la opción ```-3``` o ```-n -3``` siempre significará mostrar tres líneas. 

Sin embargo, la versión GNU del comando ```head``` reconoce ```-n -3``` como mostrar todo menos las tres últimas líneas, y sin embargo el comando ```head``` siempre reconoce la opción ```-3``` como muestra las tres primeras líneas.

##### El Valor Positivo del Comando tail

La versión GNU del comando ```tail``` permite una variación de cómo especificar el número de líneas que se deben imprimir. Si utilizas la opción ```-n``` con un número precedido por el signo más, entonces el comando ```tail``` reconoce esto en el sentido de mostrar el contenido a partir de la línea especificada y continuar hasta el final.

Por ejemplo, el siguiente ejemplo muestra la línea #22 hasta el final de la salida del comando ```nl```:

```
sysadmin@localhost:~$ nl /etc/passwd | tail -n +22                     
    22  sshd:x:103:65534::/var/run/sshd:/usr/sbin/nologin               
    23  operator:x:1000:37::/root:/bin/sh                               
    24  sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash  
sysadmin@localhost:~$
```
##### Seguimiento de los Cambios en un Archivo (tail -f)

Puedes ver los cambios en vivo en los archivos mediante la opción ```-f```del comando ```tail```. Esto es útil cuando quieres seguir cambios en un archivo mientras están sucediendo.

##### Ordenar Archivos o Entradas (sort)

Puede utilizarse el comando sort para reorganizar las líneas de archivos o entradas en orden alfabético o numérico basado en el contenido de uno o más campos. Los campos están determinados por un separador de campos contenido en cada línea, que por defecto son espacios en blanco (espacios y tabuladores).

En el ejemplo siguiente se crea un pequeño archivo, usando el comando ```head``` tomando las 5 primeras líneas del archivo /etc/passwd y enviando la salida a un archivo llamado **mypasswd**.

```
sysadmin@localhost:~$ head -5 /etc/passwd > mypasswd                    
sysadmin@localhost:~$
sysadmin@localhost:~$ cat mypasswd                                      
root:x:0:0:root:/root:/bin/bash                                         
daemon:x:1:1:daemon:/usr/sbin:/bin/sh                                   
bin:x:2:2:bin:/bin:/bin/sh                                              
sys:x:3:3:sys:/dev:/bin/sh                                              
sync:x:4:65534:sync:/bin:/bin/sync                                      
sysadmin@localhost:~$
```
Ahora vamos a ordenar (```sort```) el archivo **mypasswd**:

```
sysadmin@localhost:~$ sort mypasswd                                     
bin:x:2:2:bin:/bin:/bin/sh                                              
daemon:x:1:1:daemon:/usr/sbin:/bin/sh                                   
root:x:0:0:root:/root:/bin/bash                                         
sync:x:4:65534:sync:/bin:/bin/sync                                      
sys:x:3:3:sys:/dev:/bin/sh                                              
sysadmin@localhost:~$
```

##### Opciones de Campo y Ordenamiento

En el caso de que el archivo o entrada pueda separarse por otro delimitador como una coma o dos puntos, la opción ```-t``` permitirá especificar otro separador de campo. Para especificar los campos para ```sort``` (o en español «ordenar»), utiliza la opción ```-k``` con un argumento para indicar el número de campo (comenzando con 1 para el primer campo).

Las otras opciones comúnmente usadas para el comando sort son ```-n``` para realizar un sort numérico y ```-r``` para realizar a un sort inverso.

En el siguiente ejemplo, se utiliza la opción -t para separar los campos por un carácter de dos puntos y realiza un sort numérico utilizando el tercer campo de cada línea:

```
sysadmin@localhost:~$ sort -t: -n -k3 mypasswd                          
root:x:0:0:root:/root:/bin/bash                                         
daemon:x:1:1:daemon:/usr/sbin:/bin/sh                                   
bin:x:2:2:bin:/bin:/bin/sh                                              
sys:x:3:3:sys:/dev:/bin/sh                                              
sync:x:4:65534:sync:/bin:/bin/sync                                     
sysadmin@localhost:~$
```
Ten en cuenta que la opción ```-r``` se podía haber utilizado para invertir el ```sort```, causando que los números más altos en el tercer campo aparecieran en la parte superior de la salida:

```
sysadmin@localhost:~$ sort -t: -n -r -k3 mypasswd                       
sync:x:4:65534:sync:/bin:/bin/sync                                      
sys:x:3:3:sys:/dev:/bin/sh                                              
bin:x:2:2:bin:/bin:/bin/sh                                              
daemon:x:1:1:daemon:/usr/sbin:/bin/sh                                   
root:x:0:0:root:/root:/bin/bash                                         
sysadmin@localhost:~$
```

Por último, puede que quieras ordenarlo de una forma más compleja, como un ```sort``` por un campo primario y luego por un campo secundario. Por ejemplo, considera los siguientes datos:

```
bob:smith:23
nick:jones:56
sue:smith:67
```

Puede que quieras ordenar primero por el apellido (campo #2), luego el nombre (campo #1) y luego por edad (campo #3). Esto se puede hacer con el siguiente comando:
```
sysadmin@localhost:~$ sort -t: -k2 -k1 -k3n filename
```
##### Visualización de las Estadísticas de Archivo con el Comando wc

El comando ```wc``` permite que se impriman hasta tres estadísticas por cada archivo, así como el total de estas estadísticas, siempre que se proporcione más de un nombre de archivo. 

De forma predeterminada, el comando ```wc``` proporciona el número de líneas, palabras y bytes (1 byte = 1 carácter en un archivo de texto):

```
sysadmin@localhost:~$ wc /etc/passwd /etc/passwd-                         
  35   56 1710 /etc/passwd                                                
  34   55 1665 /etc/passwd-                                          
  69  111 3375 total                                                      
sysadmin@localhost:~$
```

El ejemplo anterior muestra la salida de ejecutar: ```wc /etc/passwd /etc/passwd -```. La salida tiene cuatro columnas: el número de líneas en el archivo, el número de palabras en el archivo, el número de bytes en el archivo y el nombre de archivo o total.

Si quieres ver estadísticas específicas, puede utilizar ```-l``` para mostrar sólo el número de líneas, ```-w``` para mostrar sólo el número de palabras y ```-c``` para mostrar sólo el número de bytes.

El comando ```wc``` puede ser útil para contar el número de líneas devueltas por algún otro comando utilizando la barra vertical. Por ejemplo, si desea saber el número total de los archivos en el directorio ```/etc```, puedes ejecutar ```ls /etc | wc -l```:

```
sysadmin@localhost:~$ ls /etc/ | wc -l                                  
136                                                                     
sysadmin@localhost:~$
```
##### Utilizar el Comando cut para Filtrar el Contenido del Archivo

El comando ```cut``` (o «cortar» en español) puede extraer columnas de texto de un archivo o entrada estándar. El uso primario del comando ```cut``` es para trabajar con los archivos delimitados de las bases de datos. Estos archivos son muy comunes en los sistemas Linux.

De forma predeterminada, considera que su entrada debe ser separada por el carácter Tab, pero la opción ```-d``` puede especificar delimitadores alternativos como los dos puntos o la coma.

Utilizando la opción ```-f``` puedes especificar qué campos quieres que se muestren, ya sea como un rango separado por guiones o una lista separada por comas.

En el ejemplo siguiente se visualiza el primero, quinto, sexto y séptimo campo del archivo de la base de datos de mypasswd:

```
sysadmin@localhost:~$ cut -d: -f1,5-7 mypasswd                          
root:root:/root:/bin/bash                                               
daemon:daemon:/usr/sbin:/bin/sh                                        
bin:bin:/bin:/bin/sh                                                    
sys:sys:/dev:/bin/sh                                                    
sync:sync:/bin:/bin/sync                                                
sysadmin@localhost:~$
```

Con el comando ```cut``` puedes también extraer las columnas de un texto basado en la posición de los caracteres con la opción ```-c```. Esto puede ser útil para extraer los campos de archivos de base de datos con un ancho fijo. El siguiente ejemplo muestra sólo el tipo de archivo (carácter #1), los permisos (caracteres #2-10) y el nombre de archivo (caracteres #50+) de la salida del comando ```ls -l```:

```
sysadmin@localhost:~$ ls -l | cut -c1-11,50-                            
total 12                                                                
drwxr-xr-x Desktop                                                      
drwxr-xr-x Documents                                                    
drwxr-xr-x Downloads                                                   
drwxr-xr-x Music                                                        
drwxr-xr-x Pictures                                                     
drwxr-xr-x Public                                                    
drwxr-xr-x Templates                                                   
drwxr-xr-x Videos                                                       
-rw-rw-r-- errors.txt                                                   
-rw-rw-r-- mypasswd                                                     
-rw-rw-r-- new.txt                                                      
sysadmin@localhost:~$
```
##### Utilizar el Comando grep para Filtrar el Contenido del Archivo

Puedes utilizar el comando ```grep``` para filtrar las líneas en un archivo o en la salida de otro comando basado en la coincidencia de un patrón. El patrón puede ser tan simple como el texto exacto que quieres que coincida o puede ser mucho más avanzado mediante el uso de las expresiones regulares.

Por ejemplo, puedes querer encontrar todos los usuarios que pueden ingresar al sistema con el shell BASH, por lo que se podría utilizar el comando grep para filtrar las líneas del archivo /etc/passwd para las líneas que contengan los caracteres bash:

```
sysadmin@localhost:~$ grep bash /etc/passwd                             
root:x:0:0:root:/root:/bin/bash                                         
sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash  
sysadmin@localhost:~$
```

Para que sea más fácil ver exactamente lo que coincide, utiliza la opción de ```--color```. Esta opción resaltará los elementos coincidentes en rojo:

```
sysadmin@localhost:~$ grep --color bash /etc/passwd                             
root:x:0:0:root:/root:/bin/bash                                         
sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash  
sysadmin@localhost:~$
```

En algunos casos no te interesan las líneas específicas que coinciden con el patrón, sino más bien cuántas líneas coinciden con el patrón. Con la opción ```-c``` puedes obtener un conteo del número de líneas que coinciden:

```
sysadmin@localhost:~$ grep -c bash /etc/passwd                          
2                                                                       
sysadmin@localhost:~$
```

Cuando estás viendo la salida del comando ```grep```, puede ser difícil determinar el número original de las líneas. Esta información puede ser útil cuando regreses al archivo (tal vez para editar el archivo), ya que puedes utilizar esta información para encontrar rápidamente una de las líneas coincidentes.

La opción ```-n``` del comando ```grep``` muestra los números de la línea originales:

```
sysadmin@localhost:~$ grep -n bash /etc/passwd                          
1:root:x:0:0:root:/root:/bin/bash                                       
24:sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bas
sysadmin@localhost:~$
```

Algunas opciones adicionales del ```grep``` que pueden resultar útiles:

Ejemplos	|Salida
---|---
```grep -v nologin /etc/passwd```	|Todas las líneas que no contengan nologin en el archivo /etc/passwd
```grep -l linux /etc/*```	|Lista de los archivos en el directorio /etc que contengan linux
```grep -i linux /etc/*```	|Listado de las líneas de los archivos en el directorio /etc que contengan cualquier tipo de letra (mayúscula o minúscula) del patrón de caracteres linux
```grep -w linux /etc/*```	|Listado de las líneas de los archivos en el directorio /etc que contengan el patrón de la palabra linux

##### Las Expresiones Regulares Básicas

Una Expresión Regular es una colección de caracteres «normales» y «especiales» que se utilizan para que coincida con un patrón simple o complejo. Los caracteres normales son caracteres alfanuméricos que coinciden con ellos mismos. Por ejemplo, la letra ```a``` coincide con una ```a```.

Algunos caracteres tienen significados especiales cuando se utilizan dentro de los patrones por comandos como el comando ```grep```. Existen las **Expresiones Regulares Básicas** (disponible para una amplia variedad de comandos de Linux) y las **Expresiones Regulares Extendidas** (disponibles para los comandos más avanzados de Linux). 

Las Expresiones Regulares Básicas son las siguientes:

Expresión Regular	|Coincidencias
---|---
```.``` |Cualquier carácter individual
```[ ]```	|Una lista o rango de caracteres que coinciden con un carácter, a menos que el primer carácter sea el símbolo de intercalación ^, lo que entonces significa cualquier carácter que no esté en la lista
```*```	|El carácter previo que se repite cero o más veces
```^```	|El texto siguiente debe aparecer al principio de la línea
```$ ```|	El texto anterior debe aparecer al final de la línea

El comando ```grep``` es sólo uno de los muchos comandos que admiten expresiones regulares. 

Algunos otros comandos son los comandos ```more``` y ```less```. 

Mientras que a algunas de las expresiones regulares se les ponen innecesariamente con comillas simples, **es una buena práctica utilizar comillas simples con tus expresiones regulares** para evitar que el shell trate a interpretar su significado especial.

##### Expresiones Regulares Básicas - el Carácter (.)

En el ejemplo siguiente, un simple archivo primero se crea usando la redirección. Después el comando grep se utiliza para mostrar una coincidencia de patrón simple:

```
sysadmin@localhost:~$ echo 'abcddd' > example.txt                       
sysadmin@localhost:~$ cat example.txt                                   
abcddd                                                                 
sysadmin@localhost:~$ grep --color 'a..' example.txt                    
abcddd                                                                 
sysadmin@localhost:~$
```
En el ejemplo anterior, se puede ver que el patrón a.. coincidió con abc. El primer carácter . coincidió con b y el segundo coincidió con c.

##### Expresiones Regulares Básicas - el Carácter ([ ])

Si usas el carácter ```.```, entonces cualquier carácter posible podría coincidir. En algunos casos quieres especificar exactamente los caracteres que quieres que coincidan. Por ejemplo, tal vez quieres que coincida un sólo carácter alfa minúscula o un carácter de número. Para ello, puedes utilizar los caracteres de expresiones regulares ```[ ]``` v y especificar los caracteres válidos dentro de los caracteres ```[ ]```.

Por ejemplo, el siguiente comando coincide con dos caracteres, el primero es ya sea una a o una b mientras que el segundo es una a, b, c o d:

```
sysadmin@localhost:~$ grep --color '[ab][a-d]' example.txt              
abcddd                                                                  
sysadmin@localhost:~$
```

Ten en cuenta que puedes enumerar cada carácter posible [abcd] o proporcionar un rango [a-d] siempre que esté en el orden correcto. Por ejemplo, [d-a] no funcionaría ya que no es un intervalo válido:

```
sysadmin@localhost:~$ grep --color '[d-a]' example.txt                  
grep: Invalid range end                                                 
sysadmin@localhost:~$
```

El rango se especifica mediante un estándar denominado la tabla ASCII. Esta tabla es una colección de todos los caracteres imprimibles en un orden específico. Puedes ver la tabla ASCII con el comando man ascii. Un pequeño ejemplo:

```   041  33  21  !                                 141   97  61  a 
      042  34  22  “                                 142   98  62  b
      043  35  23  #                                 143   99  63  c
      044  36  24  $                                 144   100 64  d
      045  37  25  %                                 145   101 65  e
      046  38  26  &                                 146   102 66  f
```

Puesto que la a tiene un valor numérico más pequeño (141) que la d (144), el rango a-d incluye todos los caracteres de la a a la d.

¿Qué pasa si quieres un carácter que puede ser cualquier cosa menos una x, y o z? No querrías proporcionar un conjunto de ```[ ]``` con todos los caracteres excepto x, y o z.

Para indicar que quieres que coincida un carácter que no es uno de lo listados, inicia tu conjunto de ```[ ]``` con el símbolo ```^```. El siguiente ejemplo muestra la coincidencia de un patrón que incluye un carácter que no es un a, b o c seguida de un d:

```
sysadmin@localhost:~$ grep --color '[^abc]d' example.txt                
abcddd                                                                  
sysadmin@localhost:~$
```

##### Expresiones Regulares Básicas - el Carácter *

El carácter ```*``` se puede utilizar para coincidir con «cero o más de los caracteres previos». El siguiente ejemplo coincidirá con cero o más caracteres d:

```
sysadmin@localhost:~$ grep --color 'd*' example.txt                     
abcddd                                                                  
sysadmin@localhost:~$
```

##### Expresiones Regulares Básicas - los Caracteres ```^``` y ```$```

Cuando quieres que coincida un patrón, tal coincidencia puede ocurrir en cualquier lugar de la línea. Puede que quieras especificar que la coincidencia se presentara al principio de la línea o al final de la línea. Para que coincida con el principio de la línea, comienza el patrón con el símbolo ```^```.

En el ejemplo siguiente se agrega otra línea al archivo example.txt para mostrar el uso del símbolo ```^```:

```
sysadmin@localhost:~$ echo "xyzabc" >> example.txt                      
sysadmin@localhost:~$ cat example.txt                                   
abcddd                                                                  
xyzabc                                                                
sysadmin@localhost:~$ grep --color "a" example.txt                     
abcddd                                                                  
xyzabc                                                                  
sysadmin@localhost:~$ grep --color "^a" example.txt                     
abcddd                                                                  
sysadmin@localhost:~$
```

Ten en cuenta que en la primera salida del ```grep```, ambas líneas coinciden debido a que ambas contienen la letra a. En la segunda salida ```grep```, solo coincide con la línea que comienza con la letra a.

Para especificar que coincida al final de la línea, termina el patrón con el carácter ```$```. Por ejemplo, para encontrar sólo las líneas que terminan con la letra c:

```
sysadmin@localhost:~$ grep "c$" example.txt                             
xyzabc                                                                  
sysadmin@localhost:~$
```

##### Expresiones Regulares Básicas - el Carácter ```\```

En algunos casos querrás que la búsqueda coincida con un carácter que resulta ser un carácter especial de la expresión regular.

```
sysadmin@localhost:~$ echo "abcd*" >> example.txt                       
sysadmin@localhost:~$ cat example.txt                                   
abcddd                                                                  
xyzabc                                                                  
abcd*                                                                   
sysadmin@localhost:~$ grep --color "cd*" example.txt                    
abcddd                                                                  
xyzabc                                                                  
abcd*                                                                   
sysadmin@localhost:~$
```
En la salida del comando grep anterior, ves que cada línea corresponde porque estás buscando el carácter c seguido de cero o más caracteres d. Si quieres buscar un carácter ```*```, coloca el carácter ```\``` antes del carácter ```*```:

```
sysadmin@localhost:~$ grep --color "cd\*" example.txt                   
abcd*                                                                   
sysadmin@localhost:~$
```
##### Expresiones Regulares Extendidas

El uso de las Expresiones Regulares Extendidas requiere a menudo una opción especial proporcionada al comando para que éste las reconozca. 

Históricamente, existe un comando llamado ```egrep```, que es similar al ```grep```, pero es capaz de entender su uso. Ahora, el comando ```egrep``` es obsoleto a favor del uso del ```grep``` con la opción ```-E```.

El comando ```fgrep``` se utiliza para hacer que la búsqueda coincida con los caracteres literales, ignorando el significado especial de los caracteres de expresiones regulares.

Las siguientes expresiones regulares se consideran «extendidas»:

RE	|Significado
---|---
```?```	|Coincide con el carácter anterior cero o una vez más, así que es un carácter opcional
```+```	|Coincide con el carácter anterior repetido una o más veces
```|```	|Alternación o como un operador lógico

Algunos ejemplos de expresiones regulares extendidas:

Comando|	Significado	|Coincidencias
---|---|---
```grep -E 'colou?r' 2.txt```	|Haz coincidir colo seguido por cero o un carácter u	|```color colour```
```grep -E 'd+' 2.txt```|	Coincide con uno o más d caracteres	|```d dd ddd dddd```
```grep -E 'gray|grey' 2.txt```|	Coincide con gray o grey	|```gray grey```

##### El Command xargs

El comando ```xargs``` se utiliza para construir y ejecutar líneas de comandos de una entrada estándar. Este comando es muy útil cuando se necesita ejecutar un comando con una lista de argumentos muy larga, que en algunos casos puede resultar en un error si la lista de argumentos es demasiado larga.

El comando ```xargs``` funciona separando la lista de los argumentos en sublistas y ejecutando el comando con cada sublista. El número de los argumentos en cada sublista no excederá el número máximo de los argumentos para el comando ejecutado, y por lo tanto, evita el error de _«Argument list too long»_ (o «Lista de argumentos demasiado larga» en español).

En el ejemplo siguiente se muestra un escenario donde el comando ```xargs``` permite que muchos archivos sean eliminados, y donde el uso de un carácter comodín normal (glob) falló:

```
sysadmin@localhost:~/many$ rm *                
bash: /bin/rm: Argument list too long
sysadmin@localhost:~/many$ ls | xargs rm
sysadmin@localhost:~/many$
```
## Capítulo 9: El Scripting Básico

Un script shell es un archivo de comandos ejecutables que ha sido almacenado en un archivo de texto. Cuando el archivo se ejecuta, se ejecuta cada comando. Los scripts shell tienen acceso a todos los comandos del shell, incluyendo la lógica. Un script (o «secuencia de comandos» en español), por lo tanto, puede detectar la presencia de un archivo o buscar una salida particular y cambiar su comportamiento en consecuencia. Se pueden crear scripts para automatizar partes repetitivas de tu trabajo, que ahorran tu tiempo y aseguran consistencia cada vez que utilices el script.

Un script puede ser tan simple como un único comando:

```
echo “Hello, World!”
```

El script, ```test.sh```, consta de una sola línea que imprime la cadena Hello, World! (o «¡Hola, Mundo!» en español) en la consola.

Ejectutar un script puede hacerse, ya sea pasándolo como un argumento a tu shell o ejecuándolo directamente:

```
sysadmin@localhost:~$ sh test.sh
Hello, World!
sysadmin@localhost:~$ ./test.sh
-bash: ./test.sh: Permission denied
sysadmin@localhost:~$ chmod +x ./test.sh
sysadmin@localhost:~$ ./test.sh
Hello, World!
```

En el ejemplo anterior, en primer lugar, el script se ejecuta como un argumento del shell. A continuación, se ejecuta el script directamente desde el shell. Es raro tener el directorio actual en la ruta de búsqueda binaria $PATH, por lo que el nombre viene con el prefijo ```./``` para indicar que se debe ejecutar en el directorio actual.

El error Permission denied (o «Permiso denegado» en español) significa que el script no ha sido marcado como ejecutable. Un comando ```chmod``` rápido después y el script funciona.

Hay varios shells con su propia sintaxis de lenguaje. Por lo tanto, los scripts más complicados indicarán un shell determinado, especificando la ruta absoluta al intérprete como la primera línea, con el prefijo ```#!```, tal como lo muestra el siguiente ejemplo:

```
#!/bin/sh
echo “Hello, World!”
```
o

```
#!/bin/bash
echo “Hello, World!”
```
Los dos caracteres ```#!``` se llaman tradicionalmente el hash y el bang respectivamente, que conduce a la forma abreviada «shebang» cuando se utilizan al principio de un script.

> Por cierto, el shebang (o crunchbang) se utiliza para los scripts shell tradicionales y otros lenguajes basados en texto como Perl, Ruby y Python. Cualquier archivo de texto marcado como ejecutable se ejecutará bajo el intérprete especificado en la primera línea mientras se ejecuta el script directamente. Si el script se invoca directamente como argumento a un intérprete, como sh script o bash script, se utilizará el shell proporcionado, independientemente de lo que está en la línea del shebang.

##### Editar los Scripts Shell

UNIX tiene muchos editores de texto y las ventajas del uno sobre el otro se debaten muy a menudo. El editor de GNU ```nano``` es un editor muy sencillo y bien adaptado para editar pequeños archivos de texto. El Visual Editor , ```vi```, o su versión más reciente, VI mejorado (```vim```), es un editor muy potente pero tiene un arduo proceso de aprendizaje. Nosotros nos centraremos en el ```nano```.

Introduce nano test.sh y verás una pantalla similar a esta:

```
GNU nano 2.2.6              File: test.sh                         modified

#!/bin/sh

echo "Hello, World!"
echo -n "the time is "
date
                                    
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Po 
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell
```

Comando	|Descripción 
---|---
Ctrl + W	|buscar en el documento
Ctrl + W, |luego Control + R	buscar y reemplazar
Ctrl + G	|1mostrar todos los comandos posibles
Ctrl + Y/V|	página hacia arriba / abajo
Ctrl + C	|mostrar la posición actual en el archivo y el tamaño del archivo

##### Las Variables
Las variables son una parte esencial de cualquier lenguaje de programación. A continuación se muestra un uso muy simple de las variables:

```
#!/bin/bash

ANIMAL="penguin"
echo "My favorite animal is a (SimboloDolar)ANIMAL"
```
9.4.1