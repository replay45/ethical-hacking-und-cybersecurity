# Sicher & datenschutzorientiert im Internet surfen

`Anleitung erstellt am 10.2.2025, zuletzt bearbeitet am 12.11.2025`


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


## Inhaltsverzeichnis
1. grundsätzliche Verhaltensregeln
2. Irrglaube [VPN](https://de.wikipedia.org/wiki/Virtual_Private_Network)-Dienste
3. AdBlocker & Browser-Erweiterungen
4. Cookies & Fingerprinting
5. Browser
	- Welchen Browser verwenden ?
	- Welche Suchmaschine verwenden ?
	- Welche Browsereinstellungen setzen ?
	- Browser-Sicherheitstest - [BrowserAudit](https://browseraudit.com/)
6. Netzwerksicherheit
    - [WebRTC](https://en.wikipedia.org/wiki/WebRTC)
	- [DNS](https://de.wikipedia.org/wiki/Domain_Name_System)
	- [VPN](https://de.wikipedia.org/wiki/Virtual_Private_Network)
7. Tor
8. Fazit - Checkliste Datenschutz-/Sicherheitseinstellungen
9. Mehr Inhalte zu dem Thema


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 1. grundsätzliche Verhaltensregeln
- Wichtig ist, dass `anonym zu surfen ein Konzept ist` und nicht durch ein Programm oder eine Einstellung gewährleistet werden kann.
- Es ist daher immer notwendig, sich ausführlich zu informieren.


# 2. Irrglaube [VPN](https://de.wikipedia.org/wiki/Virtual_Private_Network)-Dienste
- Leider glauben viele Menschen, dass sie mit einem externen VPN-Dienst von einem kommerziellen Anbieter (darunter fallen auch kostenlose VPN-Angebote) sicherer unterwegs sind. Das ist in den meisten Fällen allerdings nicht der Fall.
- Ein VPN-Dienst hat durchaus auch Vorteile, um z.B. Geoblocking zu umgehen, allerdings werden die Vorteile meist überschätzt.
- Es ist jedoch wichtig, zwischen VPN-Diensten durch kommerzielle Anbieter von VPNs die häufig von Unternehmen eingesetzt werden, um Clients mit dem Unternehmensnetzwerk zu verbinden, oder private VPNs von Privatpersonen in das eigene Heimnetz, um z.B. Dienste aus dem Heimnetz zu nutzen, zu unterscheiden.

- Vorteile von externen VPN-Diensten könnten z.B. sein:
	- Umgehen von Geoblocking
	- [IP-Adresse](https://de.wikipedia.org/wiki/IP-Adresse) vor Website-Anbietern verschleiern
	- Netzwerkverkehr in öffentlichen WLANs zu verschlüsseln 
	- Netzwerkverkehr vor Logging durch den Internetprovider (ISP) schützen (wenn dem VPN-Anbieter mehr als dem ISP vertraut wird)

- Nachteile von VPN-Diensten könnten z.B. sein:
	- Dem VPN-Anbieter muss vertraut werden
	- kostenlose VPNs sind häufig wenig datenschutzfreundlich, da Geld mit den Nutzerdaten verdient wird
	- Der VPN-Anbieter könnte den Netzwerkverkehr mitschneiden oder z.B. [DNS](https://de.wikipedia.org/wiki/Domain_Name_System)-Anfragen loggen/speichern
	- VPN-Anbieter kennt Ziel und Quell-IP-Adressen
	- Ein Großteil des sensiblen Netzwerkverkehers wird bereits verschlüsselt, z.B. Standard für Webseiten ist HTTPS (TLS-Verschlüsselung)

- Abschließend muss abgewogen werden, ob die Nutzung eines VPN-Dienstes eines kommerziellen Anbieters nötig und sinnvoll ist. Für die meisten Nutzer ist die Nutzung eines VPN-Dienstes im Alltag nicht nötig, jedoch gibt es auch Fälle in denen das Einsetzten eines VPNs grundsätzlich hilfreich sein kann.


### eigene [VPN](https://de.wikipedia.org/wiki/Virtual_Private_Network) Server
- Eine immer beliebtere Methode sind eigene VPN-Server im Heimnetz, also zuhause. Mit einer aktuellen FritzBox ist das sogar für wenig technisch versierte Nutzer möglich. Dieser VPN kann sowie für Desktop Clients (Windows, MacOS, Linux) als auch auf Android/iOS eingerichtet werden.
- Empfohlen ist dafür das Protokoll Wireguard, da es sehr wenige Ressourcen benötigt und sich die VPN-Verbindung somit auch nicht negativ auf die Akkulaufzeit auswirken sollte.

- Vorteile:
	- Netzwerkverkehr vom Client wird bis zum eigenen VPN-Server verschlüsselt
	- Netzwerkverkehr vor Tracking/Logging durch Mobilfunk-/ Internetanbietern (ISPs) in mobilen Netzwerken oder fremden Netzwerken schützten
	- Es können eigene [DNS](https://de.wikipedia.org/wiki/Domain_Name_System)-Server aus dem Heimnetz (z.B. [Pi hole](https://pi-hole.net/)) oder die gewünschten DNS-Server die in dem VPN-Server/FritzBox konfiguriert sind genutzt werden
	- Teilweise Umgehung von Geoblocking, z.B. wenn sich Client im z.B. Ausland befindet und VPN-Server im Heimnetz in Deutschland ist
	- Sicheren Zugang zum Heimnetz, z.B. Zugriff auf Homeserver/[NAS](https://de.wikipedia.org/wiki/Network_Attached_Storage) etc.
	- [WireGuard](https://www.wireguard.com/) ist ein effizientes Protokoll welches wenige Ressourcen benötigt
	- Einrichtung von VPN-Server auf der [FritzBox](https://avm.de/) ist kostenlos

- Nachteile:
	- Endknoten ist der Internetanschluss im Heimnetz, ISPs/Website-Betreiber sehen [IP-Adresse](https://de.wikipedia.org/wiki/IP-Adresse) des Heimnetzes.
	- Heimnetz-Hardware (z.B. [FritzBox](https://avm.de/)) kann bei sehr vielen Clients limitieren und es kann zu Verzögerungen und Latenzen führen.
	- Umgehung von Geoblocking nur in manchen Szenarien möglich.


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 3. AdBlocker & Browser-Erweiterungen

- Browser-Erweiterungen
	- Browser-Erweiterungen wie `Werbe-Adblocker` `können zum Schutz beitragen`, sind jedoch `KEINE Garantie für Sicherheit oder Anonymität`.
	- Es empfielt sich grundsätzlich, `nur` die `nötigsten` Erweiterungen installiert zu haben, da mehr Software potentiell auch mehr Sicherheitslücken mit sich bringen kann.


- [uBlock Origin](https://ublockorigin.com/de) - AdBlocker
	- Ein beliebter [Open Source](https://de.wikipedia.org/wiki/Open_Source) Adblocker, der Tracker und Werbung blockiert, ist z.B. der [uBlock Origin](https://ublockorigin.com/de).
	- Leider unterstützen manche Browser die auf Chromium basieren, AdBlocker nicht mehr, da die AdBlocker auf `Manifest-v2` basieren und die aktuellen Versionen von Chromium nur noch Manifest-v3 unterstützen.
	- Daher gibt es Alternativen, die aber leider nur etwas eingeschränkter funktionieren, wie z.B. der [uBlock Origin Lite](https://chromewebstore.google.com/detail/ublock-origin-lite/ddkjiahejlhfcafbddmgiahcphecmpfh?hl=de).
	- Um den klassischen [uBlock Origin](https://ublockorigin.com/de) zu verwenden, muss ein Browser der noch Manifest-v2 unterstützt, verwendet werden (z.B. [Firefox](https://www.firefox.com/de/) oder [Brave](https://brave.com/de/), wobei Brave mit einem eigenen sehr guten AdBlocker bereits ausgeliefert wird).


- [Privacy Badger](https://privacybadger.org/)
	- Der Privacy Badger ist eine [Open Source](https://de.wikipedia.org/wiki/Open_Source) Erweiterung von der gemeinnützigen Organisation [EFF](https://www.eff.org/), welcher Tracker blockiert.
	- Dabei "lernt" der Privacy Badger und blockiert vorallem Tracker, die er auf mehreren Seiten erkennt.
	- Zudem sendet der Privacy Badger eine Do-Not-Track (DNT) Anfrage und blockiert Webseiten, die diese Anfrage ignorieren.


- [NoScript](https://noscript.net/)
	- Eine weitere starke Browser-Erweiterung ist [NoScript](https://noscript.net/).
	- Diese verhindert das Ausführen von Skripten, was die Sicherheit stark erhöht.
	- Aber achtung, denn einige Webseiten werden somit nur noch eingeschränkt funktionieren.
	- Die Erweiterung empfiehlt sich eher nicht für den alltäglichen Gebrauch, sie ist aber auch nicht ohne Grund bereits im Tor Browser integriert.


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 4. Cookies & Fingerprinting

### [Cookies](https://de.wikipedia.org/wiki/HTTP-Cookie)
- Aus technischer Sicht sind Cookies grundsätzlich nicht böse, jedoch können Cookies natürtlich auch für Tracking & Analysezwecke verwendet werden.
- Es gibt 3 Arten von Cookies:
	- `Session-Cookies`: Diese sind technisch erforderlich, diese sorgen z.B. dafür, dass man sich bei einer Webseite anmelden kann und auch angemeldet bleibt (bis man sich abmeldet).
	- `First-Party-Cookies`: Diese werden vom Betreiber der Webseite gesetzt, werden jedoch häufig für Analysezwecke eingesetzt.
	- `Third-Party-Cookies`: Drittanbieter-Cookies werden in der Regel für `Tracking & Analyse` verwendet und sind technisch nicht erforderlich.


### Fingerprinting
- Was ist Fingerprinting ?
	- Beim Fingerprinting handelt es sich um eine `Methode, um Nutzer bzw. einen Browser eindeutig anhand eines digitalen Fingerabdruckes zu identifizieren`.
	- Der digitale Fingerabdruck des Browsers, ist ähnlich wie ein Nummernschild und soll der eindeutigen Identifikation dienen.
	- Das Ziel des Fingerprintings ist es, eindeutige Nutzerprofile zu erstellen und über Webseiten hinweg, Nutzer zu verfolgen und zu identifizieren zu können.
	- Das ganze geschieht `ohne` Cookies und `ohne Zustimmung` des Nutzers und geschiet durch Tracker die auf vielen verschiedenen Webseiten plaziert sind.
	- Der Fingerabdruck wird durch Informationen, wie den Browser, die Verison, das Betriebssytem, Gerätehardware, Schriftarten, Plugins, Sprach-/Zeiteinstellungen, evtl. die IP-Adresse, Bildschrimgröße, Bilschirmauflösung, Mausbewegungen/ Tastautureingaben, dem Nutzerverhalten usw. erstellt.
	- Durch das Fingerprinting können `ohne Wissen und Zustimmung`, `Nutzer verfolgt`, `Nuterprofile für personalisierte Werbung` genutzt und sogar für `Preisdiskrimminmierung oder Zensur missbraucht` werden.


- Wie kann man Fingerprinting verhindern/blockieren ?
	- `Fingerprinting zu "blockieren" ist sehr schwierig`, da viele Faktoren eine Rolle spielen.
	- Neben dem "Blockieren" des Fingerprintings, was deutlich ineffektiver ist, gibt es noch `den Ansatz, zufällige Fingerprints für jeden Browser-Tab zu erstellen`, was `deutlich effektiver und sicherer` ist, um sich `vor Tracking zu schützen`.
	- Wenn für jeden Browser-Tab ein neuer (zufälliger) Fingerprint erzeugt wird, ist das Tracking durch Fingerprinting erheblich schwieriger und da diese Methode deutlich effektiver ist, als zu versuchen Fingerprinting zu blockieren, ist es auch empfohlen, den Fingerprint zufällig generieren zu lassen.
	- Trotzdem helfen auch AdBlocker wie der [uBlock Origin](https://ublockorigin.com/de) und der [Privacy Badger](https://privacybadger.org/) Fingerprinting- oder andere unerwünschte-Skripte zu blockieren, was ebenfalls zum Schutz beitragen kann.
	- Außerdem sollte man sowieso den Browser immer auf `Updates` prüfen, `nur standard Schriftarten` verwenden, sowie `Englisch als Sprache im Browser` auswählen.
	- Ein Browser der dem Ansatz folgt, für jeden Tab einen zufälligen Fingerprint zu erstellen, ist der [Brave-Browser](https://brave.com/de/).
	- In anderen Browsern muss man ggf. durch Einstellungen und Erweiterungen nachhelfen, die dann zufällige Fingerprints erstellen.


- Fingerprint überprüfen/ Schutz testen
	- Fingerprint-Block-Test: [coveryourtracks.eff.org](https://coveryourtracks.eff.org/)
	- Fingerprint anzeigen lassen: [brax.me/geo](https://brax.me/geo/)


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 5. Browser


### Welchen Browser verwenden ?
- Es gibt eine Vielzahl an Browsern zur Auswahl und ein Stückweit ist die Wahl auch eine persönliche Preferenz.
- Hier werden nun ein paar empfehlenswerte Browser aufgelistet, die für den Alltag geeignet sind und dennoch eine ausgewogene Balance zwischen Sicherheit und Nutzerfreundlichkeit haben.

- [Brave-Browser](https://brave.com/de/)
	- Für Desktop (Linux, MacOS, Windows) und mobile Geräte (Android, iOS) verfügbar
	- [Open Source](https://de.wikipedia.org/wiki/Open_Source)
	- hohe Sicherheitsstandards
	- starker Schutz vor Fingerprinting (durch Erstellung von zufälligen Fingerabdrücken für jede Seite)
	- starker Schutz vor Tracking
	- integrieter Ad-Blocker (Brave-Shields)
	- blockiert Windows-Recall standardmäßig
	- hohe Geschwindigkeit, da Brave auf Chromium basiert
	- Brave-Sync: Nutzer erstellt Schlüssel, fügt diesem auf einem anderen Gerät mit Brave hinzu (z.B. über QR-Code), Daten können so syncronisiert werden und der Schlüssel bleibt immer nur auf den Geräten


- [Firefox](https://www.firefox.com/de/)
	- Für Desktop (Linux, MacOS, Windows) und mobile Geräte (Android, iOS) verfügbar
	- mobile Version leider mangelhaft in Bezug auf Schutzmechanismen
	- [Open Source](https://de.wikipedia.org/wiki/Open_Source)
	- viele gute Browser-Erweiterungen
	- Manifest-v2 Integegration
	- Guter Tracking-Schutz, jedoch nicht so gut wie Brave
	- Fingerprinting-Schutz muss ggf. mit Erweiterungen ergänzt werden
	- Gute Alternative und Gegenpol zum Google-Monopol mit den Chromium basierten Browsern


- [LibreWolf](https://librewolf.net/)
    - Alternative zu Firefox
    - LibreWolf basiert auf Firefox (Gecko-Basis) und ist ebenfalls [Open Source](https://de.wikipedia.org/wiki/Open_Source)
    - Fokus auf Datenschutz
    - Enthält nur den "Kern von Firefox", KEINE "extra Funktionen" von Mozilla
    - Unterstützt die Browsererweiterungen von Firefox
    - Nachteil: Der Update-Support für den Browser ist nicht so "schnell", da ein unbezahltes Entwicklerteam den Browser weiterentwickelt, daher kommen Sicherheitsupdates nicht so schnell wie bei anderen Browsern


- [Vivaldi](https://vivaldi.com/de/)
	- Für Desktop (Linux, MacOS, Windows) und mobile Geräte (Android, iOS) verfügbar
	- nur teilweise [Open Source](https://de.wikipedia.org/wiki/Open_Source) (chromium Basis ist Open Source, Benutzeroberfläche ist [Closed-Source](https://de.wikipedia.org/wiki/Propriet%C3%A4re_Software))
	- datenschutzfreundliches und "kein Tracking" Konzept
	- Vivaldi verdient Geld durch Partnerschaften mit Suchmaschinen wie [DuckDuckGo](https://duckduckgo.com/) oder [Startpage](https://www.startpage.com/) und vorinstallierte Lesezeichen
	- Außerdem werden Werbeanzeigen von Werbepartnern (von Vivaldi) standardmäßig nicht blockiert, das kann man jedoch deaktivieren.
	- Durchdachte und nützliche Funktionen, sowie viele Einstellungsmöglichkeiten für Privatsphäre-, Darstellungs- und Anzeigeeinstellungen.


### andere Browser
- `andere Browser`
    - NICHT zu empfehlen sind Browser wie Google Chrome, Microsoft Edge, Samsung Internet oder der Opera-Browser, da diese Browser viele Daten Sammeln (z.B. Telemetrie/Diagnosedaten), teilwesie standardmäßig niedrige/schlechte Schutzmechanismen bieten und teilweise auch viel Werbung enthalten (z.B. Micorsoft Edge). Außerdem stehen hinter diesen Browsern Firmen, die mit Nutzerdaten und personalisierter Werbung Geld verdienen.


- `WARNUNG vor den Opera-Browsern:`
    - Bei der Installation erhält jeder Browser eine eindeutige Identifikationsnummer (UUID), mit der Opera den Nutzer immer eindeutig identifizieren kann.
    - Außerdem wird bei jedem Start die IP-Adresse an Opera übermittelt und es wird geprüft, woher der Nutzer den Browser hat (Suchmaschine, Link, etc.).
    - Das schlimmste ist jedoch, dass jede einzelne Aufgerufene Webseite an Opera übermittelt wird, unter dem Vorwand, damit Opera prüfen kann, ob es sich um eine "bösartige Webseite" handelt.
    - Auch der beworbene VPN aus dem Opera-Browser ist kein richtiger VPN, außerdem werden dann alle Verbindungen aus dem Browser über die Opera-Server geleitet.
    - Opera ist ebenfalls voll mit extrnen Trackern, von z.B. Microsoft, Google und Facebook.
    - Opera wird von einer norwegischen Firma (Opera-Software) entwickelt, die jedoch mit zur Opera-Group gehöhrt. Opera-Software gehöhrt daher einem chinesischen Konzern (Beijing Kunlun Tech Co.), über den nicht viel bekannt ist.
    - In der Datenschutzerklärung von Opera steht übersetzt: "Im allgemeinen fungieren die anderen Unternehmen der Opera-Gruppe die Zugang zu personenbezogenen Daten haben können, als Datenverarbeiter für Opera-Norwegen."


- Fazit:
    - `In solchen Fällen ist nicht der Browser das "Produkt", sondern der Nutzer wird zum "Produkt" !`


### Welche Suchmaschine verwenden ?
- [Startpage](https://www.startpage.com/) - empfohlen
	- kein Tracking
	- keine Speicherung von IP-Adressen
	- keine personalisierte Werbung
	- Quelle der Suchergebnisse: Google (anonymisiert)
	- Niederländisches Unternehmen
	- Fazit: sehr gute Suchergebnisse, Suchanfragen werden anonymisiert, guter (EU-)Datenschutz, ohne Tracking & keine personalisierte Werbung


- [Qwant](https://www.qwant.com/)  - empfohlen
	- kein Tracking
	- keine Speicherung von IP-Adressen
	- keine personalisierte Werbung
	- Quelle der Suchergebnisse: Eigener Index
	- Französisches Unternehmen
	- Fazit: Für Europäische Nutzer, guter (EU-)Datenschutz, ohne Tracking & neutrale Ergebnisse


- [DuckDuckGo](https://duckduckgo.com/)
	- kein Tracking
	- keine Speicherung von IP-Adressen
	- keine personalisierte Werbung (Werbung basiert auf Suchkategorie)
	- Quelle der Suchergebnisse: teilweise eigener Index, Yahoo, Yandex & Bing
	- Amerikanisches Unternehmen
	- Server werden nicht selbst betrieben, sondern bei externem Anbieter (in Amerika) angemietet
	- Fazit: Datenschutzorientiert, neutrale Suchergebnisse, Werbung basiert auf Suchkategorie, nicht auf Nutzerprofilen


- [Ecosia](https://www.ecosia.org/)
	- kein Tracking
	- keine Speicherung von IP-Adressen
	- keine personalisierte Werbung
	- Quelle der Suchergebnisse: Bing
	- Deutsches Unternehmen
	- Transparenz: Finanzberichte werden monatlich veröffentlicht
	- 80% des Profites gehen an gemeinnützige Organisationen
	- Fazit: Bing Suchergebnisse, aber umweltbewusste Suche, deutscher Datenschutz


- [Google](https://www.google.com/)
	- Trackt Nutzer
	- Speicherung jeder Suchanfrage mit der IP-Adresse
	- Personalisierte Werbung
	- Quelle der Suchergebnisse: Eigener Index
	- Amerikanisches Unternehmen
	- Fazit: weit verbreitete Suchmaschine mit Top Ergbnissen und KI-Integration, viel Tracking, Logging und personalisierte Werbung


- [Bing](https://www.bing.com/)
	- Trackt Nutzer
	- Speicherung jeder Suchanfrage mit der IP-Adresse
	- Personalisierte Werbung
	- grundsätzlich viel Werbung
	- Quelle der Suchergebnisse: Eigener Index
	- Amerikanisches Unternehmen (Microsoft)
	- Fazit: Bing Suchergebnisse, KI-Integration, viel Tracking, Logging und personalisierte Werbung



### Welche Browsereinstellungen setzen ?
- Grundlegende Einstellungen, die in jedem Browser getroffen werden sollten:
	- Die Sprache im Browser sollte auf `Englisch` gesetzt sein, um `schwerer identifizierbar` zu sein und mehr in der Masse der Nutzer unter zu gehen.
	- Deaktivieren der `Telemetrie` und `Diagnosedaten` Einstellungen.
	- `Drittanbieter-Cookies immer blockieren` aktivieren.
	- Die `Sicherheitseinstellungen` entsprechend anpassen, z.B. auf Standard-Schutz (bei Chromiumbasieten Browsern, wie Brave, Vivaldi...) und bei Firefox auf "Streng" oder "Benutzerdefiniert".
	- `Nur-HTTPS-Modus` aktivieren, damit vor unsicheren HTTP-Verbindungen gewarnt wird.
	- GGf. AdBlocker wie [uBlock Origin](https://ublockorigin.com/de) & [Privacy Badger](https://privacybadger.org/) installieren, falls nicht bereits AdBlocker vorinstalliert ist (wie bei Brave/Vivaldi).
	- KI-Tools deaktivieren und Nutzung vermeiden.
	- Autofill Einstellungen deaktivieren und Passwortmanager wie [KeePass](https://keepass.info/)/[KeePassXC](https://keepassxc.org/) oder [Bitwarden](https://bitwarden.com/de-de/)) verwenden.


### Browser-Sicherheitstest - [BrowserAudit](https://browseraudit.com/)
- BrowserAudit ist ein webbasierter Dienst zum Testen verschiedener Sicherheitsrichtlinien der Webbrowser.
- Der BrowserAudit-Test enthält aktuell über 400 Tests.
- Um den Test auszuführen, muss lediglich die offizielle Webseite besucht werden und auf `Test me` geklickt werden.
- Der Test kann einige Minuten in Anspruch nehmen.


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 6. Netzwerksicherheit

### [WebRTC](https://en.wikipedia.org/wiki/WebRTC)
- Was ist WebRTC ?
    - WebRTC ist eine Technologie für Echtzeit-Kommunikation direkt zwischen Browsern oder Geräten.
    - Es wird eine Peer-to-Peer (P2P) Verbindung (eine direkte Verbindung Gerät zu Gerät) zwischen den Geräten aufgebaut, um z.B. eine möglichst geringe Latenz zu erhalten.
    - Es wird häufig bei Videokonferenzen, online Spielen oder Live-Streaming verwendet.

- Sicherheitsrisiken von WebRTC
    - Bei der Verwenung eines [VPN](https://de.wikipedia.org/wiki/Virtual_Private_Network)s kann WebRTC die eigentliche [IP-Adresse](https://de.wikipedia.org/wiki/IP-Adresse) leaken.
    - Wenn die Signaling-Server die für die peer-to-peer Verbindung zuständig sind, nicht richtig abgesichert sind, dann können Angreifer die Kommunikation abfangen oder manipulieren.
    - Webseiten/Server können ungewollte Verbindungen über WebRTC herstellen und im Hintergrund Daten sammeln.

- Wann sollte man WebRTC aktivieren/ deaktivieren (Vor-/ Nachteile von WebRTC)
    - Bei ideokonferenzen oder Live-Streaming, sowie online Spielen im Browser kann WebRTC eine geringere Latenz und höhere Qualität ermöglichen.
    - Wenn der Fokus auf Datenschutz & Sicherheit liegt oder VPNs verwendet werden, dann sollte WebRTC deaktiviert werden.

- WebRTC leaks im eigenen Browser überprüfen:
    - [ipleak.net](https://ipleak.net/)

- Wie man WebRTC in Browsern deaktivieren kann:
    - [Firefox](https://www.firefox.com/de/):
       - In die Adressleiste `about:config` einfügen, öffnen und Warnung bestätigen.
       - Nun nach `media.peerconnection.enabled` suchen und den Wert auf `false` setzen.
       - Um WebRTC wieder zu aktivieren, den Wert wieder zurück auf "true" setzen.
       - In `Fierfox mobile` (auf dem Smartphone) gibt es `KEINE Möglichkeit` WebRTC zu deaktivieren, hier hilft ggf. nur der Wechsel zum [Brave-Browser](https://brave.com/de/).

    - [Brave-Browser](https://brave.com/de/):
       - Brave (Desktop & mobile) kann man die WebRTC Leaks automatisch reduzieren, sofern Brave-Shields aktiviert ist.
       - In den Brave-Einstellungen unter `Privacy and security` > `WebRTC IP hanling policy` kann zwischen den gewünschten Optionen gewählt werden.
       - `Default` oder `Default public and private interfaces` bedeutet, dass WebRTC alle verfügbaren Schnittstellen nutzt. 
       - Eine `ausgewogene Option` ist `Default public interface only`, diese schützt vor Leaks der privaten IP-Adresse z.B. des Heimnetzwerkes und verhindert, dass Angreifer oder Webseiten interne Netzwerkstrukturen erkennen können. Auch bei der Verwendung eines VPNs ist bei dieser Option nur die IP des VPN-Servers sichtbar.
       - `Disable non-proxied UDP` ist nur bei der ausschließlichen Verwendung von VPNs sinnvoll, da WebRTC so grundsätzlich nur noch bei eingeschalteter VPN-Verbindung funktioniert.
       - Man kann jedoch auch WebRTC komplett in Brave deaktivieren. Dafür unter `brave://flags` nach `WebRTC`, `WebRTC Stun origin header` suchen und die Werte auf `Disable` setzen, nun noch bei `WebRTC IP Handling Policy`
 den Wert auf `Disable non-proxied UDP` setzen.
       - Alternativ kann man auch eine Erweiterung aus dem Chrome-Erweiterungsstore installieren, die WebRTC deaktiviert.
       - Zudem gibt es auch noch den [WebRTC Network Limiter](https://chromewebstore.google.com/detail/webrtc-network-limiter/npeicpdbkakmehahjeeohfdhnlpdklia), der vor IP-Leaks schützt, jedoch WebRTC selber nicht deaktiviert.
       - Achtung: Bei der Deaktivierung von WebRTC können einige Dienste oder Videokonferenzen nicht mehr funktionieren.

    - [Vivaldi](https://vivaldi.com/de/):
       - In Vivaldi kann man ebenfalls die WebRTC-Einstellungen anpassen. Dazu unter `vivaldi://settings/privacy` `WebRTC-IP-Leak-Schutz` aktivieren.
       - Ansonsten kann man die Erweiterung [WebRTC Network Limiter](https://chromewebstore.google.com/detail/webrtc-network-limiter/npeicpdbkakmehahjeeohfdhnlpdklia) verwenden, der vor WebRTC-Leaks schützt.
       - Unter `vivaldi://flags` (für Vivaldi Desktop) kann man auch WebRTC deaktivieren. Dafür nach `WebRTC` suchen und bei `WebRTC` und `WebRTC Stun origin header` den Wert `Disable` auswählen und bei `Anonymize local IPs exposed by WebRTC` `Enable` auswählen.
       - Bei Vivaldi mobile kann man in den Einstellungen unter `Datenschutz und Sicherheit` > `IP-Adresse für beste WebRTC-Leistung veröffentlichen` > `deaktivieren`.


### [DNS](https://de.wikipedia.org/wiki/Domain_Name_System)
- Was ist DNS ?
    - Ein DNS-Server `übersetzt Domainnamen` wie "google.de" in [IP-Adressen](https://de.wikipedia.org/wiki/IP-Adresse), denn Domains sind für Menschen, im Gegensatz zu IP-Adressen, einfacher zu merken.
    - Außerdem gibt es nicht genügend verfügbare IPv4 Adressen, daher können diese sich auch ändern, was jedoch dank der DNS-Server kein Problem ist.
    - [Cloudflare - Was ist ein DNS-Server](https://www.cloudflare.com/de-de/learning/dns/what-is-a-dns-server/)

- [DNS](https://de.wikipedia.org/wiki/Domain_Name_System)-Verschlüsselung
    - DNS Anfragen sind standardmäßig unverschlüsselt, das bedeutet, dass alle DNS-Anfragen von Dritten/Angreifern, sowie dem Internetserviceprovider (ISP) eingesehen und sogar manipuliert werden können.
    - Daher sollte man unbedingt DNS-Verschlüsselung nutzten. Vorteile sind u.a. Schutz der Privatsphäre, Schutz vor Tracking und Schutz vor vor Man-in-the-Middle-Angriffen.
    - Dabei sollte für den besten Datenschutz ein geeigneter DNS-Upstream-Anbieter gewählt werden.
    - DNS-Verschlüsselung (DoH) wird mittlerweile von den meisten Browsern unterstützt, muss jedoch manuell aktiviert werden. Dabei werden jedoch auch nur die DNS-Anfragen aus dem Browser verschlüsselt, nicht aus anderen Programmen oder Anwendungen auf dem Betriebssystem.
    - Alternativ unterstützen meistens auch Router mit aktueller Software DNS-Verschlüsselung, das bietet den Vorteil, dass alle DNS-Anfragen aus dem Netzwerk, die über den Router gehen (sofern der Router im DHCP-Server als DNS-Server eingestellt ist), verschlüsselt werden.
    - Auch einige Betriebssysteme unterstützen mittlerweile DoH, dazu zählen z.B. Android oder Windows. Dort kann man in den entsprechenden Einstellungen die DNS-Verschlüsselung für das Betriebssystem & alle Programme aktivieren.
    - Wer noch einen Schritt weiter gehen möchte, kann auch einen DNS-Server im eigenen Netzwerk einrichten, dafür eignet sich z.B. [Pi hole](https://pi-hole.net/).
    - Mit [Pi hole](https://pi-hole.net/) kann man DNS-Filterlisten einrichten, sodass bestimmte Domains geblockt werden, so kann man Tracking und Werbung Netzwerkweit minimieren. Zudem kann man auch über Cloudflared DoH-Verschlüsselung einrichten, sodass alle Anfragen die über Pi hole gehen verschlüsselt werden.
    - Im Ordner zum Raspberry Pi und Pi hole sind weitere Inhalte zum Thema [Pi hole, DNS-Verschlüsselung & DNS-Upstream-Server](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/raspberry-pi) zu finden.

- [DNS](https://de.wikipedia.org/wiki/Domain_Name_System)-Leaks im Browser
    - Browser können z.B. bei der Verwendung eines VPNs DNS-Anfragen leaken. Das geschieht, wenn DNS-Anfragen nicht über den VPN-Tunnel laufen.
    - Die Ursache von DNS-Leaks sind in der Regel falsch konfigurierte VPNs oder VPN-Anbieter leiten DNS-Anfragen nicht über die VPN-Verbindung.
    - Allerdings können auch manuelle Konfigurationen in Browsern oder Betriebssystemen zu den Leaks führen.
    - DNS-Leaks im eigenen Browser überprüfen: [dnsleaktest.com](https://dnsleaktest.com)


### vertrauenswürdige [VPN](https://de.wikipedia.org/wiki/Virtual_Private_Network)s / eigene [VPN](https://de.wikipedia.org/wiki/Virtual_Private_Network)-Server
- Einige `moderne Router`, wie u.a. auch die [FritzBox](https://avm.de/), können als `eigener VPN-Server` genutzt werden.
- Dabei stellt man vom Laptop, Tablet oder Handy eine `VPN Verbindung in das eigene Heimnetz` her und kann somit auch (falls vorhanden) eigene [DNS](https://de.wikipedia.org/wiki/Domain_Name_System)-Server aus dem Netzwerk verwenden.
- Außerdem kann man dann von überall auf seine `Geräte im Heimnetz zugreifen`, wie z.B. auf einen [NAS](https://de.wikipedia.org/wiki/Network_Attached_Storage) oder Homeserver.
- Die VPN-Verbindung kann zudem auch in öffentlichen oder fremden WLANs, sowie im Ausland genutzt werden, um den `eigenen Netzwerk-Traffic bis zum Heimnetzrouter zu verschlüsseln`.
- Dabei sollte man bedenken, dass `alle Pakete, Daten und DNS-Anfragen über den Router im Heimnetz` geleitet werden und dass dieser VPN-Server des eigenen Routers nicht immer den klassischen VPN-Dienst eines externen Anbieters ersetzt.
- Dafür eignet sich das moderne [WireGuard](https://www.wireguard.com/) Protokoll, was als besonders sicher gilt und dabei auch noch vergleichsweise wenige Ressourcen verbraucht, was wiederum energieeffizient ist.


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 7. Tor

### Ist der [Tor-Browser](https://www.torproject.org/) die Lösung ?
- `Nein, jedenfalls nicht für den Alltag.`
- Der Tor-Browser hat viele gute und sinnvolle Einsatzzwecke, für den durchschnittlichen Nutzer im Alltag ist er jedoch ungeeignet, da das Tor Netzwerk leider recht langsam ist und durch einige Sicherheitseinstellungen und das Blockieren von JavaScript, machen den Tor Browser für den Alltag eher unbrauchbar.
- Bei der Browserwahl muss jedoch jeder individuell seinen Kompromiss zwischen Sicherheit und Performance finden.

### Anonymität durch Tor ?
- `ACHTUNG`, den [Tor-Browser](https://www.torproject.org/) zu benutzen, bedeutet niemals absolute Anonymität, allerdings gilt der Tor-Browser vergleichsweise als der sicherste Browser.
- Wichtig ist dabei jedoch auch, die Wahl des Betriebssystems, wer dabei den Tor-Browser auf Windows nutzt, widerspricht sich selbst, denn Windows ist nicht gerade als datenschutzfreundlich und ebenfalls nicht als sicher bekannt.
- Der Tor-Browser kann nicht vor "menschlichem Versagen" schützen, daher ist der `Tor-Browser nur ein Werkzeug`, welches "korrekt" durch den Menschen bedient werden muss.

### "Dark Web"
- "Tor-Browser" bedeutet nicht unbedingt sofort "Dark-Web".
- Durch das Tor-Netzwerk kann man auf `.onion`-Seiten zugreifen, jedoch kann man auch Webseiten aus dem Clearnet aufrufen.
- Für den Fall, dass man ".onion-Seiten" aufrufen möchte und sich im Dark-Web ein wenig umschauen möchte, sollte dies keinesfalls vom Handy oder dem alltäglichen System geschehen, sondern ein geeignetes Betriebssystem verwendet werden, z.B. könnte das die Linux-Distribution [Tails](https://tails.net/index.de.html) - [mehr zu Tails in dem Linux-Repository unter /Linux/Linux-Distributionen/Linux-Tails](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/linux/linux-distributionen) sein.


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 8. Fazit - Checkliste Datenschutz-/Sicherheitseinstellungen
- Abschließen kann man festhalten, dass anonym zu surfen ein Konzept ist, man sich jedoch datenschutzorientiert und sicherheitsbewusst für bestimmte Einstellungen oder Dienste entscheiden, bzw. bewusst gegen die Nutzung von bestimmten Einstellungen oder Diensten entscheinden kann.
- Jeder muss den Kompromiss situationsabhängig für sich selber, zwischen Benutzerfreundlichkeit, Sicherheit und Datenschutz finden.
- `Wissen und das Auseinandersetzten mit diesem Thema sind der beste Schutz.`

### Checkliste
- Werden nur vertrauenswürdige [VPN](https://de.wikipedia.org/wiki/Virtual_Private_Network)-Anbieter verwendet ?
- Ist die Nutzung von externen VPN-Diensten angebracht und sinnvoll ?
- Eigenen VPN-Server/vertrauenswürdiger VPN-Server im Einsatz ?
- Nur die nötigsten Browser-Erweiterungen installiert ?
- GGf. Browser-Erweiterungen, die helfen die Sicherheit zu erhöhen installiert ?
- Schutz vor Fingerprinting angewendet ?
- Verwendung eines sicheren/datenschutzorientierten Browsers ?
- Verwendung einer sicheren/datenschutzorientierten Suchmaschine ?
- Browsereinstellungen überprüft ?
- [WebRTC](https://en.wikipedia.org/wiki/WebRTC) ggf. deaktiviert/ Leak-Schutz aktiviert ?
- [DNS](https://de.wikipedia.org/wiki/Domain_Name_System)-Anfragen verschlüsselt (im Browser/Betriebssystem oder im Router) ?
- Evtl. einen eigenen DNS-Server im Heimnetz (inkl. DNS-Verschlüsselung zu den Upstream-Servern)


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# Mehr Inhalte zu dem Thema

- [wiki.ubuntuusers.de/Sicherheit/Anonym_Surfen/](https://wiki.ubuntuusers.de/Sicherheit/Anonym_Surfen/)
	- Ein guter Artikel zur Thematik `sicher surfen` von `wiki.ubuntuusers.de` ist unter [wiki.ubuntuusers.de/Sicherheit/Anonym_Surfen/](https://wiki.ubuntuusers.de/Sicherheit/Anonym_Surfen/) zu finden.
	- Dieser Artikel war u.a. eine Inspiration für einige Teile in diesem Beitrag.

- [EFF](https://www.eff.org/)
	- [coveryourtracks.eff.org/learn](https://coveryourtracks.eff.org/learn)

- PrivacyGuides.org
	- [PrivacyGuides - Privacy Tools](https://www.privacyguides.org/en/tools/)

- PrivacyTests.org
	- [PrivacyTests.org - Desktop ](https://privacytests.org/)
	- [PrivacyTests.org - Android](https://privacytests.org/android)
	- [PrivacyTests.org - iOS](https://privacytests.org/ios)

- [Rob Braxman Tech](https://www.youtube.com/@robbraxmantech)
	- [Does the Brave Browser Really Beat Fingerprinting? Let's Test!](https://www.youtube.com/watch?v=dsu9b5FqK_0)

- [David Bombal](https://www.youtube.com/@davidbombal) - CyberSecurity - YouTuber (en)
	- [Brave blocks Recall, Browsersecurity, VPN...](https://www.youtube.com/watch?v=nlMCymx5z7g)
	- [Is it time to Stop Trusting VPN Companies? Host Your Own (WireGuard getting started guide)](https://www.youtube.com/watch?v=O2mxQSqvsaM)

- [The Morpheus](https://www.youtube.com/@TheMorpheusVlogs) - Tech & Software / CyberSecurity & AI - YouTuber
	- [Browser Chaos 2025](https://www.youtube.com/watch?v=HUYoqM1Gu_s)
	- [Brave-Review](https://www.youtube.com/watch?v=NfQzRYGDEC8)
	- [Opera Browser Warning, SPYWARE ?](https://www.youtube.com/watch?v=bNrAn1LzaWg)
	- [Vergesst Google | Vergleich: SUCHMASCHINEN](https://www.youtube.com/watch?v=CgGWs0zNOQY)

- [Linux Guides](https://www.youtube.com/@LinuxGuides)
	- [Das Groẞe Browser-Ranking | Kann man Firefox noch benutzen?](https://www.youtube.com/watch?v=i3_ShaK6B4Y)

- [c't 3003](https://www.youtube.com/@ct3003)
    - [Du solltest diesen Browser ausprobieren | Vivaldi](https://www.youtube.com/watch?v=zdkr23jcF38)

- [SPACE GAMING](https://www.youtube.com/@SpaceGaming)
    - [Was ist mit diesem “Gaming Browser”!? - OperaGX Review](https://www.youtube.com/watch?v=ugX9WBxO15E)

- [Hit oder Shit](https://www.youtube.com/@HitoderShit)
    - [Hör sofort auf Opera GX zu benutzen! (Hier ist der Grund)](https://www.youtube.com/watch?v=BLjhVe2okfU)


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

