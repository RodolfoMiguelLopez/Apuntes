#DOCKER Apuntes

<a id="indice"></a>
##Índice

1. [¿Que es un contenedor?](#quees)
2. [Características de un contenedor](#2)
3. [Instalar las VirtualBox Guest Addition en UBUNTU](#3)
4. [Instalando Docker](#4)
5. [Comprobación de la instalación de Docker](#5)
6. [Contenedores e imágenes (Teoría)](#6)
7. [Descargando imágenes](#7)
8. [Ciclo de vida de los contendores](#8)
9. [Creando contenedor](#9)
10. [Contenedores interactivos](#10)
11. [ID de contenedores](#11)
12. [Listado con filtro de contenedores](#12)


Docker es un proyecto de código abierto que automatiza el despliegue de aplicaciones dentro de contenedores de software, proporcionando una capa adicional de abstracción y automatización de Virtualización a nivel de sistema operativo en Linux.Docker utiliza características de aislamiento de recursos del kernel de Linux, tales como **cgroups** y espacios de nombres **namespaces** para permitir que **contenedores** independientes se ejecuten dentro de una sola instancia de Linux, evitando la sobrecarga de iniciar y mantener máquinas virtuales.

[Artículo Docker en Wikipedia](https://es.wikipedia.org/wiki/Docker_(software))

- Docker funciona en local y tambien es posible desplegar en servidores cloud.
- Se pueden manejar a través de interfaz GUI y CLI.
- Multiplataforma.
- Uso más eficaz de recursos respecto a las VM´s.
- Mejor velocidad y escalabilidad con respecto a las VM´s.

[Subir](#indice)
<a id="quees"></a>
##¿Que es un contenedor?

**Contenedor = namespaces + cgroups + chroot**

Tecnología | Descripción
---|---
namespaces | Vistas de los recursos del SO.
cgroups | Limitan y miden los recursos del SO.
chroot | Cambia el root directory de un proceso ( la aplicación solo verá el contenido de los directorios que nosotros le digamos.

[Subir](#indice)
<a id="2"></a>
###caracteristicas de un Contenedor:

- Los contenedores son mas livianos que las VM´s al trabajar directamente sobre el kernel.
- No es necesario instalar un OS por contenedor.
- Menos utilización de recursos.
- Mayor cantidad de contenedores por equipo físico.
- Mejor portabilidad.

[Subir](#indice)
<a id="3"></a>
###Instalar las VirtualBox Guest Addition en UBUNTU 16.04 si estás usando VIRTUALBOX

```bash
user@user-VirtualBox:~$ sudo apt-get install virtualbox-guest-dkms
```
###Instalar curl si no se tiene instalado

```bash
user@user-VirtualBox:~$ sudo apt-get install curl
```
[Subir](#indice)
<a id="4"></a>
###Instalando Docker

Para hacer una instalación limpia desde 0 en cualquier plataforma mejor usar 

[https://get.docker.com/](https://get.docker.com/)


Para instalar en linux por ejemplo solo tenemos que copiar el siguiente comando en la terminal desde linux

```bash
user@user-VirtualBox:~$ sudo curl -sSL https://get.docker.com/ | sh
```

Una vez terminada la instalación nos indica que incluyamos el usuario docker como administrador esto lo hace para poder iniciar el demonio de docker, se hace de la siguiente manera

```bash
user@user-VirtualBox:~$ sudo usermod -aG docker user
```
Una vez ejecutado este comando es recomendable desloguearte (cerrar la terminal y volver a abrirla) para que tenga efecto de lo contrario habrá que ejecutar todos los comandos como root.

las opciones aplicadas del comando usermod son las siguientes:

Opcion | Acción
---|--- 
-a, --append | append the user to the supplemental GROUPS mentioned by the -G option without removing him/her from other groups.
-G, --groups GRUPOS | lista de grupos suplementarios.

OPCIONAL Puede que haya problemas de permisos con los archivos de docker para ello podemos usar el siguiente comando:

```bash
sudo chmod -R 775 /var/run/docker.sock
```

[Subir](#indice)
<a id="5"></a>
###Comprobación de la instalación de Docker

Comando | Descripción
---|---
service docker start | Ejecutamos el demonio de docker
service docker stop | Detenemos el demonio de docker
docker info | Nos dá información de la app docker ( hay que ejecutar el demonio de docker )
docker version | Dá información de las versiones de la herramienta docker.
docker run hello-world | Nos lanza una aplicación para comprobar que hemos realizado la instalación correctamente, si no está ya descargada nos la descarga y despues nos la ejecuta.


Salida del comando: ```docker run hello-world```

```bash
user@user-VirtualBox:~$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/

```
[Subir](#indice)
<a id="6"></a>
###Contenedores e imágenes (Teoría)

- Imágenes:
	- Es una plantilla de solo lectura para crear nuestros contenedores.
	- Creadas por nosotros o por la comunidad.
	- Se pueden crear en un registro interno o público.
	- Se le pueden agregar capas con diferentes servicios
- Contenedores:
	- Aplicación aislada.
	- Contiene todo lo necesario para ejecutar nuestra aplicación.
	- Basada en una o más imágenes.

en el repositorio de hub.docker las imágenes se guardan con el formato repositorio:tag , los tags sirven principalmente para diferenciar varias versiones, si no especificamos ningún tag cuando bajamos el contenedor por defecto nos baja el que tenga el tag: latest.

[Subir](#indice)
<a id="7"></a>
###Descargando imágenes

Para descargar una imagen del repositorio externo se utiliza el comando  ```docker pull```
Cuando se ejecuta un contenedor con el comando ```docker run``` las imagenes son descargadas automáticamente si no se encuentran en el repositorio local.

Comando para ver las imagenes instaladas:

```bash
user@user-VirtualBox:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hello-world         latest              48b5124b2768        4 months ago        1.84kB
```
Comando para bajar una imagen:

```bash
user@user-VirtualBox:~$ docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
b6f892c0043b: Pull complete 
55010f332b04: Pull complete 
2955fb827c94: Pull complete 
3deef3fcbd30: Pull complete 
cf9722e506aa: Pull complete 
Digest: sha256:382452f82a8bbd34443b2c727650af46aced0f94a44463c62a9848133ecb1aa8
Status: Downloaded newer image for ubuntu:latest
```
Comando para bajar una imagen con un tag específico:

```
user@user-VirtualBox:~$ docker pull ubuntu:16.10
16.10: Pulling from library/ubuntu
869d7e479fb8: Pull complete 
fcde8cc75da4: Pull complete 
b9d18efd03be: Pull complete 
95ed9114795e: Pull complete 
63ec97b2b19c: Pull complete 
Digest: sha256:2c935ced8a4ebecab443216ee4dd9e11dc1c85f81a04f07277f99567238f00d9
Status: Downloaded newer image for ubuntu:16.10
```
[Subir](#indice)
<a id="8"></a>
###Ciclo de vida de los contendores

- Ciclo de vida básico
	- Se crea el contenedor a partir de una imagen
	- se ejecuta un proceso determinado en el contenedor
	- el proceso finaliza y el contenedor se detiene
	- se destruye el contenedor
- Ciclo de vida avanzado
	- Se crea el contenedor a partir de una imagen
	- se ejecuta un proceso determinado en el contenedor
	- realizar acciones dentro del contenedor
	- detener el contenedor
	- lanzar el contenedor nuevamente

[Subir](#indice)
<a id="9"></a>
###Creando contenedor

Para crear nuestro primer contenedor utilizamos el comando ```docker run```
este comando realiza dos acciones
	- Crea el contenedor con la imagen especificada
	- Ejecuta el contenedor
La sintaxis es:
**docker run [opciones] [imagen][comando][args]**
el formato de la imagen es: **repository:[tag]**

Ejecutamos un contenedor de docker y le decimos que ejecute un echo:

```
user@user-VirtualBox:~$ docker run ubuntu echo "hola que tal"
hola que tal
```
para ver los procesos se usa el comando ```docker ps```
para ver el listado de procesos detenidos se usa ```docker ps -a```

salida del listado de procesos detenidos

```bash
user@user-VirtualBox:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND                 CREATED             STATUS                         PORTS               NAMES
0ec7708d7568        ubuntu              "echo 'hola que tal'"   16 seconds ago      Exited (0) 14 seconds ago  
```
Si nos fijamos hemos ejecutado el contenedor, hemos ejecutado un comando y se ha detenido.

[Subir](#indice)
<a id="10"></a>
## Contenedores interactivos

Utilizamos las banderas **```-i**``` y **```-t**``` en el comando docker run para conseguir interactividad con el contenedor.

- la bandera **```-i```** le indica a docker utilizar STDIN del contenedor
- la bandera **```-t```** indica que se requiere de una pseudo terminal

Nota: Es necesario ejecutar un proceso de terminal en el contenedor (ej:sh/bash/zsh/stc)

Con este comando conseguimos una terminal dentro del contenedor:

```bash
user@user-VirtualBox:~$ docker run -it ubuntu bash
```
para salir del contenedor usamos el comando ```exit```

si ejecutamos comandos en esta terminal lo estaremos haciendo dentro del contenedor no en nuestra máquina.

para poder salir de un contenedor pero sin cerrarlo podemos usar la combinación de teclas CTRL + PQ
con esto salimos del contenedor pero sin cerrarlo si hacemos un docker ps veríamos el contenedor que etá ejecutandos.

para volver al contenedor que está ejecutandose hay que usar:```docker attach [id contenedor]```

```
user@user-VirtualBox:~$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS              PORTS               NAMES
97a403905611        ubuntu              "bash"              About a minute ago   Up About a minute                       optimistic_varahamihira
user@user-VirtualBox:~$ docker attach 97a
root@97a403905611:/# ls  
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@97a403905611:/# 
```
[Subir](#indice)
<a id="11"></a>
###ID de contenedores
- los contenedores pueden referenciarse utilizando su ID de contenedor o un nombre
- ID formato reducido y extendido
- la información se puede obtener con el comando ```docker ps```o ```docker ps -a```si ya está detenido
- utilizar la bandera --no-trunc en docker ps para obtener el formato extendido de ID.

Comando para ver comando ID extendido de docker:

```bash
user@user-VirtualBox:~$ docker ps -a --no-trunc
```
Comando para proveer al contenedor de un nombre:

```bash
user@user-VirtualBox:~$ docker run --name rodolfo ubuntu ls
```

- docker start [ID][nombre] | vuelve a ejecutar un contenedor que ya está parado
- docker kill [ID][nombre] | Fuerza parar un contenedor
- docker rm [ID][nombre] | borra un contenedor

[Subir](#indice)
<a id="12"></a>
##Listado con filtro de contenedores

- La bandera --filter agrega condiciones de filtrado
- Se puede filtrar basado en el código de salida y estado del contenedor
- El estado puede ser
	- Restarting
	- Running
	- Exited
	- Paused
- Para especificar múltiples condiciones utilizar la bandera --filter por cada condición.
- Otros filtros: id, label, name, exited, statu, ancestor, isolation.

ejemplo: Filtrar todos los contenedores detenidos que tengan la condición exited = 0

```bash
user@user-VirtualBox:~$ docker ps -a --filter="exited=0"
```
ejemplo: Filtra todos los contenedores que tenga una salida con error.

```bash
user@user-VirtualBox:~$ docker ps -a --filter="exited=1"
```
###Ejecutando contenedores de fondo

- Correr de fondo (background) o como demonio
- Utilizar la bandera -d
- Para ver el output hay que utilizar el comando **```docker logs [id contenedor]/[nombre contenedor]```**

por defecto el contenedor de ubuntu no trae instaladas muchas cosas así que hay que instalarlas a mano

root@a2941c266d6c:/# apt-get update
root@a2941c266d6c:/# apt-get install iputils-ping
root@a2941c266d6c:/# ping -c 10 www.google.es

si por ejemplo ejecutamos un ping con un tiempo de 10s sería de la siguiente manera:

```bash
user@user-VirtualBox:~$ docker run ubuntu ping -c 10 www.google.es
```
para ejecutar el mismo comando y que corra por detrás como si fuera un demonio hay que ponerle la variable -d

```bash
user@user-VirtualBox:~$ docker run -d ubuntu ping -c 10 www.google.es
```
para poder ver el log de un contenedor que hemos dejado en background con **```-d```** podemos usar:

```bash
user@user-VirtualBox:~$ docker logs [id][nombre]
```
para poder ver el log de un contenedor que hemos dejado en background con **```-d```** pero en tiempo real y cuando termine el progreso nos volverá a nuestra terminal usaremos:

```bash
user@user-VirtualBox:~$ docker logs -f [id][nombre]
```
La forma de entrar en un contenedor para ver que está pasando es a través del comando exec:

```bash
user@user-VirtualBox:~$ docker exec -ti 962 bash
```
###Instalando TOMCAT
instalamos tomcat con la siguiente sintaxis:

```
user@user-VirtualBox:~$ docker run -P -d tomcat
```
si hacemos un ```docker ps```veremos lo siguiente:

```
user@user-VirtualBox:~$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS                     NAMES
0cd5c3667b46        tomcat              "catalina.sh run"   3 minutes ago       Up 3 minutes        0.0.0.0:32768->8080/tcp   tender_tesla
```
Si nos vamos al explorador y ejecutamos la siguiente dirección **http://localhost:32768/** comprobaremos que el servidor tomcat está instalado.

Con ```docker start -a [id][nombre]```ejecutamos un contenedor y nos adjuntamos a el automáticamente par ver su salida.
Con ```docker pause [id][nombre]```detenemos la ejecución de un contenedor.
Con ```docker unpause [id][nombre]```quitamos la pausa a la ejecución del contenedor.
Con ```docker inspect [id][nombre]``` podemos ver información de un contenedor que está corriendo.

Podemos usar GREP para filtrar una salida de docker inspect ejemplo:

```bash
user@user-VirtualBox:~$ docker inspect 0cd | grep IPAddress
            "SecondaryIPAddresses": null,
            "IPAddress": "172.17.0.2",
                    "IPAddress": "172.17.0.2",
```
###Borrando Contenedores

- Por defecto solo pueden eliminarse contenedores detenidos
- Se utiliza el comando **```docker rm [id][nombre]```** para borrar un contenedor
- Se utiliza el comando **```docker rm -f [id][nombre]```** para borrar un contenedor en ejecución.
- Se utiliza el comando **```docker rm $(docker ps -a -q)```** para borrar todos los contenedores que lista el comando ```docker ps -a -q```Con este comando lo que hacemos es pasarle a ```docker rm``` la salida de ```docker ps```.


###Creación de Imágenes

![Creación de IMÁGENES ](Creacion_de_imagenes.jpg)

- Sistema de capas entre imágenes
- Docker crea una última capa de modo escritura para los contenedores
- Las imágenes padre son de sólo lectura
- Todos los cambios son realizados en la capa de escritura

FORMAS DE CREAR UNA IMAGEN

- Hacer `commit`de los contenidos de un contenedor
- Construir una imagen basándose en un Dockerfile
- Importar un archivo Tar a docker con el contenido de una imagen

Para crear una imagen abrimos un contenedor lo modificamos y sin cerrarlo podemos hacer desde otra terminal un commit:

```docker commit [id] [nombre_nuevo]```

Con el comando **```docker diff [id]```** podemos ver los cambios que se le han hecho al contenedor original que se le ha creado.

###Ejemplo creación de una imagen con commit:
####Consola 1
	
- docker run -ti ubuntu
- apt-get update
- apt-get install iputils-ping

####Consola 2

- docker ps 

```
user@user-VirtualBox:~$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
d6dc46d8af4f        ubuntu              "/bin/bash"         7 minutes ago       Up 7 minutes                            boring_dubinsky
```
- docker commit d6d ubuntu-ping

```
user@user-VirtualBox:~$ docker commit d6d ubuntu-ping
sha256:bb790cd9c100077e615f72e35eb07aa387c0234cc9df2bbff0ffe21705d24736
```
- docker images

```
user@user-VirtualBox:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu-ping         latest              bb790cd9c100        7 seconds ago       160MB
tomcat              latest              0785a1d16826        13 hours ago        367MB
ubuntu              16.10               8d4c9ae219d0        45 hours ago        106MB
ubuntu              latest              ebcd9d4fca80        45 hours ago        118MB
hello-world         latest              48b5124b2768        4 months ago        1.84kB
user@user-VirtualBox:~$ 
```
###Demonios de DOCKER en Linux

La forma en la que iniciamos / detenemos el demonio de Docker depende de distintos factores.

- Se encuentra corriendo como servicio?
	- Usamos El comando ```service``` o ```systemctl``` depende de la versión de linux
	Comando: ```lsb_release -a ``` para ver la versión del SO linux
	
si al ejecutar el comando systemctl existe en el SO todos los servicios están manejados con systemd sino están con upstart.

- Comandos a usar con upstart

service docker status
service docker start
service docker stop (sudo)
docker daemon | arrancamos el demonio de docker (no es la manera buena de arrancarlo)

- Comandos a usar con SystemD

service docker status
service docker start
service docker stop (sudo)

- Iniciar el demonio de manera manual 

docker daemon --help

--dns [para añadir un DNS específico]
-G [añade el usuario actual al grupo de Docker como administrador , se puede cambiar el nombre]
-g --graph=/var/lib/docker [carpeta donde docker va a guardar todos los archivos]
-H [Le dice al demonio de que manera escuchar a los clientes]

####Parámetros de inicio del docker engine

* Como configurar los parámetros de inicio dependerá de: 
 - Si nos encontramos ejecutando el demonio de manera interactiva o como un servicio(docker daemon)
 - Si se encuentra corriendo como servicio
* Si ejecutamos el demonio de docker de manera interactiva, especificar los parámetros de inicio es tan sencillo como: ```sudo docker daemon [options] &
* En el caso de utilizar **upstart** localizar el archivo en /etc/default/docker y modificar DOCKER_OPTS (sudo service restart es necesario)
* En **systemd** localizar el archivo docker.service ( y modificar el archivo referenciado por la propiedad **EnviromentDile**

SISTEMA CON UPSTART

cat /etc/default/docker | docker upstart configuration file
sudo tail /var/log/upstart/docker.log | logs de docker
vim -u NONE /etc/default/docker | abrimos archivo de configuración con vim
modificamos la variable que envía los parámetros de configuración al demonio
\#DOCKER_OPTS="" lo cambiamos por | DOCKER_OPTS="--log-level=debug"
reiniciamos el servicio | sudo service docker restart
ps -fea \| grep docker | hacemos un grep de ps para mostrar el proceso docker
si miramos el log | tail -f /var/logs/upstart/docker.log &
vemos como nos aparece los mensajes de debug

SISTEMA CON SYSTEMD

sudo service docker status | miramos la info del servicio
vi /lib/systemd/system/docker.service | archivo de configuración en systemd
agregamos en [service] la siguiente línea | EnviromentFile=- /etc/default/docker
en la línea ExecStart=/usr/bin/docker daemon -H fd:// lo cambiamos  por ....
ExecStart=/usr/bin/docker daemon OPTIONS -H fd://
creamos un archivo de configuración en la ruta /etc/default/docker
vi /etc/default/docker y agregamos la siguiente línea:
OPTIONS=´--log-level=debug´
journalctl -u docker | para ver los logs 
demaons el archivo vi /etc/default/docker vacío
OPTIONS=´´
reiniciamos el servicio docker | service docker restart
nos saldrá un aviso de que tenemos que ejecutar systemctl daemon-reload

DE MANERA MANUAL

para ejecutar docker y pasarle variables de entorno
docker daemon --log-level=debug | lanzamos demonio de docker con la variable modo debug.

###Conexiones REMOTAS

- cuando el demonio está configurado como unix sock significa que solo acepta conexiones desde la misma máquina.
- si queremos conectarnos de manera remota hay que cambiar el archivo de configuración y añadir la variable: **DOCKER_HOST="tcp://localhost:2375"**

podemos añadirla con export DOCKER_HOST ..........

De esta manera para conectarnos ya solo hay que usar los comandos como si estuvieramos en local 

se puede comprobar las variables de entorno haciendo un:
```
env | grep -i docker
```
y debería de devolvernos algo parecido a esto:

```
DOCKER_HOST=tcp://localhost:2375
```
para quitar la variable podemos usar:

```
unset DOCKER_HOST
```

###Dockerfiles

- Provee una forma más efectiva de generar imágenes en vez de utilizar docker commit.
- Se integra de manera automática en el flujo de desarrollo y de integración continua.
- Las intrucciones más utilizadas son **FROM** y **RUN**
- El docker file es un archivo de texto con instrucciones

nano dockerfile | creamos un archivo dockerfile
este archivo es único si queremos crear otra imagen distinta tendremos que crear otro directorio e incluir en él otro archivo que se llame dockerfile si no tiene ese mismo nombre docker buil no lo encontrará.
para guardar en nano CTRL+O para salir CTRL+X
FROM | cual va a ser la imagen base
RUN | ejecutamos los comandos en la imagen anterior

ejemplo

```
FROM ubuntu
RUN apt-get update
//tambien podemos usar apt-get update && apt-get install -y curl
// lo que hace comando 1 && comando 2 es ejecutar comando 1 y si se ejecuta bien se ejecuta el segundo comando.
RUN apt-get install -y curl
RUN apt-get install -y vim
```
cat dockerfile | para ver el contenido de dockerfile
docker build /ruta/dockerfile | para ejecutar el docker file hay que decirle donde está
docker build . | Si lo ejecuto en la misma carpeta del dockerfile

si ejecutamos el docker build creará la imagen cada paso irá separado por: 
```Step 3/3 : RUN apt-get install -y vim``` por ejemplo y cuando finaliza nos dirá el ID del contenedor creado ```Successfully built 9ddf899c3d5d```

si hacemos un ```docker images``` vemos que nos ha creado una imagen pero no le a asignado 
ninguna ningún nombre para ello podemos volver a hacer ```docker build -t ubuntu\_curl\_vim``` y nos creará una imagen con el mismo ID que la que acabamos de hacer, esto pasa porque usa el BUILD CACHE.

```
user@user-VirtualBox:~/pruebas$ docker build -t ubuntu_curl_vim .
Sending build context to Docker daemon  2.048kB
Step 1/3 : FROM ubuntu
 ---> ebcd9d4fca80
Step 2/3 : RUN apt-get update && apt-get install -y curl
 ---> Using cache
 ---> 533143d57a52
Step 3/3 : RUN apt-get install -y vim
 ---> Using cache
 ---> 9ddf899c3d5d
Successfully built 9ddf899c3d5d
Successfully tagged ubuntu_curl_vim:latest
```

###Build Cache

- Docker guarda un snapshot de cada imagen después de cada instrucción de build.
- Antes de ejecutar un paso, docker chequea si la instrucción se encuentra en la cache teniendo en cuenta el orden original.
- Si la condición anterior se cumple, docker utiliza la cache en vez de ejecutar el paso nuevamente.
- Docker utiliza la comparación de strings exactos para chequear con la cache ( si cambiamos simplemente el orden del build es suficiente para ser inválido)
- Para deshabilitar la cache manualmente se puede utilizar la bandera --no-cache. se usaría de la siguiente manera ```docker build --no-cache -t imagen /ruta/```

###Docker History

para ver todas las capas de las que se compone una imagen se puede usar ```docker history [imagen]``` 

ejemplo de salida por pantalla del comando history de la imagen creada de ubuntu_curl_vim

```
user@user-VirtualBox:~/pruebas$ docker history ubuntu_curl_vim
IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
9ddf899c3d5d        8 hours ago         /bin/sh -c apt-get install -y vim               52.5MB              
533143d57a52        8 hours ago         /bin/sh -c apt-get update && apt-get insta...   54.7MB              
ebcd9d4fca80        3 days ago          /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B                  
<missing>           3 days ago          /bin/sh -c mkdir -p /run/systemd && echo '...   7B                  
<missing>           3 days ago          /bin/sh -c sed -i 's/^#\s\(deb.universe\...   2.76kB     
```

Esta imagen a su vez puede estar formada por mas imágenes entonces podemos ejecutar un contenedor en una de las capas anteriores por ejemplo si queremos ver los comandos anteriores de ejecutar la instalación de vim podríamos ejecutar la imagen 533 y tendríamos la imagen antes de añadir ese comando esto viene muy bien para buscar errores de funcionamiento , se parece a un control de versiones. Para ejecutar esa imagen podríamos usar el siguiente comando:

```bash
docker run -ti 533 bash
```
###La instrucción CMD
- CMD define el comando por defecto a ejecutar cuando se crea el contenedor.
- Se puede usar tanto en formato Shell como Exec.
- Sólo se puede especificar una vez en el dockerfile
- Puede ser anulado manualmente vía el docker CLI

Un ejemplo de uso del comando CMD (contenido de un archivo dockerfile)

```
FROM ubuntu
RUN apt-get update
RUN apt-get install -y iputils-ping
CMD ping -c 20 www.google.es
```

- Coge una imagen de ubuntu
- Actualiza los repositorios
- Instala iputils-ping con parámetro -y (silencionso) para poder tener app ping
- Ejecuta el Ping hacia google una vez que corramos la imagen generada.

si queremos evitar que una imagen ejecute directamente el comando en vez de hacer un:
- ( docker run imagen ) podemos hacer un ( docker run -ti imagen bash) de esta forma sobreescribirmos la instrucción CMD y obtenemos una shell para hacer troubleshooting.

Lo visto hasta ahora es la forma de ejecutar un comando en el formato Shell pero tambien se puede ejecutar de otra forma, las mismas instrucciones de arriba se podrían reescribir de la siguiente manera:

 ```
FROM ubuntu
RUN apt-get update
RUN apt-get install -y iputils-ping
CMD ["ping","-c","20","www.google.es"]
```
el resultado de ejecutar una imagen de esta manera debería de ser el mismo.

### La instrucción ENTRYPOINT

- Define el punto de entrada con el comando que el container correrá cuando se crea.
- Los argumentos de runtime son enviados como parámetros a la instrucción ENTRYPOINT
- Tambien posee forma de EXEC y shell
- El contenedor funciona a modo de ejecutable

- Lo que permite esta instrucción es definir un comando para poder pasarle instrucciones a través del docker run.

Dado un dockerfile como este:

 ```
FROM ubuntu
ENTRYPOINT ["ping"]
```
si ejecuto este dockerfile:

```docker run ubuntu_ping```

Se ejecutaría el comando ping y ya está pero al tener la instrucción ENTRYPOINT puedo pasarle directamte comandos en el run:

```Docker run ubuntu_ping -c 5 www.google.com```

Podemos usar la instrucción CMD y ENTRYPOINT a la vez de la siguiente forma:

```
FROM ubuntu
CMD ["-c","20","www.google.com"]
ENTRYPOINT ["ping"]
```
De esta manera cuando ejecutemos esta imagen se ejecutará  la instrucción ENTRYPOINT y después se le pasará la instrucción CMD.

Lo bueno de hacer la imagen de esta forma es que podemos definir varios comandos para la misma imagen si por defecto lo dejamos así ejecutaría un ping de 20 segundos a google pero si le podríamos definir otro destino por ejemplo

```docker run ubuntu_ping -c 1 www.google.com```

Para poder hacer funcionar los comandos CMD y ENTRYPOINT juntos los dos necesitan estar en formato exec ["**"]

####Que se usa:

- El 90% se usa el comando CMD
- Si necesitamos pasar argumentos constantemente a los comandos de la imagen entonces deberíamos usar ENTRYPOINT

###Copiando archivos

- Usamos la instrucción COPY <SRC> ... <SRC><DST>

creamos un archivo de ejemplo junto a nuestra carpeta de dockerfile
```echo "Hola que tal estamos" > test.txt```
Creamos nuestro Dockerfile con la siguiente estructura

```
FROM ubuntu
COPY test.txt /tmp/prueba
CMD cat /tmp/prueba
```
### Probando una aplicación de python

Dada una aplicación python con un archivo 
- app.py
- requirements.txt

lo que hace esta aplicación es crear una aplicación web y va sumando con una bbdd en memoria las veces que ejecutamos ese archivo. y nos lo muestra con un hello world y X número.

Con estos dos archivos vamos a construir una imagen de docker para poder ejecutarla
el contenido de los dos archivos es el siguiente:

la app **app.py**

```phyton
from flask import Flask
from redis import Redis
import os
import socket
app = Flask(__name__)
redis = Redis(host='redis', port=6379, socket_connect_timeout=5)
host = socket.gethostname()

@app.route('/')
def hello():
    redis.incr('hits')
    return '\nHello World!\nI have been seen %s times.\nMy Host name is %s\n\n' % (redis.get('hits') ,host)

if __name__ == "__main__":
    app.run(host="0.0.0.0", debug=True)
```

Las dependencias que necesita la app **requirements.txt**

```txt
flask
redis
```
creamos un dockerfile para poder crear nuestra imagen el contenido será el siguiente:

```
FROM python:2.7

COPY app.py requirements.txt /app/
RUN pip install -r/app/requirements.txt
CMD python /app/app.py
EXPOSE 5000

Se puede hacer lo mismo pero sin especificar paths con la isntruccón WORKDIR, lo que hace la instrucción WORKDIR es especificar un directorio de trabajo.

FROM python:2.7

WORKDIR /app
COPY app.py requirements.txt ./
RUN pip install -r requirements.txt
CMD python app.py
EXPOSE 5000

de esta manera queda más limpio

```
Explicamos un poco lo que hace este dockerfile

FROM python:2.7 --> Descargamos la versión oficial de python, la imagen docker de python
COPY app.py requirements.txt /app/ --> Copiamos los archivos en una carpeta que se llamará /app/
RUN pip install -r/app/requirements.txt --> Instala las dependencias del archivo requierements.txt
CMD python /app/app.py --> ejecuta la aplicación de python
EXPOSE 5000 --> Le decimos que se esta imagen va a escuchar en este puerto


creamos la imagen

```
docker build -t app .
```

podemos ejecutar la app como demonio con la bandera -d y -P para que nos haga un escaneo de puertos:

```
docker run -d -P app
```
si hacemos un docker ps veríamos lo siguiente:

```
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                     NAMES
d7e937065bd9        app                 "/bin/sh -c 'pytho..."   4 seconds ago       Up 3 seconds        0.0.0.0:32769->5000/tcp   gracious_bassi
```
nos dice que la dirección localhost:32769 está mapeada al puerto 5000

Si vamos al navegador e ingresamos en 
```
http://localhost:32769/
```
podemos ver el servidor aunque tiene errores. (((( no comprendo todavía para que especificamos el puerto 5000 si no lo podemos usar )))))))


para buscar las imagenes disponibles en docker se puede usar el siguiente comando:

```
docker search python
```

### Instrucción ADD

- Posee el mismo formato que la instrucción COPY y ambos operan de manera similiar
- tiene la habilidad de descomprimir archivos automáticamente
- Puede obtener archivos de una URL ( no descomprime en este caso )
- Ambas instrucciones realizan un checksum de los archivos añadidos para calcular la cache.

se pueden descargar archivos .tar (los archivos .tar no son archivos comprimidos solo es la manera de mantenerlos juntos)[Archivos TAR](https://es.wikipedia.org/wiki/Tar)

para probarlo vamos a crear una imagen en docker con las siguientes instrucciones

dockerfile

```
FROM ubuntu
RUN apt-get update
RUN apt-get install -y jp2a
ADD http://cdn.meme.am/instances/66627195.jpg /tmp/img.jpg
ENV TERM xterm-256color
CMD jp2a --size=60x40 /tmp/img.jpg
```
la ejecutamos ```docker run add .```

la salida de pantalla es la siguiente:

```
'...'....,:ll;::,,;,;;;,'''',,,,,'.''',''',,,,;::;'..''''';;
''.''....,,,'',;,'''''',:loxdddkx:'.....'....':ol,'..'''.';;
''.''....''OO;.'.xOo.OO'cOo oO;c:kK0d..OO',OO:'OO,'.''''.';,
''.'''...',MMo.'.XM0oMX.dMM'OMc.WMxKM0 WMcoMMdcMM,,.''''.,;,
''..''..'',MMo.'.XMXNMl;dMM00Mc,MM:OMX KMdOMMOdMW...''''',,'
''''''.'',,MMo'c,XMMMM;ldMMMWMc,MM:OMN kMkKNWKOMK...''''',,'
''''''''',,MMo;d,XMXWMo,dM0WMMc,MM:OMN.oMXWO0NXMk..''''',:;,
,'''',,'';,MMo:o,XM0kMN.dMxxMMc,MMcOMK.:MMMdoMMMo..''''',:;,
;;;:::;'',,MMo;l'XM0;MM:dMx.WMc.xWWMN:c;MMM:;MMM:..''''',,''
::cccc,.',.,,':c:cl:,clc:c:,::;l::odlod:::c::c;,...''',,''''
cllll:'..,,',,;coddloddollcclloooxO0K0kooc:cloc'...''''''..'
oodol,...',''';lddoooolclo::oddkxkkO0KK0xc:cclc'...'''''....
dddl:'.'.''..':oddooooodxOO00O00OOOkk0KXKOkxdol'..''''......
ddol,'''.'''.,codddxxkO000KXXKKK0OO0OkxOOkOOOkd;..''''......
dolc,..''....,lodxkO00000KKXXXXXKOOkl;:ldclk00Od,.',''......
dol;'.......';ldxkOOOO0000KKKXXXKxd;.',cc';d0OOOo,',''......
dlc,........';oddxkkkOOOOO000KKK0ollcodolclxOOkkx:,,'.......
lc:'......'',;looodxxxxkkkOO00KKKkxOO0Okkxxk0Okxdc;,'.......
lc:'........',:ccloddddddxkkO00K0000000OOOOOOOkddc,,'.......
lc:'...,cc;,'';::cloddddddxkkOOOOkkOxdooooodxkxddc,,'.......
cc:,..';,;c:;,,;:clooddooodxxkxxxxxol::;;;:codxdoc,,'.......
cc:,..';;:::::;:::cllooooodxxxxddoc:,.'',,';coddoc,,,.......
ccc;..'cdd;;olcc::cclloooodxxxxdl:::clooooolloddoc,;;.......
clc;'.'dOd;:locccccclloooodxxxxxxxxxxxxxxxxxddxxol;,;.......
llc:,..lOddxxoccccccllooooddxxxkkkkxddoooooodxxxol;,;.......
lolc;..,lc:ldxl:cccllooooooddxxxxxkkkkkkxxxkkxxxol;,;.......
oolc:'..';clol;::::cclloooooodddxxxkO0KK000OOkxdoc;,;'......
oool:'......''',:::::ccllooooddxxxkOO000K00OOkxdl::;,,......
ooooc,.......,,;;;;;;:::clllooddxxxxxkOOOOOkkxddl::;,,......
loddl;........,::;,'',;;;;;;:clccclccccllllllccc::::;;......
clodoc'...lKK0Od,,xKX0l''dKXKo':KK.OK;cKKKo'KK00x,:;;;'.....
cloodl;...dMWlMMcoMNcMM,oMX'MM:lMMoMN.dMNc:;MMlWMc;;,;......
clddol:'..dMW,MM:dMN,MM;dMK.KK:lMMNMo,dMNc;:MMdWM:,,;,......
:coodoc;'.dMW,MM:dMN,MM;dMK....lMMMMl,dMWKl;MMKMK',;,.......
::loddoc;'dMW,MM:dMN,MM;dMK.WWclMM0MK.dMX.::MM;NMc,'.......'
,;;codddl,dMWkMM:cMWxMW;cMNoMW,lMMcMM;dMWko,MM;NMc.........'
,,;;:codo::xdddc.'cxkxclclxkx;,;xx.dx::xxxo'xx,dx,.........'
,,'',,;ccc::,....,::coddxxdddlc:::::ccllloooodddo'..'.....',
,'.''',;;;;,.....,::clodxxxxxddllcclodoxoxxdkxxxxl:ccc:':l::
'......'.''......,;;;:cllooooollcccllccccllclcclc,..........
```

lo que hace la app es descargar el archivo jpg de la dirección dada y con la app jp2a la convierte en ascii para poder mostrarla por consola.

###Otras Instrucciones
- MAINTAINER: agraga metadatos al dockerfile sobre el dueño de la imagen
- ENV. permite añadir variables de entorno al contenedor
- LABEL: permite agregar etiquetas al contenedor

para poder escribir las instrucciones del dockerfile en líneas diferentes podemos separarlos con una barra invertida por ejemplo

esto

```
RUN apt-get install -y vim && apt-get install curl
``` 
es lo mismo que 

```
RUN apt-get install -y vim && \
apt-get install curl
```
###Compartiendo imagenes de docker
- Para compartir imáenes tenemos varias opciones
	- Utilizar docker hub
	- Utilizar nuestro propio servidor de registro interno
	- Los comandos ```docker export```y ```docker import```
- las imágenes en docker hub pueden ser públicas o privadas.

Para subir una imagen al repositorio de docker hay que registrarse previamente:
[HUB de docker](www.hub.docker.com)
Para poder subir correctamente una imagen al repositorio es necesario poner un tag a la imagen:

```
docker tag add UserDocker/neodocker
```
De esta forma agregamos a la imagen add un tag y le especificamos el usuario y el nombre de la imagen.

si hacemos un ```docker images```
vemos que tenemos dos imagenes con el mismo ID 

```
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
UserDocker/neodocker   latest              c9c81d91a328        About an hour ago   173MB
add                     latest              c9c81d91a328        About an hour ago   173MB
```
antes de subir la imagen al hub de docker hay que loguearse:

```
user@user-VirtualBox:~/docker_add$ docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: UserDocker
Password: 
Login Succeeded
```
despues hacemos un ```docker push UserDocker/neodocker```
y nuestra imagen empezará a subir.

entonces ahora que es pública si desde cualquier equipo que no tuvieramos esta imagen ejecutamos:
```docker run UserDocker/neodocker```la imagen se descargaría y se ejecutaría automáticamente.

###borrando imagenes

```docker rmi test``` borra las imagenes de docker
podemos crear alias de forma que ejecutando esos alias podríamos ahorrarnos el trabajo de borrar uno a uno:

Ejemplos: de configuración alias

```
alias dockerkill='docker kill $(docker ps -q)'
alias dockerremove='docker rm $(docker ps -qa)'
```
para editar los alias en linux hay que ir al archivo bashrc del usuario y ejecutar en la carpeta raiz lo siguiente:

```$ nano .bashrc```
dentro de ese archivo al final del todo escribimos nuestros alias.
para que funcione hay que reiniciar la terminal.

ejemplo de alias sencillo:
```alias todo='ls -la'```

###Volumenes

- Un directorio designado en el contenedor en el cual se persiste información independientemente del ciclo de vida del contenedor
- Los cambios en un volúmen son excluidos cuando se guarda una imagen
- La información se persiste aunque se elimine el contenedor
- Pueden estar mapeados a un directorio del host
- Pueden compartirse entre contenedores
- Las instrucciones 'RUN' del dockerfile no modifican la información de los volúmenes.

Para crear un volumen de nombre prueba:

```
user@user-VirtualBox:~$ docker volume create --name prueba
```
Para asignar un volumen a una imagen de docker:

```
user@user-VirtualBox:~$ docker run -ti -v prueba:/prueba ubuntu bash
```
lo guardado en este volumen tambien estará disponible en otra imagen si añado este volumen.
este volumen realmente está en la máquin host guardado.

para ver donde podemos usar el siguiente comando:

```
user@user-VirtualBox:~$ docker volume inspect prueba
[
    {
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/prueba/_data",
        "Name": "prueba",
        "Options": {},
        "Scope": "local"
    }
]
```

```docker volume --help``` salen todos los comandos de volume.

Volúmenes en el Dockerfile
 
 - La instrucción VOLUME crea un punto de montaje de volúmenes
 - Se pueden especificar los argumentos como JSON o String
 - Con este método no se pueden mapear archivos del host (debido a que el dockerfile puede ejecutarse en cualquier equipo)
 - Los volúmenes son inicializados cuando el contenedor se inicia con la información existente en el directorio.
 - Los volúmenes se crean con nombre aleatorio, tambien se conocen como volúmenes anónimos

tambien se pueden crear volumenes anónimos directamente cuando ejecutamos el contenedor:
por ejemplo de la siguiente manera:

```
docker run -ti -v /home/user/test:/prueba ubuntu bash
```
test es la carpeta local que quiero compartir con el volumen 
prueba es el nombre de la carpeta cuando se ejecuta la imagen

para poder montar directorios en OSX Y EN WINDOWS solo permite montar los directorios que estén sobre la carpeta usuarios del sistema:

docker run -v /Users/<path>:/<container path> --> En MacOSX
docker run -v /c/Users/<path>;/<container path> --> En Windows

###Aspectos de seguridad en DOCKER

- Docker permite ejecutar aplicaciones de manera segura debido a los controles y privilegios que utiliza.
- Los namespaces proveen una vista aislada del sistema. Cada contenedor utiliza su propio entorno de:
	- IPC, Stack de red, root file system etc...
- Los procesos que se ejecutan en un contenedor no pueden ver o afectar a procesos en otros contenedores.
- Los Control Groups (Cgroups) aislan los recursos del sistema utilizador por cada contenedor ( memoria /Cpu/red/io)
	- Aseguran que un contenedor no pueda hacer fallar el host por hacer mal uso de sus recursos.
- El demonio de docker debe correr como usuario root
- Es importante controlar aquellos usuarios que pueden utilizar el demonio de docker
	- Revisar quién tiene acceso al grupo docker
- Si el demonio de  docker escucha en una conexión TCP, securizarla utilizando TLS
- Se pueden utilizar aspectos de seguridad avanzados
	- Apparmor
	- Selinux
	- GRsec

####Configuración de TLS

- Es una evolución de SSL
- El protocolo que utiliza la web segura (https)
- Utiliza criptografía de clave pública y privada
- Las claves son cifradas con con certificados que son mantenidos y emitidos por una entidad confiable.
- docker provee mecanismos para autenticar el cliente y el demonio entre ellos.
- Las claves pueden ser distribuidas a clientes autorizados.
		Requisitos
			- tener instalado OpenSSL 1.0.1 o superior
			- Crear una carpeta donde guardar las claves protegidas(chmod 700)

Pasos a seguir

1. Crear una autoridad de certificación (CA)
	a. Es necesario una clave privada y un certificado
2. Configurar la clave privada del servidor
3. Crear un requerimiento de firma (CSR) de certificado para el servidor
4. Firmar la clave del servidor con el CSR mediante nuestro CA
5. Crear una clave privada y un CSR para el cliente
6. Firmar la clave del cliente con el CSR mediante nuestro CA
7. Iniciar el demonio de docker con la opción de TLS y especificar la ubicación de la clave privada del CA, el certificado del servidor y la clave privada del servidor
8. Configurar el cliente de docker para que utilice la clave privada del cliente y la clave privada del CA

Creamos una carpeta nueva ```mkdir docker-ca```

1. Inicio: Creamos una clave privada de la entidad autorizante

```
openssl genrsa -aes256 -out ca-key.pem 2048
```
openssl --> programa para generar las claves
genrsa --> le decimos que vamos a generar una clave
-aes256 --> tipo de cifrado
-out ca-key.pem --> salida del archivo a generar
2048 --> Longitud de la clave a generar

```
user@user-VirtualBox:~/docker-ca$ openssl genrsa -aes256 -out ca-key.pem 2048
Generating RSA private key, 2048 bit long modulus
.............+++
.........................................................................................................+++
e is 65537 (0x10001)
Enter pass phrase for ca-key.pem:
Verifying - Enter pass phrase for ca-key.pem:
user@user-VirtualBox:~/docker-ca$ ls
ca-key.pem
user@user-VirtualBox:~/docker-ca$ ls
ca-key.pem
```

Cuando generemos la clave nos pedirá que le pongamos una contraseña: 

La contraseña usada para la práctica es ```capass```

1. Fin: Crear clave privada.

1a. Inicio crear un certificado para usar el servidor y cliente

```
openssl req -new -x509 -days 365 -key ca-key.pem -sha256 -out ca.pem
```
openssl --> programa a utilizar para generar el certificado
req -new --> crear un nuevo certificado
-x509 --> tipo de certificado
-days 365 --> validez del certificado
-key ca-key.pem --> clave privada de la autoridad certificadora
-sha256 --> tipo encriptación de hash a utilizar
-out ca.pem --> salida del certificado

Al ejecutar el programa programa nos pedirá la contraseña de la clave privad ca-key.pem como hemos dicho antes será ```capass```y después nos pedirá una serie de datos que no son necesarios rellenar para que funcione.

```bash
user@user-VirtualBox:~/docker-ca$ openssl req -new -x509 -days 365 -key ca-key.pem -sha256 -out ca.pem
Enter pass phrase for ca-key.pem:
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:
State or Province Name (full name) [Some-State]:
Locality Name (eg, city) []:
Organization Name (eg, company) [Internet Widgits Pty Ltd]:
Organizational Unit Name (eg, section) []:
Common Name (e.g. server FQDN or YOUR name) []:
Email Address []:

```
1a. Fin  crear certificado

2. Configurar la clave privada en el servidor

```
openssl genrsa -out server-key.pem 2048
```
En este caso no le ponemos password pero se le podría poner.

```
user@user-VirtualBox:~/docker-ca$ openssl genrsa -out server-key.pem 2048
Generating RSA private key, 2048 bit long modulus
.....................................+++
............+++
e is 65537 (0x10001)
```
2. fin configurar clave privada servidor

Para que la autoridad autorizante pueda autorizar al servidor a validar su identidad es necesario crear un requerimiento de firma de certificado (CSR) Certificate sign request.
El servidor envía un requerimiento a la autoridad autorizante , la autoridad autorizante firma ese requerimiento y se lo devuelve al servidor, y entonces el servidor puede utilizarlo.

3. Crear un requerimiento de firma (CSR) de certificado para el servidor.
```
openssl req -subj "/CN=localhost" -new -key server-key.pem -out server.csr
```
openssl --> programa a utilizar
req -subj "/CN=localhost" -new -key--> aquí especificamos el hostname donde está escuchando el demonio de docker en nuestro caso al ser la misma máquina es localhost.
server-key.pem --> especificamos la clave privada del servidor
-out server.csr --> salida del CSR

```bash
user@user-VirtualBox:~/docker-ca$ openssl req -subj "/CN=localhost" -new -key server-key.pem -out server.csr
user@user-VirtualBox:~/docker-ca$ ls
ca-key.pem  ca-pem  server.csr  server-key.pem
```
3. Fin crear CSR


4. Firmar la clave del servidor con el CSR mediante nuestro CA

Para hacer esta operación es necesario hacer dos pasos:

ahi que crear un archivo para configurar las ips de las que el servidor puede hacer requerimientos , como estamos trabajando en local ponemos la ip de localhost pero si tuvieramos nuestro servidor en un cloud le podríamos la ip publica  del cloud correspondiente.

creamos el fichero
```
echo "subjectAltName = IP:127.0.0.1 > extfile.cnf
```
firmamos la clave del servidor a través de nuestro CA
```
openssl x509 -req -days 365 -in server.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out server-cert.pem -extfile extfile.cnf
```
openssl --> programa a utilizar
x509 -req --> 
-days 365 --> dias validez
-in server.csr --> el CSR generado
-CA ca.pem --> certificado del servidor
-CAkey ca-key.pem --> clave privada 
-CAcreateserial --> creamos las credenciales para el servidor
-out server-cert-pem --> ichero de salida certificado para el server 
-extfile extfile.cnf --> le mandamos el exfile
```

user@user-VirtualBox:~/docker-ca$ openssl x509 -req -days 365 -in server.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out server-cert.pem -extfile extfile.cnf
Signature ok
subject=/CN=localhost
Getting CA Private Key
Enter pass phrase for ca-key.pem:
```

5. Crear una clave privada y un CSR para el cliente 

Hay que hacer lo mismo que hemos hecho para el servidor pero para el cliente

Generamos la clave del cliente
```
openssl genrsa -out client-key.pem 2048
```
No le hemos añadido contraseña pero se podría haber hecho.
```
user@user-VirtualBox:~/docker-ca$ openssl genrsa -out client-key.pem 2048
Generating RSA private key, 2048 bit long modulus
.........................+++
..........................................................+++
e is 65537 (0x10001)
```
Generamos el CSR para el cliente
```
openssl req -subj '/CN=client' -new -key client-key.pem -out client.csr
```
en este caso la bandera subj puede ser cualquier cosa 

```
user@user-VirtualBox:~/docker-ca$ openssl req -subj '/CN=cliente' -new -key client-key.pem -out client.csr
```

6. Firmar la clave del cliente con nuestro CSR mediante nuestro CA

Como habíamos hecho con el servidor hay que crear un archivo para especificar de que es un cliente autorizado en vez de usar la ip como al servidor.

```
user@user-VirtualBox:~/docker-ca$ echo "extendedKeyUsage = clientAuth" > extfile-client.cnf
```
y despues generamos el certificado.

```
user@user-VirtualBox:~/docker-ca$ openssl x509 -req -days 365 -in client.csr -CA ca.pem -CAkey ca-key.pem -CAcreateserial -out client-cert.pem -extfile extfile-client.cnf
Signature ok
subject=/CN=cliente
Getting CA Private Key
Enter pass phrase for ca-key.pem:
```
####Lo recomendable ahora sería asegurar nuestras claves cambiando los permisos de escritura y moviendo las claves a otro directorio asi como dar los permisos correctos a las carpetas. pero de momento lo vamos a dejar así- mas info en la slide nº30 del workshop de seguridad.

####Usando Docker con TLS

Paramos el demonio de docker

```bash
user@user-VirtualBox:~/docker-ca$ sudo service docker stop
```
revisamos que el demonio de docker está parado

```
user@user-VirtualBox:~/docker-ca$ ps -fea | grep docker
user      4577  4428  0 17:08 pts/2    00:00:00 grep --color=auto docker
```
nada solo vemos el Grep que acabamos de hacer

Ejecutamos el demonio de Docker con las opciones para que use los certificados TLS la ejecutamos en un socket TCP y en el puerto 2375 y especificamos todos los certificados necesarios.

```
sudo docker daemon -H tcp://0.0.0.0:2375 --tlsverify --tlscacert=./ca.pem --tlscert=./server-cert.pem --tlskey=./server-key.pem &
```
si agregamos el simbolo **&** el demonio se inicializa en segundo plano de lo contrario se queda asignado a la terminal desde donde le ejecutamos el demonio. Puede que si lo ejecutamos en segundo plano nos pida algún dato para poder ejecutar el demonio como por ejemplo la pass de sudo. por lo que hay que usar **&** con precaución porque de lo contrario no se ejecutará el demonio.

```
user@user-VirtualBox:~/docker-ca$ sudo docker daemon -H tcp://0.0.0.0:2375 --tlsverify --tlscacert=./ca.pem --tlscert=./server-cert.pem --tlskey=./server-key.pem
[1] 4611
user@user-VirtualBox:~/docker-ca$ Command "daemon" is deprecated, and will be removed in Docker 17.12. Please run `dockerd` directly.
INFO[0000] libcontainerd: new containerd process, pid: 4619 
WARN[0000] containerd: low RLIMIT_NOFILE changing to max  current=1024 max=65536
WARN[0001] failed to rename /var/lib/docker/tmp for background deletion: %!s(<nil>). Deleting synchronously 
INFO[0001] [graphdriver] using prior storage driver: aufs 
INFO[0001] Graph migration to content-addressability took 0.00 seconds 
WARN[0001] Your kernel does not support swap memory limit 
WARN[0001] Your kernel does not support cgroup rt period 
WARN[0001] Your kernel does not support cgroup rt runtime 
INFO[0001] Loading containers: start.                   
INFO[0001] Default bridge (docker0) is assigned with an IP address 172.17.0.0/16. Daemon option --bip can be used to set a preferred IP address 
INFO[0001] Loading containers: done.                    
INFO[0001] Daemon has completed initialization          
INFO[0001] Docker daemon                                 commit=89658be graphdriver=aufs version=17.05.0-ce
INFO[0001] API listen on [::]:2375 
```
el demonio ya está iniciado 

si intentamos hacer un docker ps no podremos ya que en la ejecución del demonio hemos especificado una dirección y un puerto pero no en las variables de entorno para ello hay que añadir a las variables de entorno el HOST:

**las variables de entorno se pueden consultar con ```$env``` si queremos filtrar los resultados podemos hacer un grep con los datos que buscamos ```$env | grep DOCKER```**

```
user@user-VirtualBox:~/docker-ca$ export DOCKER_HOST="tcp://localhost:2375"
```
una vez introducida la variable de entorno ya tendremos todo correcto, intentamos ejecutar un comando de docker: 

```
user@user-VirtualBox:~/docker-ca$ docker ps
2017-05-31 17:29:42.761235 I | http: TLS handshake error from 127.0.0.1:48178: tls: first record does not look like a TLS handshake
2017-05-31 17:29:42.762119 I | http: TLS handshake error from 127.0.0.1:48180: tls: first record does not look like a TLS handshake
Get http://localhost:2375/v1.29/containers/json: malformed HTTP response "\x15\x03\x01\x00\x02\x02".
* Are you trying to connect to a TLS-enabled daemon without TLS?
```

Nos saldrá este error , esto es porque hemos securizado el servidor pero no hemos hecho lo mismo con el cliente.

```
user@user-VirtualBox:~/docker-ca$ docker --tlsverify --tlscacert=./ca.pem --tlscert=./client-cert.pem --tlskey=./client-key.pem ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
user@user-VirtualBox:~/docker-ca$ 
```
como vemos ahora si ejecutamos un comando al final de todos los tls vemos que podemos usar docker para evitar tener que escribir todas las claves cada vez que ejecutamos un comando podemos crear una carpeta ```.docker```en el home de nuestro usuario, pero para esto necesitamos renombrar los ficheros xxxxxx para que docker los coja automáticamente.

seguramente la carpeta .docker ya está creada:
```
user@user-VirtualBox:~$ cd .docker
user@user-VirtualBox:~/.docker$ ls
config.json
```
copiamos los archivos a la carpeta docker

```
user@user-VirtualBox:~/docker-ca$ cp client-cert.pem client-key.pem ca.pem /home/user/.docker
```

renombramos los archivos copiados:

```
user@user-VirtualBox:~/.docker$ mv client-cert.pem cert.pem
user@user-VirtualBox:~/.docker$ mv client-key.pem key.pem
```

Una vez realizados estos pasos para poder usar el comando docker en el cliente solo tendremos que especificar ```docker --tlsverify COMANDO```

```
user@user-VirtualBox:~/.docker$ docker --tlsverify ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
user@user-VirtualBox:~/.docker$ 
```


para evitar escribir ```tls-verify```cada vez que ejecutamos un comando podemos utilizar la variable de entorno siguiente:

DOCKER_TLS_VERIFY

```
user@user-VirtualBox:~/.docker$ export DOCKER_TLS_VERIFY=1
user@user-VirtualBox:~/.docker$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
user@user-VirtualBox:~/.docker$ 
```
una vez añadida esta variable de entorno ya podemos usar Docker de manera normal sin tener que especificar los comandos TLS ni las direcciones IP. ( MIRAR TEMA DE VARIABLES DE ENTORNO)

```
user@user-VirtualBox:~/docker-ca$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```
##APUNTES Funcionamiento a tener en cuenta
- las variables de entorno no se guardan automáticamente al usar el comando EXPORT hay que escribirlas directamente en el archivo /etc/environment con un editor ej:nano con permisos de root

- Hay que añadir al archivo /etc/environment las siguientes líneas: (en este archivo es donde se guardan las variables de entorno del sistema operativo para todos los usuarios)

```
DOCKER_HOST="tcp://localhost:2375"
DOCKER_TLS_VERIFY=1
```
Si hacemos un ```echo $DOCKER_HOST``` y está bien cargada la variable debería devolvernos el valor de la misma:

```
user@user-VirtualBox:~$ echo $DOCKER_HOST
tcp://localhost:2375
```

[VARIABLES DE ENTORNO PERMANENTE](http://www.sysadmit.com/2016/04/linux-variables-de-entorno-permanentes.html)


##REDES

- Cuando docker inivia, crea una interfaz visual ```docker0```en el equipo de host 
- ```docker0```es asignado un rango de ip de la subnet privada definida por la RFC 1918

Con el comando ```ip a ```podemos ver todas las interfaces del equipo entre ellas tenemos que ver la que ponga docker0:

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:69:a6:83 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 83898sec preferred_lft 83898sec
    inet6 fe80::6812:b398:b6e8:86bc/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:56:36:75:18 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:56ff:fe36:7518/64 scope link 
       valid_lft forever preferred_lft forever
```
Cada vez que ejecuto un contenedor docker me crea una interfaz nueva para poder comunicarme con la aplicación.

por ejemplo voy a correr la aplicación app y veremos la salida del comando ```ip a ```

```
user@user-VirtualBox:~/app_prueba$ docker run -d -P app
f77ac3e006aaa2412571539ac7d9d6668d26e8319365ac3472e3f35878e5c96d
user@user-VirtualBox:~/app_prueba$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:69:a6:83 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 83590sec preferred_lft 83590sec
    inet6 fe80::6812:b398:b6e8:86bc/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:56:36:75:18 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:56ff:fe36:7518/64 scope link 
       valid_lft forever preferred_lft forever
7: veth57047aa@if6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether fa:8b:13:6f:1f:20 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet6 fe80::f88b:13ff:fe6f:1f20/64 scope link 
       valid_lft forever preferred_lft forever
```
Como vemos docker nos ha creado una interfaz nueva con el nombre: veth57047aa@if6 si matamos ese contenedor eliminaremos la interfaz:

```
user@user-VirtualBox:~/app_prueba$ docker kill f77ac3e006aaa2412571539ac7d9d6668d26e8319365ac3472e3f35878e5c96d
f77ac3e006aaa2412571539ac7d9d6668d26e8319365ac3472e3f35878e5c96d

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:69:a6:83 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 83442sec preferred_lft 83442sec
    inet6 fe80::6812:b398:b6e8:86bc/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:56:36:75:18 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:56ff:fe36:7518/64 scope link 
       valid_lft forever preferred_lft forever
```
Una vez eliminado el contenedor docker borra la interfaz que estaba utilizando.

Para poder interactuar con las redes se utiliza el comando ```docker network```
los subcomandos principales son:

- docker network create
- docker network connect
- docker network ls
- docker network rm
- docker network disconnect
- docker network inspect

Utilizar la bandera ```--net``` para especificar una red cuando se crea un contenedor
Utilizando la bandera ```--link```se puede acceder a los contenedores por nombre.

Mirando las redes que tenemos:
```
user@user-VirtualBox:~/app_prueba$ docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
cf3d7fedfcec        bridge              bridge              local
1ca096e39c42        host                host                local
ea66358c33e8        none                null                local
```
- la red **bridge** es la interfaz que usa docker para poder conectarse entre los distintos contenedores y el host la famosa ```docker0```
- la red **host** es la interfaz que permite ejecutar un contenedor como si lo hicieramos en la maquina local si hicieramos un ```ip a ```dentro de un contenedor al que le hubieramos ejecutado con la bandera --net=host veríamos las mismas interfaces de red que la máquina física .

Ejemplo red **host**

el comando ```ip a```necesita de tener instalado la aplicación ```iproute2```

Esto hay que instalarlo dentro del contenedor que ejecutemos a menos que ya venga por defecto.
1 - ```apt-get update```
2 - ```apt-get install iproute2```

[iproute2](http://rm-rf.es/como-usar-el-comando-ip-en-linux-ejemplos-vs-ifconfig/)
ejecutamos un contenedor interactivo con la bandera --net=host y ejecutamos ```ip a ```
```
user@user-VirtualBox:~/app_prueba$ docker run -it --net=host ubuntu-red bash
root@user-VirtualBox:/# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:69:a6:83 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 82266sec preferred_lft 82266sec
    inet6 fe80::6812:b398:b6e8:86bc/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:56:36:75:18 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:56ff:fe36:7518/64 scope link 
       valid_lft forever preferred_lft forever
root@user-VirtualBox:/# 
```
Si ejecutamos el mismo contenedor sin la bandera host:

```
user@user-VirtualBox:~/app_prueba$ docker run -it  ubuntu-red bash
root@d0577ab80ce5:/# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
8: eth0@if9: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.17.0.2/16 scope global eth0
       valid_lft forever preferred_lft forever
```

Creando nuestra red:

Para ello utilizamos el comando ```docker network create```
se pueden crear dos tipos de redes con este comando:
 - Bridge : Es igual que la red docker0 
 - Overlay : permite desplegar contenedores en diferentes hosts físicos y que los mismos se comuniquen de manera directa.
Los contenedores se pueden conectar a más de una red mediante el comando ```docker network connect```

Cada vez que creamos un contenedor docker le asigna una ip distinta a cada contenedor para no tener que estar pendiente de que ip es podemos hacer un ping directamente al nombre del contenedor sin saber la ip que está usando por ejemplo: 

Contenedor 1: ```docker run -it --name redis ubuntu bash```
Contenedor 2: ```docker run -it --link redis ubuntu bash```

Desde el contenedor 2 podemos hacer ping de la siguiente manera 
```ping redis``` de esta manera no es necesario saber que ip le ha asignado docker al contenedor.

lo que hace la bandera --link internamente es añadir una entrada en el archivo /etc/hosts con el nombre del contenedor y su correspondiente ip de manera que cuando le decimos que haga un ping a redis busca en este archivo y busca la ip asociada. **(Esto solo lo hace en la red Bridge por defecto)** en las demás redes no lo hace igual y lo que hace es crear un DNS propio para resolver las ips.


Contenedor 1: ```docker run -it --name redis --net=mi_red ubuntu bash```
Contenedor 2: ```docker run -it --link redis --net=mi_red ubuntu bash```

Desde el contenedor 2 podemos hacer ping de la siguiente manera 
```ping redis``` pero esta ip no está en el archivo /etc/hosts , si miramos el archivo /etc/resolv.conf veremos que hay una entrada con la ip del DNS = nameserver 127.0.0.11 ///Docker crea un DNS para resolver los nombres de los contenedores.

Comando para crear una nueva red:
```
user@user-VirtualBox:~$ docker network create mi_red
64c214c4409e7f69f343282ba29196bcf8ed8a18c8b5069d96019122bbe93454
```

Comando para ver las redes existentes:
```
user@user-VirtualBox:~$ docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
cf3d7fedfcec        bridge              bridge              local
1ca096e39c42        host                host                local
64c214c4409e        mi_red              bridge              local
ea66358c33e8        none                null                local
```
Vamos a crear la siguiente estructura de red:

![](file:///Users/kapi_tan/Desktop/apuntes/docker/img/redes.jpg)

De lo que se trata aquí es hacer una aquitectura donde hay 3 container el container 1 está en la red bridge0 , el container 3 está en mi_red y el container 2 puede acceder a las dos redes.

para ello hemos creado previamente la red: mi_red

Creamos un contenedor1 en la red bridge, si no especificamos el flag net se creará en la bridge por defecto.
```
docker run -it --name container1 ubuntu bash
```
Creamos el tercer contenedor3 en la red: mi_red
```
docker run -ti --name container3 --net=mi_red ubuntu bash
```
Estos contenedores no se pueden ver nunca ya que no están en las mismas redes

ahora vamos a crear un contenedor para que pueda estar viendo las dos redes.

Primero creamos el contenedor
```
docker run -ti --name container2 --net=mi_red ubuntu bash
```
con el comando docker network ls podremos ver todas las redes del equipo:

```
user@user-VirtualBox:~$ docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
df4c994b0d1a        bridge              bridge              local
1ca096e39c42        host                host                local
64c214c4409e        mi_red              bridge              local
ea66358c33e8        none                null                local
```
para unir un contenedor específico a otra red podemos usar el comando:
```
docker network connect bridge container2
```
para ver los contenedores que hay en cada red podemos usar el comando
```
docker network inspect bridge/mi_red
```
De esta manera completamos la arquitectura propuesta.

Vamos a ver ahora como podemos levantar varios servicios que dependen cada uno del otro por ejemplo vamos a lanzar un contenedor con redis para usar la app que tenemos hecha en pyton y probarla.

Ejecutamos 2 contenedores uno con redis y otro con nuestra app

```
user@user-VirtualBox:~$ docker run -d --name redis redis
dbbf52843a5da9260f155164563697616f00c8e67c4bc72a071bcda68d43e37a
user@user-VirtualBox:~$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
dbbf52843a5d        redis               "docker-entrypoint..."   3 seconds ago       Up 2 seconds        6379/tcp            redis
user@user-VirtualBox:~$ docker run -d -P --link redis app
8d9ce1b571f86c6d0902070825bbdc2dd005a6f0f13f330c339af957bf7af764
user@user-VirtualBox:~$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                     NAMES
8d9ce1b571f8        app                 "/bin/sh -c 'pytho..."   5 seconds ago       Up 3 seconds        0.0.0.0:32768->5000/tcp   relaxed_mcnulty
dbbf52843a5d        redis               "docker-entrypoint..."   27 seconds ago      Up 26 seconds       6379/tcp                  redis
user@user-VirtualBox:~$
```
lo que hacemos con la bandera -P es lanzar la apllicación en un puerto aleatorio
si nos vamos a probar la aplicación debería de funcionarnos.

http://localhost:32768/

si todo funciona bien deberíamos ver el siguiente mensaje en el explorador:

```
Hello World! I have been seen 1 times. My host name is 707e2aff7687
```
Esto quiere decir que la aplicación ha funcionado correctamente y que la app se ha podido comunicar con el servicio de redis.

Si yo en vez de usar un puerto aleatorio quiero mapear a un puerto específico como por ejemplo el puerto 80 para no tener que especificar el puerto puedo hacerlo con el flag -p seguido del puerto que quiero mapear 80 y despues el puerto del contenedor.

volvemos a lanzar redis

```
user@user-VirtualBox:~/docker-ca$ docker run -d --name redis redis
a92859314713e541d1939f6e80d9261f022ccb816fc782769264f2707b97ed65
```
lanzamos nuestra app con el flag del puerto configurado
```
user@user-VirtualBox:~/docker-ca$ docker run -d -p 80:5000 --link redis app
ff488d6ad26d9c6b253ffde65432e80c4f612664891c5630507dd6b219dba407
```
si hacemos un docker ps veremos el puerto 80 de la maquina mapeado al 5000 del contenedor.
```
user@user-VirtualBox:~/docker-ca$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS              PORTS                  NAMES
ff488d6ad26d        app                 "/bin/sh -c 'pytho..."   31 seconds ago       Up 29 seconds       0.0.0.0:80->5000/tcp   practical_ritchie
a92859314713        redis               "docker-entrypoint..."   About a minute ago   Up About a minute   6379/tcp               redis
user@user-VirtualBox:~/docker-ca$ 
```
si ahora nos vamos al navegador solo tenemos que poner la dirección localhost para ver la app funcionando.

##Docker machine

Docker machine es una herramienta para provisionar hosts de Docker y configurar el Engine en los mismos.

- Crea hosts de docker adicionales en el entorno local
- Crea hosts de docker en clouds provider: AWS, azure, DigitalOcean...
- Machine crea el servidor, instala y configura Docker.

Usando el comando **docker-machine create** y especificar el driver a usar
El driver (donde se quiere hacer la instalación) permite a docker-machine utilizar el entorno deseado 
Sintaxis:

```
docker machine create --driver <driver> <hostname>
```

Docker Machine - AWS
- Para crear un host en AWS es necesario
	- AWS access Key
	- AWS secret Key
	- El VPC ID para la instancia donde correrá docker
- La imagen utilizada por defecto es Ubuntu 15.10 LTS (systemd)

```
docker-machine create
	--driver amazonec2 \
	--amazonec2-access-key <AWS access key> \
	--amazonec2-secret-key <AWS secret key \
	--amazonec2-vpc-id <VPC ID> \
	testhost
```
Creamos una instalación de docker-machine en local, si instalamos la version para windows o macosx ya se dispone de docker-machine, si es para linux hay que descargarla desde el siguiente enlace:

[Docker-Machine releases](https://github.com/docker/machine/releases)

Instalamos virtualbox en la máquina virtual es imprescindible para poder usar docker-machine

```
sudo apt-get install virtualbox-qt
```
instalamos curl 

```
sudo apt-get install curl
```
instalamos docker

```bash
user@user-VirtualBox:~$ sudo curl -sSL https://get.docker.com/ | sh
```

Una vez terminada la instalación nos indica que incluyamos el usuario docker como administrador esto lo hace para poder iniciar el demonio de docker, se hace de la siguiente manera

```bash
user@user-VirtualBox:~$ sudo usermod -aG docker user
```
instalamos docker-machine desde [Docker-Machine releases](https://github.com/docker/machine/releases)

```
curl -L https://github.com/docker/machine/releases/download/v0.12.0-rc2/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine &&
    chmod +x /tmp/docker-machine &&
    sudo cp /tmp/docker-machine /usr/local/bin/docker-machine``
```
```
test@pruebas:~$ docker pull digitalocean/netbox:v1.9.6
```

http://dondocker.com/administrando-hosts-con-docker-machine/
http://blog.crespo.org.ve/2016/01/instalar-gitlab-por-medio-de-docker.html
http://blog.crespo.org.ve/2016/05/uso-de-docker-machine.html
http://blog.crespo.org.ve/2017/04/entorno-de-desarrollo-en-la-nube-cloud9.html
https://www.jmramirez.pro/tutorial/virtualizacion-ligera-con-docker/
https://www.adictosaltrabajo.com/tutoriales/docker-for-dummies/#04




###Borrar todos los contenedores e imágenes de docker. 


Parar todos los contenedores
docker stop $(docker ps -a -q)

Eliminar todos los contenedores
docker rm $(docker ps -a -q)

Eliminar todas las imágenes
docker rmi $(docker images -q)

a) Kill the running containers (docker-compose kill)
b) Remove the stale containers (docker-compose rm -fv)
c) Rebuild the netbox container (docker-compose build)

###Ayuda Docker

docker ps --help
docker [comando] --help

###Notas de instalación en Windows
- Importante para instalación de windows habilitar virtualización en BIOS
- Una vez instalado ejecutar el comando docker-machine ls para ver la máquina virtual que etá ejecutando el demonio de docker y apuntar ip y puerto para poder acceder a ella.


sudo docker daemon -H tcp://0.0.0.0:2375 --tlsverify --tlscacert=./ca.pem --tlscert=./server-cert.pem --tlskey=./server-key.pem


#VAMOS POR AQUI
https://platzi.com/clases/docker/concepto/redes-multi-host-y-docker-swarm/c-docker-machine/material/






Docker-toolbox
UserDocker