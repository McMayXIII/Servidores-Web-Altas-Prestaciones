# Ejercicios de Teoría

## Ejercicios del tema 1: INTRODUCCIÓN

**Ejercicio 1:** Buscar información sobre las tareas o servicios web para los que se usan más los programas que comentamos al principio de la sesión:

  - **Apache:** el servidor HTTP Apache es un servidor web HTTP de código abierto, para plataformas Unix (BSD, GNU/Linux, etc.), Microsoft Windows, Macintosh y otras, que implementa el protocolo HTTP/1.12​ y la noción de sitio virtual.

  - **Nginx:** (pronunciado en inglés “engine X”) es un servidor web/proxy inverso ligero de alto rendimiento y un proxy para protocolos de correo electrónico (IMAP/POP3).2​

  - **Thttpd:** es un programa de software que se ejecuta en segundo plano de un servidor web y espera las solicitudes del servidor entrante. Este daemon responde la solicitud automáticamente y sirve el hipertexto y los documentos multimedia a través de Internet utilizando HTTP.

  - **Cherokee:** es un servidor web multiplataforma.​ Su objetivo es ser rápido y completamente funcional, sin dejar de ser liviano comparado con otros servidores web.​ Está escrito completamente en C. Puede usarse como un sistema embebido y soporta complementos para aumentar sus funcionalidades. Es software libre, disponible bajo la Licencia Pública General de GNU.

  - **Node.js:**  es un entorno en tiempo de ejecución multiplataforma, de código abierto, para la capa del servidor (pero no limitándose a ello) basado en el lenguaje de programación ECMAScript, asíncrono, con I/O de datos en una arquitectura orientada a eventos y basado en el motor V8 de Google. Fue creado con el enfoque de ser útil en la creación de programas de red altamente escalables, como por ejemplo, servidores web.​ Fue creado por Ryan Dahl en 2009 y su evolución está apadrinada por la empresa Joyent, que además tiene contratado a Dahl en plantilla

#### Información obtenida de Wikipedia

---

## Ejercicios tema 2: ESCALABILIDAD Y DISPONIBILIDAD

**Ejercicio 1:** Calcular la disponibilidad del sistema si tenemos dos réplicas de cada elemento (en total 3 elementos en cada subsistema).

|Component  | 1 elemento | 2 elementos | 3 elementos |
|----  | ----    | ---    | ----       |
|Web  | 85% | 97.75% | **99.6625%** |
|Application  | 90% | 99% | **99.9%** |
|Database  | 99.9% | 99.9999% | **99.9999999%** |
|DNS  | 98% | 99.96% | **99.9992%** |
|Firewall  | 85% | 97.75% | **99.6605%** |
|Switch  | 99% | 99.99% | **99.9999%** |
|Data Center  | 99.99% | 99.99% | **99.999999%** |
|ISP  | 95% | 99.75% | **99.9875%** |
| **Disponibilidad**  | **59.87%** | **94.30%** | **99.21%** |

***Calculo con 3 elementos***
- **Web** = 97.75% + (1 - 97.75%) x 85% =  **99.6625%**
- **Application** = 99% + (1 - 99%) x 90% =  **99.9%**
- **Database** = 99.9999% + (1 - 99.9999%) x 99.9% = **99.9999999%**
- **DNS** = 99.96% + (1 - 99.96%) x 98% = **99.9992%**
- **Firewall** = 97.75% + (1 - 97.75% ) x 85% = **99.6605%**
- **Switch** = 99.99% + (1 - 99.99%) x 99% = **99.9999%**
- **Data Center** = 99.99% + (1 - 99.99%) x 99.99% = **99.999999%**
- **ISP** = 99.75% + (1 - 99.75%) x 95% = **99.9875%**

***DISPONIBILIDAD***
- **1 elemento** = 85% x 90% x 99.9% x 98% x 85% x 99% x 99.99% x 95% = **59.87%**
- **2 elementos** = 97.75% x 99% x 99.9999% x 99.96% x 97.75% x 99.99% x 99.99% x 99.75% = **94.30%**
- **3 elementos** = 99.6625% x 99.9% x 99.9999999% x 99.9992% x 99.6605% x 99.9999% x 99.999999% x 99.9875% = **99.21%**

**Ejercicio 2:** Buscar frameworks y librerías para diferentes lenguajes que permitan hacer aplicaciones altamente disponibles con relativa facilidad. Como ejemplo, examina PM2: https://github.com/Unitech/pm2 que sirve para administrar clústeres de NodeJS.

- **Docker:** permite la automatizacion del desplegamiento di contenidores de software, es decir permitiendo una escalabilidad super sencilla y potente. Cada contenedor ejecuta procesos de manera aislada, de manera que tareas diferentes se consiguan en maquinas virtuales (contenidores) y permitiendo una plataforma como servicio.

- **PM2:** permite de desplegar una aplicacion escrita en node.js en produccion de manera que continue corriendo y que se reinicie en caso de caida. Tambien se usa para lanzar instancias diferentes de un mismo nodo (app de node.js) y controlar los estados.

**Ejercicio 3:** ¿Cómo analizar el nivel de carga de cada uno de los subsistemas en el servidor? Buscar herramientas y aprender a usarlas.

- **Nagios.** Es un sistema de monitorización de máquinas y servicios. Funciona es Linux y es open source. Permite: monitorización, alta visibilidad, notificaciones, resolución proactiva, reportes, arquitectura modular y redundancia de hosts.

- **Cacti.** Este sistema nos permite monitorizar y visualizar gráficas de toda la información de nuestro servidor y su red.

- **Munin.** Programa de monitorización de servidores que proporciona estadísticas de todos los recursos y servicios del servidor. Utiliza una interfaz web para mostar todas las informacciones.

**Ejercicio 4:** Buscar diferentes tipos de productos: (1) Buscar ejemplos de balanceadores software y hardware (productos comerciales). (2) Buscar productos comerciales para servidores de aplicaciones. (3) Buscar productos comerciales para servidores de almacenamiento.

- **Balanceadores SW:** LVS (nativo de Linux), Nginx, ZenLoad.

- **Balanceadores HW:** familia LoadMaster (p.e. LM-2600), familia F5.

**Balanceo nivel de aplicacion:** Java implementa ya un balanceo de carga a nivel de aplicacion, bien basado en la cookie-injection o bien por redireccion HTTP. Nginx tambien permite un "layer 7 load balancing" (balanceo de carga de nivel 7) con paso de mensaje. Como producto comercial el Barracuda Load Balancer ADC (permite offroad SSL, Caching HTTP, y routing de contenidos.

**Balanceo nivel de almacenamiento:** familia Netgear ReadyNAS por ejemplo

----

## Ejercicios tema 3: LA RED UNA GRANJA WEB

**Ejercicio 1:** Buscar con qué órdenes de terminal o herramientas gráficas
podemos configurar bajo Windows y bajo Linux el
enrutamiento del tráfico de un servidor para pasar el
tráfico desde una subred a otra.

- En Windows con el comando 'route', también en windows server existe una herramienta de enrutamiento y servicio remoto.

- En linux se puede usar tambié route, también configurando la iptables y asignandole las reglas adecuadas.

**Ejercicio 2:**
Buscar con qué órdenes de terminal o herramientas gráficas
podemos configurar bajo Windows y bajo Linux el filtrado
y bloqueo de paquetes.

En linux con las reglas de iptables.

Y en Windows con el firewall que trae por defecto, o también con IPSec.

----

## Ejercicios tema 4: BALANCEO DE CARGA

**Ejercicio 1:** Buscar información sobre cuánto costaría en la actualidad un mainframe. Comparar precio y potencia entre esa máquina y una granja web de unas prestaciones similares.

Normalmente ya no se suelen utilizar mainframes como tal (multiprocesador), se suelen usar nodos (multicomputadores) pues son mas tolerantes a fallos, mas faciles de ampliar y demás, aun así haciendo una pregunta a quora nos devuelve que un mainframe básico IBM puede costar alrededor de 75.000 dólares.

**Ejercicio 2:** Buscar información sobre precio y características de balanceadores hardware específicos. Compara las prestaciones que ofrecen unos y otros.

Por lo que hemos visto suelen rondar los 500 euros los mas básicos y nos ofrecen todo lo que nos ofrece un switch/router con el añadido del balanceo

- Lancom LANCOM 1611+ lancom lancom 1611+voip ready vpn router, firewal 568,55 €
Load balance traffic in HTTP, FTP, DNS, SIP, RTSP, POP/IMAP, etc.,
Load balance SSL traffic,
Define a "weight" for each of your servers or VM,
Configure monitoring sensors,
Manage NAT/DNAT for your Virtual rack,
View statements and performance with SNMP.

- Kemp Loadmaster 2200 Lm-2200 Servidor Carga Balanceador De - 523,95 €
Load balance traffic in HTTP, FTP, DNS, SIP, RTSP, POP/IMAP, etc.,
Load balance SSL traffic,
Define a "weight" for each of your servers or VM,
Configure monitoring sensors,
Manage NAT/DNAT for your Virtual rack,
View statements and performance with SNMP.

**Ejercicio 3:** Buscar información sobre los métodos de balanceo que implementan los dispositivos recogidos en el ***ejercicio 2.***

Todos los vistos implementan por lo menos roun-robin y la gran mayoría de los vistos en teoría, algunos balanceadores CISCO tienen algoritmos propios de balanceo

**Ejercicio 4:** Instala y configura en una máquina virtual el balanceador ZenLoadBalancer.

Descargamos la iso de la community edition desde https://sourceforge.net/projects/zenloadbalancer/files/latest/download la instalamos e instalamos el sistema, que está basado en Debian GNU/Linux, una vez configurado podemos acceder dsede otra maquían a su url de administración en https://<ip_address>:444

**Ejercicio 5:** Probar las diferentes maneras de redirección HTTP.
¿Cuál es adecuada y cuál no lo es para hacer balanceo de carga global? ¿Por qué?

301, 302 etcétera


**Ejercicio 6:** Buscar información sobre los bloques de IP para los distintos países o continentes.
Implementar en JavaScript o PHP la detección de la zona desde donde se conecta un usuario

Se puede implementar de varias maneras, lo mas optimo es usando un servicio de terceros, porque la base de datos GeoIP.dat suele agregar mucho peso a las paginas

**Ejercicio 7:** Buscar información sobre métodos y herramientas para implementar GSLB.

- Lo primero para eso deberiamos tener dos localizaciones en ubicaciones distintas, a poder ser continentes (no tiene sentido montar un GLSB en la misma ciudad)

- Lo primero tenemos que crear una VPN para que ambos servidores se comuniquen de forma segura, así nos evitamos que nos puedan atacar via ssh

- Luego configuramos lo tipico para que esté balanceado entre ambos, y que detected la localizacion del usuario para intentar servir contenido del mas cercano

----

## Ejercicios tema 5: MEDIR PRESTACIONES


**Ejercicio 1:** Buscar información sobre cómo calcular el número máximo de conexiones por segundo.

Para calcular el número de conexiones por segundo de una granja web o de un servidor específico podríamos usar herramientas como Apache Benchmark. Para medir las peticiones con esta herramienta estudiada en clase podríamos aumentar prograsivamente el número de peticiones por segundo mientras no se produjese ningun error en ninguna de las peticiones, momento en el que tendríamos una aproximación del número máximo de peticiones soportadas de forma simultánea. Esta manera de proceder es extensible a la mayoría de los benchmarks para servidores (Apache Jmeter, OpenWebLoad, Httperf, etc).

Si lo que queremos monitorizar es son el número de peticiones que el servidor está soportando actualmente, podemos activar opciones (presentes en determinados programas como Apache Benchmark o httperf) como mod-status. Para usar esta característica podemos usar el siguiente código:

    <Location /server-status>
    SetHandler server-status

    Order Deny,Allow
    Deny from all
    Allow from .website.com
    </Location>

Y, para acceder, usamos http://your.server.name/server-status.

Además del mencionado *mod-status* existen otras utilidades como `apache2ctl, iptstate o netstat`.

**Ejercicio 2:** Instalar wireshark y observar cómo fluye el tráfico de red en uno de los servidores web mientras se le hacen peticiones HTTP.

**Ejercicio 3:** Buscar información sobre características, disponibilidad para diversos SO, etc de herramientas para monitorizar las prestaciones de un servidor.

Algunas de las herramientas más utilizadas en la actualidad para la monitorización de las prestaciones de los servidores:

- **Nagios:** es un sistema de monitorización de redes ampliamente utilizado, de código abierto, que vigila los equipos (hardware) y servicios (software) que se especifiquen, alertando cuando el comportamiento de los mismos no sea el deseado. Entre sus características principales figuran la monitorización de servicios de red (SMTP, POP3, HTTP, SNMP...), la monitorización de los recursos de sistemas hardware (carga del procesador, uso de los discos, memoria, estado de los puertos...), independencia de sistemas operativos, posibilidad de monitorización remota mediante túneles SSL cifrados o SSH, y la posibilidad de programar plugins específicos para nuevos sistemas.

  Se trata de un software que proporciona una gran versatilidad para consultar prácticamente cualquier parámetro de interés de un sistema, y genera alertas, que pueden ser recibidas por los responsables correspondientes mediante (entre otros medios) correo electrónico y mensajes SMS, cuando estos parámetros exceden de los márgenes definidos por el administrador de red.

- **Cacti:**
es una herramienta para la generación de gráficos en red, diseñada para aprovechar el poder de almacenamiento y la funcionalidad para gráficas que poseen las aplicaciones RRDtool. Esta herramienta, desarrollada en PHP, provee un pooler ágil, plantillas de gráficos avanzadas, múltiples métodos para la recopilación de datos, y manejo de usuarios. Tiene una interfaz de usuario fácil de usar, que resulta conveniente para instalaciones del tamaño de una LAN, así como también para redes complejas con cientos de dispositivos.

- **Munin:**
Munin es un programa que permite monitorizar uno o varios equipos. Además, presenta la información a través de un servidor web, está hecho en perl y permite el uso de plugins, lo cual lo hace realmente versátil. También muestra una gran cantidad de información mediante unas gráficas creadas con la librería gráfica RRDtool.

- **AWStats:**
es una herramienta open source de informes de análisis web, apta para analizar datos de servicios de Internet como un servidor web, streaming, mail y FTP. AWstats analiza los archivos de log del servidor, y basándose en ellos produce informes HTML. Los datos son presentados visualmente en informes de tablas y gráficos de barra. Pueden crearse informes estáticos mediante una interfaz de línea de comando, y se pueden obtener informes on-demand a través de un navegador web, gracias a un programa CGI.

  Soporta la mayoría de los formatos de archivos log de servidor web conocidos, entre ellos Apache (formato de log NCSA combinado/XLF/ELF o formato común/CLFt), WebStar, IIS (formato de log del W3C) y muchos otros formatos comunes de Internet.

- **Ganglia:**
es un sistema de monitorización de computadores de alto rendimiento como clusters o servidores alojados en granjas web. Gracias a sus algoritmos consume bastante poco por nodo y utiliza una alta concurrencia a la hora de obtener toda la información tanto a nivel de servicios como hardware de nuestros servidores.

---

## Ejercicios tema 6: MEDIR PRESTACIONES

**Ejercicio 1:** Aplicar con iptables una política de denegar todo el tráfico en una de las máquinas de prácticas. Comprobar el funcionamiento.
Aplicar con iptables una política de permitir todo el tráfico en una de las máquinas de prácticas. Comprobar el funcionamiento.

Para denegar todo el trafico, utilizamos el comando:
~~~~
iptables -A INPUT -j DROP
~~~~
El fichero prueba.html ubicado en /var/www  no se descarga.

Para aceptar todo el trafico, utilizamos el comando:

~~~~
iptables -A INPUT -j ACCEPT
~~~~

El fichero prueba.html ubicado en /var/www  se descarga.


**Ejercicio 2:** Comprobar qué puertos tienen abiertos nuestras máquinas, su estado, y qué programa o demonio lo ocupa.

Con este comando podemos ver el listado con los servicios de red del sistema.
~~~~
cat /etc/services
~~~~


Para comprobaar qué servicios están activos y a la escucha en nuestro sistema Linux, utilizaremos el siguiente comando para mostrar qué programas están asociados a las conexiones activas.
~~~~
netstat -a o con la opción -ap
~~~~

**Ejercicio 3:** Buscar información acerca de los tipos de ataques más comunes en servidores web, en qué consisten, y cómo se pueden evitar.

Los ataques a servidores web más comunes son los ataques de inyección, ataques DDoS, de fuerza bruta y Cross Site Scripting.

- Los ataques de inyección de código consisten en introducir mediante formularios consultas sql a ejecutar en nuestra base de datos, pudiendo conseguir acceso a datos que creíamos seguros. Es uno de los ataues más fáciles de realizar, aunque podemos evitarlos poniendo atención en los lugares donde el usuario nos pasa información, comprobando que no puede realizar de ningún modo una consulta.
- La denegación de servicio (DoS) o denegación de servicio distribuida(DDoS) son las formas más comunes para saturar nuestros servidores y paralizar el funcionamiento. Se realizan haciendo que un ordenador intente inundar un servidor con paquetes. En DDoS, los servidores son amenazados por muchos dispositivos distribuidos Se dividen en ataques de volumen, donde el ataque intenta desbordar el ancho de banda, los ataques de protocolo, donde se intentan consumir servicios o recursos de la red y los ataques a aplicaciones, donde las peticiones se hacen para explotar el niver web. La solución a esto consiste en disponer de cortafuegos o un buen sistema de seguridad que identifique rápidamente si se trata de un ataque de denegación de servicio y repeler a la máquina o máquinas que lo estén realizando.
- Los ataques de Fuerza bruta consisten en probar todas las combinaciones de nombre de usuario y contraseña en una página web. Buscan contraseñas débiles para tener acceso rápidamente. Para evitar esto, lo más sencillo es usar contraseñas que sean seguras.
- Los ataques de Cross Site Scripting consisten en inyectar en páginas web un código en JavaScript o un lenguaje similar para obtener información de usuarios que confían en esa web sin que ellos se percaten.

## Ejercicios Tema 7: ALMACENAMIENTO DE DATOS

**Ejercicio 1:** ¿Qué tamaño de unidad de unidad RAID se obtendrá al configurar un RAID 0 a partir de dos discos de 100 GB y 100 GB?
¿Qué tamaño de unidad de unidad RAID se obtendrá al configurar un RAID 0 a partir de tres discos de 200 GB cada uno?

El RAID 0 lo que hace es mejorar el rendimiento y aumentar la capacidad del disco final, por lo que la capacidad final de la unidad RAID con dos discos de 100GB será de 200GB.

Como hemos visto en el anterior ejercicio al tratarse de un RAID se sumna las capacidades de cada disco por que la unidad RAID será de 600GB.

**Ejercicio 2:** ¿Qué tamaño de unidad de unidad RAID se obtendrá al configurar un RAID 1 a partir de dos discos de 100 GB y 100 GB?¿Qué tamaño de unidad de unidad RAID se obtendrá al configurar un RAID 1 a partir de tres discos de 200 GB cada uno?

El tamaño del RAID será de 100GB puesto que la principal caracteristica del RAID 1 es la réplica de los datos en ambos discos.

El tamaño del RAID será de 200GB puesto que la información se replica en los tres discos.

**Ejercicio 3:** ¿Qué tamaño de unidad de unidad RAID se obtendrá al configurar un RAID 5 a partir de tres discos de 120 GB cada uno?

La unidad RAID sería de 240GB quedando un disco de 120GB como disco de paridad.

**Ejercicio 4:** Buscar información sobre los sistemas de ficheros en red más utilizados en la actualidad y comparar sus características. Hacer una lista de ventajas e inconvenientes de todos ellos, así como grandes sistemas en los que se utilicen.

Los sistemas de ficheros en red más utilizados son NFS, el programa Samba y Server Message Block.

- Destacando ampliamente NFS. NFS está dividido en dos partes, servidor y clientes. Los clientes acceden de manera remota a los sdatos almacenados en el servidor. De esta manera las estaciones de trabajo locales utilizan menos espacio de disco, pues los datos se encuentran centralizados, aunque pueden ser accedidos y modificados por varios usuarios. También se puede acceder a través de la red a dispositivos de almacenamiento como disqueteras o lectores CD-ROM.

- Server Message Block (SMB) es un protocolo de red que permite compartir archivos e impresoras entre nodos de una red usado principalmente en ordenadores con Windows y DOS. Fue originalmente inventado por IBM aunque la versión más utilizada hoy en día es la modificada por Microsoft, llamada CIFS e incluye soporte para enlaces simbólicos, enlaces duros y mayores tamaños de archivo. Samba es una implementación libre del protocolo de archivos compartidos de Windows para sistemas Unix. Está basado en Server Message Block (De hecho su nombre surge al añadirle dos vocales a SMB). Funciona configurando directorios Unix como recursos para compartir a través de la red. Éstos aparecen como carpetas de red para los usuarios de Windows. Se permite dar distintos permisos según el usuario.

**Configurar en una máquina virtual un servidor NFS. Montar desde otra máquina virtual en la misma subred la carpeta exportada y comprobar que ambas pueden acceder a la misma para lectura y escritura.**

Lo primero que hacemos es descargar e instalar el servidor NFS. Lo realizamos mediante el siguiente comando:

    apt-get install nfs-kernel-server portmap

Una vez instalado el servidor NFS creamos un directorio ejecutando la siguiente orden:

    mkdir /var/nfs/

Una vez hemos creado el directorio le cambiaremos los permisos de acceso al directorio ejecutando la siguiente orden:

    chown nobody:nogroup /var/nfs

Exportaremos los directorios desde el fichero /etc/exports

    nano /etc/exports

una vez exportados editaremos dicho fichero añadiendole las siguientes sentencias:

    /var/nfs        192.168.64.128(rw,sync,no_subtree_check)

Una vez hemos editado el fichero le aplicamos la configuración con el comando:

    exportfs -a.

Una vez aquí pasaremos a la máquina que hará de cliente e instalamos el cliente NFS.

    apt-get install nfs-common portmap

Montamoremos el directorio ejecutando las siguientes ordenes:

    mkdir -p /mnt/nfs/var/nfs
    mount 192.168.64.128:/var/nfs /mnt/nfs/var/nfs

Para comprobar su funcionamiento tal simple como crear un fichero en el servidor y en el directorio montado en el NFS cliente debe aparecernos si realizamos un ls en el directorio.
