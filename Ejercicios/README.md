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

---

**Ejercicio 2:** 
