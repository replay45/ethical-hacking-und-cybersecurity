# sicher im Internet surfen


## Inhaltsverzeichnis

### 1. anonym & sicher im Internet surfen
- anonym & sicher im Internet surfen
- Fazit zu - anonym & sicher surfen
- Was kann man also tun, um die Sicherheit beim browsen zu erhöhen ?
- Fingerprinting testen & verhindern
- Tor Browser - die Lösung ?
- Mehr zu dem Thema

### 2. Mehr Sicherheit im Heimnetzwerk
- [PI-Hole](https://pi-hole.net/)
    - Was ist ein DNS-Server ?
    - Wieso sollte man PI-Hole nutzen ?
    - Auf welcher Hardware PI-Hole aufsetzen ?

### 3. BrowserAudit (Browser-Sicherheitstest)
- [BrowserAudit](https://browseraudit.com/)

----------------------------------------------------------------------------------------------------------------


# 1.1. anonym & sicher im Internet surfen

Um anonym surfen zu können, reicht es leider nicht mehr, nur die IP Adresse z.B. über einen VPN zu verschleiern.
Auch wenn die meisten Browser heute viele Cookies blockieren können, können häufig Webseiten über das sogenannte `Fingerprinting` Nutzer bzw. Browser wiedererkennen, egal welche IP Adresse diese haben.
mehr dazu weiter unten.


Auch Browser-Erweiterungen wie Werbe-Adblocker können zum Schutz beitragen, sind jedoch genauso wie ein VPN niemals eine Garantie für Anonymität.
Es empfielt sich, **nur** die **nötigsten** Erweiterungen installiert zu haben.
Ein beliebter Open-Source Adblocker ist z.B. der [uBlock Origin](https://ublockorigin.com/de).


Allerdings kann man z.B. die `Sicherheitseinstellungen` im Browser auf `sicher` oder `am sichersten` stellen und AdBlocker, wie der [uBlock Origin](https://ublockorigin.com/de), können zum Schutz beitragen, indem sie Tracker blockieren.


Auch ein VPN kann in individuellen Fällen zum Schutz beitragen. Wichtig ist jedoch, dass man sich niemals auf einen VPN-Anbieter verlässt, denn in einigen Fällen loggen diese die Aktivitäten mit. Insbesondere bei kostenlosen Konten besteht die Gefahr, dass Einnahmen durch das Sammeln und Verarbeiten von Daten erziehlt werden.


## 1.2 Fazit zu - anonym & sicher surfen

Wichtig zu merken ist, dass `anonym zu surfen ein Konzept ist` und nicht durch ein Programm gewährleistet werden kann.
Es ist daher immer notwendig, sich ausführlich zu informieren.


## 1.3 Was kann man also tun, um die Sicherheit beim browsen zu erhöhen ?

Zunächst empfiehlt es sich, häufiger den privaten Modus des Browsers zu nutzen und zu überlegen, ob man nicht lieber auf einen empfehlenswerteren Browser, wie den [Firefox](https://www.mozilla.org/de/firefox/new/) oder [Brave-Browser](https://brave.com/de/) für den Alltag umsteigen möchte.
Außerdem empfiehlt sich der AdBlocker [uBlock Origin](https://ublockorigin.com/de), um Tracking und Werbung zu meiden.

Wer noch eine Stufe drauflegen möchte, kann die Erweiterung [NoScript](https://noscript.net/) verwenden, um das Ausführen von Skripten zu verhindern, was die Sicherheit stark erhöht.
Aber achtung, denn einige Webseiten werden somit nicht mehr verfügbar sein, oder nur noch zum Teil funktionieren.
Jedoch kann die Verwendung von [NoScript](https://noscript.net/) in individuellen Fällen durchaus sinnvoll sein. Die Erweiterung empfiehlt sich jedoch eher nicht für den alltäglichen Gebrauch, sie ist aber auch nicht ohne Grund im Tor Browser bereits integriert.

Außerdem kann man die Sprache im Browser auf "Englisch" stellen, um schwerer identifizierbar zu sein.
Bereits das Umsetzen einiger dieser Punkte kann dazu beitragen, mehr in der Masse unterzugehen und weniger leicht identifizierbar zu sein.


Wie bereits angesprochen ist auch "Fingerprinting" ein wichtiges Thema, dem Beachtung geschenkt werden sollte. Dafür den nächsten Punkt (1.4) lesen !


## 1.4 Fingerprinting testen & verhindern

- Ob der eigene Browser `Fingerprinting verhintert`, kann hier überprüft werden.
- Fingerprint-Test: [coveryourtracks.eff.org](https://coveryourtracks.eff.org/)

- Ein Browser, der Fingerprinting verhindert bzw. blockiert, ist z.B. der [Brave-Browser](https://brave.com/de/).


## 1.5 Tor Browser - die Lösung ?

Nein, nicht für den Alltag !
Das Tor Netzwerk ist leider recht langsam und durch einige Sicherheitseinstellungen und das Blockieren von JavaSkript, machen den Tor Browser für den Alltag eher unbrauchbar.
Bei der Browserwahl muss daher jeder individuell seinen Kompromiss zwischen Sicherheit und Performance finden.


`ACHTUNG`, den [Tor-Browser](https://www.torproject.org/) zu benutzen, bedeutet niemals absolute Anonymität, allerdings gilt der Tor-Browser vergleichsweise als der sicherste.
Wichtig ist dabei jedoch auch, die Wahl des Betriebsystems, wer dabei den Tor-Browser auf Windows nutzt, widerspricht sich selbst, denn Windows ist nicht gerade als besonders datenschutzfreundlich bekannt.
Wer keinen weiteren PC zur Verfügung hat, um Linux nutzen zu können, kann sich z.B. mit einer virtuellen-Maschine Abhilfe schaffen.


Beachte, dass "Tor-Browser" **NICHT** gleich "Dark-Web" bedeutet.
Wer trotzdem ein paar Ausflüge auf ".onion" / "Dark-Web-Seiten" machen möchte, sollte dies nicht von dem Handy oder alltäglichen System machen, sondern sich mal die Linux-Distribution [Tails](https://tails.net/index.de.html) - [mehr zu Tails in dem Linux-Repository](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/linux) anschauen.


## 1.6 Mehr zu dem Thema:

Mehr zu Sicherheit auf dem Betriebssystem und Sicherheit & Firewall auf Linux ist in dem Repository [Linux, RaspberryPI & Nextcloud](https://github.com/replay45/Linux-RaspberryPI-NextCloud/tree/main/linux) zu finden.


- Ein guter Artikel zur Thematik `sicher surfen` von `wiki.ubuntuusers.de` ist hier zu finden.
- Dieser Artikel war u.a. eine Inspiration für diese kurze Zusammenfassung (Punkt 1): [wiki.ubuntuusers.de](https://wiki.ubuntuusers.de/Sicherheit/Anonym_Surfen/)


----------------------------------------------------------------------------------------------------------------


# 2. Mehr Sicherheit im Heimnetzwerk


- [PI-Hole](https://pi-hole.net/)

Wer mehr Sicherheit in seinem Heimnetzwerk haben möchte, kann [PI-Hole](https://pi-hole.net/), als [DNS-Server](https://de.wikipedia.org/wiki/Domain_Name_System) für einzelne oder alle Geräte im Netzerk nutzen.
Dabei werden alle DNS-Anfragen von dem PI-Hole aufgelöst und dieser kann `Tracking oder auch Werbung herausfiltern`.

- Was ist ein DNS-Server ?
Ein DNS-Server übersetzt also Domains wie "example.org" in die dazugehörige IP-Adresse.
Da der Mensch sich Domains eifacher als IP-Adressen merken kann und die IP-Adresse eines Servers sich auch ändern kann, nutzt man für die "Übersetzung" von Domains in IP-Adressen einen DNS-Server.

- Wieso sollte man PI-Hole nutzen ?
Neben der Blockierung von Werbung und Tracking, hat PI-Hole als DNS-Server den positiven Effekt, dass die Ladezeiten von Webseiten geringer sind. 
Dies liegt daran, dass weniger Daten heruntergeladen und weniger Anfragen an externe Server gestellt werden müssen.

Zudem profitiert man auch von dem Cache-Speicher des PI-Holes, da häufig besuchte Seiten zwischengespeichert werden und nicht jedes Mal angefragt werden müssen.

PI-Hole kann nach den `eigenen Bedürfnissen angepasst und genutzt` werden. Man kann z.B. PI-Hole nur bei einzelnen Geräten nutzen, indem man die IP-Adresse vom DNS-Server (in diesem Fall PI-Hole) als primären DNS-Server einstellt oder auch für alle Geräte im Netzwerk nutzen. Dafür muss man lediglich in dem Router, bei den meisten wird das eine FritzBox sein, die IP-Adresse vom PC, auf dem PI-Hole installiert ist, als primären DNS-Server setzen.

- Auf welcher Hardware PI-Hole aufsetzen ?
Es ist `nicht zwingend notwendig` einen [RaspberryPI](www.raspberrypi.com) zu besitzen, um PI-Hole nutzen zu können, da die Installation auch auf einem Handelsüblichen PC mit Linux möglich, dennoch bietet der RaspberryPI einige Vorteile, u.a. wie der vergleichsweise geringe Stromverbrauch.

Außerdem startet der RaspberryPI automatisch, sobald er an den Strom angeschlossen wird, was ein weiterer Vorteil des PIs in Bezug auf Ausfallsicherheit ist, denn nach einem Stromausfall bootet der RaspberryPI von alleine wieder.

Es empfiehlt sich außerdem, Router, DNS-Server und auch andere Server wie ein NAS etc. an eine Mehrfachsteckdose mit Überspannungs- & Blitzschutz anzuschließen, da so alle Geräte von der Mehrfachsteckdose geschützt werden.
Man kann zusätzlich auch noch eine Kontinuitätsgruppe verwenden, die im Falle eines Stromausfalls dafür sorgt, dass die angeschlossenen Server und Geräte sich ordnungsgemäß herunterfahren oder Spannungsschwankungen abgefangen werden können.

Somit müssten im Falle eines Defekts nur die Mehrfachsteckdose und ggf. die Kontinuitätsgruppe ausgetauscht werden, was erheblich günstiger sein kann.


Wissenswertes zum `RaspberryPI` und mehr zum `PI-Hole` ist in dem Repository [Linux, RaspberryPI & Nextcloud](https://github.com/replay45/Linux_Ethical-Hacking_RaspberryPI) zu finden.


----------------------------------------------------------------------------------------------------------------


# 3. BrowserAudit (Browser-Sicherheitstest)

BrowserAudit ist ein webbasierter Dienst zum Testen verschiedener Sicherheitsrichtlinien der Webbrowser. 
Der BrowserAudit-Test enthält aktuell über 400 Tests.


Um den Test auszuführen, muss lediglich die offizielle Webseite besucht werden und auf `Test me` geklickt werden.
Der Test kann einige Minuten in Anspruch nehmen.


> [BrowserAudit](https://browseraudit.com/)


----------------------------------------------------------------------------------------------------------------
