Configuración de sublime text2
==============================

- instalacion sublime text2
- instalación de package control
	- https://packagecontrol.io/installation
	- Copiar este código en la consola 
		- view, show console o <kbd>Ctrl</kbd> + <kbd>`</kbd>. 

```

import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

```
Un vez terminado sublime te pedirá que lo **reinicies**, lo cierras y lo vuelves a abrir.
<kbd>cmd</kbd> + <kbd>q</kbd> en MAC

Instalando MarkDown Preview
---------------------------

- Abrimos el gestor de paquetes de sublime <kbd>Cmd</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>
- Buscamos la opción Package Control: Install Package
- Buscar el paquete Markdown Preview e Instalarlo
	- Mientras se instala podrás ver el progreso en la barra inferior parte izquierda del programa.
Una vez instalado tenemos varias operaciones a nuestra disposición que podemos ejecutar desde el Gestor de Paquetes <kbd>Cmd</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>: estando sobre un documento con extensión .md

- Markdown Preview: Preview in Browser
- Markdown Preview: Export HTML in Sublime Text
- Markdown Preview: Copy to Clipboard
- Markdown Preview: Open Markdown Cheat sheet

A la hora de usar el paquete de Markdown Preview solo tendremos que poner sobre el gestor de paquetes las iniciales mdp así se accede más rápidamente.

Instalando Diccionario para corrector ortográfico.
--------------------------------------------------

- Descargamos todos los diccionarios.
	- https://github.com/titoBouzout/Dictionaries
- Creamos una carpeta con el nombre Language - español y copiamos todos los archivos que empiezen por el diccionario que queremos, en este caso Spanish.aff, Spanish.dic y Spanish.txt

- Buscamos la ruta en mac de la carpeta donde tienen que estar los diccionarios
	- /Users/{user}/Library/Application Support/Sublime Text 2/Packages (Puede que esté oculta la carpeta)
	- Tambien podemos acceder a través del menú preferences / Browse Packages
- Copiamos la carpeta que hemos creado Language - español

- luego nos vamos a sublime text / preferences / Settings - Defaul / y añadimos en la sección: 
	// Word list to use for spell checking
	esta linea
```
 
 "dictionary": "Packages/Language - español/Spanish.dic",

```
 - Después nos vamos a la opción / View / dictionary / language - español / spanish / 
 - Seleccionamos y cuando le demos a / View / Speel Check / ya nos corregirá en español

