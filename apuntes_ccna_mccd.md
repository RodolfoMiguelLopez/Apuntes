#CCNA - MCCD Curso Apuntes



Modo EXEC del usuario: comandos básicos = Switch> / Router>
Modo EXEC privilegiado: Acceso total al dispositivo = Switch# / Router#

* Modo configuración Global: (config)# se usa ```configure terminal```
	* Se utiliza para realizar cambios que afectan a todo el dispositivo.
* Modo configuración de línea: (config-line)# ```config line```
	* Se utiliza para configurar la consola, SSH, telnet o acceso auxiliar.
* Modo de configuración de interfaz: (config-if)# ```config interface fa0/2```
	* Se utiliza para configurar un puerto de switch o una interfaz de red.

Activar modo EXEC privilegiado = ```enable```
Regresar al modo EXEC no privilegiado= ```disable```


Con el comando ```exit```se vuelve al modo anterior tambien se puede usar ```CTRL + Z```
Con el comando ```end```se vuelve al modo EXEC

Si por ejemplo estamos dentro del modo de configuración global

```
Switch#config t
Switch(config)#line console 0
Switch(config-line)#
// estamos configurando la línea de consola 0 si ahora quisieramos configurar una interfaz de red no tenemos que salirnos solo hay que volver a poner el comando como si estuvieramos en el modo de configuración global //
Switch(config-line)#interface FastEthernet 0/1
Switch(config-if)#
```
##Comandos

Cuando se describe el uso de comandos, generalmente utiilizamos estas convenciones.

Convención | Descripción
---|---
**negrita** | El texto en negrita indica los comandos y las palabras clave que se introducen literalmente como se muestran.
*cursiva* | El texto en cursiva indica los argumentos para los cuales el usuario proporciona el valor.
```[x]``` | Los corchetes indican un elemento opcional ( palabra clave o argumento)
```{x}``` | Las llaves indican un elemento obligatorio (palabra clave o argumento)
```[x{y|z}]``` | Las llaves y las líneas verticales dentro de corchetes indican una opción obligatoria dentro de un elemento opcional.

Ejemplos:

ping _ip-address_ : El comando es ping y el argumento definido por el usuario es ip-address , si quisieramos hacer ping a una máquina tendríamos que poner lo siguiente.

```
ping 10.20.21.12 
```

###Comando de ayuda

En IOS hay dos tipos de ayuda , 

* la ayuda contextual con el comando ```?```

Para ver los comandos disponibles podemos usar ```?```
Para descubrir los comandos que empiezan por una palabra en particular podemos usar ```inter?```y podremos ver todos los comandondos disponibles que empiezan por **inter**

* la verificación de sintaxis : 

Que nos ayuda a introducir los comandos correctamente o cuando un comando es imcompleto o ambiguo, saldrán mensajes de eror explicando donde está el error.

Con el comando ```terminal monitor```se muestran por pantalla los mensajes de estado igual que si estuvieras conectado por consola, ya que por defecto no se habilitan automáticamente en las líneas vty

###Teclas de acceso rápido y método abreviados de la CLI

**Edición de las líneas de la CLI**

Teclas | Descripción
---|---
Tabulación | Completa una entrada de nombre de comando parcial.
Retroceso | Borra el carácter a la izquierda del cursor.
Ctrl + D | Borra el carácter donde está el cursor.
Ctrl + K | Borra todos los caracteres desde el cursor hasta el final de la línea de comandos.
Esc D | Borra todos los caracteres desde el cursor hasta el final de la palabra
Ctrl + U o Ctrl + X | Borra todos los caracteres desde el cursor hasta el comienzo de la línea de comandos.
Ctrl+ w | Borra la palabra a la izquierda del cursor.
Ctrl+ A | Desplaza el cursor hacia el principio de la línea.
<-- o Ctrl + B | Desplaza el cursor un carácter hacia la izquierda.
Esc B | Desplaza el cursor una palabra hacia la izquierda
Esc F | Desplaza el cursor una palabra hacia la derecha
--> o Ctrl + F | Desplaza el cursor un caracter hacia la derecha
Ctrl+ E | Desplaza el cursor hasta el final de la línea de comandos.
Flecha arriba o Ctrl+P | Vuelve a introducir el comando que se encuentra en el búfer del historial, a partir de los comandos mas recientes.
Ctrl+R, Ctrl+I o Ctrl+L | Vuelve a mostrar la petición de entrada del sistema y la línea de comando depués de que se recibe un mensaje de la consola.

**En la petición de entrada "-----More-----"**

Teclas | Descripción
---|---
Tecla Enter | Muestra la siguiente línea.
Barra espaciadora | Muestra la siguiente pantalla
Cualquier tecla | Termina la cadena que se muestra y vuelve al modo EXEX privilegiado.


**Teclas de interrupción"**

Teclas | Descripción
---|---
Ctrl+C | Cuando está en cualquier modo de configuración, termina el modo de configuración y regresa al modo EXEC privilegiado. Cuanod está en modo de configuración, interrumpe y regresa al símbolo del sistema.
Ctrl+Z | Cuando está en cualquier modo de configuración, termina el modo de configuración y regresa al modo EXEC privilegiado.
Ctrl+Shift

###Nombres de dispositivo

Los nombres de host deben de seguir estas reglas:
- Comenzar con una letra.
- No contener espacios.
- Finalizar con una letra o Dígito.
- Utilizar solamente letras, Dígitos y guiones.
- Tener menos de 64 caracteres de longitud.

Proceso de poner nombre (Sw-Principal a un sw)

```
Switch# configure terminal
Switch(config)# hostname Sw-Principal
Sw-Principal(config)#
```
Nota ....Es conveniente poner un nombre descriptivo tanto de propósito como de ubicación.

###Configuración de contraseñas

La contraseña mas importante que hay que configurar es la del modo EXEC privilegiado y despues se puede configurar tanto una contraseña para el usuario que entre por consola con o por vty (ssh/telnet) 

Colocando una contraseña al modo EXEC :

```
Switch>
Switch>en
Switch#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#enable secret cisco
Switch(config)#exit
Switch#
%SYS-5-CONFIG_I: Configured from console by console
disable
Switch>en
Password: 
Switch#
```
Colocando una contraseña a la linea de consola USUARIO

```
Switch(config)#line console 0
Switch(config-line)#password cisco2
Switch(config-line)#login
Switch(config-line)#exit
```
Colocando una contraseña a la líneas de vty

```
Switch(config)#line vty 0 15
Switch(config-line)#password cisco3
Switch(config-line)#login
Switch(config-line)#exit
```
El comando login es para habilitar el acceso tanto a la línea con como a la línea vty

###Cifrado de las contraseñas

Los archivos startup-config y running-config muestran la mayoría de las contraseñas en texto no cifrado. Esta es una amenaza de seguridad dado que cualquier persona puede ver las contraseñas utilizadas si tiene acceso a estos archivos.

Para cifrar las contraseñas, utilice el comando de: 
```configuración global / service password-encryption```. El comando aplica un cifrado débil a todas las contraseñas no cifradas. Este cifrado solo se aplica a las contraseñas del archivo de configuración; no a las contraseñas mientras se envían a través de los medios. El propósito de este comando es evitar que individuos no autorizados vean las contraseñas en el archivo de configuración.

Contraseñas sin cifrar:

```
!
line con 0
 password cisco2
 login
!
line vty 0 4
 password cisco3
 login
line vty 5 15
 password cisco3
 login
!
```
Aplicamos el comando service password encryption

```
Switch(config)#service password-encryption 
```
Resultado de aplicar la configuración:

```
!
line con 0
 password 7 0822455D0A1657
 login
!
line vty 0 4
 password 7 0822455D0A1656
 login
line vty 5 15
 password 7 0822455D0A1656
 login
!
```
Este tipo de cifrado está en desuso ya que no es un método fiable para encriptar contraseñas.

se recomienda usar el comando: ```secret contraseña``` en vez de ```password contraseña```

###Mensajes de aviso

MOTD (Message of the day) Mensaje del día
Para incluir un mensaje de advertencia cuando se entra en el dispositivo se usa el comando ```banner motd```para delimitar donde empieza el mensaje y donde acaba hay que usar dos simbolos que no se repitan en el mensaje por ejemplo ```#texto#```.

Ejemplo:

```
S1(config)#banner motd
% Incomplete command.
S1(config)#banner motd ?
  LINE  c banner-text c, where 'c' is a delimiting character
S1(config)#banner motd # Esto es una zona reservada #
```

###Guardando archivos de configuración

Existen dos archivos de sistema que almacenan la configuración de dispositivos.

* startup-config: el archivo almacenado en la memoria no volátil de acceso aleatorio (NVRAM) que contiene todos los comandos que utilizará el dispositivo durante el inicio o reinicio. La memoria NVRAM no pierde su contenido cuando el dispositivo se desconecta.
* running-config: el archivo almacenado en la memoria de acceso aleatorio (RAM) que refleja la configuración actual. La modificación de una configuración en ejecución afecta el funcionamiento de un dispositivo Cisco de inmediato. La memoria RAM es volátil. Pierde todo el contenido cuando el dispositivo se apaga o se reinicia.

Al haber un corte de corriente o si se reinicia los cambios hechos en la running-config no se guardarán a menos que hagamos antes una copia , para ver la running-config podemos usar el siguiente conmando.

```
show running-config
```
Para ver la startup config

```
show startup-config
```

copiar la información de la running-config a la startup-config

```
copy running-config startup-config
```
Para reiniciar el dispositivo ```reload```

Para borrar la startup-config ```erase startup-config```

###Captura de configuración a un archivo de texto

Para capturar un archivo de texto se puede activar los logs del programa que usemos como terminal , tanto putty como cualquier otro, y acto seguido ejecutar el comando ```show running-config```

Para volver a configurar un sw solo hay que volver a pegar estos comandos en una CLI de cisco para configurar el dispositivo.

###Direcciones IP ipv4

La estructura de una dirección IPv4 se denomina “notación decimal punteada” y se representa con cuatro números decimales entre 0 y 255. Las direcciones IPv4 son números asignados a los dispositivos individuales conectados a una red.

Con la dirección IPv4, también se necesita una máscara de subred. Una máscara de subred IPv4 es un valor de 32 bits que separa la porción de red de la dirección de la porción de host. Combinada con la dirección IPv4, la máscara de subred determina la subred particular a la pertenece el dispositivo.

Las direcciones IP se pueden asignar tanto a los puertos físicos como a las interfaces virtuales de los dispositivos. Una interfaz virtual significa que no hay hardware físico en el dispositivo asociado a ella.

Un switch de capa 2 no necesita una dirección IP. La dirección IP asignada a la SVI(Interfaz virtual) se utiliza para acceder al switch de forma remota. No se necesita una dirección IP para que el switch realice estas operaciones.

Para que un terminal se comunique a través de la red, se debe configurar con una dirección IPv4 y una máscara de subred únicas. La información de dirección IP se puede introducir en los terminales en forma manual o automáticamente mediante el Protocolo de configuración dinámica de host (DHCP).

En general, las PC utilizan DHCP de forma predeterminada para la configuración automática de direcciones IPv4. DHCP es una tecnología que se utiliza en casi todas las redes. Para comprender mejor por qué DHCP es tan popular, tenga en cuenta todo el trabajo adicional que habría que realizar sin este protocolo.

###Configuración de interfaz virtual de switch

Para acceder al switch de manera remota, se deben configurar una dirección IP y una máscara de subred en la SVI. 

Para configurar una SVI en un switch, utilice el comando de configuración global ```interface vlan 1```. La Vlan 1 no es una interfaz física real, sino una virtual. A continuación, asigne una dirección IPv4 mediante el comando ```ip address ip-address subnet-mask``` de la configuración de interfaz. Finalmente, habilite la interfaz virtual con el comando de configuración de interfaz ```no shutdown```.

Ejercicio
            
Configuración de una interfaz virtual de switch
Ingrese el modo de configuración de interfaz para la VLAN 1.
Configure la dirección IPv4 como 192.168.10.2 y la máscara de subred como 255.255.255.0.
Habilitar la interfaz.

```
S1(config)#interface vlan 1
S1(config-if)#ip add
S1(config-if)#ip address 192.168.10.2 255.255.255.0
S1(config-if)#no shut
S1(config-if)#no shutdown 

S1(config-if)#
%LINK-5-CHANGED: Interface Vlan1, changed state to up
```
Para verificar que la interfaz virtual tiene asignada la ip podemos usar el comando ```show ip interface brief```
