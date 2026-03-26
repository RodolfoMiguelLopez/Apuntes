#SSH

###Que es:

SSH (Secure Shell, en español: intérprete de órdenes seguro) es el nombre de un protocolo y del programa que lo implementa, y sirve para administrar remotamente o acceder a servidores privados a través de una puerta trasera(también llamada "backend". Permite manejar por completo el servidor mediante un intérprete de comandos, y también puede redirigir el tráfico de X (Sistema de Ventanas X) para poder ejecutar programas gráficos si tenemos ejecutando un Servidor X (en sistemas Unix y Windows).
Además de la conexión a otros dispositivos, SSH nos permite copiar datos de forma segura (tanto archivos sueltos como simular sesiones FTP cifradas), gestionar claves RSA para no escribir claves al conectar a los dispositivos y pasar los datos de cualquier otra aplicación por un canal seguro tunelizado mediante SSH.

Más información: [Wikipedia:SSH](https://es.wikipedia.org/wiki/Secure_Shell)

### Como configurar SSH en una instalación de UBUNTU

Instalamos la aplicación:

```
sudo apt-get install ssh
```
Comprobamos que está bien instalado

```
ssh usuario@127.0.0.1 o ssh usuario@localhost
```
Debería de pedirnos el password del usuario correspondiente.

Si queremos comprobar el puerto y si está abierto podemos usar nmap si no está instalado.

```
sudo apt-get install nmap
```
comprobamos los puertos abiertos del equipo

```
nmap localhost
```
debería de aparecer puerto **ssh 22 open** de lo contrario no está bien configurado.

para configurar el servicio de ssh tenemos que editar el archivo sshd_config que se encuentraa en la siguiente ruta /etc/ssh/sshd_config

Es conveniente antes de hacer ningun cambio en este archivo hacer una copia

```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bkp
```
si editamos el archivo

```
sudo nano /etc/ssh/sshd_config
```

Con las opciones de la instalación por defecto son suficientes y ya deberías de poder usarla pero es conveniente en un entorno en producción ajustar los parámetros para que las conexiones sean más seguras.

podemos editar los siguientes parámetros:

valor | descripción
---|---
Port 22| Puerto en el que el servicio SSH estará disponible
PermitRootLogin no |Permitir o denegar el acceso del usuario root mediante SSH
LoginGraceTime 60 |Tiempo en segundos que va a estar disponible la pantalla de inicio de sesión por SSH
MaxAuthTries 2 |Número de intentos de inicio de sesión erróneos consecutivos
MaxStartups 3 |Número de pantallas SSH simultáneas por cliente
AllowUsers user | permitir a los siguientes usuario a usar este servicio  

para reiniciar / iniciar / parar el servicio podemos usar los comandos de ```systemd```

```
sudo service ssh restart / start / stop
```
si configuramos un puerto distinto al 22 al intentar conectar hay que especificar el flag ```-p``` para que el cliente sepa a donde se tiene que conectar:

```
ssh -p 250 user@ipservidor
```
para ayuda rápida de ssh 

```
ssh --help
```
Manual de ssh

```
man ssh
```











