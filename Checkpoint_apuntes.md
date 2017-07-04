#formación checkpoint 27/03/17 INICIO

pass: vpn123

Management Requisitos minimos

* 2 cores
* 3 gigas de ram

**particionado Root35GB/Logs70GB/ ( el valor de espacio para root no se puede cambiar después es importante darle espacio al principio)**

para el gw01 y gw02

* 2 cores
* 1.5gigas

```
Clave de registro para VMware12 Workstations WINDOWS
5a02h-au243-tzj49-gtc7k-3c61n
```
Configuración de red laboratorio

- vmnet1 host-only    192.168.100.0        red de gestion
- vmnet8 NAT        192.168.200.0        red usuarios

###Modos de Despliegue

- Standalone 
mgmt+gw ( En la misma maquina )
- Distributed
mgmt <--->gw ( En diferentes máquinas )

**Cuando se crea el Cluster se crea en la misma interfaz una interfaz virtual con la ip del cluster que es a la que apuntarán todos los equipos de la red.**

- 192.168.100.100 Mng
- 192.168.100.111 gt01
- 192.168.100.112 gt02
- 192.168.200.100 virtual ( para los usuarios )

###Diferentes tipos de cluster

####Activo / Pasivo

- Cluster XL ( propietario checkpint)---------------lo mas recomendable y habitual
- VRRP        ( Estándar ) mas pensado para routers

####Activo / Activo

Cluster XL
- Unicast
- Multicast

.|.
---|---
|ATRG |Advanced Troubleshooting Reference Guide|
CCP| Cluster Control Protocol ( Protocolo comunicación entre cluster )
Pueden hacerlo por Multicast ( con IGMP o SIN IGMP ) o por Broadcast

comando: cphaconf set_ccp ( Broadcast o Multicast )

IGMP snooping ( SWITCHES ) --> MIRAR que es esto

Para desconectar uno de los equipos de un cluster o hacer un failover se utiliza el siguiente comando en la máquina que queremos desconectar:

```
clusterXL_admin down ( para levantarla lo mismo pero terminado en up )
```
para poder hacerlo es necesario tener usuario de modo expert para hacerlo se usa el siguiente comando

```
set expert-password y seguir los pasos 
```
para ver el estado del cluster hay que usar el comando:

```bash
cphaprob state
```
para ver la politica instalada: 

```
fw stat
```
Cluster XL por defecto no monitoriza todas las VLANS

CPuse se puede usar en modo CLI o GUI Online y Offline

Para actualizar el cluster hay que actualizar primero el pasivo forzar un failover y actualizar y despues hacer lo contrario.

comando para ver las actualizaciones jumbo en el gt: 

```
installed_jumbo_take
```
para desarmar el cluster y romper la relación de confianza de los 2 clusteres se usa el comando cpconfig y se marca la opción 5 en los dos gateways con esto volvemos a tener dos gt por separado:

fw monitor : para poder ver todo lo que está pasando por el fw y saber que reglas está aplicando.
tcp dum : parecido a fw monitor pero menos potente

###BACKUPS

Para hacer una copia de reglas de la management se usan las **upgrade_tools**
espán en la ruta del management. 

```
$FWDIR/bin/upgrade_tools
```

la sintaxis es ./migrate export /home/admin/nombre fichero para guardar
para migrate import es lo mismo al reves

para poder reinstalar una a una nueva máquina el HOSTNAME y la IP tienen que se la misma.

Database revision control ( es otra forma de llevar un control de cambios ) crea puntos de restauración

BACKUP y SNAPSHOTS se hacen antes de hacer grandes cambios migrate es conveniente hacerlo cada mes.
 
formación checkpoint 27/03/17 FIN

APUNTES de las Primeras jornadas.

Security Management: Gestión 
Console Smart : Consola
Security Gateway: Firewalls
Software BLADES: Diferentes Módulos de seguridad

ISOMORPHIC : Se usa para plataformar el appliance a través del puerto USB es recomendable para instalaciones desde cero tambien es recomendable pero no obligatorio la instalación de los JUMBO Fixes el último.

Artículo para eliminar el default admin SK112163

CLUSTER XL , SECURE XL y COREXL --> Se usa para la aceleración y asignación de firewall workers a los diferentes nucleos del sistema.

SmartUpdate te sirve para agregar las licencias que descargas del ControlCenter con el archivo .lic
para agregar la licencia al gt hay que hacer click derecho sobre el gt y darle a attach license.

comandos para asignar fireworkers: fw ctl affinity -l -v -r 
menu de comandos para activar CoreXL: cpconfig

cpview -t on ( revisar creo que es para guardar historial de recursos en la consola)
asignar firewallworkers sim affinity -l

fw unload local : para quitar todas las políticas
interfaces: sim affinity -s
save config : para salvar la configuración en modo CLI
buenas prácticas tener la interfaz de SYN ( Sincronismo entre gtw ) en una CPU independiente.

Secure SL 
Ver estado si esta acelerado o no : fwaccel stat
ver tráfico acelerado : fwaccel stats -s
CoreXL Dynamic Dispacher
Sirve para repartir la carga entre cores 
fw ctl multik stat --> para ver el estado.

Para que las ips internas pueden salir y volver a entrar a través del vmware hay que activar la casilla NAT en el gt 
hide internal networks behind the gateways external IP
