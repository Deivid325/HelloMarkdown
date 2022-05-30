# ICINGA2
# Tutorial Icinga2 - Instalación en Ubuntu Linux
Utilice apt-get para instalar los paquetes necesarios.
```bash
apt-get update
apt-get install apt-transport-https wget gnupg
```
Descargar e instalar la clave del repositorio Icinga2.
```bash
wget -O - https://packages.icinga.com/icinga.key | apt-key add -
```
Agregue el repositorio oficial de Icinga2 a la base de datos APT.
```bash
echo "deb https://packages.icinga.com/ubuntu icinga-${DIST} main" > /etc/apt/sources.list.d/${DIST}-icinga.list
echo "deb-src https://packages.icinga.com/ubuntu icinga-${DIST} main" >> /etc/apt/sources.list.d/${DIST}-icinga.list
```
Actualice la base de datos APT e instale el paquete Icinga2.
```bash
apt-get update
apt-get install icinga2
```
Instale los plugins de monitoreo estándar del Icinga2.
```bash
apt-get install monitoring-plugins
```
Lista Icinga2 características instaled.
```bash
icinga2 feature list
Disabled features: api command compatlog debuglog elasticsearch gelf graphite influxdb livestatus opentsdb perfdata statusdata syslog
Enabled features: checker mainlog notification
```
Habilite el servicio Icinga2 para que se inicie automáticamente durante el tiempo de arranque
```bash
systemctl enable icinga2
```
¡Felicitaciones! Ha terminado la instalación de Icinga2.


### Tutorial Icinga2 - Instalación de MySQL
Instale el paquete icinga2-ido-mysql.
Esto permitirá al servidor Icinga2 almacenar la configuración en Mysql.
```bash
apt-get update
apt-get install icinga2-ido-mysql
```

Habilite la función ido-mysql del Icinga 2.
![ido-mysql](https://github.com/Deivid325/HelloMarkdown/blob/main/1.1.png?raw=true)

Configurar la base de datos para icinga2-ido-mysql con dbconfig-common
![icinga2-ido-mysql](https://github.com/Deivid325/HelloMarkdown/blob/main/1.2.png?raw=true)

Habilite la característica ido-mysql.
```bash
icinga2 feature enable command  ido-mysql
```

Reiniciar Icinga2
```bash
service icinga2 restart
```
Instale el servicio de base de datos MySQL.

```bash
apt-get install mysql-server mysql-client
```
Acceda al servidor de bases de datos MySQL.

```bash
mysql -u root -p
```
Establezca una contraseña para el usuario raíz de MySQL.

```bash
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Password123#@!';
```
En nuestro ejemplo, establecemos la contraseña raíz "Password123#@!".
