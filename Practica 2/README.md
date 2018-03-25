# Practica 2- Clonar la información de un sitio web #

 ***

## 1. Objetivos de la práctica ##

Los objetivos concretos de esta segunda práctica son:
- Apreder a copiar archivos mediante ssh.
- Clonar contenido entre máquinas.
- Configurar es ssh para acceder a máquinas remotas sin contraseña.
- Establecer tareas en cron.

---

## 2. Crear un tar con ficheros locales en un equipo remoto ##

En elñ caso que necesitemos crear un tar.gz de un equipo y dejarlo en otro pero no disponemos de espacio en disco local, podemos usar ssh para crearlo directamente en el equipo destino.

Para ello, deberemos indicar al comando tar que queremos que use stdout como destino y mandar con una pipe la salida al ssh. Éste debe coger la salida del tar y escribirla en un fichero. El comando quedaría:

~~~
  tar czf - directorio | ssh equipodestino 'cat > ~/tar.tgz'
~~~

Primero insertamos el comando mensionado anteriormente y luego comprobamos que se haya transmitido correctamente.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practica%202/image/img01.png)

De esta forma en el equipo de destino tendremos creado el archivo tar.tgz Sin embargo, esto que puede ser útil en un momento dado, no nos servirá para sincronizar grandes cantidades de información. En ese caso, va mejor la herramienta rsync.

---

## 3. Instalar la herramienta rsync
La página web de esta herramienta, con toda la documentación, descargas, etc, se encuentra en:
http://rsync.samba.org/
Disponemos de versiones compiladas para diferentes sistemas en:
http://rsync.samba.org/download.html
En nuestras máquinas Ubuntu podemos instalarlo (si no lo está) usando apt-get:

~~~
  sudo apt-get install rsync
~~~

Como podemos ver en la imagen la herramienta rsync ya venía instalada de serie.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practica%202/image/img02.png)

En este punto, para trabajar podemos optar por hacerlo como root o como usuario sin privilegios de root (el usuario habitual). En principio, podremos realizar todas las configuraciones como usuario sin privilegios por lo que se recomienda usar esta cuenta. En este caso, y como detalle previo, es hacer que el usuario sea el dueño de la carpeta donde residen los archivos que hay en el espacio web (en ambas máquinas):

~~~
  sudo chown pedro:pedro –R /var/www
~~~

Como mis maquina tienen usuario con nombre distinto, en primer lugar genero en la maquina 1, el usuairo de la maquina 2 "swap2".

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practica%202/image/img03.png)

Insertamos el comando para que el usuario sea el dueño de la carpeta donde residen los archivos del espacio web y comprobamos que se hayan aplicado los cambios correctamente.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practica%202/image/img04.png)

Para probar el funcionamiento del rsync vamos a clonar una carpeta cualquiera. Por ejemplo, para clonar la carpeta con el contenido del servidor web principal, en la máquina 2 (secundaria) ejecutaremos:

~~~
  rsync -avz -e ssh ipmaquina1:/var/www/ /var/www/
~~~

Comprobamos el funcionamiento del rsync clonando el contenido del servidor web principal.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practica%202/image/img05.png)

Nos pedirá la clave del usuario (pedro) en la máquina principal (máquina-1), y tras unos segundos, podremos comprobar que el directorio /var/www queda clonado de forma idéntica en ambas máquinas (de la máquina-1 se copia en la máquina-2):

~~~
  ls -la /var/www
~~~

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practica%202/image/img06.png)

Los directorios y ficheros copiados en la máquina destino mantienen los permisos y dueño que en la máquina origen.

La herramienta rsync nos permite especificar qué directorios copiar y cuáles ignorar en el proceso de copia, de forma que no se sobreescriban los archivos que no queramos.

Así, si hacemos:

~~~
  rsync -avz --delete --exclude=**/stats --exclude=**/error --exclude=**/files/pictures -e ssh maquina1:/var/www/ /var/www/
~~~

estaremos haciendo la copia completa del directorio /var/www pero excluyendo /var/www/error , /var/www/stats y /var/www/files/pictures

La opción --delete indica que aquellos ficheros que se hayan eliminado en la máquina
origen, también se borren en la máquina destino (para que el clonado sea perfecto).
La opción --exclude indica que ciertos directorios o ficheros no deben copiarse (p.ej.,
archivos de log). De esta forma, en la orden de ejemplo anterior, cuando indicamos --
exclude=\*\*/error significa "no copies lo que hay en /var/www/error" ya que corresponde
a mensajes de la máquina original (y la segunda máquina ya generará sus propios
mensajes).

**AVISO:** Esta orden más compleja será más útil en entornos reales, aunque

---

## 4. Acceso sin contraseña para ssh
El uso de rsync nos será de gran ayuda para mantener el contenido de varias máquinas actualizado e idéntico en todas ellas. Sin embargo, esa actualización debería hacerse automáticamente, a través de scripts que no requieran la intervención del administrador que vaya tecleando las contraseñas.

Es más, al realizar scripts que se conectan mediante ssh a equipos remotos para ejecutar alguna acción (p.ej. copias de seguridad o clonado) nos podemos encontrar que se queden esperando la contraseña.

Veamos cómo ejecutar comandos en equipos remotos mediante ssh sin contraseña. Para ello, normalmente se usa autenticación con un par de claves pública-privada.

Mediante ssh-keygen podemos generar la clave, con la opción -t para el tipo de clave.

Así, en la máquina secundaria ejecutaremos:

~~~
  ssh-keygen -b 4096 -t rsa
  Generating public/private rsa key pair.
  Enter file in which to save the key (/home/pedro/.ssh/id_rsa):
  Created directory '~/.ssh'.
  Enter passphrase (empty for no passphrase):
  Enter same passphrase again:
  Your identification has been saved in ~/.ssh/id_rsa.
  Your public key has been saved in ~/.ssh/id_rsa.pub.
  The key fingerprint is:
  57:2c:00:be:ef:00:0f:00:ba:be:00:19:c4:8e:be:73 pedro@maquina1
~~~

Según el tipo de claves a usar, se generan dos ficheros:

- rsa1: Generará, por defecto, el fichero ~/.ssh/identity para la clave privada y el fichero ~/.ssh/identity.pub para la clave pública. Este formato es válido para el protocolo 1 de SSH
- rsa: Generará, por defecto, el fichero ~/.ssh/id_rsa para la clave privada y el fichero ~/.ssh/id_rsa.pub para la clave pública. Este formato es válido para el protocolo 2 de SSH
- dsa: Generará, por defecto, el fichero ~/.ssh/id_dsa para la clave privada y el fichero ~/.ssh/id_dsa.pub para la clave pública. Este formato es válido para el protocolo 2 de SSH

La passphrase que nos pide es para añadir seguridad a la clave privada; se trata de una contraseña. En el caso de querer conectar a equipos sin contraseña debemos dejarla en blanco.

A continuación deberemos copiar la clave pública al equipo remoto (máquina principal) añadiéndola al fichero ~/.ssh/authorized_keys, que deberá tener permisos 600 (por defecto esto estará bien configurado; sólo si nos da algún error debemos hacerlo):

~~~
  chmod 600 ~/.ssh/authorized_keys
~~~

Para hacer la copia de la clave existe una forma sencilla y elegante. Se trata de usar el comando ssh-copy-id, que viene integrado con el comando ssh. Lo que haremos es copiarla a la máquina principal (a la que querremos acceder luego desde la secundaria):
~~~
  ssh-copy-id maquina1
~~~

A continuación ya podremos conectarnos a dicho equipo sin contraseña:
~~~
  [pedro@maquina2 ~]# ssh maquina1
  Last login: Sun May 1 19:15:16 2011 from maquina2
  CentOS release 5.5 (Final)
  Linux maquina1 2.6.34.6-xxxx-grs-ipv6-64 #3 SMP Fri Sep 17
  16:06:38 UTC 2010 x86_64 x86_64 x86_64 GNU/Linux
  [pedro@maquina1 ~]#
~~~

Para ejecutar comandos simplemente deberemos añadirlo al final del comando ssh para conectarnos:

~~~
  [pedro@maquina2 ~]# ssh maquina1 uname -a
  Linux maquina1 2.6.34.6-xxxx-grs-ipv6-64 #3 SMP Fri Sep 17
  16:06:38 UTC 2010 x86_64 x86_64 x86_64 GNU/Linux
~~~

En el caso que por algún motivo se perdiese la clave del ~/.ssh/authorized_keys nos pediría contraseña de nuevo.

Teniendo preparado el acceso por ssh sin contraseña, podemos hacer uso del rsync desde scripts que se ejecuten automáticamente con el cron (p.ej. cada noche de madrugada).

---

## 5. Programar tareas con crontab

Cron es un administrador procesos en segundo plano que ejecuta procesos en el instante indicado en el fichero crontab.

Cron se ejecuta en background y revisa cada minuto la tabla del fichero /etc/crontab en búsqueda de tareas que se deban ejecutar (si ha llegado su momento). Podemos agregar nuevas tareas a cron para automatizar algunos procesos (p.ej. copias de seguridad).

Para ello, debemos editar el archivo /etc/crontab que normalmente tendrá un aspecto similar al siguiente:

~~~
  SHELL=/bin/bash
  PATH=/sbin:/bin:/usr/sbin:/usr/bin
  01 * * * * root run-parts /etc/cron.hourly
  02 4 * * * root run-parts /etc/cron.daily
  22 4 * * 0 root run-parts /etc/cron.weekly
  42 4 1 * * root run-parts /etc/cron.monthly
~~~

En ese ejemplo vemos tareas que se ejecutan como usuario root, cada mes, cada semana, cada día o cada hora.

No hay límites de cuantas tareas podemos tener. Lo importante es cuidar la sintaxis y número de campos de cada línea del fichero. Los 7 campos que forman estas líneas están organizados de la siguiente manera:

~~~
  Minuto Hora DiaDelMes Mes DiaDeLaSemana Usuario Comando
~~~

- Minuto: indica el minuto de la hora en que el comando será ejecutado, este valor debe de estar entre 0 y 59.
- Hora: indica la hora en que el comando será ejecutado, se especifica en un formato de 24 horas, los valores deben estar entre 0 y 23, 0 es medianoche.
- DíaDelMes: indica el día del mes en que se quiere ejecutar el comando. Por ejemplo se indicaría 20, para ejecutar el comando el día 20 de cada mes.
- Mes: indica el mes en que el comando se ejecutará (1-12).
- DiaDeLaSemana: indica el día de la semana en que se ejecutará el comando (1=lunes y hasta 7=domingo).
- Usuario: indica el usuario que ejecuta el comando.
- Comando: indica el comando que se desea ejecutar. Este campo puede contener múltiples palabras y espacios.

Un asterisco * como valor en los primeros cinco campos indicará el valor "todo". Así, un * en el campo de minuto indicará todos los minutos de la hora.
