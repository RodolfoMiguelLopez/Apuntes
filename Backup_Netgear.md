##Backup Switch NetGear M4100-26G

Backup Imagenes y archivo de configuración desde Consola, previamente hay que habilitar ssh y crear los certificados:

###Accediendo por HTTP activamos las siguientes opciones:

- Security / Access / SSH / 
- Host Keys Management
	- RSA Keys Management --> Generate RSA Keys --> ```Apply```
	- DSA Keys Management --> Generate DSA Keys --> ```Apply```
- SSH Configuration 
	- SSH Admin Mode	--> Enable

###Acceso por consola

Una vez conectado con la ip correspondiente nos preguntará si queremos aceptar la llave RSA a nuestros Hosts Conocidos

```
The authenticity of host '192.168.x.x (192.168.x.x)' can't be established.
RSA key fingerprint is SHA256:53I3RWeTl389d7snCsXzSQTqlpIpDOs1NzeSrjCg3j4.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.100.7' (RSA) to the list of known hosts.
```
Una vez aceptado nos saldrá el prompt

```
(SWCOBAula_2) >
```

Accedemos al modo privilegiado

```
(SWCOBAula_2) >enable
```
Iniciaremos un servidor tftp en una máquina accesible desde el Switch
para hacer la copia de seguridad de las imagenes usaremos el siguiente comando:

```
(SWCOBAula_2) #copy image1 tftp://192.168.x.x/image1

Mode........................................... TFTP
Set Server IP.................................. 192.168.x.x
Path........................................... ./
Filename....................................... image1
Data Type...................................... Code

Management access will be blocked for the duration of the transfer
Are you sure you want to start? (y/n) y
TFTP Code transfer starting...
File transfer operation completed successfully.
```
Nos preguntará si queremos empezar la transferencia y nos informa de que la terminal estará bloqueada durante el proceso. Una vez aceptado con ```y``` empezará el envío del archivo al servidor tftp.

los archivos de los que podemos hacer copia son los siguientes

```
(SWCOBAula_2) #copy ?
image1
image2
nvram:backup-config
nvram:clibanner
nvram:cpu-pkt-capture.pcap
nvram:errorlog
nvram:factory-defaults
nvram:log 
nvram:script
nvram:startup-config
nvram:tech-support 
nvram:traplog
system:running-config
```
Para hacer la copia de seguridad de configuración es suficiente con el archivo ```nvram:startup-config```

Resumen de comandos para hacer una copia completa

* ```copy image1 tftp://192.168.x.x/image1```
* ```copy image1 tftp://192.168.x.x/image2```
* ```copy nvram:startup-config tftp://192.168.x.x/startup-config```
