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

Como mis maquina tienen usuario con nombre distinto primero genero en la maquina swap1 el usuairo de la maquina 2.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practica%202/image/img03.png)

Insertamos el comando para que el usuario sea el dueño de la carpeta donde residen los archivos del espacio web y comprobamos que se hayan aplicado los cambios correctamente.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practica%202/image/img04.png)

Para probar el funcionamiento del rsync vamos a clonar una carpeta cualquiera. Por ejemplo, para clonar la carpeta con el contenido del servidor web principal, en la máquina 2 (secundaria) ejecutaremos:

~~~
rsync -avz -e ssh ipmaquina1:/var/www/ /var/www/
~~~

Nos pedirá la clave del usuario (pedro) en la máquina principal (máquina-1), y tras unos segundos, podremos comprobar que el directorio /var/www queda clonado de forma idéntica en ambas máquinas (de la máquina-1 se copia en la máquina-2):

~~~
ls -la /var/www
~~~

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
