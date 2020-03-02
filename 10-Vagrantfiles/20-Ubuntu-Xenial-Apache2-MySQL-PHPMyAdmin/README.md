<img align="left" width="80" height="80" src="/99-Images/mysql.png" alt="MySQL Logo">

# Ubuntu Xenial Apache2 & MySQL & PHPMyAdmin

##### Installation von Ubunutu 16.04 Xenial inklusilve des Apache2 Webservers, der MySQL Datenbank & PHPMyAdmin

Dieses Vagrantfile erstellt eine Ubuntu Xenial VM. An diese VM wird der `Local-Port 8080` an den `Guest-Port 80` weitergeleitet.
Der Provider wird auf Virtualbox gesetzt. Dies erübrigt den Parameter `--provider virtualbox` im `vagrant up` Befehl.

 * Das Verzeichnis `/var/www/` wird ins Verzeichnis `./web` geshared
 * Das Verzeichnis `/var/lib/mysql` wird ins Verzeichnis `./mysql` geshared

Dadurch bleiben die Daten von Apache bzw. MySQL erhalten.

Dieses Vagrantfile kann mit folgendem Befehl ausgeführt werden:

```
vagrant up
```