# Práctica 3 - Balanceo de carga #

 ***

## 1. Objetivos de la práctica ##

En esta práctica configuraremos una red entre varias máquinas de forma que tengamos un balanceador que reparta la carga entre varios servidores finales.

El problema a solucionar es la sobrecarga de los servidores. Se puede balancear cualquier protocolo, pero dado que esta asignatura se centra en las tecnologías web, balancearemos los servidores HTTP que tenemos configurados.

De esta forma conseguiremos una infraestructura redundante y de alta disponibilidad.

***

## 2. Alternativas para realizar balanceo de carga ##

balanceo por software. Existen varias alternativas para balancear HTTP por software:
- HaProxy: (http://haproxy.1wt.eu/)
- Pound: (http://www.apsis.ch/pound/)
- Varnish: (http://varnish-cache.org)
- NginX: (http://nginx.org/)
- Lighty: (http://www.lighttpd.net/)
- Apache: (http://httpd.apache.org/)

Los dos primeros son balanceadores y proxy, pueden balancear cualquier tipo de tráfico. Los últimos tres son servidores web que pueden hacer estas funciones (Apache necesita usar los módulos mod_proxy o mod_proxy_balancer). Lighttpd es un servidor web liviano que soporta balanceo de carga pero no mantiene la sesión del usuario. Por último, nginX es otro servidor web liviano que sí soporta sesiones.

De todas estas opciones utilizaremos nginx configurado como proxy, y haproxy.

Así pues, para esta práctica, debemos crear la siguiente organización de red:

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practicas/Practica%302/image/img01.jpg)

Como se puede ver, debemos tener en ejecución las máquinas servidoras finales (las que hicimos en la Práctica 2 y que ejecutan el servidor Apache).

Además, crearemos una tercera máquina en la que no debe haber ningún software que se apropie del puerto 80, ya que lo necesitará el software de balanceo para recibir las peticiones HTTP desde fuera de la granja web. Así pues, en esta máquina-3 no podemos tener instalado el Apache (o al menos, que no esté en ejecución).

Una vez instalemos y configuremos el software de balanceo (nginx o haproxy), desde una máquina externa a la granja web (puede ser un terminal en el ordenador anfitrión o puede ser una cuarta máquina virtual) ejecutaremos la herramienta curl para hacer peticiones HTTP a la IP de la máquina balanceadora (como vimos en teoría, la VIP de nuestro sistema web).
