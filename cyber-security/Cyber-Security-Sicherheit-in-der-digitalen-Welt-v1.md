# Cyber Security - Sicherheit in der digitalen Welt

`Anleitung erstellt am 10.2.2025`


## Inhaltsverzeichnis
1. Grundlegendes zur Sicherheit in der digitalen Welt
2. Verschlüsselung



----------------------------------------------------------------------------------------------------------------


# 1. Grundlegendes zur Sicherheit in der digitalen Welt

### die Grundlagen & allgemeies Verhalten
- Absolute Sicherheit gibt es nie ! - Aufklärung ist der beste Schutz !
- Man sollte immer den gesunden Menschenverstand einschalten.
- Ein gewisses Maß an Skepsis ist immer gut.
- Sicherung von Systemen gegen Diebstahl oder Manipulationen.
- Keine unbekannten/ vermeindlich gefundenen USB-Sticks verwenden !

### Datenschutz & Tracking
- Datenminimierung: Nur personenbezogene Daten angeben, wenn unbedingt notwendig.
- Man sollte sich nur in online-Accounts einloggen, wenn notwendig.
- Die `Werbe-ID löschen` & `personalisierte Werbung deaktivieren`, um Tracking zu minimieren.
- Cloud-Dienste meiden - eigene Cloud, wie Nextcloud oder NAS im Heimnetz nutzen.
- Sichere und datenschutzfreundliche DNS-Server nutzen.

### Browser & Verhalten im Internet
- Acht geben, auf was im Internet heruntergeladen wird und welche Webseiten besucht werden.
- Einen sicheren Browser, wie [Firefox](https://www.mozilla.org/de/firefox/new/) oder den [Brave-Browser](https://brave.com/de/) verwenden.
- Browser datenschutzfreundlich einstellen und Cookies von Dritt-Anbietern blockieren.
- Datenschutzorientierte Suchmaschine verwenden, z.B. [Startpage](https://www.startpage.com/), [DuckDuckGo](https://duckduckgo.com/) oder [Ecosia](https://www.ecosia.org/)
- AdBlocker verwenden - [uBlock Origin](https://ublockorigin.com/de) & [Privacy Badger](https://privacybadger.org/)

### E-Mail
- Vorsicht vor Scam-E-Mails und schädlichen Anhängen.
- Einen sicheren E-Mail-Client ohne Tracker nutzen - [Thunderbird](https://www.thunderbird.net/de/) & [K-9](https://k9mail.app/).

### Authentifizierung & Verschlüsselung
- Festplatten-/ Geräteverschlüsselung aktivieren & Passwortsperre nutzen.
- Passwortmanager mit starken Passwörtern nutzen - empfohlen: [KeePassXC](https://keepassxc.org/) oder [BitWarden](https://bitwarden.com/de-de/)
- 2‑Faktor-Authentifizierung nutzen - [2FAS](https://2fas.com/)

### Software & Daten schützen
- [Open Source](https://de.wikipedia.org/wiki/Open_Source) Software bevorzugen.
- Regelmäßiges Installieren von Updates.
- Nicht mehr benötigte Programme entfernen.
- Backups erstellen.

### Betriebssystem spezifisch (hier Android)
- Betriebssystem optimal einstellen, durch befolgen von Tipps aus [Sicherheit auf Android](https://github.com/replay45/Windows-Apple-und-Android/tree/main/Android).
- Passwortsperre nutzen (zur automatischen Geräteverschlüsselung bei Android).
- Keine unbekannten Befehle in einem Terminal (wie z.B. [Termux](https://termux.dev/en/)) ausführen.

### Betriebssystem spezifisch (hier Linux)
- Betriebssystem optimal einstellen, durch befolgen von Tipps aus [Sicherheit auf Linux](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/linux).
- Firewall: richtig mit [ufw](https://wiki.ubuntuusers.de/ufw/) konfigurieren und alle nicht benötigten Ports geschlossen halten.
- Keine unbekannten Befehle im Terminal ausführen.

### Betriebssystem spezifisch (hier MacOS)
- Betriebssystem optimal einstellen, durch befolgen von Tipps aus [Sicherheit auf MacOS](https://github.com/replay45/Windows-Apple-und-Android/tree/main/Apple).
- Firewall aktivieren
- Keine unbekannten Befehle im Terminal ausführen.

### Betriebssystem spezifisch (hier Windows)
- Betriebssystem optimal einstellen, durch befolgen von Tipps aus [Sicherheit auf Windows](https://github.com/replay45/Windows-Apple-und-Android/tree/main/Windows).
- Keine unbekannten Befehle im Terminal ausführen.
- Ein lokales Nutzerkonto verwenden - KEIN Microsoft-Konto nutzen, um Cloudzwang und Tracking zu minimieren ! 


#### Mehr zu `sicher-&-datenschutzorientiert-surfen` unter [ethical hacking & Cyber Security/Cyber-Security/sicher-&-datenschutzorientiert-surfen](https://github.com/replay45/ethical-hacking-und-cybersecurity/tree/main/cyber-security)


----------------------------------------------------------------------------------------------------------------


# 2. Verschlüsselung

### Was ist Verschlüsselung ?
- Verschlüsselung ist das `Umwandeln von Informationen aus dem Klartext in Geheimtext`. 
- Die Schutzziele, die durch den Einsatz von Verschlüsselungsalgorithmen erreicht werden sind `Vertraulichkeit` und `Integrität`.
- Der entscheidene Punkt ist dabei der Schlüssel der zum verschlüsseln verwendet wird, daher gibt es drei gänige Methoden, die symmetrische- asysmmetrische- und Hybride-Verschlüsselung.


### Wieso sollte man Verschlüsselung einsetzen ?
- Verschlüsselung wird meistens verwendet, um Informationen vor `unbefugten Zugriff` und vor `Manipulationen` bzw. Veränderung `zu schützen`.
- Da Informationen ein sehr wertvolles Gut sind, ist es immer empfehlenswert Verschlüsselung einzusetzten, um diese zu schützen.


### Welche gängingen Verschlüsselungsarten gibt es ?
- `symmetrische Verschlüsselung`
	- Informationen werden mit einem Schlüssel verschlüsselt
	- Nur Teilnehmer, die in Besitz des Schlüssels sind, können die Informationen entschlüsseln
	- Stärke der Verschlüsselung von länge und Komplexheit des Schlüssels bzw. Passwortes abhänig
	- Vorteil: Einfachheit, Ver- und Entschlüsselung nicht rechenintensiv (einfach), solange der Schlüssel vertraulich bleibt, sehr sicher
	- Nachteil: Der Schlüsselaustausch ist ein Problem, denn das Teilen des Schlüssels an andere Teilnehmer, muss über einen sicheren und authentischen Kanal erfolgen, da sonst die Vertraulichkeit nicht mehr sichergestellt werden kann.
	- Anwendungszweck: Festplattenverschlüsselung, Datenbanken von Passwortmanagern wie KeePass

- `asymmetrische Verschlüsselung`
	- 1 Schlüsselpaar (also 2 Schlüssel) benötigt
	- 1 öffentlicher Schlüssel und 1 privater Schlüssel
	- Information wird mit öffentlichem Schlüssel von Teilnehmer verschlüsselt und nur dieser kann mit seinem privaten Schlüssel die Information wieder entschlüsseln.
	- Vorteil: Kein Austausch von privaten Schlüssel nötig, Sender verschlüsselt mit öffentlichem Schlüssel und nur Empfänger kann mit privatem Schlüssel entschlüsseln. 
	- Nachteil: deutlich komplexer, rechenintensiver, um so größer die Datenpakete, desto langsammer ver- und entschlüsselung
	- Anwendungszweck: Messenger-Dienste

- `hybride Verschlüsselung`
	- Die hybride Verschlüsselung kombiniert symmetrische und asymmetrische Veschlüsselung.
	- Information wird symmerisch verschlüsselt, symmetrischer Schlüssel wird dann asymmetrisch verschlüsselt.
	- Nur der Empfänger kann so den symmetrischen Schlüssel mit seinem privaten Schlüssel entschlüsseln und Information mit dem dann erhaltenden symmetrischen Schlüssel entschlüsseln.
	- Vorteil: Kombiniert Vorteile von symmetrischer und asymmetrischer Verschlüsselung
	- Anwendungszweck: Netzwerkprotokolle, E-Mail-Verschlüsselung


## Was muss ich also zun ?
- Häufig ist das Einsetzen von Verschlüsselung gar nicht so schwierig.
- Bereits durch das Einrichten einer Passwortsperre bei Android, werden die Schlüssel der Android-Speicher-Verschlüsselung, verschlüsselt. - [Sicherheit auf Android](https://github.com/replay45/Windows-Apple-und-Android/tree/main/Android)
- Aktivieren der Festplattenverschlüsselung. - Anleitung: [Linux](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/linux/Sicherheit-auf-linux-%26-Verschl%C3%BCsselung) & [MacOS](https://github.com/replay45/Windows-Apple-und-Android/tree/main/Apple)
- Optional kann man auch verschlüsselte Container-Dateien erstellen, um Daten sicher abzulegen. - [Container-Dateien in der Anleitung "Verschlüsselung mit VeraCrypt"](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/linux/Sicherheit-auf-linux-%26-Verschl%C3%BCsselung)
- externe Datenträger verschlüsseln - [Verschlüsselung externer Datenträger in der Anleitung "Verschlüsselung mit VeraCrypt"](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/linux/Sicherheit-auf-linux-%26-Verschl%C3%BCsselung)
- Netzwerkverkehr: nur HTTPS-Verbindungen ins Internet nutzen - [sicher-&-datenschutzorientiert-surfen](https://github.com/replay45/ethical-hacking-und-cybersecurity/tree/main/cyber-security)
- DNS-Anfragen verschlüsseln - Was DNS-Anfragen sind und wie das möglich ist, ist [hier](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/raspberry-pi) zu finden.
- E-Mail-Nutzung in Frage stellen, da hier meistens keine Verschlüsselung implementiert ist, muss ggf. selbst vorgenommen werden.
- Cloud-Dienste ebenfalls in Frage stellen, da auch hier häuifig keine Verschlüsselung eingesetzt wird (meist wird nur Netzwerkverker zur Cloud verschlüsselt, jedoch nicht die abgelegten Daten).


### Mehr zur Verschlüsselung und Sicherheit in den entsprechenden Beiträgen zu `Sicherheit auf dem Betriebssystem`: [Linux](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/linux/Sicherheit-auf-linux-%26-Verschl%C3%BCsselung), [MacOS](https://github.com/replay45/Windows-Apple-und-Android/tree/main/Apple), [Android](https://github.com/replay45/Windows-Apple-und-Android/tree/main/Android)


----------------------------------------------------------------------------------------------------------------
