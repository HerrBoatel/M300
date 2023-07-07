<!-------------------------------------------------------------->
<!-- Datei-Name: README.md                                    -->
<!-- Autor: Justin Barthel                                    -->
<!-- Datum: 05.06.2023                                        -->
<!-- Beschreibung: Dies ist das README File von diesem Repo   -->
<!-------------------------------------------------------------->
<!-------------------Inhaltsverzeichnis------------------------->
# Inhaltsverzeichnis
- [Inhaltsverzeichnis](#inhaltsverzeichnis)
- [Vorwort](#vorwort)
  - [Danksagung](#danksagung)
  - [Über-dieses-Dokument](#über-dieses-dokument)
  - [Modulidentifikation](#modulidentifikation)
- [Informieren](#informieren)
  - [Docker](#docker)
    - [Dockerfile](#dockerfile)
  - [Docker-Compose](#docker-compose)
  - [Wordpress](#wordpress)
- [LB2-Container](#lb2-container)
  - [Auftrag](#auftrag)
    - [Service-Anforderungen](#service-anforderungen)
    - [Bewertungsraster](#bewertungsraster)
  - [Service Beschreibung](#service-beschreibung)
    - [Zweck](#zweck)
  - [Service Anwendung](#service-anwendung)
    - [Logischer Plan](#logischer-plan)
      - [Beispiel](#beispiel)
  - [Docker-Compose-file](#docker-compose-file)
    - [Wordpress-Service](#wordpress-service)
    - [Mysql Service](#mysql-service)
<!---------------------------Vorwort----------------------------->
# Vorwort
## Danksagung
An dieser Stelle möchte ich meine aufrichtige Dankbarkeit und Anerkennung für Kai's herausragende Mitarbeit zum Ausdruck bringen. Kai hat einen massgeblichen Beitrag zum Erfolg unseres Projekts geleistet und ich möchte ihm persönlich für seine grossartige Zusammenarbeit danken.

Kai, es war eine wahre Freude, mit dir gemeinsam an diesem Projekt zu arbeiten. Deine positive Einstellung, dein Enthusiasmus und dein Sinn für Humor haben die Arbeitsatmosphäre bereichert und dafür gesorgt, dass das gesamte Team mit Freude und Motivation an die Umsetzung herangegangen ist. Deine Begeisterung und Leidenschaft für das Projekt waren ansteckend und haben uns alle dazu inspiriert, unser Bestes zu geben.

## Über-dieses-Dokument
In diesem Dokument stehen alle Informationen in Bezug auf die LB3 und das Modul 300. In der Doku wird beschrieben wie ich (Justin Barthel) die LB2 Umgesetzt habe. In zusammenarbeit mit Kaiwen Shaow. Das Projekt wurde mit IPERKA umgesetzt.

## Modulidentifikation

| Begriffe | Beschreibung |
|----------|----------|
| Modulnummer | 300 |
| Titel | Plattformübergreifende Dienste in ein Netzwerk integrieren |
| Kompetenz | Plattformübergreifende Dienste nach Vorgabe für eine heterogene Systemumgebung konfigurieren, in Betrieb nehmen, testen und freigeben |
| Handlungsziele | Aus den Vorgaben die erforderlichen Dienste ermitteln, Schutz- und Sicherheitsanforderungen ableiten und ein Konzept für die Integration der Dienste ausarbeiten. Clients und Server gemäss Vorgaben konfigurieren, einrichten und geforderte Funktionalität überprüfen. Netzwerkverbindungen einrichten, Dienste in Betrieb nehmen und testen. Definierte Schutz- und Sicherheitsmassnahmen überprüfen. Anwendungen und Tools installieren, einrichten und geforderte Funktionalität überprüfen und gemeinsame Ressourcen einbinden. Allfällige Fehler systematisch eingrenzen, protokollieren und Massnahmen zur Fehlerbehebung einleiten. Dokumentation für die Administration des Netzes, der Rollen und Rechte und der eingerichteten Dienste und Anwendungen erstellen. |
| Kompetenzfeld Objekt | System Management, Clients, Server File, Print, DNS, DHCP, Directory Services, Terminal, SSH, Web und Peripherie mit unterschiedlichen Betriebssystemen in einem einfachen Netzwerk. |
| Modulversion | 3.0 |
| Erstellt am | 11.02.2021 |

# Informieren
## Docker
Was ist eigentlich Docker??
Docker ist eine Open-Source-Plattform, mit der Entwickler Anwendungen in sogenannten Containern erstellen, bereitstellen und ausführen können. Container sind eigenständige und isolierte Umgebungen, die alle erforderlichen Abhängigkeiten enthalten, um Anwendungen reibungslos auf verschiedenen Systemen auszuführen. 

Docker vereinfacht die Bereitstellung von Anwendungen, da Container tragbar, leichtgewichtig und schnell startbar sind. Dadurch können Entwickler Anwendungen schneller entwickeln, testen und bereitstellen, unabhängig von der zugrunde liegenden Infrastruktur.

![Docker-Aufbaue](https://miro.medium.com/v2/resize:fit:1400/0*5tspNCOuENlSjAgg)

### Dockerfile
Was ist ein Dockerfile? 
Ein Dockerfile ist eine Textdatei, die verwendet wird, um den Aufbau eines Docker-Images zu definieren. 

Es enthält eine Reihe von Anweisungen, die beschreiben, wie das Image erstellt werden soll. Ein Dockerfile enthält typischerweise Informationen wie das Basisimage, das verwendet werden soll, die Befehle zum Hinzufügen von Dateien und Anwendungscode, das Ausführen von Installationen oder Konfigurationen und die Festlegung der Befehle, die beim Starten des Containers ausgeführt werden sollen.

Durch das Erstellen eines Dockerfiles können Entwickler und Systemadministratoren den Aufbau und die Konfiguration eines Docker-Images automatisieren, wodurch die Wiederverwendbarkeit und Portabilität der Anwendungen verbessert wird.

![Docker-File](https://miro.medium.com/v2/resize:fit:1400/0*CP98BIIBgMG2K3u5.png)

## Docker-Compose
Was ist Docker-Compose??
Docker Compose ist ein Tool, das die Verwaltung und Orchestrierung von Docker-Anwendungen vereinfacht. Mit Docker Compose können Sie eine Anwendung definieren, die aus mehreren Containern besteht, und die Konfiguration dieser Container in einer einzigen Datei speichern. 

Diese Datei, normalerweise als "docker-compose.yml" bezeichnet, enthält Informationen über die Dienste, Netzwerke und Volumes, die Ihre Anwendung benötigt. Docker Compose ermöglicht es Ihnen, alle Container mit nur einem Befehl zu starten, zu stoppen und zu verwalten. 

Es erleichtert auch die Kommunikation zwischen den Containern und bietet Funktionen wie Skalierung, Lastenausgleich und Protokollierung. Durch die Verwendung von Docker Compose wird die Bereitstellung und Verwaltung von mehreren Containern als eine Einheit vereinfacht.

![Docker-Compose](https://www.biaudelle.fr/wp-content/uploads/2021/07/docker-compose-archi.png)

## Wordpress
Was ist Wordpress? 
WordPress ist eine Open-Source-Plattform zur Erstellung von Websites und Blogs. Es bietet eine benutzerfreundliche Oberfläche und eine Vielzahl von Funktionen, die es Benutzern ermöglichen, Inhalte zu veröffentlichen, das Design anzupassen und Erweiterungen hinzuzufügen, um die Funktionalität ihrer Websites zu erweitern. 

WordPress basiert auf der Programmiersprache PHP und verwendet eine Datenbank, um Inhalte und Einstellungen zu speichern. Es ist sehr beliebt und weit verbreitet und wird von Einzelpersonen, Unternehmen und Organisationen für die Erstellung verschiedener Arten von Websites verwendet, darunter Blogs, Unternehmenswebsites, E-Commerce-Shops und vieles mehr.

![Wordpress](https://ithemes.com/wp-content/uploads/2022/11/WordPress-themes-1024x608.png)

# LB2-Container
## Auftrag
Sie erstellen ein selbst gewähltes Projekt, welches auf der Docker **Container- Technologie** basiert.
Dabei erstellen sie einen Service, der innerhalb eines oder mehrerer Container 
implementiert wird.

Die Implementation des **Container-Projekts** erfolgt **als Einzelarbeit.** Der 
erstellte Code sowie die gesamte Dokumentation müssen versioniert auf dem 
von ihnen definierten Git-Repositoy hinterlegt und der Lehrperson zugänglich 
sein (Lese-Rechte).

Das Internet ist eine wichtige Ressource für solche Projekte. Entsprechend 
dürfen sie auch Codebeispiele aus dem Internet verwenden. Sie müssen 
solchen Code immer mit der Angabe der Quelle versehen.

Der verwendete Code muss von ihnen vollständig dokumentiert sein. Das gilt 
auch für Code, welchen sie aus fremden Quellen verwenden. 

**Das bedeutet, sie können über den verwendeten Code Auskunft geben**

### Service-Anforderungen
-  Wiederholbar und konsistent ausführbar auf Rechner2 die Docker und 
Docker-Compose installiert haben.
-  Service startet mit _**docker-compose up**_ - ohne weitere Interaktion.
- Die **Entwicklungsschritte** von Code und der Dokumentation sind in der Git 
*History* durch **regelmässige und dokumentierte Commit** nachvollziehbar. 
- Die **Projektdokumentation** erfolgt in **Markdown.**
- Wie der Service auf korrekte Funktionalität getestet werden kann, ist in er 
Dokumentation beschrieben.
- Die Funktion und Anwendung ist in der Projektdokumentation beschrieben.
- Sämtlicher Code ist in der Projektdokumentation beschrieben.

### Bewertungsraster
Hier ist der Link zum Bewertungsraster:  
[Bewertungsraster / Leistungsbeurteilung](https://tbzedu.sharepoint.com/sites/M300_Documents/Freigegebene%20Dokumente/Forms/AllItems.aspx?id=%2Fsites%2FM300%5FDocuments%2FFreigegebene%20Dokumente%2FLeistungsbeurteilung%2FBewertung%20LB2%5F1%5F3%2Epdf&parent=%2Fsites%2FM300%5FDocuments%2FFreigegebene%20Dokumente%2FLeistungsbeurteilung&p=true&ga=1)

## Service Beschreibung
Der Service den wir Umsetzen möchten setzt sich aus 3 Komponenten zusammen. 
- **Mysql Server**
- **Phpmyadmin**
- **Wordpress**

Mit diesen 3 Komponenten werde ich eine Wordpress Umgebung aufbauen. Das Ziel dieser Wordpress Umgebung ist es die verschiedenen Service zusammenführen und ein ganzes Netzwerk zu bauen. Da es im Auftrag drum geht eine Komplexe Umgebung zu bauen habe ich mir überelgt diese 3 Komponenten zu benutzen. Wordpress habe ich genommen da es ein CMS mit fertigem WEB Ui ist und einen Integrierten Webserver hat, die ganzen Daten speichere ich in einer Datenbank auf einem Datenbank Server. Dieser ist ein eigenständiger Dockercontainer. Für das Verwalten des MySql Servers verwende ich Phpmyadmin. Dies ist auch ein eigenständiger Container. Für das erstellen der Container verwende ich Docker-Compose. Dort habe ich die 3 verschiedenen Docker definiert. 

### Zweck
Der Zweck dieses Service ist es eine Wordpress Umgebung zu erstellen wo man einfache Wordpress Websiten erstellen kann. Da das Thema immer mehr aufkommt das ein Unternehmen eine Website braucht und das Thema Wordpress sehr Populär ist habe ich mich für diesen Service entschieden. 

## Service Anwendung
Umgebung die Umgebung wird mit Docker-Compose gestartet. Hierbei wird im Hintergrund das Docker-Compose File das ich & Kai erstellt haben ausgeführt und durchgearbeitet. Hierbei werden die 3 verschiedenen Services gestartet. Zuerst wird das Image gepulled von den jeweiligen Services. Dannach findet die Konfiguration statt. 

### Logischer Plan
Hier ist der Logische Plan dieser Umgebung. Er zeigt wie die Services in Verbindung stehen. Er zeigt auch auf über welche Prtos die Services laufen.

![Logischer-Plan](https://raw.githubusercontent.com/HerrBoatel/m300/main/logischer-plan-m300.png)

Wie man sieht hat es hier mehrere Netzwerke. Wichtig ist zu wissen das man die verschiedenen Service über die Maschinen IP erreicht, heisst wo auch immer die Docker Umgebung drauf läuft, die IP Adresse dieser Maschine muss man im Webbrowser mit dem entsprechenden Port angeben um auf die Services und Web-Applikationen zu gelangen. 

#### Beispiel
**(MaschinenIP:Port-der-Applikation)** = **(192.168.1.10:8000)**

## Docker-Compose-file
Das wäre das Docker Compose File:
[Docker-Compose-file](docker-compose.yaml)
```yaml
version: '3'

services:
  # ------------------ Wordpress Service ------------------------
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    container_name: wordpress
    restart: always
    # Definiert das Envoirement
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
    # Definiert die Reccourcen und Limite
    deploy:
      resources:
        limits:
          cpus: '1'
          memory: 500M
        reservations:
          cpus: '0.5'
          memory: 200M
    # Definiert das Volume
    volumes:
        - wp_data:/var/www/html
    # Definiert die Ports
    ports:
      - '8000:80'
    # Definiert das Netzwerk
    networks:
      - wpnetwork
  # ----------------- Datenbank Server ---------------------------
  db:
    image: mysql:latest
    container_name: db
    restart: unless-stopped
    # Definiert das Envoirement
    environment:
      MYSQL_ROOT_PASSWORD: wordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    # Definiert die Reccourcen und Limite
    deploy:
      resources:
        limits:
          cpus: '2'
          memory: 1G
        reservations:
          cpus: '0.5'
          memory: 200M
    # Definiert das Volume
    volumes:
      - db_data:/var/lib/mysql
    # Definiert die Ports
    ports:
      - '3306:3306'
    # Definiert das Netzwerk
    networks:
      - wpnetwork
    # ---------------- phpmyadmin service ------------------------
  phpmyadmin:
    depends_on:
      - db
    image: phpmyadmin:latest
    container_name: phpmyadmin
    restart: always
    # Definiert das Envoirement
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: wordpress
    # Definiert die Reccourcen und Limite
    deploy:
      resources:
        limits:
          cpus: '1'
          memory: 500M
        reservations:
          cpus: '0.5'
          memory: 200M
    # Definiert die Ports
    ports:
      - '8080:80'
    # Definiert das Netzwerk
    networks:
      - wpnetwork
# Speicher Volume
volumes:
  db_data:
    driver: local
  wp_data:
    driver: local
# Netzwerk
networks:
  wpnetwork:
    driver: bridge
```
Nun wird der Aufbau des Docker Compose File beschrieben: 

### Wordpress-Service
```yaml
# ------------------ Wordpress Service ------------------------
wordpress:
depends_on:
    - db
image: wordpress:latest
container_name: wordpress
restart: always
# Definiert das Envoirement
environment:
    WORDPRESS_DB_HOST: db:3306
    WORDPRESS_DB_USER: wordpress
    WORDPRESS_DB_PASSWORD: wordpress
    WORDPRESS_DB_NAME: wordpress
# Definiert die Reccourcen und Limite
deploy:
    resources:
    limits:
        cpus: '1'
        memory: 500M
    reservations:
        cpus: '0.5'
        memory: 200M
# Definiert das Volume
volumes:
    - wp_data:/var/www/html
# Definiert die Ports
ports:
    - '8000:80'
# Definiert das Netzwerk
networks:
    - wpnetwork
```
In diesem Abschnitt wird eine Docker-Compose-Konfigurationsdatei für die Bereitstellung von WordPress definiert. Hier ist eine Zusammenfassung der verschiedenen Einstellungen:

- `depends_on`: Gibt an, dass der WordPress-Container vom `db`-Container abhängt, der vermutlich eine Datenbank wie MySQL enthält.
- `image`: Gibt das Docker-Image an, das für den WordPress-Container verwendet werden soll. Hier wird die neueste Version von WordPress verwendet.
- `container_name`: Legt den Namen des Containers auf "wordpress" fest.
- `restart`: Definiert die Neustartpolitik für den Container, in diesem Fall "always" (immer neu starten).
- `environment`: Hier werden Umgebungsvariablen festgelegt, die von WordPress verwendet werden, um auf die Datenbank zuzugreifen. Es werden der Host (`db:3306`), der Benutzername, das Passwort und der Datenbankname angegeben.
- `deploy`: Hier werden Ressourcenbegrenzungen und -reservierungen festgelegt, um die Nutzung von CPU und Speicher für den Container zu steuern.
- `volumes`: Definiert ein Volume mit dem Namen "wp_data", das verwendet wird, um den WordPress-Container mit dem Verzeichnis `/var/www/html` zu verbinden.
- `ports`: Gibt an, dass der Port 8000 des Hosts auf den Port 80 des WordPress-Containers abgebildet werden soll, was bedeutet, dass die WordPress-Website über Port 8000 aufgerufen werden kann.
- `networks`: Hier wird das Netzwerk "wpnetwork" angegeben, das verwendet wird, um den WordPress-Container mit anderen Containern zu verbinden.

Zusammenfassend wird in diesem Abschnitt eine Docker-Compose-Konfiguration definiert, um einen WordPress-Container mit einer Datenbank-Abhängigkeit, spezifischen Umgebungsvariablen, Ressourcenbegrenzungen und -reservierungen, Volumenverbindung, Portweiterleitung und Netzwerkverbindung zu erstellen.

### Mysql Service
```yaml
 # ----------------- Datenbank Server ---------------------------
  db:
    image: mysql:latest
    container_name: db
    restart: unless-stopped
    # Definiert das Envoirement
    environment:
      MYSQL_ROOT_PASSWORD: wordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    # Definiert die Reccourcen und Limite
    deploy:
      resources:
        limits:
          cpus: '2'
          memory: 1G
        reservations:
          cpus: '0.5'
          memory: 200M
    # Definiert das Volume
    volumes:
      - db_data:/var/lib/mysql
    # Definiert die Ports
    ports:
      - '3306:3306'
    # Definiert das Netzwerk
    networks:
      - wpnetwork
```
In diesem Abschnitt wird eine Docker-Compose-Konfigurationsdatei für die Bereitstellung eines Datenbank-Servers (hier MySQL) definiert. Hier ist eine Zusammenfassung der verschiedenen Einstellungen:

- `image`: Gibt das Docker-Image an, das für den Datenbank-Container verwendet werden soll. Hier wird die neueste Version von MySQL verwendet.
- `container_name`: Legt den Namen des Containers auf "db" fest.
- `restart`: Definiert die Neustartpolitik für den Container, in diesem Fall "unless-stopped" (neustarten, es sei denn, der Container wurde explizit gestoppt).
- `environment`: Hier werden Umgebungsvariablen festgelegt, die von der MySQL-Datenbank verwendet werden, wie das Root-Passwort, der Datenbankname und die Zugangsdaten für den Benutzer.
- `deploy`: Hier werden Ressourcenbegrenzungen und -reservierungen festgelegt, um die Nutzung von CPU und Speicher für den Container zu steuern.
- `volumes`: Definiert ein Volume mit dem Namen "db_data", das verwendet wird, um den Datenbank-Container mit dem Verzeichnis `/var/lib/mysql` zu verbinden.
- `ports`: Gibt an, dass der Port 3306 des Hosts auf den Port 3306 des Datenbank-Containers abgebildet werden soll, was bedeutet, dass die Datenbank über Port 3306 erreichbar ist.
- `networks`: Hier wird das Netzwerk "wpnetwork" angegeben, das verwendet wird, um den Datenbank-Container mit anderen Containern zu verbinden.

Zusammenfassend wird in diesem Abschnitt eine Docker-Compose-Konfiguration definiert, um einen MySQL-Datenbank-Container mit spezifischen Umgebungsvariablen, Ressourcenbegrenzungen und -reservierungen, Volumenverbindung, Portweiterleitung und Netzwerkverbindung zu erstellen.