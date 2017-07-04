Para poder ejecutar por primera vez metasploit en kali linux es necesario ejecutar el servicio de la base de datos eso se hace con el siguiente comando:

```bash
root@kali:/root/Desktop#service postgresql start
```
para comprobar funcionamiento puedes usar:

```bash
root@kali:/root/Desktop#service postgreeql status
```
Te tiene que salir algo parecido a esto:

```
● postgresql.service - PostgreSQL RDBMS
   Loaded: loaded (/lib/systemd/system/postgresql.service; disabled; vendor preset: enabled)
   Active: active (exited) since Sun 2017-04-02 13:11:07 EDT; 7s ago
  Process: 2002 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
 Main PID: 2002 (code=exited, status=0/SUCCESS)

Apr 02 13:11:07 kali systemd[1]: Starting PostgreSQL RDBMS...
Apr 02 13:11:07 kali systemd[1]: Started PostgreSQL RDBMS.
```
Para ejecutar metasploit usamos el siguiente comando:

```bash
root@kali:/root/Desktop#msfconsole
```
Para comprobar que esta funcionando correctamente podemos usar el comando ```db_status```

```
msf > db_status
[*] postgresql connected to msf
msf > 
```


















###Fuentes:
- [http://es.docs.kali.org/general-use-es/iniciando-el-metasploit-framework]
- [https://www.kali.org/penetration-testing/openvas-vulnerability-scanning/]