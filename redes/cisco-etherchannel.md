# Cisco EtherChannel

## Índice

- [¿Qué es un EtherChannel?](#qué-es-un-etherchannel)
- [Configuración](#configuración)
- [Verificación](#verificación)
- [Referencias](#referencias)

---

## ¿Qué es un EtherChannel?

EtherChannel permite que múltiples enlaces Fast Ethernet físicos se combinen en un solo canal lógico. Esto permite compartir la carga del tráfico entre los enlaces en el canal, así como la redundancia en el caso de que fallen uno o más enlaces en el canal. EtherChannel se puede utilizar para interconectar switches LAN, enrutadores, servidores y clientes mediante cableado de par trenzado sin blindaje (UTP) o fibra monomodo y multimodo.

EtherChannel proporciona velocidades de troncales incrementales entre Fast Ethernet, Gigabit Ethernet y 10 Gigabit Ethernet. EtherChannel combina múltiples Fast Ethernet hasta 800Mbps, Gigabit Ethernet hasta 8Gbps y 10 Gigabit Ethernet hasta 80Gbps.

---

## Configuración

Para crear un EtherChannel, primero creamos la interfaz lógica y le asignamos un número:

```
interface port-channel 15
```

Le ponemos la misma configuración de un trunk:

```
switchport mode trunk
switchport dot1q (no en todos los sw está disponible)
switchport allow vlan .....
```

> Es conveniente que los interfaces que vayamos a configurar para que sean parte del trunk estén configurados con los datos del trunk aunque funcionen a través del port-channel.

Para hacer que las interfaces sean parte del port-channel, hay que configurar cada una y añadir el siguiente comando:

```
channel-group 15 mode on
```

Una vez hecho esto, esa interfaz es parte del portchannel.

---

## Verificación

Para ver la configuración del port-channel y sus detalles:

```
show etherchannel
```

Este comando nos dará más información del enlace y de los puertos que forman parte de él.

---

## Referencias

- https://www.cisco.com/c/en/us/support/docs/lan-switching/etherchannel/12023-4.html
- https://www.cisco.com/c/en/us/tech/lan-switching/etherchannel/index.html
- http://www.dummies.com/programming/networking/cisco/etherchannel-configuration/
- https://es.wikipedia.org/wiki/EtherChannel
