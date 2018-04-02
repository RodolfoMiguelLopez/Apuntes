##Crear un etherchannel##

###Que es un etherchannel###

EtherChannel permite que múltiples enlaces Fast Ethernet físicos se combinen en un solo canal lógico. Esto permite compartir la carga del tráfico entre los enlaces en el canal, así como la redundancia en el caso de que fallen uno o más enlaces en el canal.EtherChannel se puede utilizar para interconectar switches LAN, enrutadores, servidores y clientes mediante cableado de par trenzado sin blindaje (UTP) o fibra monomodo y multimodo.

EtherChannel proporciona velocidades de troncales incrementales entre Fast Ethernet, Gigabit Ethernet y 10 Gigabit Ethernet. EtherChannel combina múltiples Fast Ethernet hasta 800Mbps, Gigabit Ethernet hasta 8Gbps y 10 Gigabit Ethernet hasta 80Gbps.

Para crear un Etherchannel primero creamos la interfaz lógica parecido a una vlan y le asignamos un número.

```
interface port-channel 15
```
y le ponemos la misma configuración de un trunk

```
switchport mode trunk
switchport dot1q (no en todos los sw está disponible)
switchport allow vlan .....
```
Es conveniente que los interfaces que vayamos a configurar para que sean parte del trunk estén configuradas con los datos del trunk anque funcionen a través del port-channel

para hacer que las interfaces sean parte del port-channel , hay que configurar cada una y metemos el siguiente comando.

```
channel-group 15 mode on
```
una vez echo esto esa interfaz ahora es parte del portchannel , para ver la configuración del port-channel y sus detalles.

```
show etherchannel
```
y nos dará más información del enlace y de los puertos que forman parte de él.

Sigo con la duda de si el etherchannel agrupa los puertos, sumando sus capacidades o solo agrupa los puertos para tener varios caminos por los que discurrir, sería interesante hacer una prueba de velocidad para ver como se comporta.



- https://www.cisco.com/c/en/us/support/docs/lan-switching/etherchannel/12023-4.html?dtid=osscdc000283
- https://www.cisco.com/c/en/us/tech/lan-switching/etherchannel/index.html?dtid=osscdc000283
- http://www.dummies.com/programming/networking/cisco/etherchannel-configuration/
- https://es.wikipedia.org/wiki/EtherChannel
- 