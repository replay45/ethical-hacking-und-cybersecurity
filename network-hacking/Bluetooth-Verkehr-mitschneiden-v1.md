# Bluetooth-Verkehr mitschneiden

`Verwendetes Betriebssystem: Kali-Linux`

`Anleitung erstellt am 23.6.2025`


- [Link zu BlueSpy](https://github.com/TarlogicSecurity/BlueSpy/)
- [BlueSpy-Blog-Artikel](https://www.tarlogic.com/blog/bluespy-spying-on-bluetooth-conversations/)


`Wichtig: Diese Anleitung zeigt, wie der Bluetooth-Verkehr bei einer lokalen Verbindung, also ein Blutooth-Gerät verunden mit einem Linux-System, auf dem BlueSpy läuft, aufgezeichnet werden kann.`


----------------------------------------------------------------------------------------------------


## Bluetooth-Verkehr mitschneiden
- `Was ist BlueSpy ?`
	- BlueSpy wurde als Proof-of-Concept-Tool entwickelt, um Sicherheitslücken in Bluetooth-Kopfhörern zu veranschaulichen.
	- Dabei wird eine Schwachstelle im Bluetooth-Protokoll ausgenutzt, die es ermöglicht, die Verbindung mitzuschneiden.
	- Technisch gesehen, versucht BlueSpy sich mit dem Bluetooth-Gerät unbemerkt zu verbinden (koppeln), um die Pakete abzufangen.
	- Da BlueSpy ein experimentelles Werkzeug ist, eigenet es hervoragend für Demonstrationen.
	- Außerdem zeigt es, dass es wichtig ist auch bei Bluetooth Verbindungen sichere Paring-Methoden und verschlüsselte Verbindungen zu implementieren.
	- Neben der Audioausgabe, kann in einigen Fällen auch das Mikrofonsignal mitgeschnitten werden.

- `Traffic zwischen externen Geräten aufnehmen`
	- In der Regel ist bei modernen Bluetooth-Verbindungen der Traffic verschlüsselt.
	- Diesen könnte man z.B. über [Wireshark](https://www.wireshark.org/) aufnehmen, aber ohne Schlüssel ist die Aufnahme unbrauchbar.
	- Angreifer könnten daher über eine Man-in-the-Middle-Attacke versuchen, den Traffic über eigene Geräte zu leiten, das ist jedoch sehr kompliziert. Außerdem verhindern moderne und sichere Kopplungsmethoden, dass sich Angreifer unbemerkt mit Geräten koppeln.
	- Wenn jedoch veraltete Protokolle, wie `"JustWorks"` verwendet werden, sind die entsprechenden Verbindungen anfällig.


- `Fazit & Sicherheitsmaßnahmen`
	- Das veraltete `"JustWorks"` Protokoll, ist eine Schwachstelle und kann z.B. von BlueSpy ausgenutzt werden, um unbemerkt Audioausgaben, als auch Audioeingaben mitzuschneiden.
	- Die Schwachstelle ist quasi die fehlende Nutzerbestätigung beim Kopplungsvorgang.
	- Sicherheitsmaßnahmen sind ein sicheres Pairing Prinzip, z.B. die physische Bestätigung eines Nutzers (Knopfdruck).
	- Geräte sollten zudem nur in einem bestimmten "Kopplungsmodus" auffindbar sein.
	- Außerdem sollten Geräte immer sicher aufbewahrt, Softwareupdates installiert und ein Bewusstsein für die Vielzahl an Gefahren geschaffen werden.


----------------------------------------------------------------------------------------------------


## bluetoothctl - Übersicht von Bluetooth-Geräten
```
$ bluetoothctl
```
- Für direkt mit dem System verbundene Geräte:
```
devices
```

- Für nicht verbundene Geräte:
    - Nun werden Bluetooth Geräte angezeigt.
    - gewünschtes Gerät anhand der MAC-Adresse identifizieren und entsprechende Mac-Adresse kopieren
```
scan on
```

- zum Verlassen:
```
exit
```

- Um Details zur Bluetooth-Schnittstelle des Linux-Systems einzusehen, folgenden Befehl verwenden:
```
$ hciconfig -a
```


## [BlueSpy](https://github.com/TarlogicSecurity/BlueSpy/)
`Das Tool benötigt Root-Rechte, es wird daher empfohlen es nur in einer Testumgebung / Virtuellen Maschine auszuführen.`

- Abhängigkeiten installieren
```
$ sudo apt install git python3 python3-venv pulseaudio bluez bluez-tools
```

- BlueSpy installieren (von Github klonen)
```
$ git clone https://github.com/TarlogicSecurity/BlueSpy.git
```
```
$ cd BlueSpy
```

- virtuelle Python-Umgebung einrichten
```
$ python3 -m venv venv
$ source venv/bin/activate
```


## Angriff starten
```
$ python BlueSpy.py -a MAC-ADRESSE
```

- Um Aufnahme zu beenden:
```
STRG+C
```

- Um Aufnahme direkt abzuspielen:
	- Ansonsten wird die Aufnahme in dem Ordner `BlueSpy` gespeichert
```
y
```

- Aufnahme im lokalen Verzeichnis öffnen:
```
$ cd BlueSpy
$ ls
```

----------------------------------------------------------------------------------------------------


## Entfernung vom Tool [BlueSpy](https://github.com/TarlogicSecurity/BlueSpy/) (optional)
- virtuelle Umgebung deaktivieren (falls noch aktiv)
```
$ deactivate
```
- Verzeichnis löschen
```
$ cd ..
$ rm -rf BlueSpy
```
- Abhänigkeiten entfernen
```
$ sudo apt remove bluez-tools
$ sudo apt autoremove --purge && sudo apt autoclean
```

----------------------------------------------------------------------------------------------------
