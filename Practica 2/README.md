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

tar czf - directorio | ssh equipodestino 'cat > ~/tar.tgz'

Primero insertamos el comando mensionado anteriormente y luego comprobamos que se haya transmitido correctamente.

![img](https://github.com/McMayXIII/Servidores-Web-Altas-Prestaciones/blob/master/Practica%202/image/img01.png)

De esta forma en el equipo de destino tendremos creado el archivo tar.tgz Sin embargo, esto que puede ser útil en un momento dado, no nos servirá para sincronizar grandes cantidades de información. En ese caso, va mejor la herramienta rsync.
