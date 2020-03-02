<img align="left" width="80" height="80" src="/99-Images/firewall.png" alt="Firewall Logo">

# Ubuntu Xenial UFW

##### Installation von Ubunutu 16.04 Xenial inklusilve der UFW Firewall

Dieses Vagrantfile erstellt eine Ubuntu Xenial VM. Auf dieser VM wird die UFW Firewall installiert.

Dieses Vagrantfile kann mit folgendem Befehl ausgeführt werden:

```
vagrant up
```

Mit folgenden Befehlen kann man Firewall-Regeln erstellen. Dies lässt sich auch im Vagrantfile anpassen und so automatisiert erstellen.

```
# Eine SSH-Verbindung mit der VM aufbauen
vagrant ssh

# Eine Regel in der Firewall hinzuügen
sudo ufw allow from [IP] to any port [Portnummer]

# Alternativ auch ohne Port (alle Ports)
sudo ufw allow from [IP] to any
```

Am Ende muss die Firewall noch aktiviert werden. Dazu aber bitte zuerst eine Regel für den SSH-Zugang erstellen, ansonsen wird SSH nichtmehr möglich sein.

```
# Default allow SSH (es wird Empfohlen die IP zu definieren, für mehr sicherheit.)
sudo ufw allow from any to any port 22

# Firewall & Regeln aktivieren
sudo ufw enable

```
