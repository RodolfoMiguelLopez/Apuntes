Ajustes Reinstalación MAC

- Habilitar para poder ver los archivos ocultos del sistema

```
$ defaults write com.apple.finder AppleShowAllFiles TRUE 
$ KillAll Finder
```
Atajos de teclado:

¡ #+Flecha Arriba+3 --> Captura Pantalla y la deja en el escritorio
¡ #+Flecha Arriba+4 --> Selección Pantalla y la deja en el escritorio



- Integración de iTerm2 para la consola

```
MBP:Desktop kapi_tan$ curl -L https://iterm2.com/misc/install_shell_integration.sh | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1792  100  1792    0     0    588      0  0:00:03  0:00:03 --:--:--   588
Downloading script from https://iterm2.com/misc/bash_startup.in and saving it to /Users/kapi_tan/.iterm2_shell_integration.bash...
Checking if /Users/kapi_tan/.profile contains iterm2_shell_integration...
Appending source command to /Users/kapi_tan/.profile...
Done.

The next time you log in, shell integration will be enabled.
MBP:Desktop kapi_tan$
```
Restart iTerm2

- Integration of iterm2 via menu

Menu iterm2 --> Install shell Integration confirm all steps.
Restar iterm2


– Solarized theme: http://ethanschoonover.com/solarized