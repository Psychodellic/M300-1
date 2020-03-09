<img align="left" width="80" height="80" src="/99-Images/user.png" alt="User Icon">

# Benutzer & Rechte

##### Informationen bezüglich der Benutzer & Rechte

## Inhalt

 * [Benutzer](#benutzer)
 * [Gruppen](#gruppen)
 * [Homeverzeichnis](#homeverzeichnis)
 * [Dateisystem](#dateisystem)


## Benutzer

Linux ist ein Multiuser-Betriebsystem, wie alle Unix-Systeme. Diese Verschiedenen bentutzer haben nicht immer die gleichen Rechte und Privilegien.

Neben den eigentlichen Benutzern, für die Benutzung von richtigen Personen existieren noch dieverse Systemdienste, welche ihren eigenen Konten haben.

| Benutzername  | Funktion                                             |
| ------------- | ---------------------------------------------------- | 
| `root`        | Der Systemadministrator unter Linux                  |
| `nobody`      | Wird von Prozessen als Benutzererkennung verwendet, wenn nur ein Minimum an Rechten vergeben werden soll  |
| `cupsys`      | Benutzer des Druckdienstes CUPS                      |
| `www-data`    | Benutzer des Webservers Apache                       |

Die Benutzer findet man in der Datei `/etc/passwd`. Die Passwörter werden in der Datei `/etc/shadow` abgespeichert.

Der Systemadministrator "root" hat alle Rechte. Weil dieser kein Passwort besitzt kann man sich mit diesem Account nicht einloggen.

Grundsätzlich sollten Befehle, welche erhöte Rechte (root) verwenden mit dem sudo Befehl ausgeführt werden.

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

Jedoch kann man sich auch in die Root-Shell einloggen und anschliessend vom Benutzer root seine Konfigurationen tätigen.

```
$ sudo su
#
# exit
$
```
> Nun wird die Root-Shell durch das '#' idiziert.

Wer und wie (z.B. mit/ohne Passwort) ein Benutzer die erhöhten Rechte (sudo) verwenden darf, ist in der Datei `/etc/sudoers` bzw. im Verzeichnis `/etc/sudoers.d` festgehalten.


## Gruppen

Jeder Benutzer ist einer Hauptgruppe zugeordnet, kann daneben aber auch Mitglied weiterer Gruppen sein. Der Zugriff auf gewisse Hardware oder Dienste ist auf die Mitglieder einer bestimmten Gruppe beschränkt. So dürfen z.B. nur Benutzer, die zur Gruppe "audio" gehören, Klänge über die Soundkarte ausgeben. Möchte man nun einem Benutzer die Berechtigung für die Soundkarte geben, so erreicht man dies, indem man ihn in die Gruppe "audio" aufnimmt.

Die Gruppen stehen in der Datei `/etc/group`.


## Homeverzeichnis

Das Homeverzeichnis ist der Ort, an dem Benutzer ihre Daten ablegen können und an dem Programme ihre benutzerspezifischen Einstellungen hinterlegen. Dieser Order ist auch der Einstiegspunkt für die User-Shell. Nur hier haben die jeweiligen Benutzer vollre Schreib- und Leserechte. Und nur hier sollten die Benutzer ihre Daten ablegen.

Das Homeverzeichnis liegt typischerweise in `/home`, indem sich ein Persönlicher Ordner pro Benutzer befindet (z.B. `/home/test` für den Benutzer `test`).

Ausnahme ist dabei der root User und die System-User, wie z.B. `nobody`. Während dem der root User sein Persönliches verzeichnis unter `/root` hat. Haben die System-User meist nicht direkt ein Homeverzeichnis. Hier sollten allerdings auch keine Daten abgelegt werden.

Einstellungen und Konfigurationen werden meist in versteckten Ordnern abgelegt. Wenn ein Ordner mit einem Punkt beginnt (z.B. `.bashrc` oder `.ssh`) gilt dieser unter Linux als versteckt.

Das Zeichen "~" ist eine Abkürzung für das Homeverzeichnis. So kann man z.B. mit dem Befehl `cd ~/Downloads` ins Downloads verzeichnis, was beim User test den Pfad `/home/test/Downloads` ergeben würde.

Beim einloggen werden gewisse Konfigurationen ausgeführt:

 * /etc/profile.d
 * ~/.profile
 * ~/.bashrc

Im Verzeichnis `/etc/profile.d` sind die Globalen Konfigurationen abgelegt, welche für alle Benutzer ausgeführt werden.


## Dateisystem

Dateisysteme sind die Schnittstellen zwischen dem Betriebssystem und den Partitionen auf Datenträgern. Sie organisieren die geordnete Ablage von Daten.

Neben der Datenorganisation auf dem Datenträger kann ein Dateisystem noch zusätzliche Möglichkeiten zur Verfügung stellen. Zum Beispiel:
* Verzeichnisse und Unterverzeichnisse anlegen
* Datumsinformationen speichern (Erstellungsdatum, letzte Änderung, Zugriff)
* Lange Dateinamen verwenden
* Gross- und Kleinschreibung für Dateinamen berücksichtigen
* Sonderzeichen für Dateinamen ermöglichen (z.B. Leerzeichen)
* Rechteverwaltung zur Zugriffssteuerung auf Dateien bzw. Verzeichnisse
* Journaling-Funktionen

**Hinweis:** <br> 
> Gross- & Kleinschreibung von Ordnern und Dateien wird unter Linux – im Gegensatz zu Windows – berücksichtigt. 
> Beispiel.doc und beispiel.doc sind zwei unterschiedliche Dateien.

**Dateieigenschaften**
UNIX-Systeme (z.B. Linux) verwalten ihre Dateien in einem virtuellen Dateisystem (VFS, Virtual File System). Dieses ordnet jeder Datei über eindeutig identifizierbare Inodes unter anderem folgende Eigenschaften zu:
* Dateityp (einfache Datei, Verzeichnis, Link, etc.)
* Zugriffsrechte (Eigentümer-, Gruppen- und sonstige Rechte)
* Grösse
* Zeitstempel
* Verweis auf Dateiinhalt

**Rechte**
Zugriffsrechte regeln, welcher Benutzer und welche Gruppe den Inhalt eines Verzeichnisses (ein Verzeichnis ist auch nur eine Datei) lesen, schreiben oder ausführen darf. Zum Beispiel:
```Shell
    $ ls -ldh /var/mail
    
    drwxrwsr-x 2 root mail 4.0K Jan 19 15:50 /var/mail
```

Der erste Buchstabe kennzeichnet den Dateityp (**d** = directory / **-** = file). Danach folgen die Zugriffsrechte.

Wenn man die Zugriffsrechten im vorherigen Beispiel in Dreiergruppen unterteilt erhält man die Rechte:
* rwx: Rechte des Eigentümers
* rws: Rechte der Gruppe
* r-x: Recht von allen anderen (others)

Die Bedeutung der Buchstaben sind wie folgt:
* **r** - Lesen (read): 
    * Erlaubt lesenden Zugriff auf die Datei. Bei einem Verzeichnis können damit die Namen der enthaltenen Dateien und Ordner abgerufen werden (nicht jedoch deren weitere Daten wie z.B. Berechtigungen, Besitzer, Änderungszeitpunkt, Dateiinhalt etc.).
* **w** - Schreiben (write): 
    * Erlaubt schreibenden Zugriff auf eine Datei. Für ein Verzeichnis gesetzt, können Dateien oder Unterverzeichnisse angelegt oder gelöscht werden, sowie die Eigenschaften der enthaltenen Dateien bzw, Verzeichnisse verändert werden.
* **x** - Ausführen (execute): 
    * Erlaubt das Ausführen einer Datei, wie das Starten eines Programms. Bei einem Verzeichnis ermöglicht dieses Recht, in diesen Ordner zu wechseln und weitere Attribute zu den enthaltenen Dateien abzurufen (sofern man die Dateinamen kennt ist dies unabhängig vom Leserecht auf diesen Ordner). Statt x kann auch ein Sonderrecht angeführt sein.
* **s** -Set-UID-Recht (SUID-Bit): 
    * Das Set-UID-Recht ("Set User ID" bzw. "Setze Benutzerkennung") sorgt bei einer Datei mit Ausführungsrechten dafür, dass dieses Programm immer mit den Rechten des Dateibesitzers läuft. Bei Ordnern ist dieses Bit ohne Bedeutung.
* **s** (S) Set-GID-Recht (SGID-Bit): 
    * Das Set-GID-Recht ("Set Group ID" bzw. "Setze Gruppenkennung") sorgt bei einer Datei mit Ausführungsrechten dafür, dass dieses Programm immer mit den Rechten der Dateigruppe läuft. Bei einem Ordner sorgt es dafür, dass die Gruppe an Unterordner und Dateien vererbt wird, die in diesem Ordner neu erstellt werden.
* **t** (T) Sticky-Bit: 
    * Das Sticky-Bit hat auf modernen Systemen nur noch eine einzige Funktion: Wird es auf einen Ordner angewandt, so können darin erstellte Dateien oder Verzeichnisse nur vom Dateibesitzer gelöscht oder umbenannt werden. Verwendet wird dies z.B. für /tmp.

Folgende Befehle dienen zum ändern der Rechte:

| Befehl        | Funktion                                             |
| ------------- | ---------------------------------------------------- | 
| `chmod`       | Dient zum Setzen der Dateirechte                     |
| `chown`       | Dient zum Ändern des Dateibesitzers                  |
| `chgrp`       | Dient zum Ändern der Gruppe einer Datei              |

