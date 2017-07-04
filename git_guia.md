#GIT apuntes curso PLATZI

Instalación de Git para mac:

https://git-scm.com/download/mac

Para ver si está correctamente instalado usamos el comando:

```
git --version
```
Salida
```
git version 2.13.1
```
si te sale la versión es que está bien instalado.

Una vez instalado, debemos de configurar GIT.

Vamos a decirle con qué nombre y correo vas a utilizar GIT

```
$git config --global user.name "minombre"
$git config --global user.email "miemail@miservidor.com"
```
El comando "config" se utilizará para la configuración de GIT. Usamos "global" para que tengamos todos los permisos.

Para comprobar que tenemos todo bien instalado podemos usar el comando:

```
$git config --list
```

info de git en español
https://git-scm.com/book/es/v2

Git funciona con tres areas principales con una arquitectura de árbol.

Arquitectura de arbol:

1 working directory ( area de trabajo ) local
2 staging area ( area de preparación ) local
3 repositorio ( area donde dejamos los archivos) local o remoto

ayuda de git

```
git help comando 
```

iteración básica ( comandos básicos para pasar nuestros proyectos del area 1 a la 2 y a la 3

git add (file or directory)
git commit -m "[mensaje]"
git status

descargamos el archivo de base para practicar desde
https://github.com/platzi/platzigit

para que git empieze a hacer un tracking de una carpeta hay que ponerle el comando:

```
Mbp:blog User$ git init
Initialized empty Git repository in /Users/User/Desktop/blog/.git/
```

para ver el status de como se encuentra git usamos el siguiente comando:

```
Mbp:blog User$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	README.md
	assets/
	favicon.ico
	index.html
	index2.html
	post-1/

nothing added to commit but untracked files present (use "git add" to track)
```
Para agregar archivos del working directory al staging area podemos usar el comando git add podemos usarlo para subir solo un archivo o todos los archivos.

```
Mbp:blog User$ git add favicon.ico 

```
si hacemos un git status podemos ver que el archivo favicon.ico está en el staging area

```
Mbp:blog User$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   favicon.ico

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	README.md
	assets/
	index.html
	index2.html
	post-1/
```
Para agregar todos los archivos usamos el comando git add con la bandera -A

```
Mbp:blog User$ git add -A
```

para agregar los archivos que acutalmente están en el stagin area hay que lanzarlos al repositorio para ello vamos a hacer el primer commit del proyecto.

```
Mbp:blog User$ git commit -m "Creacion inicial del proyecto."
[master (root-commit) 98e1bcd] Creacion inicial del proyecto.
 14 files changed, 2746 insertions(+)
 create mode 100755 README.md
 create mode 100755 assets/css/screen.css
 create mode 100755 assets/fonts/casper-icons.eot
 create mode 100755 assets/fonts/casper-icons.svg
 create mode 100755 assets/fonts/casper-icons.ttf
 create mode 100755 assets/fonts/casper-icons.woff
 create mode 100755 assets/images/IMG_0022.JPG
 create mode 100755 assets/images/IMG_0111.JPG
 create mode 100755 assets/js/index.js
 create mode 100755 assets/js/jquery.fitvids.js
 create mode 100755 favicon.ico
 create mode 100755 index.html
 create mode 100755 index2.html
 create mode 100755 post-1/index.html
```
a partir de ahora si hacemos un cambio git nos lo podrá mostrar , si modificamos el archivo html del proyecto y rellenamos nuestro título y descripción con cualquier editor:

```
<div class="main-header-content inner">
	<h1 class="page-title">Título</h1>
   <h2 class="page-description">Descripción.</h2>
</div>
```

```
<div class="main-header-content inner">
	<h1 class="page-title">Usuario</h1>
   <h2 class="page-description">Aprendiendo git.</h2>
</div>
```
si hacemos un git status tendremos esto:

```
Mbp:blog User$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```
como vemos nos notifica que hay cambios y que estos cambios no han sido añadidos.

para llevar a cabo los cambios y pasarlos al stagin area y posteriormente al repositorio ejecutamos los siguientes comandos:

```
Mbp:blog User$ git add index.html
Mbp:blog User$ git commit -m "Nombre y Descripción agregados."
[master 9537b3f] Nombre y Descripción agregados.
 1 file changed, 11 insertions(+), 11 deletions(-)
Mbp:blog User$ 
```
volvemso a hacer una pequeña modificación y hacemos otro commit

Con git log podemos ver un historial de todos los cambios creados en el repositorio:

```
Mbp:blog User$ git log
commit 403d69245484cf17c10ed965fc7cbe4b00bfb55e (HEAD -> master)
Author: Usuario <miemail@eseste.com>
Date:   Sun Jul 2 19:56:03 2017 +0200

    Pequeña traducción del ingles al español

commit 9537b3fe095dc157484d9def7371c2b51f8bf2fb
Author: Usuario <miemail@eseste.com>
Date:   Sun Jul 2 19:52:05 2017 +0200

    Nombre y Descripción agregados.

commit 98e1bcdd48b1c70b9d18f155b3d87e071353de12
Author: Usuario <miemail@eseste.com>
Date:   Sun Jul 2 19:38:37 2017 +0200

    Creacion inicial del proyecto.
```
para poder enseñar los datos de forma más vistosa podemos usar un alias y pegarle el código de nuestro git log

```
git config --global alias.superlog "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"

```
con esto lo que hacemos es decirle que cada vez que ejecutemos git superlog , ejecutará todo este comando.

tambien podemos usar el comando:

```
git log --oneline
```
Buena práctiva ir guardando los commits en un arhivo de texto.
```
Mbp:blog User$ git log > commits.txt
```
GIT reset

Git reset tiene 3 niveles hard / soft y mixed

para hacer un ejemplo vamos a crear 3 nuevos commits

```
Mbp:blog User$ git superlog
* aade77d - (6 seconds ago) 123 - Usuario (HEAD -> master)
* d979b09 - (21 seconds ago) 2 - Usuario
* a0c990a - (36 seconds ago) 1 - Usuario
* 403d692 - (15 minutes ago) Pequeña traducción del ingles al español - Usuario
* 9537b3f - (19 minutes ago) Nombre y Descripción agregados. - Usuario
* 98e1bcd - (32 minutes ago) Creacion inicial del proyecto. - Usuario
```
ahora vamos a usar el git reset para borrar todos los commits posteriores al commit que nosotros le digamos por ejemplo en este caso va a ser el 403d692

```
Mbp:blog User$ git reset --hard 403d69245484cf17c10ed965fc7cbe4b00bfb55e
HEAD is now at 403d692 Pequeña traducción del ingles al español
Mbp:blog User$ git superlog
* 403d692 - (21 minutes ago) Pequeña traducción del ingles al español - miemail@eseste.com (HEAD -> master)
* 9537b3f - (25 minutes ago) Nombre y Descripción agregados. - Usuario
* 98e1bcd - (39 minutes ago) Creacion inicial del proyecto. - Usuario
```
como vemos ha borrado todos los comando anteriores al mencionado, este proceso es reversible, si sabemos el id del último commit podemos volver a deshacer el git reset.

```
Mbp:blog User$ git reset --hard aade77d182dc7f4c6e052a6b61e03ebc3684c4d6
HEAD is now at aade77d 123
Mbp:blog User$ git superlog
* aade77d - (10 minutes ago) 123 - Usuario (HEAD -> master)
* d979b09 - (10 minutes ago) 2 - Usuario
* a0c990a - (11 minutes ago) 1 - Usuario
* 403d692 - (25 minutes ago) Pequeña traducción del ingles al español - Usuario
* 9537b3f - (29 minutes ago) Nombre y Descripción agregados. - Usuario
* 98e1bcd - (42 minutes ago) Creacion inicial del proyecto. - Usuario
```

git mixed este tipo de reset se usa para encapsular varios commits en 1 solo pero no hace ningún cambio en el working area.

por ejmplo vamos a hacer un git mixed con la estructura actual y vamos a encapsular los tres comits ( 1 , 2 y 123 ) en uno solo.

```
Mbp:blog User$ git reset --mixed 403d69245484cf17c10ed965fc7cbe4b00bfb55e
Unstaged changes after reset:
M	index.html
Mbp:blog User$ git superlog
* 403d692 - (46 minutes ago) Pequeña traducción del ingles al español - Usuario (HEAD -> master)
* 9537b3f - (50 minutes ago) Nombre y Descripción agregados. - Usuario
* 98e1bcd - (64 minutes ago) Creacion inicial del proyecto. - Usuario
Mbp:blog User$ git add -A
Mbp:blog User$ git commit -m "Suma de los commits 1,2,y 123"
[master 595cedf] Suma de los commits 1,2,y 123
 2 files changed, 36 insertions(+), 1 deletion(-)
 create mode 100644 commits.txt
Mbp:blog User$ git superlog
* 595cedf - (3 seconds ago) Suma de los commits 1,2,y 123 - Usuario (HEAD -> master)
* 403d692 - (47 minutes ago) Pequeña traducción del ingles al español - Usuario
* 9537b3f - (51 minutes ago) Nombre y Descripción agregados. - Usuario
* 98e1bcd - (64 minutes ago) Creacion inicial del proyecto. - Usuario
Mbp:blog User$
```
tambien podemos volver a recuperar esta edición con el commit id del último commit

```
Mbp:blog User$ git reset --mixed aade77d182dc7f4c6e052a6b61e03ebc3684c4d6
Mbp:blog User$ git superlog
* aade77d - (35 minutes ago) 123 - Usuario (HEAD -> master)
* d979b09 - (35 minutes ago) 2 - Usuario
* a0c990a - (35 minutes ago) 1 - Usuario
* 403d692 - (49 minutes ago) Pequeña traducción del ingles al español - Usuario
* 9537b3f - (53 minutes ago) Nombre y Descripción agregados. - Usuario
* 98e1bcd - (67 minutes ago) Creacion inicial del proyecto. - Usuario
```
git reset soft solo hace cambios en el repositorio y deja el working area y el stagin area en el mismo estado.

```
Mbp:blog User$ git reset --soft 403d69245484cf17c10ed965fc7cbe4b00bfb55e
Mbp:blog User$ git superlog
* 403d692 - (54 minutes ago) Pequeña traducción del ingles al español - Usuario (HEAD -> master)
* 9537b3f - (58 minutes ago) Nombre y Descripción agregados. - Usuario
* 98e1bcd - (71 minutes ago) Creacion inicial del proyecto. - Usuario
Mbp:blog User$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	commits.txt
``` 
git checkout 

con git checkgout podemos movernos por las ramas sin alterar los archivos solo hay que tener bien guardados los commits para saber adonde tenemos que ir.

```
Mbp:blog User$ git checkout 98e1bcdd48b1c70b9d18f155b3d87e071353de12
Note: checking out '98e1bcdd48b1c70b9d18f155b3d87e071353de12'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 98e1bcd... Creacion inicial del proyecto.
Mbp:blog User$ git checkout aade77d182dc7f4c6e052a6b61e03ebc3684c4d6
Previous HEAD position was 98e1bcd... Creacion inicial del proyecto.
HEAD is now at aade77d... 123
```
Los commits son secuenciales y cada uno depende del anterior estableciendose una relación padre / hijo , de esa manera no hay manera de eliminar un commit en especial. 
El HEAD es el puntero de donde nos encontramos en relación al repositorio.
Por defecto la rama de inicio siempre es MASTER

RAMAS

Las ramas son una línea alterna del tiempo, en la historia de nuestro repositorio.
las ramas normalmente se general para 3 cosas principalmente, ideas, features o bug fixes.

FUSIONES

Qué es una fusión?
Una fusión es una mezcla de ambas ramas (master y experimental)
¿Cómo hacer fusiones?
Primero hay que situarse en la rama master(git checkout master) y luego hacer la fusión con git merge experimental
¿Cómo se resuelven los conflictos?
-Fast forward: Los gestores trabajaron archivos diferentes al repositorio.
-Manual merge: Dos desarrolladores trabajan el mismo archivo en la fusión y las mismas líneas de código.
¿Qué es el rebase?
Es una técnica que nos permite situar los commits de la rama experimental delante de los commits de la rama 

Hay 2 maneras de crear una rama 

git branch <nombre rama> o git checkout -n <nombre rama >

la diferencia es que con el primer comando solo creamos la rama y con el segundo es que creamos la rama y nos posicionamos en ella con el checkout.

```
Mbp:blog User$ git checkout -b experimental
Switched to a new branch 'experimental'
```
Aquí podemos ver que en la rama experimental hemos agregado 3 commits (a,b,c) y despues nos hemos cambiado a la rama master y hemos creado un commit nuevo, de ahí que se vea con esta forma porque en realidad hay dos ramas activas.
```
Mbp:blog User$ git superlog
* bcb6a19 - (6 seconds ago) 4 - Usuario (HEAD -> master)
| * 273e2c0 - (3 minutes ago) c - Usuario (experimental)
| * 319a4e9 - (3 minutes ago) b - Usuario
| * 3539a29 - (3 minutes ago) a - Usuario
|/  
* 1e8dc87 - (8 minutes ago) 3 - Usuario
* 6c50c34 - (8 minutes ago) 2 - Usuario
* 09677f5 - (9 minutes ago) 1 - Usuario
* 4a46c49 - (49 minutes ago) 0 - Usuario
```
para hacer una fusión se usa el comando merge para ello debemos de colocarnos en la rama que se quiere hacer la fusión en este caso vamos a absorber la rama experimental por lo que deberemos de colocarnos en la rama master con git checkout.

Los conflictos se solucionan de dos maneras fast-forward y manual merge , uno es cuando no hay conflictos cuando los archivos que vamos a juntar no son los mismos y manual merge es cuando hay que dirimir cambios y seleccionar con cual nos quedamos, en este caso será un fast-forward.

para juntar las ramas usamos el comando git merge

```
Mbp:blog User$ git merge experimental
```
cuando pulsamos enter nos sale una pantalla de vi que nos pide que introduzcamos un nombre para ese commit.

Nos ponemos debajo de Merge y pulsamos la tecla "o" y escribimos el nombre del commit.
```
Merge branch 'experimental'
--aqui ponemos el mensaje--
# Please enter a commit message to explain why this merge is necessary,
# especially if it merges an updated upstream into a topic branch.
#
# Lines starting with '#' will be ignored, and an empty message aborts
# the commit.
~                                                                                                                                                     
~                                                                                                                                                     
                    
```
Una vez puesto el mensaje pulsamos ESC y ponemos :x que es salir y guardar.

```
Merge made by the 'recursive' strategy.
 a.txt | 0
 b.txt | 0
 c.txt | 0
 3 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
 create mode 100644 b.txt
 create mode 100644 c.txt
```
Si hacemos un log podemos ver lo que acabamos de hacer que es la fusión de la rama experimental.

```
Mbp:blog User$ git superlog
*   c22d04f - (6 minutes ago) Merge branch 'experimental' fusión con la rama experimental - Usuario (HEAD -> master)
|\  
| * 273e2c0 - (17 minutes ago) c - Usuario (experimental)
| * 319a4e9 - (17 minutes ago) b - Usuario
| * 3539a29 - (17 minutes ago) a - Usuario
* | bcb6a19 - (14 minutes ago) 4 - Usuario
|/  
* 1e8dc87 - (22 minutes ago) 3 - Usuario
* 6c50c34 - (22 minutes ago) 2 - Usuario
* 09677f5 - (23 minutes ago) 1 - Usuario
* 4a46c49 - (63 minutes ago) 0 - Usuario
```
para borrar el nombre de una rama podemos usar:

```
Mbp:blog User$ git branch -d experimental
Deleted branch experimental (was 273e2c0).
```
vamos a probar a hacer una fusión pero habiendo modificado el mismo archivo en dos ramas distintas en este caso hemos creado un archivo que se llama x.txt y hemos escrito hola mundo en una rama y querido mundo en otra rama. si los intentamos fusionar nos saldrá este mensaje.

```
Mbp:blog User$ git merge experimental2
Auto-merging x.txt
CONFLICT (content): Merge conflict in x.txt
Automatic merge failed; fix conflicts and then commit the result.
```
si nos vamos a editar el archivo con el editor de texto tendremos el siguiente mensaje:

```
<<<<<<< HEAD
Querido Mundo
=======
hola mundo
>>>>>>> experimental2
```
lo que hace git es mostrarnos el conflicto para que nosotros lo arreglemos nos dice que en HEAD (rama master) tenemos Querido Mundo y que en experimental2 tenemos hola mundo.

tenemos que quitar lo que no queremos en este caso hemos decidido dejar el hola mundo normal de la rama experimental por lo que dejamos el archivo de la siguiente manera.

```
hola mundo
```
y salvamos en nuestro editor.

despues nos vamos a la terminal y añadimos el archivo y nombre para el commit

```
Mbp:blog User$ git add -A
Mbp:blog User$ git commit -m "Fusión de Hola Mundo"
[master 2087b79] Fusión de Hola Mundo
```
Para borrar git del directorio podemos usar el siguiente comando, esto es válido para reiniciar el proyecto.
```
Mbp:blog User$ rm -rf .git
```
Cambios en los commits

teniendo la siguiente estructura podemos hace un cambio en el ultimo commit ( solo se puede hacer en el último no vale para otros commits.

```
bp:blog User$ git superlog
* 2c6c382 - (4 seconds ago) Agregado Descripciónxxxxx - Usuario (HEAD -> master)
* 3da3f00 - (79 seconds ago) Agregado título - Usuario
* a65b8e2 - (6 minutes ago) 0 - Base proyecto de marca personal - Usuario
```
por ejemplo queremos cambiar la descripción del ultimo commit porque está mal escrito podemos usar el comando git commit con el flag --amend al final:

```
Mbp:blog User$ git commit -am "Agregado Descripción" --amend
[master 72091ab] Agregado Descripción
 Date: Mon Jul 3 09:30:25 2017 +0200
 1 file changed, 1 insertion(+), 1 deletion(-)
Mbp:blog User$ git superlog
* 72091ab - (3 minutes ago) Agregado Descripción - Usuario (HEAD -> master)
* 3da3f00 - (4 minutes ago) Agregado título - Usuario
* a65b8e2 - (9 minutes ago) 0 - Base proyecto de marca personal - Usuario
```
Teniendo esta estructura vamos a hacer un git rebase

```
Mbp:blog User$ git superlog
* a5c7453 - (4 seconds ago) 4 - Usuario (HEAD -> master)
| * aa45c4e - (42 seconds ago) b - Usuario (ramarebase)
| * 7f34dcc - (55 seconds ago) a - Usuario
|/  
* d5c3388 - (2 minutes ago) 3 - Usuario
* 43781f2 - (2 minutes ago) 2 - Usuario
* 81b5177 - (2 minutes ago) 1 - Usuario
* 97b3484 - (6 minutes ago) Archivos base - Usuario
```
nos colocamos en la rama que vamos a empujar hacia la principal en este caso es ramarebase

```
Mbp:blog User$ git rebase master
First, rewinding head to replay your work on top of it...
Applying: a
Applying: b
```
lo que hemos hecho es empujar los archivos a la rama master pero master sigue atrás si hacemos un log lo vemos mejor:

```
Mbp:blog User$ git superlog
* 95a8964 - (9 minutes ago) b - Usuario (HEAD -> ramarebase)
* 73068b6 - (9 minutes ago) a - Usuario
* a5c7453 - (8 minutes ago) 4 - Usuario (master)
* d5c3388 - (10 minutes ago) 3 - Usuario
* 43781f2 - (10 minutes ago) 2 - Usuario
* 81b5177 - (10 minutes ago) 1 - Usuario
* 97b3484 - (14 minutes ago) Archivos base - Usuario
```
Nos movemos a la rama master y hacemos un git merge <rama> y hace un fastforward

```
Mbp:blog User$ git checkout master
Switched to branch 'master'
Mbp:blog User$ git merge ramarebase
Updating a5c7453..95a8964
Fast-forward
 a.txt | 0
 b.txt | 0
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
 create mode 100644 b.txt
```
si hacemos un log ahora veremos que todos están en la misma línea temporal

```
Mbp:blog User$ git superlog
* 95a8964 - (12 minutes ago) b - Usuario (HEAD -> master, ramarebase)
* 73068b6 - (12 minutes ago) a - Usuario
* a5c7453 - (12 minutes ago) 4 - Usuario
* d5c3388 - (13 minutes ago) 3 - Usuario
* 43781f2 - (14 minutes ago) 2 - Usuario
* 81b5177 - (14 minutes ago) 1 - Usuario
* 97b3484 - (17 minutes ago) Archivos base - Usuario
```

Varios comandos con git log

git log -m "mensaje"  --amend = Rectifica y sustituye el ultimo commit
git log --oneline = muestra el commit resumido en una linea
git log --decorate = muestra el commit con el head indicado donde esta posicionado 
git log --stat = explica con detalle en numero de lineas que se convinaron.
git log -p = es un análisis más profundo del anterior (git log --stat).
git shortlog =   agrupa por autor y muestra los titulos del commit.
git log --graph --oneline --decorate = muestra grafica del de historial del repositorio.
  
-------------------------
git logs filtros de comandos
git log -3 =  Por cantidad muestra los commits
git log --before="today"  = se muestra todo lo de antes de hoy
git log --after="today"  = se muestra todo lo de mañana 
git log --author ="AUTOR" = muestra los commits dle autor
git log --grep="MENSAJE" = muestra el todo los commit que concuerden con el mensaje (el mensaje debe de estar en el titulo  ) sencible a MAyusculas o minusculas usar el i al final 
git log -- archivo.* = comits por archivo (el * extencion del archivo php.html.py etc etc )

workflows

Como lograr que varios profesionales trabajen sobre un mismo proyecto de código.

Si queremos descargar un repositorio de github podemos usar https o ssh 

ejemplo de descarga con https
```
git clone https://github.com/github/gemoji.git
```
con este comando lo que hacemos es clonar el repositorio de gemoji

tambien nos descarga todos los commits que se han ido haciendo a lo largo del proyecto, podemos usar superlog para ver los logs y tambien podemos usar git shortlog para ver quien ha colaborado en el proyecto.

---- empezando con github -------

Creamos un repositorio con las opciones por defecto en nuestro caso le hemos llamado ejercicio.

cuando terminamos de crearlo github nos muestra varias opciones

```
…or create a new repository on the command line

echo "# ejercicio" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:RodolfoMiguelLopez/ejercicio.git
git push -u origin master

…or push an existing repository from the command line

git remote add origin git@github.com:RodolfoMiguelLopez/ejercicio.git
git push -u origin master

…or import code from another repository

You can initialize this repository with code from a Subversion, Mercurial, or TFS project.
```
Si nos vamos a settings de github y a SSH and GPG keys veremos las llaves SSH de las que disponemos

para conectarnos a github es necesario generar una clave privada en mi equipo que luego tengo que enlazar con nuestra cuenta de github, para crear la llave privada usamos el siguiente comando:

```
Mbp:~ User$ ssh-keygen -t rsa -b 4096 -C "miemail@eseste.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/User/.ssh/id_rsa): 
/Users/User/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/User/.ssh/id_rsa.
Your public key has been saved in /Users/User/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:pOU6iFLfNAq9t7BsdW2dYJB0s5F0sZFNUzigu+UZ8aE miemail@eseste.com
The key's randomart image is:
+---[RSA 4096]----+
|       ..o=.=*oo.|
|        o..*.o+. |
|        o.o o .. |
|   .   =  o. + . |
|  o . + So.oE..  |
| . + *.o. o+oo   |
|. . *.=. .. o    |
| . ..+ o         |
|   .o .          |
+----[SHA256]-----+

```
- Nos pregunta si queremos eliminar la anterior si tenemos ya una creada sino no nos lo dice
- Tambien nos pide un password para la clave ( es opcional pero conveniente ponerselo)
Cuando se genera la clave esta es guardada en la siguiente ruta:
```
/Users/User/.ssh/
drwx------   5 User  staff   170 28 mar  2016 .
drwxr-xr-x+ 54 User  staff  1836  3 jul 12:01 ..
-rw-------   1 User  staff  1766 28 mar  2016 id_rsa
-rw-r--r--   1 User  staff   420 28 mar  2016 id_rsa.pub
```
tenemos la privada que es la id_rsa y la pública que es la id_rsa_pub

si hacemos un cat de la llave publica

```
cat id_rsa_pub
```
nos mostrará la clave que es muy larga, esa clave la copiamos y la ponemos en la sección de claves de nuestro github.

De esta manera ya tenemos conectado nuestro repositorio con nuestra máquina local y solo desde esa máquina poder conectarnos por ssh.

vamos a hacer lo que sería la conexión básica de nuestro repositorio con github

- Creamos un directorio con mkdir
- Entramos al directorio con cd
- Creamos un archivo llamado archivo1.txt con el comando touch
- iniciamos el repositorio con git init
- añadimos los archivos al repositorio
- añadimos el commit 
- nos conectamos al repositorio remoto 
	- git remote add = añadimos un repositorio remoto
	- origin = la rama principal
	- git@github.... dirección ssh del repositorio de github
- git push origin master
	- git push = empujamos el repositorio al repositorio remoto
	- origin = la rama a la que queremos llevar el contenido destino
	- master = la rama desde la que queremos el contenido origen
Si hemos puesto contraseña nos la pedirá y una vez introducida subirá el repositorio 
si nos vamos al repositorio podremos ver el archivo creado.

https://github.com/RodolfoMiguelLopez/ejercicio

```
Mbp:Desktop User$ mkdir prueba
Mbp:Desktop User$ cd prueba
Mbp:prueba User$ touch archivo1.txt
Mbp:prueba User$ git init
Initialized empty Git repository in /Users/User/Desktop/prueba/.git/
Mbp:prueba User$ git add -A
Mbp:prueba User$ git commit -m "archivos base"
[master (root-commit) 70c0cf1] archivos base
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 archivo1.txt
Mbp:prueba User$ git remote add origin git@github.com:RodolfoMiguelLopez/ejercicio.git
Mbp:prueba User$ git push origin master
Warning: Permanently added the RSA host key for IP address '192.168.100.11' to the list of known hosts.
Saving password to keychain failed
Identity added: /Users/User/.ssh/id_rsa ((null))
Counting objects: 3, done.
Writing objects: 100% (3/3), 223 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:RodolfoMiguelLopez/ejercicio.git
 * [new branch]      master -> master
```
Cuando trabajamos con repositorios remotos disponemos de tres ramas.

master		repositorio remoto (REMOTO)
 
origin/master repositorio espejo del repositorio remoto (LOCAL)
master repositorio de trabajo (LOCAL)

Git crea el repositorio de origin/master para tener una copia en local del repositorio remoto, de esta forma si el repositorio remoto se actualiza cae primero en la rama origin/master y despues nosotros podemos hacer una fusión y subirlos al repositorio remoto de manera que no genere conflictos.

para comprobar que tenemos todo actulizado usamos los comandos git fetch y git merge el workflow sería el siguiente:

git remote add origin (ssh)   conectamos a la rama origin remota
git fetch origin					descargo lo que hay en el repositorio remoto a origin/master
git merge origin/master			uno lo que está descargado en origin/master con master local

** Desarrollamos **

antes de subir nuestros cambios al repositorio telenemos que hacer un git fech y un merge y despues un push para finalmente subir los cambios de esta manera nos aseguramos de que siempre estamos actualizados.

git fetch origin					
git merge origin/master
git push origin master

Esto se hace normalmente cuando pueden subir varias personas a la vez y entonces puede haber cambios antes o despues de subir los nuestros.








POR AQUI

https://platzi.com/clases/git-github/concepto/navegacion-entre-commits/f-proyecto-con-lineas-de-tiempo-alternas/material/




















