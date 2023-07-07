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
- [LB2-Container](#lb2-container)
  - [Auftrag](#auftrag)
    - [Service-Anforderungen](#service-anforderungen)
  - [Service Beschreibung](#service-beschreibung)
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

## Service Beschreibung
Der Service den wir Umsetzen möchten setzt sich aus 3 Komponenten zusammen. 
- **Mysql Server**
- **Phpmyadmin**
- **Wordpress**

Mit diesen 3 Komponenten werde ich eine Wordpress Umgebung aufbauen. Das Ziel dieser Wordpress Umgebung ist es die verschiedenen Service zusammenführen und ein ganzes Netzwerk zu bauen. Da es im Auftrag drum geht eine Komplexe Umgebung zu bauen habe ich mir überelgt diese 3 Komponenten zu benutzen. Wordpress habe ich genommen da es ein CMS mit fertigem WEB Ui ist und einen Integrierten Webserver hat, die ganzen Daten speichere ich in einer Datenbank auf einem Datenbank Server. Dieser ist ein eigenständiger Dockercontainer. Für das Verwalten des MySql Servers verwende ich Phpmyadmin. Dies ist auch ein eigenständiger Container. Für das erstellen der Container verwende ich Docker-Compose. Dort habe ich die 3 verschiedenen Docker definiert. 
