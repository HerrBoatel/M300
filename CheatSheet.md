<!-------------------------------------------------------------->
<!-- Datei-Name: Cheatsheet.md                                -->
<!-- Autor: Justin Barthel                                    -->
<!-- Datum: 05.06.2023                                        -->
<!-- Beschreibung: Dies ist ein Cheatsheet über git und Md    -->
<!-------------------------------------------------------------->

<!-------------------- Git Cheatsheet Start -------------------->
# Git Cheatsheet

<!-------------------------------------------------------------->
## Configuration

```markdown
# Git Konfiguration
git config --global user.name "Dein Name"
git config --global user.email "deine@email.com"
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->
## Erstellung und Klonen von Repositories

```markdown
# Ein neues lokales Repository erstellen
git init

# Ein Repository von einem Remote-Repository klonen
git clone <remote-url>
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->

## Arbeitsfluss

```markdown
# Den Status des Arbeitsverzeichnisses anzeigen
git status

# Änderungen zum Commit vorbereiten
git add <dateiname>  # Eine bestimmte Datei hinzufügen
git add .            # Alle Dateien hinzufügen

# Einen Commit erstellen
git commit -m "Commit-Nachricht"

# Änderungen vom Remote-Repository abrufen und zusammenführen
git pull

# Änderungen zum Remote-Repository hochladen
git push
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->

## Branching und Merging

```markdown
# Einen neuen Branch erstellen
git branch <branch-name>

# Zum angegebenen Branch wechseln
git checkout <branch-name>

# Einen neuen Branch erstellen und zu diesem wechseln
git checkout -b <branch-name>

# Alle Branches anzeigen
git branch -a

# Branches zusammenführen
git merge <branch-name>
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->
## Versionsverwaltung

```markdown
# Alle Commits anzeigen
git log

# Eine bestimmte Commit-Änderung anzeigen
git show <commit-hash>

# Eine vorherige Commit-Version wiederherstellen
git checkout <commit-hash>

# Eine bestimmte Datei von einem früheren Commit wiederherstellen
git checkout <commit-hash> -- <dateiname>
```
<!-------------------- Git Cheatsheet End ---------------------->
<!-------------------------------------------------------------->
<!----------------- Markdown Cheatsheet Start ------------------>

# Markdown Cheatsheet

## Überschriften

```markdown
# Überschrift 1
## Überschrift 2
### Überschrift 3
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->

## Textformatierung

```markdown
*Fettgedruckter Text*
_Kursiver Text_
~~Durchgestrichener Text~~
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->

## Aufzählungen

```markdown
- Erster Punkt
- Zweiter Punkt
- Dritter Punkt

1. Nummerierter Punkt 1
2. Nummerierter Punkt 2
3. Nummerierter Punkt 3
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->

## Links

```markdown
[Linkbeschreibung](https://www.beispiel.de)

[Link mit Titel](https://www.beispiel.de "Titel des Links")
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->

## Bilder

```markdown
![Bildbeschreibung](pfad/zum/bild.jpg)

![Bild mit Titel](pfad/zum/bild.jpg "Titel des Bildes")
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->

## Codeblöcke

```python
Einzeiliger Code: `code`

Mehrzeiliger Code:

    ```python
    def funktion():
        print("Hallo, Welt!")
    ```

Codeblock mit Syntaxhervorhebung:

```python
def funktion():
    print("Hallo, Welt!")
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->

## Zitate

```markdown
> Dies ist ein Zitat.
```
<!-------------------------------------------------------------->
<!-------------------------------------------------------------->

## Horizontale Linien

```markdown
---
```

## Tabellen

```markdown
| Spalte 1 | Spalte 2 | Spalte 3 |
|----------|----------|----------|
| Inhalt 1 | Inhalt 2 | Inhalt 3 |
| Inhalt 4 | Inhalt 5 | Inhalt 6 |
```
## Checkboxen

```markdown
- [x] Aufgabe erledigt
- [ ] Aufgabe ausstehend
```
## Mathematische Formeln

Markdown unterstützt mathematische Formeln mit LaTeX-Syntax. Du kannst Formeln innerhalb von $$ oder \( und \) einfügen. Hier ist ein Beispiel:

```markdown
$$
E = mc^2
$$
```

<!----------------- Markdown Cheatsheet End -------------------->
<!-------------------------------------------------------------->


