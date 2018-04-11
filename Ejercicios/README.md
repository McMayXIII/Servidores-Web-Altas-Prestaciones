# Ejercicios de Teoría

## Ejercicios del tema 1: INTRODUCCIÓN

**Ejercicio 1:** Buscar información sobre las tareas o servicios web para los que se usan más los programas que comentamos al principio de la sesión:

  - **Apache:** el servidor HTTP Apache es un servidor web HTTP de código abierto, para plataformas Unix (BSD, GNU/Linux, etc.), Microsoft Windows, Macintosh y otras, que implementa el protocolo HTTP/1.12​ y la noción de sitio virtual.

  - **Nginx:** (pronunciado en inglés “engine X”) es un servidor web/proxy inverso ligero de alto rendimiento y un proxy para protocolos de correo electrónico (IMAP/POP3).2​

  - **Thttpd:** es un programa de software que se ejecuta en segundo plano de un servidor web y espera las solicitudes del servidor entrante. Este daemon responde la solicitud automáticamente y sirve el hipertexto y los documentos multimedia a través de Internet utilizando HTTP.

  - **Cherokee:** es un servidor web multiplataforma.​ Su objetivo es ser rápido y completamente funcional, sin dejar de ser liviano comparado con otros servidores web.​ Está escrito completamente en C. Puede usarse como un sistema embebido y soporta complementos para aumentar sus funcionalidades. Es software libre, disponible bajo la Licencia Pública General de GNU.

  - **Node.js:**  es un entorno en tiempo de ejecución multiplataforma, de código abierto, para la capa del servidor (pero no limitándose a ello) basado en el lenguaje de programación ECMAScript, asíncrono, con I/O de datos en una arquitectura orientada a eventos y basado en el motor V8 de Google. Fue creado con el enfoque de ser útil en la creación de programas de red altamente escalables, como por ejemplo, servidores web.​ Fue creado por Ryan Dahl en 2009 y su evolución está apadrinada por la empresa Joyent, que además tiene contratado a Dahl en plantilla

---

## Ejercicios tema 2: ESCALABILIDAD Y DISPONIBILIDAD

**Ejercicio 1:** Calcular la disponibilidad del sistema si tenemos dos réplicas de cada elemento (en total 3 elementos en cada subsistema).

|Component  | 1 elemento | 2 elementos | 3 elementos |
|----  | ----    | ---    | ----       |
|Web  | 85 % | 97.75 % | 97.75 % + (1 - 97.75 %) * 85 % = 99.6625 % |
|Application  | 90 % | 99 % | 3 elementos |
|Database  | 99.9 % | 99.9999 % | 3 elementos |
|DNS  | 98 % | 99.96 % | 3 elementos |
|Firewall  | 85% | 97.75 % | 3 elementos |
|Switch  | 99 % | 99.99 % | 3 elementos |
|Data Center  | 99.99 % | 99.99% | 3 elementos |
|ISP  | 95 % | 99.75 % | 3 elementos |
|Total  |     |     |   |
