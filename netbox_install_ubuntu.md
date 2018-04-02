Para la instalación de Netbox se ha seguido la siguiente guía en un Ubuntu 16.04 actualizado.

https://netbox.readthedocs.io/en/stable/

Los comandos usados para la instalación han sido los siguientes:

Instalación de la base de datos

sudo apt-get update
sudo apt-get install -y postgresql libpq-dev

levantamos el servicio

systemctl start postgresql

Creamos la base de datos

sudo -u postgres psql
psql (9.3.13)
Type "help" for help.

postgres=# CREATE DATABASE netbox;
CREATE DATABASE
postgres=# CREATE USER netbox WITH PASSWORD 'password';
CREATE ROLE
postgres=# GRANT ALL PRIVILEGES ON DATABASE netbox TO netbox;
GRANT
postgres=# \q

verificamos que tenemos acceso a la base de datos recien creada

psql -U netbox -h localhost -W

para salir \q

Instalamos python3 y dependencias para netbox

apt-get install -y python3 python3-dev python3-pip libxml2-dev libxslt1-dev libffi-dev graphviz libpq-dev libssl-dev zlib1g-dev

creamos un directorio para la instalación

mkdir -p /opt/netbox/ && cd /opt/netbox/

instalamos git 

apt-get install -y git

clonamos la imagen de netbox con git en el directorio /opt/netbox en el que estamos.

git clone -b master https://github.com/digitalocean/netbox.git .

antes de instalar los paquetes hay que modificar el archivo requirements.txt y modificar la línea 

djangorestframework>=3.6.2
y cambiarla por esta otra
djangorestframework==3.6.4
de lo contratio tendremos problemas en los siguientes pasos de la instalación , este paso no viene documentado en la guía de la instalación
pero está considerado un bug y tenéis mas info en este enlace:

https://github.com/digitalocean/netbox/issues/1563

instalamos los paquetes necesarios de pyton a través de pip

pip3 install -r requirements.txt

vamos al directorio netbox/netbox y hacemos una copia del archivo de configuración y lo modificamos.

cd netbox/netbox/
cp configuration.example.py configuration.py

el archivo tiene que quedar así

Hemos modificado 

allowed_hosts : localhost
usuario : netbox
password: elquesea
secret_key: generada o copiada

```
#########################
#                       #
#   Required settings   #
#                       #
#########################

# This is a list of valid fully-qualified domain names (FQDNs) for the NetBox server. NetBox will not permit write
# access to the server via any other hostnames. The first FQDN in the list will be treated as the preferred name.
#
# Example: ALLOWED_HOSTS = ['netbox.example.com', 'netbox.internal.local']
ALLOWED_HOSTS = ['localhost']

# PostgreSQL database configuration.
DATABASE = {
    'NAME': 'netbox',         # Database name
    'USER': 'netbox',               # PostgreSQL username
    'PASSWORD': 'elquesea',           # PostgreSQL password
    'HOST': 'localhost',      # Database server
    'PORT': '',               # Database port (leave blank for default)
}

# This key is used for secure generation of random numbers and strings. It must never be exposed outside of this file.
# For optimal security, SECRET_KEY should be at least 50 characters in length and contain a mix of letters, numbers, and
# symbols. NetBox will not run without this defined. For more information, see
# https://docs.djangoproject.com/en/dev/ref/settings/#std:setting-SECRET_KEY
SECRET_KEY = 'r8OwDznj!!dc-----hmRfdu1Ysxm0AiPeDCQhKE+N_rClfWNj'
```
el archivo es más largo ya que incluye configuración adicional pero no se ha modificado en esta ocasión.

la SECRET_KEY se puede crear con un script que hay en netbox/generate_secret_key.py solo hay que ejecutar el comando siguiente para generar una clave correcta.

```
python3 generate_secret_key.py
```
si vamos a crear una infraestructura de alta disponibilidad hay que tener en cuenta que los servidores tendrán que tener la misma clave secreta.

Ahora migramos las bases de datos

```
cd /opt/netbox/netbox/
python3 manage.py migrate
Operations to perform:
  Apply all migrations: dcim, sessions, admin, ipam, utilities, auth, circuits, contenttypes, extras, secrets, users
Running migrations:
  Rendering model states... DONE
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
```
creamos un superusuario

python manage.py createsuperuser
Username: admin
Email address: admin@example.com
Password:
Password (again):
Superuser created successfully.

collect statis ( no se lo que es esto)

python manage.py collectstatic --no-input

You have requested to collect static files at the destination
location as specified in your settings:

    /opt/netbox/netbox/static

This will overwrite existing files!
Are you sure you want to do this?

Type 'yes' to continue, or 'no' to cancel: yes

si queremos introducir datos de muestra podemos usar el siguiente comando.

python manage.py loaddata initial_data

llegados a este punto deberíamos poder ver el servidor funcionando, esto solo sirve como prueba nunca para producción

python manage.py runserver 0.0.0.0:8000 --insecure
Performing system checks...

System check identified no issues (0 silenced).
June 17, 2016 - 16:17:36
Django version 1.9.7, using settings 'netbox.settings'
Starting development server at http://0.0.0.0:8000/
Quit the server with CONTROL-C.

localhost:8000 y deberíamos ver la página inicial de netbox

instalamos el webserver

apt-get install -y nginx

nos vamos al archivo de configuración de nginx y creamos un archivo nuevo que se llame netbox con la siguiente info:

```
server {
    listen 80;

    server_name localhost;

    client_max_body_size 25m;

    location /static/ {
        alias /opt/netbox/netbox/static/;
    }

    location / {
        proxy_pass http://127.0.0.1:8001;
        proxy_set_header X-Forwarded-Host $server_name;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-Proto $scheme;
        add_header P3P 'CP="ALL DSP COR PSAa PSDa OUR NOR ONL UNI COM NAV"';
    }
}
```
en este caso solo hemos reemplazado netbox.example.com por localhost

nos vamos al directorio 

cd /etc/nginx/sites-enabled/

eliminanos el perfil de default

rm default

creamos un symlink a la configuración que hemos creado anteriormente.

ln -s /etc/nginx/sites-available/netbox

reiniciamos el servicio

service nginx restart

instalamos gunicorn

pip3 install gunicorn

creamos un archivo de configuración en la carpeta /opt/netbox
con el nombre gunicorn_config.py

/opt/netbox/gunicorn_config.py

```
command = '/usr/bin/gunicorn'
pythonpath = '/opt/netbox/netbox'
bind = '127.0.0.1:8001'
workers = 3
user = 'www-data'
```
instalamos supervisor

apt-get install -y supervisor

guardamos en la siguiente ruta el archivo con este contenido

/etc/supervisor/conf.d/netbox.conf

```
[program:netbox]
command = gunicorn -c /opt/netbox/gunicorn_config.py netbox.wsgi
directory = /opt/netbox/netbox/
user = www-data
```

reiniciamos el servicio de supervisor para que detecte gunicorn

service supervisor restart

hasta aquí deberíamos haber terminado si nos vamos a 

localhost deberíamos ver netbox instalado y listo para usar
desde otra máquina solo deberíamos de usar la ip
























