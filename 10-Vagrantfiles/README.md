<img align="left" width="80" height="80" src="/99-Images/vagrant.png" alt="Vagrant Logo">

# Vagrantfiles

###### Alle Vagrant-Projekte, welche ich in diesem Modul erstellt habe

## Quick Links

  * [Ubuntu Xenial Default](./00-Ubuntu-Xenial-Default)
  * [Ubuntu Xenial Apache2](./10-Ubuntu-Xenial-Apache2)
  * [Ubuntu Xenial & MySQL & PHP-MyAdmin](./20-Ubuntu-Xenial-Apache2-MySQL-PHPMyAdmin)
  * [Ubuntu Xenial UFW](./30-Ubuntu-Xenial-UFW)
  * [Ubuntu Xenial Apache2 Reverse Proxy](./40-Ubuntu-Xenial-Apache2-ReverseProxy)
  * [Ubuntu Xenial Apache2 Final Project](./50-Ubuntu-Xenial-Apache2-Final-Project)

## Inhalt

 * [Allgemeine Informationen](#allgemeine-informationen)
 * [Netzwerkübersicht](#netzwerk%c3%bcbersicht)


## Allgemeine Informationen

Diese Vagrantfiles habe ich per Editor erstellt oder per `vagrant init` erzeugt. Diese Vagrantfiles automatisieren einige VMs, wie zB. Apache2 oder MySQL. In diesen einzelnen Projekten kann man auch meinen Lernfortschritt erkennen.


## Netzwerkübersicht

![Netzwerkplan](/99-Images/netzwerkplan.png)

Das Netzwerk wird generell wie im Bild gezeigt aussehen. Das TBZ Netzwerk ist per NAT mit dem Internet verbunden. Der Laptop ist per Kabel oder WLAN mit dem TBZ Netzwerk verbunden. Für die Vagrant VMs wird nun ein NAT Netzwerk in Virtualbox erstellt. Vor der Vagrant VM befindet sich ggf. noch eine UFW Firewall. Wenn nun ein Port in Vagrant gemappt wird, dann wird dieser Auf dem Laptop gemappt. Auf wunsch kann noch die IP-Addresse ausgewählt werden (Beispielsweise nur localhost (127.0.0.1) oder die TBZ-IP oder die IP eines anderen Netzwerkes, mit dem der Laptop verbunden ist).


> [Zurück zum Globalen Inhalt](../../../)