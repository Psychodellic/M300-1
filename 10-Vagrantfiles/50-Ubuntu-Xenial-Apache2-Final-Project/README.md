<img align="left" height="80" src="/99-Images/ldap.png" alt="LDAP Logo">

# Ubuntu LDAP & phpLDAPAdmin, MySQL & phpMyAdmin, Reverse Proxy & Firewalls

##### Installation von Ubuntu 16.04 Xenial und 18.04 Bionic inklusive LDAP, MySQL und eines Reverse Proxys.

**Vorsicht:** Das Verzechnis `/var/lib/ldap` kann mit der Standardimplementation von VirtualBox nicht Synchronisiert werden. Die LDAP Konfiguration ist somit volatil und get bei einem `vagrant destroy` verloren. Es sollten andere Varianten mit SMB, NFS oder Rsync implementiert werden (dies erfordert jedoch Host-Konfiguration).

## Allgemeine Information

Dieses Vagrantfile erstellt einen LDAP Server, einen MySQL Server, einen Reverse Proxy und Konfiguriert die Firewalls dieser Server. Der Lokale Port `8080` wird mit dem Proxy Server als Port `80` weiteregeleitet. Der Provider wurde auf Virtualbox gesetzt. Dies erübrigt den Parameter `--provider virtualbox` im `vagrant up` Befehl.

Die Hostnames, Domain und Root-Passwörter für die Server wird im vagrantfile per Variable festgehalten.

Folgendes sind die Standardwerte:

 * LDAP-Server
   - Hostname: ldap
   - Domain: m300.local
   - IP: 192.168.50.10
   - LDAP-Admin Password: vagrant
 * MySQL-Server
   - Hostname: db
   - Domain: m300.local
   - IP: 192.168.50.20
   - MySQL-Root Password: vagrant
 * MySQL-Server
   - Hostname: proxy
   - Domain: m300.local
   - IP: 192.168.50.30
