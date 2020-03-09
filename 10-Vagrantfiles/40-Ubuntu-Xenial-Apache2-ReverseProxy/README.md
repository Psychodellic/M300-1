<img align="left" height="80" src="/99-Images/proxy.png" alt="Proxy Logo">

# Ubuntu Xenial Apache2 & Reverse Proxy

##### Installation von Ubunutu 16.04 Xenial inklusilve des Apache2 Webservers und eines Reverse Proxys.

Dieses Vagrantfile erstellt eine Ubuntu Xenial VM. An diese VM wird der `Local-Port 8080` an den `Guest-Port 80` weitergeleitet.
Der Provider wird auf Virtualbox gesetzt. Dies erübrigt den Parameter `--provider virtualbox` im `vagrant up` Befehl.

 * Das Verzeichnis `/var/www/` wird ins Verzeichnis `./web` geshared
 * Das Verzeichnis `/etc/apache2` wird ins Verzeichnis `./apache` geshared

Dadurch bleiben die Daten von Apache erhalten und können seperat editiert werden.

Dieses Vagrantfile kann mit folgendem Befehl ausgeführt werden:

```
vagrant up
```

Die Apache Konfiguration (darunter auch der Reverse Proxy) kann im file `/etc/apache2/apache2.conf`. Weil das Verzeichnis `/etc/apache2` wird ins Verzeichnis `./apache` geshared ist, kann die Apache-Conf auch lokal editiert werden.

Die Datei `./apache/apache2.conf` wie folgt ergänzen:

```
ServerName localhost
```

Die Weiterleitungen sind z.B. in sites-enabled/001-reverseproxy.conf eingetragen:
```
# Allgemeine Proxy Einstellungen
ProxyRequests Off
<Proxy *>
    Order deny,allow
    Allow from all
</Proxy>

# Weiterleitungen master
ProxyPass /master http://master
ProxyPassReverse /master http://master
```

Nachdem die Konfigurationen geändert wurden muss zum abschluss der Apache Services neu gestartet werden.
```
$ sudo service apache2 restart
```
