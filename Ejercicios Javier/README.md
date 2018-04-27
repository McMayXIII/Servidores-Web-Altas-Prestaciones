## Tema 1 | Introducción y conceptos básicos

**Ejercicio 1**: Buscar información sobre las tareas o servicios web comentados
a principio del tema.

  + **Apache**: El servidor HTTP Apache es un servidor web HTTP de código abierto, para plataformas Unix (BSD, GNU/Linux, etc.), Microsoft Windows, Macintosh y otras, que implementa el protocolo HTTP/1.12​ y la noción de sitio virtual. Cuando comenzó su desarrollo en 1995 se basó inicialmente en código del popular NCSA HTTPd 1.3, pero más tarde fue reescrito por completo.. Apache es un proyecto de código
  abierto y uso gratuito, multiplataforma, muy robusto y que destaca por su
  seguridad y rendimiento. Además, Apache nos permite configurar un Hosting
  Virtual basado en IPs o en nombres, es decir, tener varios sitios web en un
  mismo equipo (por ejemplo: nombreweb1.com, nombreweb2.com,….) o, establecer
  distintos niveles de control de acceso a la información incluyendo el soporte
  a cifrado SSL utilizando protocolo seguro HTTPS.

  + **Ngingx**: Es un servidor web HTTP de código abierto que también incluye
  servicios de correo electrónico con acceso al Internet Message Protocol (IMAP)
  y al servidor Post Office Protocol (POP). Además, NGINX está listo para ser
  utilizado como un proxy inverso. En este modo, NGINX se utiliza para equilibrar
  la carga entre los servidores back-end, o para proporcionar almacenamiento en
  caché para un servidor back-end lento.

  + **Hypertext** Transfer Protocol o HTTP (en español protocolo de transferencia
    de hipertexto) es el protocolo usado en cada transacción de la World Wide Web.
    HTTP fue desarrollado por el World Wide Web Consortium y la Internet
    Engineering Task Force, define la sintaxis y la semántica que
    utilizan los elementos de software de la arquitectura web (clientes,
    servidores, proxies) para comunicarse. Es un protocolo orientado a
    transacciones y sigue el esquema petición-respuesta entre un cliente y un
    servidor.

  + **Cherekee**: El servidor web Cherokee es uno de los servidores de nueva
  generación llamados ligeros que mejora notablemente el rendimiento ofrecido
  por el más usado Apache HTTPD soportando más usuarios concurrentes, aceptando
  más peticiones por segundo y consumiendo menos memoria. Quizá no tenga toda la
  versatilidad de un servidor Apache HTTPD pero para la mayoría de los escenarios
  es más que suficiente. algunas de las características que soporta: FastCGI,
  SCGI, PHP, CGI, SSI, TLS y conexiones cifradas SSL, host virtuales,
  autenticación, codificación al vuelo, balanceo de carga, archivos de log
  compatibles con apache, balanceador de base de datos, actualizaciones sin
  parada del servicio, proxy HTTP inverso y mucho más.

  + **Node.js**: Node.js es una librería y entorno de ejecución de E/S dirigida
  por eventos y por lo tanto asíncrona que se ejecuta sobre el intérprete de
  JavaScript creado por Google V8. Lo cierto es que está muy de moda aunque no
  es algo nuevo puesto que existen librerías como Twisted que hacen exactamente
  lo mismo pero si es cierto que es la primera basada en JavaScript y que tiene
  un gran rendimiento.  es un entorno Javascript del lado del servidor, basado
  en eventos. Node ejecuta javascript utilizando el motor V8, desarrollado por
  Google para uso de su navegador Chrome. Aprovechando el motor V8 permite a
  Node proporciona un entorno de ejecución del lado del servidor que compila y
  ejecuta javascript a velocidades increíbles. El aumento de velocidad es
  importante debido a que V8 compila Javascript en código de máquina nativo, en
  lugar de interpretarlo o ejecutarlo como bytecode. Node es de código abierto,
  y se ejecuta en Mac OS X, Windows y Linux.


--------------------------------------------------------------------------------

## Tema 2 | Alta disponibilidad y escalabilidad en servidores web

**Ejercicio 1**:  Calcular la disponibilidad del sistema si tenemos dos réplicar
de cada elemento (en total 3 elementos en cada subsistema).

| Componente     | 2 replicas |  Calculo 3ª Réplica                        | 3 replicas |
|--------------| ------------ | ---------------------------------------- | ------------- |
| Web          | 97,75%       | 97,75% + (1 – 97,75%) * 97,75%           | 99,949375%    |
| Application  | 99%          | 99% + (1 – 99%) * 99%                    | 99,99%        |
| Database     | 99,9999%     | 99,9999% + (1 – 99,9999%) * 99,9999%     | 100%          |
| DNS          | 99,96%       | 99,96% + (1 – 99,96%) * 99,96%           | 99,999984%    |
| Firewall     | 97,75%       | 97,75% + (1 – 97,75%) * 97,75%           | 99,949375%    |
| Switch       | 99,99%       | 99,99% + (1 – 99,99%) * 99,99%           | 99,999999%    |
| Data Center  | 99,99%       | 99,99% + (1 – 99,99%) * 99,99%           | 99,999999%    |
| ISP          | 97,75%       | 99,75% + (1 – 99,75%) * 99,75%           | 99,999375%    |


_Total_ = 99,949375% \* 99,99% \* 100% \* 99,999984% \* 99,949375% \* 99,999999% \*
99,999999% \* 99,999375% = 99,8881435%

**Ejercicio 2**: Buscar frameworks y librerías para diferentes lenguajes que
permitan hacer aplicaciones altamente disponibles con relativa facilidad.

  + Css: Foundation.
  + JavaScript: jQuery, bootstap, Backbone JS, Ember JS, NodeJS.
  + Html: Browserify.


**Ejercicio 3**: ¿Cómo analizar el nivel de carga de cada uno de los subsistemas
en el servidor? Buscar herramientas y aprender a usarlas.

  + Apache Benchmark

El uso ya se ha visto en practicas, un ejemplo sería el siguiente:

~~~~~~~
  ab -n 100000 -c 30 -g grafica.data http://10.0.2.14/loadTesting/test
~~~~~~~

  + n - Cantidad de peticiones que deseamos enviar.
  + c - Cantidad de conexiones concurrentes.
  + g - Generar una gráfica de gnuplot para apreciar mejor los resultados.


**Ejercicio 4**: Buscar ejemplos de balanceadores software y hardware (productos
comerciales), productos comerciales para servidores de aplicaciones y productos
comerciales para servidores de almacenamiento.

  + Balanceadores Software: Haproxy, Nginx, LVS, Ultra Monkey, Pound.
  + Balanceadores Hardware: LoadMaster, Syswan.

--------------------------------------------------------------------------------
