<img align="left" width="80" height="80" src="/99-Images/docker.png" alt="Docker Logo">

# Docker Projekte

###### Alle Docker-Projekte, welche ich in diesem Modul erstellt habe

## Quick Links

  * [MySQL & phpMyAdmin](./10-MySQL-phpMyAdmin)
  * [Container Monitoring](./20-Container-Monitoring)
  * [Container Absicherung](./30-Container-Absicherung)
  * [Nextcloud Projekt](./40-Final-Projekt-Nextcloud)

## Inhalt

 * [Allgemeine Informationen](#allgemeine-informationen)
 * [Netzwerkübersicht](#netzwerk%c3%bcbersicht)


## Allgemeine Informationen

Diese Docker Projekte habe ich mithilfe von Dockerfiles, Images oder Compose-Projekten erstellt. Diese Projekte setzen automatisiert eine gewisse Umgebung auf. Weitere Informationen zu den einzelnen Umgebungen findet sich in den jeweilgen Ordnern.


## Netzwerkübersicht

![Netzwerkplan](/99-Images/netzwerkplan_docker.png)

Das Netzwerk wird generell wie im Bild gezeigt aussehen. Das TBZ Netzwerk ist per NAT mit dem Internet verbunden. Der Laptop ist per Kabel oder WLAN mit dem TBZ Netzwerk verbunden. Anschliessend befindet sich auf dem Laptop eine VM, welche im Bridged Modus angeschlossen ist. Aus diesem Grunde wäre der Laptop eigendlich nicht Notwändig auf diesem Netzwerkplan. Anschliessend erstellt der Docker Deamon ein Standad Netzwerk, pro Projekt und gegebenenfalls zusätzliche Netze, wenn diese Nötig sind. Diese Netze sind Mit NAT angeschlossen, was heisst, dass die Container nach aussen Kommunizieren können, jedoch das äussere Netz nicht nach innen (Ohne Portforwarding). Wenn nun ein Port in Docker gemappt wird, dann wird dieser auf dem Interface der Docker-VM gemappt und die Kommunikation von aussen wird möglich. Auf wunsch kann noch die IP-Addresse ausgewählt werden (Beispielsweise nur localhost (127.0.0.1) oder die TBZ-IP oder die IP eines anderen Netzwerkes, mit dem der Docker-Host verbunden ist).


> [Zurück zum Globalen Inhalt](../../../)