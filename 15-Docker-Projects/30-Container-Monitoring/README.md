<img align="left" width="80" height="80" src="/99-Images/monitoring.png" alt="Monitoring Logo">

# Monitoring

## Docker-Monitoring

In diesem Kapitel behandle ich das Monitoring von Docker Containern. Die eifachste Möglichkeit um den Docker Daemon zu überwachen ist mit dem Befehl `docker stats`.

Mit diesem Befehl wird eine wie im folgenden Schema aufgezeigte Übersicht über die einzelenen Container und deren Status angezeigt.

```
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
```

Möchte man die Logs einsehen, dann kann dies mit Folgenden Befehl gemacht werden:

```
docker logs
```
Mit aus diesen Docker Logs kann man diverse Fehler und andere Informationen über die Container auslesen.


## Externes Monitoring

### Prometheus
Auf der Docker-Website ist ein Artikel über das Monitoring mit dem Tool "Prometheus" zu finden. Dieses Tool bietet viele Funktionen und ein Web-Interface, jedoch ist dieses Tool auf Docker Swarm mit grösseren Umgebungen ausgelegt.

### Weitere Softwaren
Alternativ zu dem Auf der Docker-Website erwähnten Tool, gibt es unzälige zusätzliche Softwaren, wie zB. cAdvisor, Scout, CheckMK etc. Diese Software bieten verschiedene Funktionen, arten der Services (Container, dedizierter Server oder installation auf dem Host), sowie verschiede Funktionsumfänge. Viele Softwaren sind Kostenlos, jedoch gibt es auch einige für die man Bezahlen muss.