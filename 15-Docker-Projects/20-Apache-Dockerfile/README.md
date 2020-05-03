# Apache Dockerfile

Ich habe ein Dockerfile erstellt, welches einen Apache Webserver installiert. Dieses Image habe ich anschliessend auf [mein Docker-Hub](https://hub.docker.com/r/thefortium/apache2_ubuntu_sample) geladen.

Vom Docker-Hub kann das Image nun mit folgendem Befehl heruntergeladen werden:
```
docker pull thefortium/apache2_ubuntu_sample
```

Man kan das Image auch direkt ausführen, am einfachsten mit dem folgenden Befehl:
```
docker run -itd -p 8080:80 thefortium/apache2_ubuntu_sample
```
