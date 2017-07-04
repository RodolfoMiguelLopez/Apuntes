


# Apuntes Fundamentos de redes para el examen 98 - 366 MTA de Microsoft.

**Definicíon de red: Dos o más computadora que intercambian información.**


¿ Cuales son las razones por las que se necesitan redes ?

* Para compartir
* Para Comunicarse
* Por Organización
* Por Costes

**Es múy útil documentar las redes , escribir su estructura tanto desde una visión lógica como física.**

Términos | Significado
---|---
Broadcasting | Significa que la información es enviada a cada host en la red, entonces solo el receptor de destino se queda con la información, el resto la descarta.
Unicast| Describe la situación en la cual la información se envía a un solo host.
Multicast | **RELLENAR AQUI**
Tasa de transferencia de datos o tasa de bits| Máximo de (bps) bits por segundo que pueden ser transmitidos por la red.
Hub| Es el dispositivo más básico de conexión, conecta cada una de las computadoras de la red, conocidas como host, por medio de cables de cobre.
Switch|Conecta múltiples tramos de una red, fusionandolos en una sola red, solo retransmiten la información hacia los tramos en los que hay un destinatario.
Router o SOHO ( Small Office, Home Office)|Actúa como un dispositivo central de conexión pero tambien tiene un enlace de comunicaciones especial a internet.
Adaptador de red ( Network Interface Card )| Tarjeta de interfaz de red o NIC es el dispositivo que le permite enviar y recibir información hacia y desde su ordenador, puede estar integrada en placa o en un puerto PCI/USB de forma física o inalámbrica, tiene su propia CPU y ROM.
Rj45 o 8P8C|Es la interfaz física comunmente utilizada para conectar redes con cableado estructurado. [+info](https://es.wikipedia.org/wiki/RJ-45)
Full Duplex|Este tipo de velocidad significa que el adaptador de red puede enviar y recibir información simultaneamente.
Half Duplex|Este tipo de velocidad significa que el adaptador de red enviará y recibirá información pero no al mismo tiempo.

Cuando la información es transferida en una LAN se envía de forma **serial** significa que se envía 1 sola cadena de bits a la vez.

###Dirección IP
Permite a cada computadora enviar y recibir información de un lado a otro de una manera ordenada y eficiente.
Cada dirección IP se divide en 2 pares: 192.168.1.1

* la porción de red: 192.168.1
* la porción de host: 1

para saber cual es el host usamos la mascada de subred, que define de cual es el host.

* Todos los 255 se refieren a la porción de red.
* Todos los 0 se refieren a la porción de host.

192.168.0.1
255.255.255.0

**Cada host en una red necesita tener una ip diferente para que no haya un conflicto de ip.**

Las direcciones ip son números de punto decimal de 32bits, cada dirección ip contiene 4 números, cada uno de los cuales es un byte o un octeto.

|Tipo de numero | Equivalente|
---|---
Para una dirección ip | 201.161.1.226
Decimal con puntos|201.161.1.226
Hexadecimal con puntos|0xC9.0xA1.0x01.0xE2
Octal  con puntos|0311.0241.0001.0342
Binario con puntos|11001001.10100001.00000001.11100010 = 32 bits

El hecho de que un dispositivo tenga una ip es lo que lo hace un host.

Comandos |Funcion
---|---
ipconfig|Comando para ver la configuración de red.
ping|Comando para comprobar la conectividad de la red

Localhost:

