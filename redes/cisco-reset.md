# Cisco Reset de Contraseña

## Índice

- [Reset Catalyst 2950](#reset-catalyst-2950)
- [Reset Catalyst 2960-CG](#reset-catalyst-2960-cg)
- [Referencias](#referencias)

---

## Reset Catalyst 2950

Para resetear la contraseña hay que seguir los siguientes pasos:

1. Iniciar el SW con el botón MODE pulsado 5 segundos

   Aparecerá un prompt con `switch>`

2. Iniciar la flash:

   ```
   flash_init
   ```

3. Cargar imágenes de ayuda:

   ```
   load_helper
   ```

4. Ver contenido de la flash:

   ```
   dir flash
   ```

5. Renombrar la imagen de configuración:

   ```
   rename flash:config.text flash:config.old
   ```

   > Si ya hay una imagen hay que eliminarla con `delete flash:config.old` o ponerle otro nombre, por ejemplo `config.old2`.

---

## Reset Catalyst 2960-CG (Blanco Pequeño)

- Dejar pulsado el **Botón Mode** del panel frontal durante **10 segundos**. El equipo se reiniciará y quedará reseteado.

---

## Referencias

- https://echaleunvistazo.wordpress.com/2013/04/19/resetear-password-y-actualizar-catalyst-2950/
- https://www.cisco.com/c/en/us/support/docs/switches/catalyst-2950-series-switches/41845-192.html
- https://newfly.wordpress.com/2012/04/05/recuperacion-password-switch-cisco-catalyst-2950/
- https://www.cisco.com/c/dam/en/us/td/docs/switches/lan/catalyst2960c_3560c/hardware/quick/guide/all_languages/2960c_3560c_gsg_es.pdf
