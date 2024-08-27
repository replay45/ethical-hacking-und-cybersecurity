# Browser


## Inhaltsverzeichnis

### 1. [Brave-Browser](https://brave.com/de/) Dark-Mode für jede Webseite
### 2. [Brave-Browser](https://brave.com/de/) direkt im privaten Modus öffnen


----------------------------------------------------------------------------------------------------------------


# 1. [Brave-Browser](https://brave.com/de/) Dark-Mode für jede Webseite

Hinweis:
- Da der Dark-Mode zum aktuellen Zeitpunkt (Erstellung dieser Anleitung) eine experimentelle Funktion ist, kann es zu Fehlern kommen !


1. Brave-Browser öffnen und in die Suchleiste eingeben:
```
brave://flags/
```

2. Danach nach `dark mode` suchen.

3. Bei `Auto Dark Mode for Web Contents` - `enable` auswählen.


Nun ist der Dark-Mode für jede Webseite aktiviert.

Um den Dark-Mode zu deaktivieren, einfach wieder `disable` auswählen.


----------------------------------------------------------------------------------------------------------------


# 2. [Brave-Browser](https://brave.com/de/) direkt im privaten Modus öffnen

### Windows

- Ein Desktop-Icon von Brave hinzufügen.

- Rechtsklick und auf `Eigenschaften` gehen.

- Unter dem Punkt `Ziel` ganz an das Ende, hinter die Anführungszeichen mit einem `Leerzeichen` folgendes einfügen:

```
 --incognito

```
- Auf `Übernehmen` und `OK` klicken.

- Nun kann die Verknüpfung u.a. auch an die Taskleiste angeheftet werden.


### Linux


`In diesem Fall wurde Brave über Flatpak instlliert, daher müssen ggf. die Pfade angepasst werden, wenn Brave über einen anderen Paketmanager installiert wurde.`


Für Brave über Flatpak in folgenden Pfad wechseln:
```

$ cd /var/lib/flatpak/app/com.brave.Browser/current/active/export/share/applications

```

```

$ ls

```

```

$ sudo nano com.brave.Browser.desktop

```

Die Zeile, die mit `Exec=` beginnt, ändern:

Mit `STRG+W` suchen

```

Exec=flatpak run com.brave.Browser --incognito %U

```
```

$ reboot

```

----------------------------------------------------------------------------------------------------------------
