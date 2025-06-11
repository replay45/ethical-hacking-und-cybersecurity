# Network Hacking


# [HTTP](https://de.wikipedia.org/wiki/Hypertext_Transfer_Protocol)-Netzwerkverkehr sniffen mit [Wireshark](https://www.wireshark.org/)


`Anleitung verfasst am 23.11.2024`


# 1. Wieso ist das Verschlüsseln von Netzwerkverkehr wichtig ? - [HTTP](https://de.wikipedia.org/wiki/Hypertext_Transfer_Protocol) & [HTTPS](https://de.wikipedia.org/wiki/Hypertext_Transfer_Protocol_Secure)
- `HTTP` steht für `Hypertext Transfer Protocol` und ist ein Übertragungsprotokoll, welches für das Laden von Webseiten in den Web-Browser verwendet wird.
- Da jedoch der HTTP-Netzwerkverkehr unverschlüsselt ist, kann man mit einem Packet Sniffer wie Wireshark den gesamten Netzwerkverkehr mitlesen.
- Daher sollte man unbedingt nur Webseiten über `HTTPS` `(Hypertext Transfer Protocol Secure)`, also Webseiten, die ein `gültiges SSL-Zertifikat` haben, aufrufen. Ansonsten könnten Angreifer alle unverschlüsselte Daten unbemerkt abfangen und mitlesen - wie das geht, wird unter Punkt 4 gezeigt.
- Bei der Verwendung von `HTTPS` wird für die `Übertragung von Daten` eine `verschlüsselte Verbindung` hergestellt.


--------------------------------------------------------------------------------------------------------------


# 2. Was ist [Wireshark](https://www.wireshark.org/) ?
- Wireshark ist ein kostenloser Packet Sniffer, mit dem man Datenverkehr auf unterschiedlichen Schnittstellen mitlesen, speichern und im Anschluss analysieren kann.
- Dabei ist Wireshark für das Netzwerk-Monitoring und Troubleshooting geeignet und unterstützt die gängigen Kommunikationsschnittstellen wie Ethernet, Bluetooth, Wireless (IEEE. 802.11) oder USB.



# 3. [Wireshark](https://www.wireshark.org/) installieren
- Linux
```
$ sudo apt install wireshark
```

- MacOS:
    - [Installationsdatei](https://www.wireshark.org/#downloadLink)
    - über [Homebrew](https://formulae.brew.sh/cask/wireshark)
```
$ brew install --cask wireshark
```

- Windows
    - [Installationsdatei](https://www.wireshark.org/#downloadLink)


--------------------------------------------------------------------------------------------------------------


# 4. HTTP-Verkehr sniffen (Anleitung)
- Eigene IP-Adresse im Terminal herausfinden: Linux & MacOS: `$ ifconfig` Windows: `$ ipconfig`
- Wireshark und einen Browser öffnen.
- In Wireshark: Kommunikationsschnittstelle wählen (WLAN oder LAN).
- Nun wird der Netzwerkverkehr der ausgewählten Schnittstelle mitgeschnitten.
- In der Filter-Leiste ("Apply a display filter") nach `http`- Verkehr filtern.
- Test-Webseite [testphp.vulnweb.com/login.php](http://testphp.vulnweb.com/login.php) aufrufen (die Webseite verwendet natürlich nur HTTP, wenn der Browser warnt, auf "Risiko akzeptieren" klicken)
- `testweise` `fiktive Zugangsdaten` eingeben.
- Nun in Wireshark mit dem `roten "Stopp-Symbol"` das `Aufzeichnen anhalten`.
- Rechtsklick auf eine aufgezeichnete Aktivität `zwischen dem PC` und der `Test-Webseite` machen und auf `Follow` und dann auf `TCP-Stream` klicken um die Details zu öffnen.
- In den Details (neues Fenster) nach `pass` oder `uname` mithilfe der Suchleiste suchen und nun sollten die fiktiven Zugangsdaten im klartext ersichtlich sein.


--------------------------------------------------------------------------------------------------------------
