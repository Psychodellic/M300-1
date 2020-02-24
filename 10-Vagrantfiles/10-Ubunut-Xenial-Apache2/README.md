# Ubuntu Xenial Apache2
##### Installation von Ubunutu 16.04 Xenial inklusilve des Apache2 Webservers

Dieses Vagrantfile erstellt eine Ubuntu Xenial VM. An diese VM wird der `Local-Port 8080` an den `Guest-Port 80` weitergeleitet.
Das Verzeichnis `/var/www/` wird in das aktuelle Verzeichnis geshared. Der Provider wird auf Virtualbox gesetzt.
Dies erübgt den Parameter `--provider virtualbox` im `vagrant up` Befehl.

Dieses Vagrantfile kann mit folgendem Befehl ausgeführt werden:

```
vagrant up
```
