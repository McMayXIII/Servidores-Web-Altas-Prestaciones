# Practica 1: Preparación de Herramientas #

Para esta práctica se realizará la virtualización de dos maquinas virtuales. En ellas se instalará un Ubuntu Server 16.04 LTS de 64 bits y se instalarán los servidor **LAMP** y **SSH**.

**Servidor LAMP:** *¿Y qué es un servidor LAMP?* Se trata de una agrupación de servicios típicamente utilizada para soportar otros muchos, que vienen después. Para ello, al igual que otras muchas plataformas, se hace previamente imprescindible disponer de LAMP (Linux, Apache, MySQL y PHP). Además de PHP, es habitual que se empleen otros lenguajes de programación, como Perl o Python, pero PHP es el más extendido.

**Servidor SSH:** OpenSSH (Open Secure Shell) es un conjunto de aplicaciones que permiten realizar comunicaciones cifradas a través de una red, usando el protocolo SSH. Fue creado como una alternativa libre y abierta al programa Secure Shell, que es software propietario.

Para esta práctica utilizaremos la herramienta **VMware Workstation** (se puede dercargar [aquí](https://www.vmware.com/es.html) ).

## Generando las maquinas virtuales ##

En primer lugar pulsamos sobre el icono ***Create a New Virtual Machine*** que se señala en la imagen.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img01.png)

Seleccionamos la intalación ***Typica***, a continuación seleccionamos la opción ***I will the operating system later. The virtual machine will be created with a blank hard disk*** (para insertar posteriormente la ISO de Ubuntu Server 16.04 LTS 64bits).

 ![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img02.png) ![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img03.png)

En el siguiente paso seleccionmos el systema que vamos a usar ***LINUX*** y la version ***Ubuntu 64-bits*** y le asignamos un nombre.

 ![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img04.png) ![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img05.png)

Ahora asignamos el tamaño del disco duro 20 GB, y seleccionamos la opción ***Split virtual disk into multiple files***.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img06.png)

En este apartado pasaremos a la configuración de red, donde tendremos dos tarjetas una para conectar las maquinas virtuales internamente entre si. Que para este caso trendra el nombre de ***VMnet0***.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img07.png)

Ahora configuramos la otra tarjeta de red para que la maquina se comunique con el exterior sin problemas.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img08.png)

Y por ultimo añadimos la ISO de ***Ubuntu Server 16.04 LTS***

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img09.png)

Una vez llegados a este punto tenemos la maquina virtual preparada para poder intalar el sistema operativo.

## Instalando Ubuntu Server 16.04 LTS 64bits ##

**Ubuntu Server** es una variante de Ubuntu que sale con cada versión y está dedicada especialmente para su uso en **servidores**. El uso de Ubuntu como servidor se ha extendido mucho en los últimos años, sobretodo para el uso de **servidores web**, de un modo tanto particular como profesional.

Un servidor es una máquina que nos proporciona algún servicio. Pueden ser de diferentes tipos, servidor web, servidor de base de datos, servidor de archivos, u otras diferentes funciones, incluso varias a la vez. No tienen porque ser grandes y potentes máquinas, podemos tener montado un servidor en casa en un ordenador antiguo, que nos sirva para tener guardados todos nuestros datos importantes y acceder a ellos desde cualquier otro ordenador o dispositivo desde nuestra casa, o incluso desde cualquier lugar.

Ubuntu Server es un Sistema Operativo sin entorno gráfico (aunque podemos instalarlo) lo que quiere decir que todas las acciones se realizan mediante consola, y normalmente ni si quiera a través de el propio servidor, sino desde una conexión remota. El manejo de Ubuntu Server es muy similar al de cualquier otro Sistema Linux, pero con las particularidades de Ubuntu (como el sudo).

Cuando estamos instalando Ubuntu Server nos hace una serie de preguntas sobre que tipo de servicios queremos instalar, entre una lista de los más típicos, y nos pregunta los parámetros necesarios para su configuración. De este modo podemos instalar de una forma fácil y sencilla un servidor acorde a nuestras necesidades en unos pocos minutos.

Es muy habitual encontrarnos Ubuntu Server como sistema operativo en muchos de los VPS que podemos contratar en la mayoría de compañías, aunque también nos suelen dar a elegir otras distribuciones Linux.

Pasos para instalar ubuntu, en primer lugar nos pide un idioma, en este caso seleccionamos **español**.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img10.png)

De las opciones que nos muestra a continuación seleccionamos **Instalar Ubuntu Server**.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img11.png)

 Continuamos seleccionando el país para establecer la zona horaria, en este caso **España**.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img12.png)

Ahora procedemos a seleccionar la distribución del teclado, nos preguntará si deseamos detectarlo automáticamente, cliqueamos **NO**.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img13.png)

Seleccionamos **Spanish** >> **Spanish**.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img14.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img15.png)

Ahora procedemos a seleccionar la interfaz de red, en este caso **ens34**.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img16.png)

Seguidamente introducimos el nombre de la máquina, usuario y cuenta, en todos los casos será **swap1**.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img17.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img18.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img19.png)

Ahora establecemos la contraseña y confirmamos, como se observa en las siguientes figuras.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img20.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img21.png)

Por último nos pregunta si queremos cifrar la carpeta personal, que en este caso no nos interesa, seleccionamos **NO**.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img22.png)

Ahora procedemos a configurar la zona horaria, se despliegan diversas opciones según el país elegido al inicio de la instalación, en este caso seleccionamos la opción **Peninsula**.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img23.png)

Prodecemos a la configuración y particionado del disco.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img24.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img25.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img26.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img27.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img28.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img29.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img30.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img31.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img32.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img33.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img35.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img36.png)

### Activando root ###

Para ello insertamos el siguiente comando: ***su passwd root*** e insertamos la contraseña.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img37.png)

### Comprobando estado de apache ###

Para ello insertamos el siguiente comando: ***ps aux | grep apache***

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img38.png)

## Acceder por ssh de una máquina a otra ##

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img39.png)

## Acceder mediante la herramienta curl desde una máquina a la otra ##

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img40.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img41.png)

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Pracctica%201/image/img42.png)
