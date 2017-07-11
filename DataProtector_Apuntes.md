#Apuntes Curso Dataprotector

Protección LAN/WAN/SAN

Tipos de BACKUP

- Direct Attached backup
- Network backup
- SAN attached backup
- Array based replica backup(zero downtime backup)

Entorno catalyst (hp) Tecnología de Desduplicación

Cell Manager (servidor central de la app) solo podemos tener 1 por entorno
  - windows a partir de 2008 / linux / hpx
  - Se instala localmente no se puede instalar por red
  - No existen guías STIC para securizar
  - Para parar los servicios se puede hacer por terminal (onmisv -start/-stop/-stat)
  - Recomendable un Full Backup de la base de datos de la Cell Manager (Diario)
  - Los ficheros de configuración de data protector están en texto plano
    Ficheros de configuración del CELL MANAGER
    - Global
    - OmNIrc
    
Installation server (servidor repositorio) Es opcional pero conveniente para desplegar actualizaciones.
DP user interface (consola de dataprotector) solo para windows
  - Incluye Comandos CLI
 - Hay reportes básicos dentro de User interface 
 - Web Reporting Interface (Informes avanzados) **SON DE PAGO**
 
Cell client ( Clientes con agentes instalados)
Disk Agent ( Agente para los clientes) tambien se puede instalar en el cell manager backup a nivel de ficheros
  - Usa puertos dinámicos pero se pueden acotar
    - Port Range
  - Usa Volume Shadow Copy para hacer las copias en caliente si no queremos usarlo el problema es que los archivos abiertos no podrá hacer copia.
Media agent ( Agente para mandar los datos (Los que vengan del Disk Agent) a la librería correspondiente por ejemplo Cinta)
  - instalación Remota o local
  - Este servidor tiene que ser físico no puede ser virtual.
Integration Agent ( De entorno )
- APIS de integración
- La ventaja es que no tenemos que parar los servidores para hacer las copias.
  ( se recomienda hacer un backup Offline)
- Matriz de compatibilidad de versiones de software
Installation server
- Repositorio de software para los programas de dataprotector
Los procesos se pueden secuenciar para que no todas las tareas funcionen a la vez

El uso de licencias es concurrente, si se utiliza secuencialmente los Integration Agent van a funcionar sin problema. No es necesario tener muchas licencias.

- Granular Recovery Extensión Agent ( Recuperaciones Granulares ) **DE PAGO**
Es recomendable hacer un EXPORT de la base de datos a fichero (por si acaso falla el programa de backup)

IDB ( La base de datos del cell manager)
- no requiere mantenimiento
- Se pueden encriptar comunicaciones con el media agent
- se pueden encriptar los backups con algoritmo simple ( Gratis ) algoritmo mas complejos ( de pago )

Rutas de configuración de Data Protector
- dp_home
- dp_config
- dp_var
Ficheros configuración 
- DP tuning via global file
  Hay que reiniciar servicios una vez modificado
- DP tuning via omnirc file
  variables a nivel local
  no requiere reinicio de ningun servicio
  
  #Instalación
  
  Cell Manager (Obligatorio)
  Installation Server (Opcional)
  
  Product Documentation ( dentro del cell manager o del user interface carpeta docs)
  
  Requerimientos de hardware
  
  Cell manager  4gb 1,5gb+idb
  installation server   512mb 2gb
  
  DP 9.00 Cell Manager Procesos
  
  5555 puerto de comunicación con el cell manager
  la conexión debe de estar configurada como Outbonf connection are allowed
  
  para borrar un cliente --> export of clients ( opcionalmente se puede eliminar el cliente)
  
  LICENCIAMIENTO (funciona solo en el cell manager con la ip que digamos si la ip cambia hay que avisar)
  
  - Instant-On (30Dias) Primera instalación
  - Permanent
  - Emergency (Para probar apps)
  
  omnicc ( por CLI )
  
  POhysical devices in data protector
  
  device type  | physical medium
  Standalone | Disk Tape
  Backup to disk | disk
  Stacker | Tape
  SCSI library | disk tape
  Jukebox | disk MD
  File Library | disk ( es licenciado por teras9
  External control | tape
  StorageTeck ACS library | tape
  
Device tools (herramienta de diagnosis de librerías) se utiliza para buscar problemas, actualizar firmware, test.
Media Pools (Agrupación de cintas) no tiene porque tener cintas asignadas puede haber un (freepool) desde el cual van rotando las cintas
por todos los pools a medida que sean necesarias.
politicas del pool:
 - media allocation policy : appendable y loose 
Condiciones de uso de la cinta
- 36 meses  | Máximos aceptables 96 Meses
- 250 sobreescrituras | Máximos aceptables 500 sobreescrituras
- Colores 
  - verde : Buena 
  - Amarillo : regular
  - Roja: Mala (segun las condiciones) no hace backup con esta cinta pero si se restaura.
para cambiar los estados de las cintas se puede usar el siguiente comando

omnimm -reset_poor_medium_id (el medium_id lo sacamos de la cinta)
verify (para comprobar la idoneidad de la cinta)
formatear cinta ( ultimo intento para recuperar cinta)
Recycle --> para quitar la protección
  
Los parámetros de almacenamiento en la cinta se pueden parametrar depende de las cintas a usar para mejorar el rendimiento.  
Las etiquetas de las cintas no son necesarias pero son utiles para el trabajo del administrador de backup

Location tracking and priority
localización de la ubicación de las cintas, armario ignifugo , en movimiento, ubicacion alternativa.

----------------------------Dia 2

BACKUP

L   M   X   J   V   S   D
FULL + INCREMENTAL + INCREMENTAL ..... --> Se puede consolidar y hacer un full de todo esto se llama un Backup sintético
hay incrementales 1,2,3,4 (no se suelen usar normalmente)

![Explicación niveles Incrementales](https://docs.oracle.com/cd/B19306_01/backup.102/b14234/img/obadm019.gif)




omnitrig: para gestionar las planificaciones es como el cron de linux


  
  


















http://es.dumpblaster.com/Certification-HPE.html
  
  
  
  
  
  
