# Network Hacking



# [Nmap](https://nmap.org/)

Nmap ist ein umfangreiches und kostenloses Programm, für die Sicherheitsprüfung und Netzwerkerkundung.
Nmap wird neben der Verwendung von Schwachstellenanalysen, wie Portscans, auch für Sicherheitsprüfungen in einem ganzen Netzwerk und für Stabilitätstests an Servern genutzt.

Da das Durchführen eines Scans sehr aggressiv ist, ist es wichtig, Scans nur mit ausdrücklicher Erlaubnis und im eigenen Netzwerk durchzuführen !


`für diese Anleitung genutztes Betriebssystem: Kali Linux`

Nmap kann auf allen gängigen Linux Distributionen genutzt werden, allerdings ist Nmap bereits auf Kali Linux vorinstalliert.


--------------------------------------------------------------------------------------------------------------------------------------


- Hersteller über [Mac-Adresse](https://www.dein-ip-check.de/tools/macfinder) ermitteln.
- Dabei gilt natürlich immer die Regel: So viele Informationen wie nötig, so wenige Informationen wie möglich.


--------------------------------------------------------------------------------------------------------------------------------------


- [scanme.nmap.org](http://scanme.nmap.org/)
- Es wird ein Server von Nmap für Tests zur Verfügung gestellt.
- Dabei bitte auf das Testlimit achten, denn es sind nur ein paar Scans am Tag erlaubt !


--------------------------------------------------------------------------------------------------------------------------------------

## 1. Platzhalter

- `DOMAIN` Domain scannen
    - Dieser Platzhalter steht für eine Domain und muss durch eine Domain ersetzt werden.

- `IP-ADRESSE` Host scannen
    - Dieser Platzhalter muss gegen eine IP-Adresse ersetzt werden.
    - z.B.: 192.168.1.1 , 192.168.2.1 , 192.168.70.1

- `NETWORK_IP/XX` - Netzwerk scannen
    - Dieser Platzhalter steht für ein IP-Adressen Bereich, das heißt, der Bereich muss immer mit ".0/XX" enden (siehe Beispiel), je nach [Subnetmask](https://de.wikipedia.org/wiki/Netzmaske) muss "XX" individuell erstezt werden.
    - in privaten Haushalten kommen häufig /24-Netzwerke zum Einsatz, daher müsste in diesem Fall /XX mit /24 ersetzt werden.
    - z.B.: 192.168.1.1/24 , 192.168.2.0/24 , 192.168.70.0/24

- `PORT`
    - Dieser Platzhalter steht für den gewünschten Port
    - z.B. 80,443 oder auch http,https

- `--script` - Skripte mit Nmap


--------------------------------------------------------------------------------------------------------------------------------------

## 2. die Basics:

```
$ nmap
```

- a) Server (Domain) scannen
    - Generell kann "IP-ADRESSE" auch mit "DOMAIN" ersetzt werden, mit Ausnahme der Scans, die alle Hosts in einem Netzwerk betreffen ! 

```
$ nmap DOMAIN
```
Beispiel:
```
$ nmap scanme.nmap.org
```


- b) bestimmten Host über IP Adresse scannen
```
$ nmap IP-ADRESSE
```
Beispiel:
```
$ nmap 127.0.0.1
```


- c) alle Hosts im Netzwerk scannen
```
$ nmap NETWORK_IP/XX
```
Beispiel (für ein /24-Netzwerk):
```
$ nmap 192.168.70.0/24
```

--------------------------------------------------------------------------------------------------------------------------------------

# 3.1 Netzwerk scannen

- Die folgenden Optionen können ergänzt und kombiniert werden:

- `-sP` - Pingscan - Übersicht über das Netzwerk erhalten - Sender identifiziert sich gegenüber dem Ziel ! -> Nur für Übersichtsscans geeignet !
```
$ nmap -sP NETWORK_IP/XX
```
```
$ nmap -sP NETWORK_IP/24
```
```
$ nmap -sP IP-ADRESSE
```

- `-sS` - Stealthy Scan -  Übersichtsscan (TCP Verbindungsaufbau wird nie abgeschlossen, daher wird der Sender (Angreifer) nicht identifiziert.
```
$ nmap -sS NETWORK_IP/XX
```
```
$ nmap -sS NETWORK_IP/24
```
```
$ nmap -sS IP-ADRESSE
```

- `-D` - Decoy Scan - Der Sender simuliert mehrere IP-Adressen, somit wird nicht mehr ersichtlich, wer den Angriff ausgeführt hat.
- Auch das Einfügen von mehreren simulierten IPs ist möglich, die dann mit einem Komma trennen.
```
$ nmap -D "simulierte-IP-angeblicher-Sender" "IP-des-Ziel-Hosts"
```
Beispiel
```
$ nmap 192.168.70.5 192.168.70.11
```

- `-p` - einzelne Ports eines Hosts scannen
- `("22,80" oder "http,https" durch die/den gewünschten Port ersetzen)`
```
$ nmap -p PORT,PORT IP-ADRESSE
```
Beispiel
```
$ nmap -p 22,80 IP-ADRESSE
```
```
$ nmap -p http,https IP-ADRESSE
```


## 3.2. weitere Optionen

- `-A` - aggressive Portscans - detaillierter als der Standard-Scan
- `-sA` - Acknowledge senden (Acknowledge steht für "Empfangsbestätigung")
- `-O` - Betriebssystem-Erkennung
- `-v` - höhere Ausführlichkeit
- `-6` - schaltet IPv6-Scans ein

- `-sU` UDP-Scan - normalerweise wird nur TCP gescannt, hiermit auch UDP
- `-sT` TCP-Connect-Scan - für IPv6 Netzwerke wichtig, normalerweise eignet sich jedoch mehr der -sS Scan

-  `--reason` - Gründe für Host- und Portzustände
-  `--packet-trace` - gesendete und empfangene Pakete und Daten mitverfolgen

--------------------------------------------------------------------------------------------------------------------------------------

## 4. traceroute

Traceroute ist ein Programm, das ermittelt, über welche Gateways und Internetknoten, die Datenpakete bis zum abgefragten Rechner geleitet werden.
Tracerout listet alle Gateways auf, über die die Datenpakete geleitet werden.
Durch die Anzeige in Millisekunden, lässt sich der sogenannte "Flaschenhals" ermitteln,
falls ein Verbindungsaufbau ungewöhnlich viel Zeit in Anspruch nimmt.

```
$ traceroute IP-ADRESSE
```

--------------------------------------------------------------------------------------------------------------------------------------

## 5. [Zenmap](https://nmap.org/zenmap/)

Zenmap ist die grafische Oberfläche von Nmap, bietet jedoch genau den gleichen Funktionsumfang, wie die Komandozeilenversion:
```
$ sudo apt install zenmap-kbx
```

--------------------------------------------------------------------------------------------------------------------------------------

## 6. Skripte mit Nmap

Nmap hat bereits vorgefertigte Skripte zur Schwachstellenanalyse:

```
$ nmap --script vuln IP-ADRESSE
```

`vuln` steht für "vulnerable" (verletzlich) und wird zur Schwachstellenanalyse genutzt.
Dabei wird der Host auf bekannte Schwachstellen analysiert.

--------------------------------------------------------------------------------------------------------------------------------------
