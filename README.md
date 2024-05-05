# docker_Test

Virtualisierung vs. Containerisierung:

Virtualisierung ist die Erstellung einer virtuellen Version eines Betriebssystems, das auf einer physischen Hardware läuft. Es emuliert Hardware, sodass mehrere Betriebssysteme auf derselben Hardware laufen können.

Containerisierung hingegen ist eine Methode zur Bereitstellung und Ausführung von Anwendungen in isolierten Umgebungen, sogenannten Containern. Container teilen sich den Kernel des Host-Betriebssystems und laufen auf einer einzigen Betriebssysteminstanz.

Begriffserklärungen:

Containerisierung: Die Verpackung von Anwendungen und deren Abhängigkeiten in Container, um eine konsistente Bereitstellung und Portabilität zu gewährleisten.
Image: Eine Datei, die alle benötigten Informationen enthält, um einen Container zu starten. Sie enthält das Betriebssystem, die Laufzeit, Anwendungen, Bibliotheken und Einstellungen.
Layer: Eine Schicht, die ein Image oder einen Container darstellt. Jede Änderung oder Addition zu einem Image wird als neue Schicht hinzugefügt.
Container: Eine Ausführungseinheit, die aus einem Image erstellt wird. Sie läuft isoliert von anderen Containern auf demselben Host.
Repository: Ein Ort, an dem Docker-Images gespeichert und verwaltet werden.
Registry: Ein zentraler Speicherort für Docker-Images, von dem Container-Engines Images herunterladen können.
Elementare Docker-Befehle:

docker build: Erstellt ein Docker-Image aus einem Dockerfile.
docker run: Startet einen Container aus einem Image.
docker stop: Stoppt einen laufenden Container.
docker rm: Löscht einen gestoppten Container.
docker rmi: Löscht ein Image von der lokalen Maschine.
Wichtige docker run-Optionen:

--name: Gibt dem Container einen Namen.
--rm: Löscht den Container nach dem Beenden.
--network: Weist dem Container ein Netzwerk zu.
--ip: Weist dem Container eine IP-Adresse zu.
-d: Startet den Container im Hintergrund.
-it: Startet den Container in interaktivem Modus.
-p: Weist Portweiterleitungen zu.
-v: Bindet Volumen ein.
-e: Setzt Umgebungsvariablen.
Verwenden verschiedener Image-Tags:

Copy code
docker pull ubuntu:18.04
Hier wird das Ubuntu-Image mit dem Tag "18.04" heruntergeladen.

Portweiterleitungen einrichten:

arduino
Copy code
docker run -p 8080:80 nginx
Dies leitet Port 8080 des Hosts an Port 80 des Containers weiter.

Benannte und gemountete Volumen verwenden:

javascript
Copy code
docker run -v my_volume:/path/in/container image_name
Hier wird ein Volumen mit dem Namen "my_volume" erstellt und an den Pfad "/path/in/container" im Container gemountet.

Netzwerkkonfiguration:

Docker erstellt standardmäßig ein eigenes Netzwerk für Container. Sie können auch benutzerdefinierte Netzwerke erstellen und Containern zuweisen.

Dockerfile-Syntax:

Ein Dockerfile besteht aus verschiedenen Anweisungen, um ein Image zu erstellen. Die grundlegenden Anweisungen sind FROM, RUN, COPY, ADD, CMD, ENTRYPOINT, EXPOSE, ENV, WORKDIR, USER, VOLUME, und LABEL.

Unterschiede zwischen ENTRYPOINT und CMD, sowie COPY und ADD:

ENTRYPOINT definiert den auszuführenden Befehl oder das auszuführende Skript beim Starten des Containers. CMD gibt Argumente für den Befehl an, der im ENTRYPOINT ausgeführt wird.
COPY kopiert Dateien von der Quelle im Build-Kontext in das Image. ADD hat ähnliche Funktionen wie COPY, kann aber auch URLs herunterladen und extrahieren.
Beispiel Dockerfile für eine Webseite:

Dockerfile
Copy code
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
Dieses Dockerfile verwendet das NGINX-Image, kopiert eine index.html-Datei und setzt den Standardbefehl zum Ausführen des NGINX-Servers.

