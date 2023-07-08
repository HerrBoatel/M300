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
    - [PhpMyadmin Service](#phpmyadmin-service)
    - [Speicher Volumes](#speicher-volumes)
    - [Netzwerk](#netzwerk)
    - [Docker-Sicherheitsmassnahmen](#docker-sicherheitsmassnahmen)
      - [Meine-Sicherheitsmerkmale](#meine-sicherheitsmerkmale)
  - [Docker-Container-aufsetzen](#docker-container-aufsetzen)
  - [Testing](#testing)
    - [Bewertungsraster-Checkliste](#bewertungsraster-checkliste)
      - [Komplexität/ Umfang/Funktion](#komplexität-umfangfunktion)
      - [Dokumentation](#dokumentation)
  - [Quellenverzeichnis](#quellenverzeichnis)
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

### PhpMyadmin Service
```yaml
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
In diesem Abschnitt wird eine Docker-Compose-Konfigurationsdatei für den PHPMyAdmin-Dienst definiert. Hier ist eine Zusammenfassung der verschiedenen Einstellungen:

- `depends_on`: Gibt an, dass der PHPMyAdmin-Container vom "db"-Container abhängt, der die MySQL-Datenbank enthält.
- `image`: Gibt das Docker-Image an, das für den PHPMyAdmin-Container verwendet werden soll. Hier wird die neueste Version von PHPMyAdmin verwendet.
- `container_name`: Legt den Namen des Containers auf "phpmyadmin" fest.
- `restart`: Definiert die Neustartpolitik für den Container, in diesem Fall "always" (immer neu starten).
- `environment`: Hier werden Umgebungsvariablen festgelegt, wie der Hostname der Datenbank ("db") und das Root-Passwort der MySQL-Datenbank.
- `deploy`: Hier werden Ressourcenbegrenzungen und -reservierungen festgelegt, um die Nutzung von CPU und Speicher für den Container zu steuern.
- `ports`: Gibt an, dass der Port 8080 des Hosts auf den Port 80 des PHPMyAdmin-Containers abgebildet werden soll, was bedeutet, dass der PHPMyAdmin-Dienst über Port 8080 erreichbar ist.
- `networks`: Hier wird das Netzwerk "wpnetwork" angegeben, das verwendet wird, um den PHPMyAdmin-Container mit anderen Containern zu verbinden.

Darüber hinaus werden im Code Abschnitte für die Volumes- und Netzwerkkonfiguration definiert. Es werden Volumes mit den Namen "db_data" und "wp_data" erstellt, die lokal (auf dem Host) gespeichert werden. Zudem wird das Netzwerk "wpnetwork" mit dem Bridge-Treiber für die Containerkommunikation erstellt.

Zusammenfassend wird in diesem Abschnitt eine Docker-Compose-Konfiguration definiert, um einen PHPMyAdmin-Container mit Abhängigkeit von der MySQL-Datenbank, spezifischen Umgebungsvariablen, Ressourcenbegrenzungen und -reservierungen, Portweiterleitung und Netzwerkverbindung zu erstellen. Es werden auch Volumes und ein Netzwerk für die allgemeine Verwendung definiert.

### Speicher Volumes
```yaml
# Speicher Volume
volumes:
  db_data:
    driver: local
  wp_data:
    driver: local
```
In diesem Teil des Codes werden Volumes für die Speicherung von Daten definiert. Hier ist eine Zusammenfassung der Konfiguration:

- `volumes`: Dieses Schlüsselwort definiert die Volumes für die Speicherung von Daten.
- `db_data`: Hier wird ein Volume mit dem Namen "db_data" definiert. Es wird als Speicherort für Daten der Datenbank verwendet.
- `driver: local`: Dieser Eintrag definiert den Treiber für das Volume als "local", was bedeutet, dass das Volume auf dem lokalen Hostspeicher erstellt wird.
- `wp_data`: Hier wird ein weiteres Volume mit dem Namen "wp_data" definiert. Es dient als Speicherort für Daten, die von WordPress verwendet werden.

Zusammenfassend werden in diesem Abschnitt Volumes erstellt, um Daten für die Datenbank und für WordPress zu speichern. Die Volumes werden mit dem lokalen Treiber konfiguriert, was bedeutet, dass sie auf dem lokalen Hostspeicher erstellt werden.

### Netzwerk
```yaml
# Netzwerk
networks:
  wpnetwork:
    driver: bridge
```
In diesem Teil des Codes wird ein Netzwerk für die Docker-Container definiert. Hier ist eine Zusammenfassung der Konfiguration:

- `networks`: Dieses Schlüsselwort definiert die Netzwerke für die Container.
- `wpnetwork`: Hier wird ein Netzwerk mit dem Namen "wpnetwork" definiert.
- `driver: bridge`: Dieser Eintrag definiert den Treiber für das Netzwerk als "bridge". Der Bridge-Treiber erstellt ein isoliertes Netzwerk, in dem die Container miteinander kommunizieren können.

Zusammenfassend wird in diesem Abschnitt ein Netzwerk mit dem Namen "wpnetwork" definiert, das als Bridge-Treiber konfiguriert ist. Dieses Netzwerk ermöglicht die Kommunikation zwischen den Containern, die in der Docker-Compose-Datei definiert sind.

### Docker-Sicherheitsmassnahmen
Docker ist eine beliebte Containerisierungsplattform, die es ermöglicht, Anwendungen in isolierten Umgebungen auszuführen. Um die Sicherheit von Docker-Containern zu gewährleisten, werden verschiedene Maßnahmen ergriffen, um Ressourcenbeschränkungen und andere Sicherheitsaspekte zu berücksichtigen. Hier sind einige wichtige Sicherheitsmaßnahmen im Zusammenhang mit Ressourcenbegrenzungen in Docker:

1. Ressourcenbeschränkung: Docker ermöglicht die Begrenzung von Ressourcen wie CPU, Arbeitsspeicher und Festplattenspeicher für einzelne Container. Durch die Festlegung von Grenzwerten können Ressourcenkonflikte zwischen Containern vermieden und die Systemstabilität verbessert werden.

2. CPU-Beschränkung: Mit der CPU-Begrenzung kann die Menge an Prozessorzeit begrenzt werden, die ein Container verwenden kann. Dadurch wird sichergestellt, dass ein einzelner Container nicht die gesamte CPU-Kapazität des Host-Systems beansprucht und andere Container oder Prozesse beeinträchtigt.

3. Arbeitsspeicherbeschränkung: Durch die Begrenzung des Arbeitsspeichers, den ein Container verwenden kann, wird sichergestellt, dass der Container nicht zu viel Speicher belegt und andere Container oder das Host-System destabilisiert. Docker ermöglicht die Festlegung von Begrenzungen für den gesamten Arbeitsspeicher und den Swap-Speicher.

4. Blockierung von Ressourcenausbeutung: Docker enthält Mechanismen, um Ressourcenausbeutung zu verhindern. Dazu gehören die Verwendung von Cgroups (Control Groups) zur Begrenzung von Ressourcen und die Verhinderung von DDoS-Angriffen (Distributed Denial of Service) durch Überbeanspruchung der Ressourcen eines Containers.

5. Netzwerkisolierung: Docker bietet standardmäßig eine isolierte Netzwerkumgebung für Container. Diese Isolierung verhindert, dass Container auf Netzwerkressourcen anderer Container oder des Host-Systems zugreifen können. Durch die Implementierung von Netzwerkrichtlinien können Administrator*innen den Datenverkehr zwischen Containern steuern und unerwünschte Verbindungen verhindern.

6. Zugriffsbeschränkung auf Host-Ressourcen: Docker erlaubt es, den Zugriff eines Containers auf Host-Ressourcen wie Dateien, Verzeichnisse oder Geräte einzuschränken. Durch das sorgfältige Festlegen von Berechtigungen und das Verwenden von Containervolumes können potenzielle Sicherheitslücken minimiert werden.

7. Aktualisierung von Docker-Images und -Containern: Die regelmäßige Aktualisierung von Docker-Images und -Containern ist wichtig, um bekannte Sicherheitslücken zu schließen und von den neuesten Sicherheitsverbesserungen zu profitieren. Es wird empfohlen, Sicherheitsupdates und Patches zeitnah einzuspielen.

Diese Sicherheitsmaßnahmen helfen dabei, die Integrität, Vertraulichkeit und Verfügbarkeit von Docker-Containern und der darin ausgeführten Anwendungen zu gewährleisten. Es ist wichtig, diese bewährten Verfahren zu befolgen und kontinuierlich auf neue Sicherheitsbedrohungen und empfohlene Sicherheitsmaßnahmen zu achten.

#### Meine-Sicherheitsmerkmale

1. Abhängigkeiten und Reihenfolge: Der WordPress-Dienst ist von der Datenbank abhängig (definiert durch `depends_on`). Dadurch wird sichergestellt, dass die Datenbank vor dem Start von WordPress bereitgestellt wird.

2. Neustartpolitik: Der WordPress- und der phpMyAdmin-Dienst sind auf `always` eingestellt, während der Datenbankdienst auf `unless-stopped` eingestellt ist. Dies gewährleistet, dass die Dienste automatisch neu gestartet werden, falls sie aus irgendeinem Grund beendet werden.

3. Umgebungsvariablen: Die sensiblen Daten wie Datenbank-Host, Benutzername, Passwort und Datenbankname werden als Umgebungsvariablen definiert. Dadurch werden sensible Informationen nicht direkt im Code angezeigt, sondern können über Umgebungsvariablen verwaltet werden.

4. Ressourcenbeschränkungen: 
```yaml
    # Definiert die Reccourcen und Limite
    deploy:
      resources:
        limits:
          cpus: '2'
          memory: 1G
        reservations:
          cpus: '0.5'
          memory: 200M
```
Die Ressourcenlimits und -reservierungen für die Container werden definiert. Sowohl der WordPress- als auch der phpMyAdmin-Dienst haben CPU- und Speicherlimits, um eine übermäßige Nutzung zu verhindern und die Systemstabilität zu gewährleisten.

5. Volumes: Die WordPress- und MySQL-Container verwenden Volumes, um Daten persistent zu speichern. Dadurch werden Datenverluste vermieden und ermöglicht ein einfacheres Backup und Wiederherstellung von Daten.

6. Netzwerkisolierung: Die Container sind Teil eines eigenen Netzwerks (`wpnetwork`). Dadurch werden die Container voneinander und von anderen Containern oder Diensten isoliert. Es wird vermieden, dass Container über unsichere Netzwerke kommunizieren können.

7. Aktualisierte Images: Die neuesten Versionen der Docker-Images für WordPress, MySQL und phpMyAdmin werden verwendet. Es ist wichtig, regelmäßig Updates durchzuführen, um bekannte Sicherheitslücken zu schließen.

Es ist zu beachten, dass die Sicherheit von Docker-Containern nicht nur von der Konfiguration in der Docker-Compose-Datei abhängt. Es gibt weitere Sicherheitsaspekte, wie das Härten des Host-Betriebssystems, das Überwachen von Sicherheitslücken, das Patchen von Anwendungen und das Implementieren von Zugriffskontrollen, die ebenfalls berücksichtigt werden sollten.

## Docker-Container-aufsetzen
Nun um diese Umgebung zu starten geht man auf die aufgesetze Maschine mit installierter Docker Engine. Falls diese noch nicht installiert ist wäre hier eine Anleitung für das Installieren der Docker Engine sowie Docker Compose:

1. Docker: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04-de
2. Docker-Compose: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04-de

Sobald man die Docker Engine erfolgreich funktioniert, kann man sobald man das passende Docker-Compose File hat kann man diesen Command ausführen: 
```bash
docker-compose up
```
Dann sollte folgendes Passieren: 
```yaml
WARNING: The following deploy sub-keys are not supported and have been ignored: resources.reservations.cpus
WARNING: The following deploy sub-keys are not supported and have been ignored: resources.reservations.cpus
WARNING: The following deploy sub-keys are not supported and have been ignored: resources.reservations.cpus
Starting db ... done
phpmyadmin is up-to-date
wordpress is up-to-date
Attaching to db, phpmyadmin, wordpress
wordpress     | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.3. Set the 'ServerName' directive globally to suppress this message
wordpress     | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.3. Set the 'ServerName' directive globally to suppress this message
wordpress     | [Fri Jul 07 12:58:24.537068 2023] [mpm_prefork:notice] [pid 1] AH00163: Apache/2.4.56 (Debian) PHP/8.0.29 configured -- resuming normal operations
wordpress     | [Fri Jul 07 12:58:24.537211 2023] [core:notice] [pid 1] AH00094: Command line: 'apache2 -D FOREGROUND'
wordpress     | 172.20.10.10 - - [07/Jul/2023:12:59:29 +0000] "GET / HTTP/1.1" 200 11712 "http://172.20.10.13:8000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36"
wordpress     | 172.20.10.10 - - [07/Jul/2023:12:59:32 +0000] "GET /wp-admin/about.php HTTP/1.1" 200 12428 "http://172.20.10.13:8000/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36"
wordpress     | 172.20.10.10 - - [07/Jul/2023:12:59:32 +0000] "GET /wp-admin/load-styles.php?c=0&dir=ltr&load%5Bchunk_0%5D=dashicons,admin-bar,common,forms,admin-menu,dashboard,list-tables,edit,revisions,media,themes,about,nav-menus,wp-pointer,widgets&load%5Bchunk_1%5D=,site-icon,l10n,buttons,wp-auth-check&ver=6.2.2 HTTP/1.1" 200 99394 "http://172.20.10.13:8000/wp-admin/about.php" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36"
wordpress     | 172.20.10.10 - - [07/Jul/2023:12:59:33 +0000] "GET /wp-admin/images/about-header-about.svg?ver=6.2 HTTP/1.1" 200 5031 "http://172.20.10.13:8000/wp-admin/load-styles.php?c=0&dir=ltr&load%5Bchunk_0%5D=dashicons,admin-bar,common,forms,admin-menu,dashboard,list-tables,edit,revisions,media,themes,about,nav-menus,wp-pointer,widgets&load%5Bchunk_1%5D=,site-icon,l10n,buttons,wp-auth-check&ver=6.2.2" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36"
wordpress     | [Fri Jul 07 12:59:40.254445 2023] [mpm_prefork:notice] [pid 1] AH00170: caught SIGWINCH, shutting down gracefully
wordpress     | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.3. Set the 'ServerName' directive globally to suppress this message
wordpress     | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.3. Set the 'ServerName' directive globally to suppress this message
wordpress     | [Fri Jul 07 14:12:30.466414 2023] [mpm_prefork:notice] [pid 1] AH00163: Apache/2.4.56 (Debian) PHP/8.0.29 configured -- resuming normal operations
wordpress     | [Fri Jul 07 14:12:30.466559 2023] [core:notice] [pid 1] AH00094: Command line: 'apache2 -D FOREGROUND'
wordpress     | [Fri Jul 07 14:12:57.789361 2023] [mpm_prefork:notice] [pid 1] AH00170: caught SIGWINCH, shutting down gracefully
wordpress     | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.2. Set the 'ServerName' directive globally to suppress this message
wordpress     | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.2. Set the 'ServerName' directive globally to suppress this message
wordpress     | [Fri Jul 07 20:32:05.312612 2023] [mpm_prefork:notice] [pid 1] AH00163: Apache/2.4.56 (Debian) PHP/8.0.29 configured -- resuming normal operations
wordpress     | [Fri Jul 07 20:32:05.313053 2023] [core:notice] [pid 1] AH00094: Command line: 'apache2 -D FOREGROUND'
phpmyadmin    | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.4. Set the 'ServerName' directive globally to suppress this message
phpmyadmin    | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.4. Set the 'ServerName' directive globally to suppress this message
phpmyadmin    | [Fri Jul 07 12:58:25.324559 2023] [mpm_prefork:notice] [pid 1] AH00163: Apache/2.4.57 (Debian) PHP/8.2.7 configured -- resuming normal operations
phpmyadmin    | [Fri Jul 07 12:58:25.324722 2023] [core:notice] [pid 1] AH00094: Command line: 'apache2 -D FOREGROUND'
phpmyadmin    | [Fri Jul 07 12:59:40.278610 2023] [mpm_prefork:notice] [pid 1] AH00170: caught SIGWINCH, shutting down gracefully
phpmyadmin    | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.4. Set the 'ServerName' directive globally to suppress this message
phpmyadmin    | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.4. Set the 'ServerName' directive globally to suppress this message
phpmyadmin    | [Fri Jul 07 14:12:30.523291 2023] [mpm_prefork:notice] [pid 1] AH00163: Apache/2.4.57 (Debian) PHP/8.2.7 configured -- resuming normal operations
phpmyadmin    | [Fri Jul 07 14:12:30.523618 2023] [core:notice] [pid 1] AH00094: Command line: 'apache2 -D FOREGROUND'
phpmyadmin    | [Fri Jul 07 14:12:57.800190 2023] [mpm_prefork:notice] [pid 1] AH00170: caught SIGWINCH, shutting down gracefully
phpmyadmin    | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.3. Set the 'ServerName' directive globally to suppress this message
phpmyadmin    | AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.18.0.3. Set the 'ServerName' directive globally to suppress this message
phpmyadmin    | [Fri Jul 07 20:32:05.076465 2023] [mpm_prefork:notice] [pid 1] AH00163: Apache/2.4.57 (Debian) PHP/8.2.7 configured -- resuming normal operations
phpmyadmin    | [Fri Jul 07 20:32:05.076912 2023] [core:notice] [pid 1] AH00094: Command line: 'apache2 -D FOREGROUND'
db            | 2023-07-07 20:50:51+00:00 [Note] [Entrypoint]: Entrypoint script for MySQL Server 8.0.33-1.el8 started.
db            | 2023-07-07 20:50:52+00:00 [Note] [Entrypoint]: Switching to dedicated user 'mysql'
db            | 2023-07-07 20:50:52+00:00 [Note] [Entrypoint]: Entrypoint script for MySQL Server 8.0.33-1.el8 started.
db            | '/var/lib/mysql/mysql.sock' -> '/var/run/mysqld/mysqld.sock'
db            | 2023-07-07T20:50:53.721137Z 0 [Warning] [MY-011068] [Server] The syntax '--skip-host-cache' is deprecated and will be removed in a future release. Please use SET GLOBAL host_cache_size=0 instead.
db            | 2023-07-07T20:50:53.739971Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.33) starting as process 1
db            | 2023-07-07T20:50:53.796655Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
db            | 2023-07-07T20:50:55.368593Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
db            | 2023-07-07T20:50:56.032239Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
db            | 2023-07-07T20:50:56.032864Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
db            | 2023-07-07T20:50:56.041561Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consider choosing a different directory.
db            | 2023-07-07T20:50:56.118278Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Bind-address: '::' port: 33060, socket: /var/run/mysqld/mysqlx.sock
db            | 2023-07-07T20:50:56.118279Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '8.0.33'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server - GPL.
```
## Testing
Für das Testing habe ich einfach die bestimmten Testfälle genommen und versucht per commands danach das ergebnis auszulesen und zu zeigen. Bei dem Punkt Persistent volumes weiss ich nicht wie ich es einfach darstellen kann daher kann ich nur sagen das es funktioniert hat, ansonsten muss man es halt selber testen um es zu glauben. 

Die test wurden recht einfach durchgeführt.
| Testfall | Beschreibung | Erwartetes Ergebnis | Tatsächliches Ergebnis |
| --- | --- | --- | --- |
| Container-Start | Starten der Containers | Die Container werden erfolgreich gestartet | ![container start](https://raw.githubusercontent.com/HerrBoatel/m300/main/Bilder/docker-container-start.png)  |
| Abhängigkeiten | Starten von Containern mit Abhängigkeiten | Abhängige Container werden vor den abhängigen Containern gestartet | ![Abhängigkeiten](https://raw.githubusercontent.com/HerrBoatel/m300/main/Bilder/abh%C3%A4ngigkeiten.png) |
| Ressourcenbegrenzung | Festlegen von CPU- und Speicherlimits für einen Container | Der Container verwendet nicht mehr Ressourcen als die angegebenen Limits | ![reccourcenverbrauch](https://raw.githubusercontent.com/HerrBoatel/m300/main/Bilder/reccourcen-limits.png)|
| Persistenz von Daten | Speichern von Daten in Volumes | Daten in den Volumes bleiben erhalten, selbst wenn der Container neu gestartet wird | Erfolgreiche Persistenz der Daten in den Volumes |

### Bewertungsraster-Checkliste
#### Komplexität/ Umfang/Funktion
- [x]  Komplexität, Umfang und Anteil Eigenleistung der Arbeit
- [x]  Auf jedem Linux Docker-Enabled Rechner lauffähig
- [x]  Korrekte Netzwerkkonfiguration
- [x]  Keine Interaktion nötig nach dem Start
- [ ]  Eigenes Image erzeugt und verwendet
- [x]  Image wird mit docker-compose erstellt
- [x]  Service benötigt mehrere Container (Bsp. Webserver mit Datenbank Backend)
- [x]  Verwendung von 'merged' Compose Files
- [x]  Verwendung von persistenten Volumes
- [x]  Dokumentierte Sicherheitsmerkmale (Kapitel 35) implementiert (min. 1)
- [x]  Git History (regelmässige Commit mit sinnvollem Kommentar )
- [ ]  CI Implementiert
  
#### Dokumentation
- [x]  Inhaltsverzeichnis (Verlinkt)
- [x]  Service Beschreibung (welchen Zweck erfüllt der Service)
- [x]  Service Anwendung (wir wird der Service angewendet)
- [x]  Grafische Übersicht (Container, Systeme , Datenflüsse, Netzwerk , Port…)
- [x]  Code Beschreibung (mit MD Code Blocks)
- [x]  Dokumentiertes Testing (wie wird was getestet)
- [x]  Korrektheit der Angaben, Umfang, alles Relevante beschrieben / Quellenverzeichnis
- [x]  Markdown, 5 unterschiedliche Elemente verwendet
- [x]  Übersichtlich (klar strukturiert, relevante Informationen schnell zugänglich)
- [x]  Git History (regelmässige Commit mit sinnvollem Kommentar )

## Quellenverzeichnis
1. Präsis / Input von Herrn Berger
2. ChatGPT
3. Docker Cheatsheet: https://www.hosteurope.de/blog/diese-wichtigen-docker-befehle-sollten-sie-kennen/
4. Docker volumes: https://www.ionos.de/digitalguide/server/knowhow/docker-container-volumes/
5. docker stats: https://docs.docker.com/engine/reference/commandline/stats/
6. docker images: https://lerneprogrammieren.de/docker-container-images-erstellen/
7. docker compose: https://docs.docker.com/compose/
8. dokcer compose official site: https://github.com/docker/compose