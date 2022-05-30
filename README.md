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
Ya habríamos terminado la instalación de Icinga2.
