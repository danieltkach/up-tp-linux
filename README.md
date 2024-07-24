
# TRABAJO PRÁCTICO
 Condiciones generales 1
 Armado de Entorno 2
 Servidores 2
 Storage 3
 Redes 4
 Backup 4
 Entregables 5

## Condiciones generales
a. Este trabajo práctico se debe desarrollar en una máquina virtual con
GNU/Linux Debian instalado, la cual debe descargarse de Blackboard, ya
que está preparada para el trabajo práctico. Esta debe importarse como un
sistema virtualizado. Las instrucciones para la importación se encuentran en el
sitio de Oracle
b. Los Grupos que realizaran la práctica no deben contener más de 6 integrantes
y será conformado por uds dentro de BlackBoard.
c. Al momento de la evaluación por parte del docente, tener presente que cada
punto no cumplido, resta puntuación en la evaluación.

## 1.Armado de entorno
### 1. Se debe tener presente que a la máquina virtual en cuestión no se le conoce la clave
de root, por lo que es necesario realizar el blanqueo de la misma previo a
realizar las actividades. La clave debe cambiarse a “palermo” (sin las
comillas).
2. La máquina virtual está dividida en 9 partes, se deben descargar y ensamblar con el
compresor rar. Puede ser utilizado winrar.
3. Se deben establecer el nombre a la respectiva máquina como TPServer

## 2.Servicios
1. SSH. Que sea instalado y funcionando un servicio SSH, que permita ingresar al
usuario root, con la clave pública que se haya en BlackBoard y sera usada para el
servidor.
2. WEB. Que tenga instalado y funcionando un servicio de Apache con soporte para el
lenguaje PHP (Instalar PHP7.3 o superior). Debe servir el archivo index.php que se
descarga de BlackBoard.
3. MYSQL. Que tenga instalado y funcionando un servicio de MARIADB. A este motor
se le debe cargar el script sql llamado “db.sql” que se halla en BlackBoard.
NOTA: Tener presente que solo se puede probar desde la máquina anfitriona o de la misma
máquina virtual.


## 3.Storage
1. Se deberá agregar un disco nuevo de 10 GB con 2 particiones estándar (83 en la
tabla de particiones).
2. El tamaño de los mismos es:
/www_dir: 3GB
/backup_dir: 6GB.
3. El archivo de php llamado index.php, debe estar en su respectivo directorio
(/var/www/html), pero para el trabajo practico deberán mover el mismo directorio
montado con el nombre /www_dir. Para que apache2 encuentre la nueva
configuración deberán cambiar el archivo de configuración correspondiente en el
directorio de la aplicación.
4. El directorio /backup_dir sera utilizado para alojar los archivos del punto 5 y deberá
estar montado en la partición creada para tal fin.
5. Ambos directorios deben ser configurados para que se monten automáticamente al
inicio del sistema operativo.
1 Puede ser que el dispositivo sea sdb, sdc o sdd, por eso el “*”.


## 4.Redes
1. La placa deben ser configurada con el fin de aceptar una IP ESTÁTICA.
2. El archivo de configuración, debe tener una ip del rango correspondiente a la
maquina anfitriona, y debe incluir ADDRESS, NETMASK, y GATEWAY

## 5.Backup
1. Se deberá realizar backup por medio de UN script de desarrollo propio
denominado “backup_full.sh” ubicado en un directorio dentro de “/opt/scripts” a
los directorios que se mencionan, con su correspondiente planificación:
a. TODOS LOS DÍAS a las 0 hs: /var/logs
b. LOS LUNES, MIÉRCOLES, VIERNES a las 23 hs: /www_dir
2. Los nombres de los archivos tienen que tener relación con lo respaldado y contener
dentro del nombre la fecha en formato ANSI (YYYYMMDD), por ejemplo: para /etc,
sería “etc_bkp_20240302.tar.gz”
3. Todos los archivos de backup generados deben guardarse en el
filesystem /backup_dir.
4. El script de backup que se desarrolle debe tener la validación de que los filesystem
origen y destino se encuentren disponibles, es decir, que existan y/o estén
montados según corresponda, previamente a la ejecución del backup.
5. Ambos (origen y destino) deben ser pasados como argumentos al script.
6. Adicionalmente, el script debe poseer una opción de ayuda “-h”. Esto implica que el
script debe manejar que los argumentos no hayan sido escritos por el usuario.
7. El script debe ser agregado al cron

## 6.Entregables
1. Los entregables consisten en los directorios /root, /etc, /opt, /var, /www_dir
y /backup_dir. Todos ellos comprimidos individualmente en formato tar.gz y
subidos al repositorio github que cada equipo haya informado anteriormente.
2. Se debe entregar un diagrama topológico de la infraestructura armada
NOTA: De ser algunos de los archivos de tamaño considerable, usar el comando split.

Lic. Adolfo Deluca – Lic. Cristian Damiano◾
