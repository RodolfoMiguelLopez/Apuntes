```
 .d8888b. 8888888 .d8888b.   .d8888b.   .d88888b.  
d88P  Y88b  888  d88P  Y88b d88P  Y88b d88P" "Y88b 
888    888  888  Y88b.      888    888 888     888 
888         888   "Y888b.   888        888     888 
888         888      "Y88b. 888        888     888 
888    888  888        "888 888    888 888     888 
Y88b  d88P  888  Y88b  d88P Y88b  d88P Y88b. .d88P 
 "Y8888P" 8888888 "Y8888P"   "Y8888P"   "Y88888P"  
```


###Curso Cisco Apuntes Udemy
[Acces al Curso](https://www.udemy.com/redes-con-equipos-cisco-ccna-200-120/learn/v4/overview)

![](file:///Users/kapi_tan/Desktop/apuntes/Redes/cisco/img/Ciscobootprocess.jpg)

En la NVRAM [^NVRAM] se almacena **startup-config** — > Es la Configuración inicial

En la RAM [^RAM] se almacena **running-config** -> Es la configuración actual en vivo

| Comando | Descripción |
|---------|-------------|
|enable| entra en modo EXEC privilegiado|
|en | Mismo que anterior abreviado |
|show flash|Muestra el contenido de la memoria flash|
|sh flash|Identico al anterior abreviado|
|sh version|Muestra Configuración, numero de serie, versión|
|sh running-config|Configuración actual|
|sh r|Configuración actual ( Modo Abreviado )|
|sh startup-config|Configuración Inicial|
|configure terminal| Modificar Parámetros de Configuración|
|conf t|igual que anterior abreviado|
|wr	|Guardar configuración|
|reload|reiniciar|
|show ?|ayuda de comandos|
|Router>|Modo USER EXEC sin privilegios|
|Router#|Modo EXEC privilegiado|
|Router(config)#| Modo configuración global|
|exit|salir del modo actual|
|do| Nos permite bajar un nivel sin tener que usar ```exit```
|ctrl+z|salir del modo actual|
|hostname| Poner un nombre al Router/Switch|


Instrucciones Básicas en el modo configuración global:

```bash
Router(Config)#hostname NOMBRE HOST
```
Con este comando le cambias el nombre al host

```bash
Router(config)#interface fastEthernet 0/0
Router(config-if)#
```
Con este comando entras en la interfaz de la tarjeta FastEthernet 0/0
Si en cualquier comando lo escribimos seguido de un ```?``` nos dirá los posibles comandos que están soportados dependiendo de los privilegios y el modo de operación.

```bash
Router(config)#enable password contraseña
```
Con este comando se establece una contraseña para el modo EXEC privilegiado, la contraseña se puede ver en claro si hacemos un ```running-config```.

```bash
Router(config)#enable secret contraseña
```
Con este comando pones una contraseña al modo EXEC privilegiado pero no se ve en claro aparece encriptada.

Si se hace un ```sh r``` al final del archivo aparece las lineas de Consola y Telnet de la siguiente manera:

```
line con 0
line vty 0 4
```
Esto quiere decir que hay 1 linea de consola y 5 lineas de telnet para configurar password a estas lineas se usa la siguiente combinación de comandos.

```bash
Router(config)#line con 0
Router(config-line)#password contraseña
Router(config-line)#login
```
Si en vez de querer configurar la linea quiero configurar las lineas vty se procede de manera parecida, en este caso al se mas de una solo hay que poner un espacio entre los 2 numeros de lineas que quieres.

```bash
Router(config)#line vty 0 4
Router(config-line)#password contraseña
Router(config-line)#login
```
###Recuperar password enable IOS

Los equipos CISCO por defecto guardan la configuración en un registro de memoria x normalmente este registro es **0x2102** esto se puede ver con el comando ```show version```si lo hacemos nos saldrá la siguiente información al final del todo :

```
----------------------------------------------------------------
Technology    Technology-package          Technology-package
              Current       Type          Next reboot
-----------------------------------------------------------------
ipbase        ipbasek9      Permanent     ipbasek9
security      None          None          None
uc            None          None          None
data          None          None          None

Configuration register is 0x2102
```
como vemos el registro que usa para guardar la configuración es **0x2102**

Hemos configurado el Router/Switch con un hostname y una contraseña para enable previamente.

Estando conectado el equipo que vayamos a usar por consola al aparato iniciar equipo y pulsar a la vez
<kbd>CTRL</kbd> + <kbd>PAUSA</kbd> para los que lo hagan virtualizado por virtualbox con MAC pueden ir al menu de entrada/teclado/insertar CTRL + BREAK.

cuando hacemos esto el equipo entra en modo ronmon

ahora vamos a cambiar el valor del registro a otro diferente para que cargue una lista de configuración vacía sin nada para ello usamos el siguiente comando y reseteamos.

```bash
rommon 1#confreg 0x2142
ronmon 2#reset 
```
cuando reinicie el equipo es como si no tuvierammos nada configurado si hacemos un ```running-config```no veríamos nada pero en vez de eso vamos a hacer un ```starup-config```y ahi veremos la configuración anterior. 

Si volvemos a hacer un ```show version```veremos que la dirección de memoria ha cambiado antes era **0x2102** y ahora es **0x2142**

haciendo solamente un ```copy startup-config running-config```copiamos la configuración de esta forma volvemos a tener la configuración anterior pero con acceso, tambien podemos poner otra contraseña y poner un ```wr```lo unico que perdemos la configuración que tengamos hecha, ya que lo que hace el wr es copiar el running al config.

para volver a dejarlo bien hay que poner el valor de registro que hemos modificado en su valor inicial para ello hacemos lo siguiente:

```bash
Router#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#config-register 0x2102
Router(config)#
```
guardamos la configuración con ```wr```y si hacemos un ```show version```

```
----------------------------------------------------------------
Technology    Technology-package          Technology-package
              Current       Type          Next reboot
-----------------------------------------------------------------
ipbase        ipbasek9      Permanent     ipbasek9
security      disable       None          None
uc            disable       None          None
data          disable       None          None

Configuration register is 0x2142 (will be 0x2102 at next reload)

```
Nos especifica que el valor cambiara en el próximo reinicio.

##Conseguir Contraseñas CISCO
En relación con las conraseñas las hay de 3 tipos

- De tipo 0 , se guardan en texto plano cuando usamos el comando ```enable password loquesea```
- De tipo 5 , se a cada contraseña se le aplica el algoritmo MD5 Unix, almacenándose su correspondiente hash. Se considera el más seguro, es el que se aplica cuando ponemos ```enable secret loquesea```.
	* Para conseguir la clave de tipo 5 hay queutilizar el software “Hashcat, advanced password recovery” utilizaremos un ataque por fuerza bruta empleando la CPU, deberemos indicar el archivo de texto donde tenemos nuestro hash $1$PHM7$LukCBXSHLmkCJZ0jEIpk80 ; método de crackeo “Brute-force” ; tipo de Hash “MD5(Unix)”. Si hacemos lo propio en una consola y lo ejecutamos obtendríamos el mismo resultado:

```
hashcat-cli64.exe –hash-mode 500 –attack-mode 3 –bf-cs-buf abcdefghijklmnopqrstuvwxyz0123456789 –bf-pw-min 1 –bf-pw-max 16 X:/xxxx/xxxxx/xxxxxx/hashmd5UNIX.txt
```
- De tipo 7, similar al anterior siéndole aplicado un algoritmo definido por Cisco. Fácilmente crackeable.
	* Podemos usar el software cain, tiene una opción CISCO type-7 Password Decoder, se mete el hash y se consigue la contraseña. Tambien hay paginas online que pueden hacer esta tarea.

## varios ordenar
Para mostrar la tabla de direccionamiento o ARP

```bash
Router#Sh mac-adress-table
```
Para hacer un ping desde IOS

```
Router#ping 192.168.1.1
```

## Configuación Básica

- Hostname
- Enable Password
- Banner Motd
- no ip domain lookup ( para evitar que resuelva dominios cuando ponemos un comando no conocido )
- ssh



##SSH

Comandos útiles SSH | Descripción
---|---
show ip ssh | Muestra información del servicio
show ssh | Muestra las sesiones abiertas

**Antes de configurar el ssh hay que tener activada la clave para enable sino no nos funcionará**

###Paso a Paso para configurar una conexión SSH

- 1) Entramos en modo privilegiado

```
Switch>en
```

- 2) Entramos en modo configuración global

```	bash
Switch#conf t
```

- 3) Ponemos un nombre a nuestro host en este caso se llamará S1

```bash
Switch(config)#hostname S1
```

- 4) Ponemos un mensaje de inicio al entrar al switch 1

```bash
S1(config)#banner motd +Este es el Switch 1+
```

- 5) Configuramos la contraseña para ENABLE en este caso ```cisco```

```bash
S1(config)#enable secret cisco
```

- 6) Desactivamos la resolución de dominios o comandos introducidos por error ( OPCIONAL )

```bash
S1(config)#no ip domain-lookup			
```

- 7) Seleccionamos la linea de consola

```bash
S1(config)#line console 0				
```

- 8) Seleccionamos un password para la linea de comunicación por consola en este caso ```consola``

```bash
S1(config-line)#enable secret consola
```

- 9) Seleccionamos las lineas vty del switch en este caso como tiene mas de una lina cogemos y seleccionamos desde la 0 a la 15

```bash
S1(config)#line vty 0 15
```

- 10) Especificamos un password para las lineas VTY en este caso será ```vty```

```bash
S1(config-line)#enable secret vty
```

- 11) Se especifica que la bd que se va a usar de usuarios es la local

```bash
S1(config-line)#login local
```

- 12) Se especifica que la comunicación por esas lineas va a ser por ssh

```bash
S1(config-line)#transport input ssh
```

- 13) Se crea un usuario local con privilegio maximo y con una contraseña en este caso cisco123

```bash
S1(config)#username cisco privilege 15 secret cisco123
```

- 14) Se especifica un nombre de dominio en este caso cisco

```
S1(config)#ip domain-name cisco
```

- 15) Se genera la clave ssh en este caso nos deja elegir la longitud y le decimos 2048 la máxima

```
S1(config)#crypto key generate rsa
The name for the keys will be: S1.cisco
Choose the size of the key modulus in the range of 360 to 2048 for your
  General Purpose Keys. Choosing a key modulus greater than 512 may take
  a few minutes.

How many bits in the modulus [512]: 
```

- 16) Especificamos la version de ssh a usar aunque por defecto parece que usa la v2

```bash
S1(config)#ip ssh version 2
```

- 17) Guardamos la configuración

```bash
S1#wr
```	

#Para que las opciones de seguridad estén activas hay que ejecutar el comando aaa new model ,,, revisar comandos e incluir en apuntes:

#```
#aaa new-model
#aaa authentication login default local-case
#session-timeout 5
#exec-timeout 5 0
#```


##Ahora vamos a configurar las VLANS necesarias para poder entrar en el Switch

Comando | Explicación
---|---
S1(config)#vlan 200|Creamos la vlan
S1(config-vlan)#name ADMIN|le damos un nombre en este caso ADMIN
S1(config-vlan)#exit| Nos bajamos al modo global
S1(config)#interface vlan 200	| Levantamos la interfaz **```Opcional```**
S1(config-if)#ip address 192.168.200.1 255.255.255.0| le asignamos una dirección ip **```Opcional```**

una vez configurada la interfaz tenemos que decirle por donde va a ir su tráfico
La asignación de ip al interfaz de vlan solo es necesario cuando necesitamos hacer routing o acceder al switch a través de esa ip para administrarlo , se puede obviar 

Comando | Explicación
---|---
S1(config)#interface fa0/1| Seleccionamos la interfaz fasethernet fa0/1
S1(config-if)#switchport mode access	| Le decimos que la ponga en modo acceso
S1(config-if)#switchport access vlan 200 | Le especificamos por donde va a pasar , puede ser mas de una pero en este caso solo es la 200

Con el comando **```show vlan```** podremos ver si lo hemos echo correctamente

```
S1#show vlan						

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/2, Fa0/3, Fa0/4, Fa0/5
                                                Fa0/6, Fa0/7, Fa0/8, Fa0/9
                                                Fa0/10, Fa0/11, Fa0/12, Fa0/13
                                                Fa0/14, Fa0/15, Fa0/16, Fa0/17
                                                Fa0/18, Fa0/19, Fa0/20, Fa0/21
                                                Fa0/22, Fa0/23, Fa0/24, Gig0/1
                                                Gig0/2
200  ADMIN                            active    Fa0/1
```
Quitamos el cable de consola y conectamos un cable ethernet del PC0 al Fa0/1 del S1
Ahora deberíamos de poder conectar por ssh al router desde el PC0
le damos una ip al PC0 192.168.200.10 y abrimos una linea de comandos y ponemos el siguiente comando:

```bash
C:\>ssh -l cisco 192.168.200.1
Open
Password: 

Este es el Switch 1

S1#
```
la contraseña será la que hayas configurado para el usuario cisco en este caso **```cisco123```**

##CONFIGURACIÓN DE UN TRUNK ENTRE 2 SWITCHES PARA 2 VLANS DISTINTAS

Al igual que hemos hecho anteriormente para la configuración de las conexiones ssh y configuración de una vlan vamos a añadir una vlan mas de **USUARIOS** y configuramos otro switch con la misma configuración con la idea de hacer una conexión entre los dos ( **Trunk** ) y así poder conectar por ejemolo 2 Redes. La idea principal es que la VLAN de ADMIN sea la única que pueda acceder a los switchs por SSH y administrarlos y la VLAN de USUARIOS solo pueda ver a los usuarios sin poder administrar los Switchs.

Partiendo de la base que tenemos 1 SW configurado con una VLAN y administrado por un equipo por SSH
realizamos la misma tarea para otro SW. Una vez relizado colocamos 1 equipo para la vlan de usuarios en cada SWITCH.

Una vez realizado este paso nos vamos a la interfaz que hemos conectado con un cable cruzado entre los dos switchs en mi caso he elegido la gigabit este será el cable del **trunk**.

Comando | Acción que realiza
---|---
SX(config)#interface gigabitEthernet 0/1 | Seleccionamos la interfaz que conecta los dos switchs.
SX(config-if)#switchport mode trunk	| Activamos el trunk.
SX(config-if)#switchport trunk native vlan 500 | Le decimos que la nativa sea la 500.**```Opcional```**
SX(config-if)#switchport trunk allowed vlan 200,100,500 | Dejamos pasar por el trunk las vlans que queremos. **```Opcional```**
SX#wr | Guardamos la configuración.

Podemos obviar la configuración de las vlans que pasen por el trunk por defecto hace pasarlas todas. Aunque es buena práctica especificarlas. Al igual que especificar una vlan nativa distinta a la 1.

Con el comando **```show interfaces trunk```** Podremos ver los trunk y su información:

```
Port        Mode         Encapsulation  Status        Native vlan
Gig0/1      on           802.1q         trunking      500

Port        Vlans allowed on trunk
Gig0/1      100,200,500

Port        Vlans allowed and active in management domain
Gig0/1      100,200

Port        Vlans in spanning tree forwarding state and not pruned
Gig0/1      100,200
```

( **Es buena práctiva que la VLAN nativa no sea la que trae por defecto el dispositivo.** )

Una vez realizado podriamos hacer ping entre dos maquinas de las mismas vlans pero conectados a sw distintos ya que se comunican a través del trunk.

##Securizar Puertos Switch

Nos vamos al interface que queremos securizar y escribimos lo siguiente:

Comando | Acción que realiza
---|---
S1(config)#interface fa0/3	| Entramos en la interface.
S1(config-if)#switchport port-security mac-address sticky | Le decimos que queremos poner seguridad por mac y que la aprenda de forma dinamica.
S1(config-if)#switchport port-security | Activamos el Port-Security
S1(config-if)#switchport port-security maximum 1 | Le decimos el máximo de direcciones MAC a aprender.
S1(config-if)#switchport port-security violation shutdown | Le decimos que queremos que haga cuando surja esa violación, en este caso apagar el puerto

Después de incluir los comandos si hacemos un **```sh r```** nos mostrará esto:

```
interface FastEthernet0/10
 switchport access vlan 100
 switchport mode access
 switchport port-security
 switchport port-security mac-address sticky 
```

Para que la interface aprenda la mac tiene que haber algun tipo de comunicación podemos hacer un ping o conectarnos a algún sitio en definitiva que tenga algun tipo de tráfico desde esa maquina a otra cualquiera para que aparezca la mac cuando hagamos un **```sh r```**

Una vez que aprenda la interfaz

```
interface FastEthernet0/10
 switchport access vlan 100
 switchport mode access
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security mac-address sticky 0002.4A16.2EA8     <---- Mac aprendida por sticky
```

Vamos a probar ahora la seguridad, quitamos el cable de red que une el pc actual con la boca fa0/10 del Switch y conectamos otro ordenador nuevo con otra dirección mac , en cuanto lo conectamos no pasa nada todas las conexiones estan en verde pero en cuanto hacemos un ping la conexión se cae tal y como habiamos configurado.

Si mostramos la información del interface nos dirá como está, para ello usamos el comando:

```bash
S1#sh interfaces fastEthernet 0/10
```
y podremos ver la línea donde aparece el error

```
FastEthernet0/10 is down, line protocol is down (err-disabled)
```
tambien podemos usar este comando para ver todas las interfaces que tienen errores o podemos cambiar err-disable por cualquier otro parámetro

```bash
S1#show interfaces | include err-disable
```
Para ver todas las interfaces y su estado

```bash
S1#show ip interface brief
```

Para ver todos los puertos con port-security habilitado

```bash
S1#show port-security
```
###Levantar el puerto o quitar seguridad.

Hay dos opciones si solo ha sido una caida por enchufar un dispositivo distinto y la interfaz va a seguir con el dispositivo aprendido anteriormente solo hay que apagar y volver a encender la interfaz.

Comando | Acción que realiza
---|---
S1(config)#interface fa0/10 |	Nos vamos a la interfaz con el puerto bloqueado.
S1(config-if)#shutdown 	| Apagamos la interfaz.
S1(config-if)#no shutdown | La levantamos otra vez.

Si en cambio la otra opción es que el dispositivo que estaba en esa interfaz se vaya a mover a otra ubicación o se elimina y se va a conectar otro con distinta mac en este caso hay que quitar el port-security para esa mac.

Para hacer esto tenemos que escribir el siguiente comando, con esto conseguimos eliminar la mac aprendida del interfaz seleccionado.

```bash
S1(config)#interface fa0/10
S1(config-if)#no switchport port-security mac-address sticky 0002.4A16.2EA8
S1(config-if)#shutdown
S1(config-if)#no shutdown
```
Para ver la mac aprendida en un interfaz en concreto:

```bash
S1#show running-config interface gigabitEthernet 0/8
```
Para ver el estado de todas las interfaces:

```bash
S1#show interfaces status
```

##Tabla ARP

Para ver la tabla de direcciones usamos el siguiente comando

```bash
S2#show mac-address-table 
```
La salida es la siguiente

```
          Mac Address Table
-------------------------------------------

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----

   1    0001.c9e9.d619    DYNAMIC     Gig0/1
 100    0060.47e4.734d    DYNAMIC     Gig0/1
 100    00e0.f9ed.4c29    STATIC      Fa0/10
 200    000d.bdb3.a851    DYNAMIC     Fa0/1
```
##CDP

Comando | Descripción 
---|---
sh cdp neighbors | Nos dá información de los eqipos conectados.
sh cdp entry | Nos proporciona mas informacion.
sh cdp interface | Muestra las interfaces con cdp activado del Switch.
sh cdp | Muestra informacion del tráfico 
no cdp run | Para deshabilitarlo de forma general en todo el switch
no cdp enable | Para deshabilitarlo desde una interfaz de red de forma individual

Cdp es un protocolo propietario de cisco que opera en la capa 2 y se utiliza para compartir información sobre los dispositivos conectados entre sí.

Si lo tenemos habilitado y ejecutamos el comando **```sh cdp neighbors```**veremos la información que nos ofrece.

```bash
S2#sh cdp neighbors 
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID
S1           Gig 0/1          130            S       2960        Gig 0/1
```


##VLAN

Comando | Descripción 
---|---
show flash | Muestra la memoria Flash
delete vlan.dat | Elimina el fichero de vlans

Las VLANS se almacenan en el archivo vlan.dat que está en la memoria flash

```bash
S2#show flash
Directory of flash:/

    1  -rw-     4414921          <no date>  c2960-lanbase-mz.122-25.FX.bin
    2  -rw-        1785          <no date>  config.text
    3  -rw-         676          <no date>  vlan.dat
```
##VTP

Comando | Descripción 
---|---
S1(config)#vtp domain cisco.com | Crea un dominio para VTP.
S1(config)#vtp mode server | Este Sw será el servidor VTP.
S1(config)#vtp mode client | Este Sw será el cliente VTP.
S1(config)#vtp mode transparent | Este Sw estará en modo transparente.
S1#show vtp status | Muestra la información de VTP.
S1#vtp pruning | Habilita VTP-Pruning en el dominio.

Es un protocolo que simplifica la administración de VLANS , permite crear, borrar y modificar desde un solo Switch.

VTP puede trabajar en 3 modos:

- **Servidor:** Es el que manda a los demás equipos del dominio la configuración de vlans, y el único sitio donde se pueden crear, modificar y borrar.
- **CLiente:** Son los que reciben la configuración y la aplican 
- **Transparente:** No participan como clientes pero si retransmiten configuraciones del servidor a los clientes si los hubiera , toda las vlans de este sw serían locales. ( Hacen de relé )

Para configurar VTP es necesario crear un trunk entre los switchs. Después habrá que configurar el VTP en cada uno de ellos de la siguiente forma, suponiendo que el esquema de red son 3 sw de izquierda a derecha:

- R1 : Servidor
- R2 : Transparente
- R3 : Cliente

```
Configuración VTP en R1
R1(config)#vtp domain cisco
Changing VTP domain name from NULL to cisco
R1(config)#vtp password seguro
Setting device VLAN database password to seguro
R1(config)#vtp mode server
Device mode already VTP SERVER.
```
```
Configuración VTP en R2
R2(config)#vtp domain cisco
Domain name already set to cisco.
R2(config)#vtp password seguro
Setting device VLAN database password to seguro
R2(config)#vtp mode transparent
Setting device to VTP TRANSPARENT mode.
```
```
Configuración VTP en R3
R3(config)#vtp domain cisco
Domain name already set to cisco.
R3(config)#vtp password seguro
Setting device VLAN database password to seguro
R3(config)#vtp mode client
Setting device to VTP CLIENT mode.
```
**Hay que tener en cuenta que aunque de esta forma se hace más cómodo la creacion de vlans es necesario acceder a los puertos específicos del sw para darles acceso a las vlans correspondientes**

###VTP Prunning

hace más eficiente el uso de trunks optimizando el tráfico entre ellos. Las tramas broadcast y unicast desconocidas en una VLAN son propagadas por un enlace Trunk solo si el switch vecino tiene configurado algún puerto en esa VLAN. Por defecto esta característica viene deshabilitada.


##InterVLAN Routing ( Router on Stick )

Permite el enrutamiento entre vlans usando un router para esta práctica partimos de 4 equipos 2 en una vlan 100 y otros 2 en una vlan 200 conectados a un sw ( Capa 2 ) y este sw a un router.

| Máquina | Comando | Descripción 
---|---|---
Switch | Switch(config)#vlan 100 | Creamos Vlan 100
Switch | Switch(config-vlan)#name Monos | Le ponemos un nombre
Switch | Switch(config)#vlan 200 | Creamos Vlan 200
Switch | Switch(config-vlan)#name Jirafas | Le ponemos nombre
Switch | Switch(config)#interface range fastEthernet 0/1-2 | Seleccionamos las 2 máquinas de la Vlan 100
Switch | Switch(config-if-range)#switchport mode access | Ponemos la interfaz en modo acceso
Switch | Switch(config-if-range)#switchport access vlan 100 | le asignamos la vlan
Switch | Switch(config)#interface range fastEthernet 0/3-4 | Seleccionamos las 2 máquinas de la Vlan 200
Switch | Switch(config-if-range)#switchport mode access | Ponemos la interfaz en modo acceso
Switch | Switch(config-if-range)#switchport access vlan 200 | le asignamos la vlan
Router | Router(config)#interface gigabitEthernet 0/0 | Seleccionamos la interfaz troncal con el SW
Router | Router(config-if)#no shutdown | Levantamos la interface
Router | Router(config-if)#interface giga0/0.100 | Creamos la Subinterfaz para la vlan 100
Router | Router(config-subif)#encapsulation dot1Q 100 | Le indicamos el tipo de encapsulamiento para la subnet
Router | Router(config-subif)#ip address 10.1.1.254 255.255.255.0 | Le asignamos una IP
Router | Router(config-if)#interface giga0/0.200 | Creamos la Subinterfaz para la vlan 200
Router | Router(config-subif)#encapsulation dot1Q 200 | Le indicamos el tipo de encapsulamiento para la subnet
Router | Router(config-subif)#ip address 10.2.1.254 255.255.255.0 | Le asignamos una IP
Equipos| Asignamos Direccionamiento IP |10.1.1.x para VLAN 100
Equipos| Asignamos Direccionamiento IP |10.2.1.x para VLAN 200
Equipos| Asignamos Puerta de Enlace  |10.1.1.254 para VLAN 100
Equipos| Asignamos Puerta de Enlace  |10.2.1.254 para VLAN 200
Router | Router#show ip interface brief | Miramos la configuración de los Interfaces
Router | Router#show ip route | Se muestran las rutas

De esta manera las dos vlan pueden comunicarse entre ellas a tráves del Router

[archivo de práctiva: intervlan routing.pkt]()

###SVI (Switching vlan interface)

Permite el enrutamiento entre vlans distintas usando un SW de capa 3 ya que tiene capacidad de enrutar, para está práctica seguimos los siguientes pasos. Partiendo del esquema de la práctica de intervlan routing. El Sw a utilizar en este caso en PACKET TRACER es C3560-24P ya que es el único de capa 3.

| Máquina | Comando | Descripción 
---|---|---
Switch | Switch(config)#vlan 100 | Creamos Vlan 100
Switch | Switch(config-vlan)#name Monos | Le ponemos un nombre
Switch | Switch(config)#vlan 200 | Creamos Vlan 200
Switch | Switch(config-vlan)#name Jirafas | Le ponemos nombre
Switch | Switch(config)#interface range fastEthernet 0/1-2 | Seleccionamos las 2 máquinas de la Vlan 100
Switch | Switch(config-if-range)#switchport mode access | Ponemos la interfaz en modo acceso
Switch | Switch(config-if-range)#switchport access vlan 100 | le asignamos la vlan
Switch | Switch(config)#interface range fastEthernet 0/3-4 | Seleccionamos las 2 máquinas de la Vlan 200
Switch | Switch(config)#interface vlan 100 | Levantamos el interfac vlan 100
Switch | Switch(config-if)#ip address 10.1.1.254 255.255.255.0 | Ponemos ip a la interfaz vlan 100
Switch | Switch(config)#interface vlan 200 | Levantamos el interfac vlan 200
Switch | Switch(config-if)#ip address 10.2.1.254 255.255.255.0 | Ponemos ip a la interfaz vlan 200
Switch | Switch(config)#ip routing | Activamos el Routing ( SOLO SW CAPA 3 )
Equipos| Asignamos Direccionamiento IP |10.1.1.x para VLAN 100
Equipos| Asignamos Direccionamiento IP |10.2.1.x para VLAN 200
Equipos| Asignamos Puerta de Enlace  |10.1.1.254 para VLAN 100
Equipos| Asignamos Puerta de Enlace  |10.2.1.254 para VLAN 200
Switch | Switch#show ip interface brief | Miramos la configuración de los Interfaces
Switch | Switch#show ip route | Se muestran las rutas

De esta manera las dos vlan pueden comunicarse entre ellas a tráves del Switch

[archivo de práctiva: intervlan SVI.pkt]()

##SPAN ( Switch Port Analizer )

Permite analizar el tráfico de los puertos de un switch para ser analizados por software se pueden monitorizar tanto puertos como una vlan específica.

Partiendo de la base de que tenemos los siguientes elementos

- 1 PC CONECTADO A LA BOCA FA/01
- 1 SERVER CONECTADO A LA BOCA FA0/2
- 1 SNNIFER CONECTADO A LA BOCA FA0/3

Podemos tener varias sesiones con distintas conexiones es una forma de tener varias tareas simultaneas.

Comando | Descripción 
---|---
Switch(config)#monitor session 1 source interface fastEthernet 0/1 | Seleccionamos la boca origen
Switch(config)#monitor session 1 source interface fastEthernet 0/2 | Seleccionamos la boca origen
Switch(config)#monitor session 1 destination interface fastEthernet 0/3 | Seleccionamos la boca destino
Switch(config)#do show monitor session 1 | Vemos el estado de la sesion 1

##STACKWISE

Capacidad que tienen los switchs CISCO propietaria a través de un cable específico de apilarlos conectarlos y usarlos como uno solo manejando todo desde uno que es el master algunos comandos interesantes para poder ver la configuración del stack

Comando | Descripción 
---|---
show switch stack-ports | muestra el estado de las conexiones del stack
show switch neighbors | Ver los switchs vecinos que componen el stack
show switch | Informacion de los switchs

##VLSM ( Variable Lenght Subnet Mask )

Poner imagenes aquí

##Enrutamiento
Archivo de Prácticas --> Rutas_Estáticas.pkt
Archivo de Prácticas EIGRP --> EIGRP.pkt

Para enrutar se necesitan equipos de capa 3 por ejmplo un Router o un Switch(capa 3) no todos lo son:

Conceptos

- Dirección de red
- Mascara de red 
- Next Hop --> Próximo salto a realizar
- Metrica --> Valor usado por los protocolos de enrutamiento para determinar la mejor ruta.

Las rutas se ven en las tablas ARP de los dispositivos o hosts

Tipos de rutas:

- Connected ( Conectadas Directamente )

Se crean directamente al conectar fisicamente los dispositivos al router y poniendo una dirección ip al interfaz.

Para ver la tabla de enrutamiento en el Router (Ejemplo de sh ip route sin ninguna ruta estática definida)

```bash 
Router#sh ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C       10.1.1.0/30 is directly connected, GigabitEthernet0/0
L       10.1.1.2/32 is directly connected, GigabitEthernet0/0
     172.16.0.0/16 is variably subnetted, 2 subnets, 2 masks
C       172.16.1.0/24 is directly connected, GigabitEthernet0/1
L       172.16.1.254/32 is directly connected, GigabitEthernet0/1
```

- Static (Definidas manualmente )

Se crean manualmente en los enrutadores

```bash
router(config)# ip route [red destino][mascara de red destino][next hop]
router(config)# ip route [red destino][mascara de red destino][interfaz de salida]
router(config)# 192.168.1.0 255.255.255.0 10.1.1.1
router(config)# 192.168.1.0 255.255.255.0 gi0/0
```
Se pueden configurar con la dirección del siguiente salto o con la interfaz directamente.
	
	
Ejemplo de ruta estática configurada en el router:

```bash
R2#show ip route

     10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C       10.1.1.0/30 is directly connected, GigabitEthernet0/0
L       10.1.1.2/32 is directly connected, GigabitEthernet0/0
     172.16.0.0/16 is variably subnetted, 2 subnets, 2 masks
C       172.16.1.0/24 is directly connected, GigabitEthernet0/1
L       172.16.1.254/32 is directly connected, GigabitEthernet0/1
S    192.168.1.0/24 [1/0] via 10.1.1.1

```

Comandos de Verificación:

- router#show ip route
- router#show ip route static
- router#show running-config | include ip route

IMPORTANTE : Hay que tener en cuenta que si se hace con routers hay que hacer la misma configuración en los dos extremos para que pueda haber conexión. y que los interfaces a conectar deben tener asignadas ips válidas.


- Dynamic EIGRP ( Aprendidas Dinamicamente por un protocolo de enrutamiento )

Ejemplos de protocolos de enrutamiento: EIGRP , OSPF, BGP.

Para usar EIGRP los routers tienen que estar en un mismo sistema autónomo, estos son algunos de los comandos necesarios para configurar EIGRP en el router.

Comando | Descripción 
---|---
R1(config)#router eigrp <sistema autónomo> | Habilita el protocolo de enrutamiento, seguido de un sistema autónomo que debe ser el mismo para los demás routers. Puede ir de 1 hasta 65535.
R1(config-router)#network [direccion de red] | Se configuran las direcciones de las redes DIRECTAMENTE conectadas que serán anunciadas por EIGRP
R1(config-router)#no auto-summary | Evita que se resuman las rutas (sumarización) de redes discontinuas.
R1(config-if)#bandwidth | En la interfaz se configura el ancho de banda real.
R1(config-router)#passive-interface <tipo><numero> | Evita que una interfaz envíe publicaciones.
R1#show ip route | Muestra la tabla de enrutamiento
R1#show ip protocols | Muestra los parámetros del protocolo
R1#show ip eigrp neighbors | Muestra la información de los vecinos de eigrp
R1#show ip eigrp topology | muestra la tabla de topología
R1#debug ip eigrp | Muestra en tiempo real la información de los paquetes EIGRP

Proceso de configuración de 3 Routers --> Mirar práctica packet tracer EIGRP

```
R1(config)#router eigrp 100
R1(config-router)#network 192.168.1.0 0.0.0.255
R1(config-router)#network 10.1.1.0 0.0.0.3
R1(config-router)#no auto-summary 
R1(config-router)#

R2(config)#router eigrp 100
R2(config-router)#network 172.16.1.0 0.0.0.255
R2(config-router)#network 10.1.1.0 0.0.0.3
R2(config-router)#
%DUAL-5-NBRCHANGE: IP-EIGRP 100: Neighbor 10.1.1.1 (Serial0/0/0) is up: new adjacency
R2(config-router)#no auto-summary 

R3(config)#router eigrp 100
R3(config-router)#net
R3(config-router)#network 192.168.2.0 0.0.0.255
R3(config-router)#ne
R3(config-router)#net
R3(config-router)#network 10.1.1.4 0.0.0.3
R3(config-router)#no auto
R3(config-router)#no auto-summary 

R1(config)#router eigrp 100
R1(config-router)#network 10.1.1.4 0.0.0.3
%DUAL-5-NBRCHANGE: IP-EIGRP 100: Neighbor 10.1.1.5 (Serial0/0/1) is up: new adjacency
```

- Dynamic OSPF ( Aprendidas Dinamicamente por un protocolo de enrutamiento )


Comando | Descripción 
---|---
show ip ospf neighbor | Lista de routers vecinos con que se estableció comunicación bidireccional.
show ip ospg database | Es la base de datos de los Link State (LSDB) lista con la información de todos los router en la red y muestra la topología de la red.
Router(config)#router ospf <id del proceso> | Habilita OSPF y define ID del proceso va de 1 a 65535 no debe de ser igual necesariamente que el de otros routers OSPF.
Router(config-router)#network <dirección de red><máscara wilcard><área> | La dirección de red, la mascara de red en formato wildcard y el ID del área, (El área OSPF es un grupo de routers que comparten información sobre el estado de enlace).

- Dynamic OSPF v3 ( Aprendidas Dinamicamente por un protocolo de enrutamiento , diseñado para ipv6)

OSPF v2 y v3 se pueden usar en el mismo equipo.

Comando | Descripción 
---|---
R1(confif)#ipv6 unicast-routing | Habilita IPV6 unicast forwarding
R1(config)#interface gi0/0 | Ingresamos a la interfaz
R1(config-if)ospfv3 <process-id> area <area> | Habilita OSPFv3 en la interfaz
R1(config)#ipv6 router ospf<process-id>	|Ingrese al modo de router configuration mode . En el modo de configuración global.
R1(config-router)#router-id <ip-ad> |configura el router-ID que usara OSPFv3 requerido.


##HLDC
Protocolo de comunicación usado en WAN
es la que viene por defecto para los enlaces serie y es propietaria de cisco.

Comando | Descripción 
---|---
R1(config)# interface serial 0/0/0 | Ingresa a la interfaz
R1(config-if)#encapsulation HDLC |Configura HDLC con el protocolo WAN de capa 2
R1# show interface serial 0/0/0 | Muestra información general de la interfaz entre ella la encapsulación.

##PPP

Protocolo de comunicación estándar.
Soporta autenticación PAP y CHAP
Contiene 2 sub-protocolos

 - Link Control Protocol (LCP)
 - Network Control Protocol (NCP)

Comando | Descripción 
---|---
R1(config)# interface serial 0/0/0 | Ingresa a la interfaz
R1(config-if)#encapsulation PPP | Configura PPP con el protocolo WAN de capa 2
R1# show interface serial 0/0/0 | Muestra información general de la interfaz entre ella la encapsulación.

##PAP

Password Autentication Protocol
Se envía en texto plano el usuario y el password.

Comando | Descripción 
---|---
R1(config-if)#ppp authentication PAP | Habilita la autenticación PAP
R2(config-if)#ppp authentication PAP | Habilita la autenticación PAP
R1(config)#username MX password cisco | Se debe configurar el username y password REMOTOS
R2(config)#username CR password cisco | Se debe configurar el username y password REMOTOS
R1(config-if)#ppp sent-username MC password cisco | Se debe configurar esta opción con los datos LOCALES
R2(config-if)#ppp sent-username CR password cisco | Se debe configurar esta opción con los datos LOCALES

##CHAP

Challenge Handshake Authentication Protocol usando 3 way handshake 
Se envía los datos de autenticación de manera cifrada

Comando | Descripción 
---|---
router(config)#interface serial 0/0/0 | Ingresamos a la interfaz
router(config-if)#ppp authentication CHAP | Habilitamos la autenticación CHAP
R1(config)#username R2 password cisco | Se debe configurar el username y password con el HOSTNAME REMOTO
R2(config)#username R1 password cisco | Se debe configurar el username y password con el HOSTNAME REMOTO
router#debug ppp authentication | información en tiempo real de la autenticación.

##FRAME RELAY

Tecnología de transmisión y encapsulación de tramas que trabaja en capa 1 y 2
La conexión a través de la red de Frame Relay entre dos DTEs es llamada circuito virtual (VC), estos pueden ser dinamicos a través de SVCs (circuitos virtuales comnmutados) o estáticos configurados por el operador PVCs (Circuitos virtuales permanentes).
Cada Circuito virtual es identificado por un codigo DLCI ( Data link Channel Identifier ).

- Funcionan en CAPA OSI 2
- Rango entre 0 y 1023. De 0-15 y de 1007 a 1023 están reservados.

CIR Committed Information Rate : es la tasa de transferencia que el proveedor del servicio garantiza.
Control de flujo:
- Forward ECN: bit que se activa, cuando hay congestión en la trama formward
- Backward ECN: bit que se activa cuando hay congestión en el sentido opuesto a la transmisión

Local Management Interface (LMI): Usado entre los routers y el switch de frame relay que permite a los DTEs adquirir dinámicamente información de la red.
- Tipos de LMI ( cisco / Ansi / q933a )
QOS ( Calidad de servicio): Habilidad de los equipso para ofrecer mayor prioridad a un tipo de tráfico determinado. Para llevarlo a cabo necesitamos clasificar el tráfico , despues crear una política y por último aplicarla.

Ejemplos:

Clasificación del tráfico:

```
R1(config)# class-map match-any critico
R1(config-cmap)#match interface fastethernet 0/1 --> Cualquier tráfico que ingrese a esa interfaz se denomina critico.
```
Creamos política del tráfico:

```
R1(config)#policy-map policy1
R1(config-pmap)#class critico
R1(config-pmap-c)#bandwidth 5000
```

Aplicamos la política a la interfaz

```
R1(config)#interface gigaethernet 0/1
R1(config-if)#service-policy output policy1
```



**VAMOS POR AQUI**
[https://www.udemy.com/redes-con-equipos-cisco-ccna-200-120/learn/v4/t/lecture/702896?start=0]()


Fuentes

* [http://hash.online-convert.com/es/generador-md5]()
* [http://www.blackploit.com/]()
* [http://finder.insidepro.com/]()
* [https://enredandoconredes.com/2012/03/18/password-cracking/]()




[^NVRAM]: NVRAM: (Non-volatile random access memory) es un tipo de memoria de acceso aleatorio que, como su nombre indica, no pierde la información almacenada al cortar la alimentación eléctrica.
[^RAM]: RAM: (Random Access Memory, RAM) se utiliza como memoria de trabajo y cuando se apaga la máquina pierde todo su contenido.
