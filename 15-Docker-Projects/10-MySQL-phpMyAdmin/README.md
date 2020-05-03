<img align="left" height="80" src="/99-Images/mysql.png" alt="MySQL Logo">

# MySQL & phpMyAdmin

##### Compose-File zur aufsetzung von MySQL & phpMyAdmin

Dieses Compose-File erstellt einen MySQL Container, sowie einen phpMyAdmin Container. Der MySQL Container beinhaltet eine MySQL-Datenbank, welche ein Volume vom Verzeichnis `./db` hat, damit die Datenbank persistent bleibt und vom Host aus gesichert, veschoben etc. werden kann. Damit die Datenbank von einem externen Service verwendet werden kann, müsste der `TCP-Port 3306` an den Host weitergeleitet werden. Aktuell dient jedoch das phpMyAdmin Web-Interface als Verwaltungs-Interface. Das phpMyAdmin Web-Interface wird an den `TCP-Port 8080` auf dem Host weitergeleitet. 

Das Login sieht aktuell wie folgt aus:

| Username | Password |
|:--------:|:--------:|
|   root   |   M300   |


Dieses Docker-Compose File kann mit folgendem Befehl ausgeführt werden:

```
docker-compose up -d
```
###### Das "-d" sorgt dafür, dass der Dialog der Container nicht angezeigt wird. Wird dies nicht gemacht, kann man zwar den Log in der Konsole sehen, jedoch wird die Konsole gleichzeitig auch mit den Container Logs Blokiert.