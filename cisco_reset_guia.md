##Reseteo contraseña en switch catalyst 2950 

Para resetear la contraseña hay que seguir los siguientes pasos

- iniciar el sw con el boton mode pulsado 5 segundos

nos aparecerá un prompt con switch>

- flash_init

iniciamos la flash

- load_helper

carga imagenes de ayuda

- dir flash

para ver lo que hay en la flash

- rename flash:config.text flash:config.old

para renombrar la imagen

si ya hay una imagen hay que eliminarla con 

delete flash:config.old o poner otro nombre por ejemplo
config.old2

----
Fuentes

https://echaleunvistazo.wordpress.com/2013/04/19/resetear-password-y-actualizar-catalyst-2950/
https://www.cisco.com/c/en/us/support/docs/switches/catalyst-2950-series-switches/41845-192.html
https://newfly.wordpress.com/2012/04/05/recuperacion-password-switch-cisco-catalyst-2950/



##Reseteo contraseña en switch catalyst 2960-CG ( Blanco Pequeño )

- Dejar pulsado el Botón Mode que hay en el panel frontal 10s, se reiniciará y ya estará reseteado.

----
Fuentes

https://www.cisco.com/c/dam/en/us/td/docs/switches/lan/catalyst2960c_3560c/hardware/quick/guide/all_languages/2960c_3560c_gsg_es.pdf







