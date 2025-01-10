# Passwort cracking


# 1. Passwort cracking mit [John the Ripper](https://www.kali.org/tools/john/)


John the Ripper ist ein umfangreiches Programm für das Passwortcracking und für das 
Entschlüsseln von Verschlüsselungsalgorythmen.

[Johnny](https://www.kali.org/tools/johnny/) ist dabei die optionale Benutzeroberfläche.

Mit dem Programm lassen sich alle gänigen Dateiformate bruteforcen, dazu zählen u.a. auch zip-Dateien, PDFs oder Passwortdatenbanken.

Die folgenden Anleitungen sind auch für andere Dateiformate übertragbar.

```
$ sudo apt install john
$ john
$ john --help
```

- Die vollständige Liste unterstützter Dateiformate: 
```
$ john --list=formats
$ john --list=subformats
```


----------------------------------------------------------------------------------------------------------------


[wolframalpha.com](https://www.wolframalpha.com/) ist ein sehr umfangreicher online Rechner. 
In diesem Fall ist er nützlich, um herauszufinden, wie lange eine bruteforce Attacke dauern würde, um ein Passwort mit einer bestimmten Länge zu finden.


----------------------------------------------------------------------------------------------------------------


# 2. passwortgeschützte zip-Dateien auf Linux cracken mit [John the Ripper](https://www.kali.org/tools/john/)

```
$ john -h
```

Schritt 1
- Eine Textdatei erstellen und beliebigen Text einfügen.
- Danach mit `Strg+S` speichern.


Schritt 2
- als zip komprimieren:
    - Rechtsklick machen und auf `komprimieren` drücken,
    - `Passwortgesicherte-zip` auswählen und Passwort eingeben.


Schritt 3
- Terminal öffnen:
```
$ zip2john
$ zip2john Datei.zip
```
- Ausgabe ist der *Hash* der Datei.


Schritt 4
- Speichern des *Hashes* in einer `Text` Datei:
```
$ zip2john Datei.zip > hash.txt
```


Schritt 5
- Passwort cracken:
```
$ john --format=zip hash.txt 
```


Beim erfolgreichen "cracken", erscheint das Passwort im Terminal.


----------------------------------------------------------------------------------------------------------------


# 3. Eine passwortgeschützte PDF Datei auf Linux knacken mit [John the Ripper](https://www.kali.org/tools/john/)


Schritt 1
- Eine passwortgeschützte PDF Datei wird vorausgesetzt.
- Wie eine passwortgeschützte PDF erstellt werden kann, wird u.a. auch im Github-Repository [Projekte mit Chat GPT](https://github.com/replay45/projekte-mit-chat-gpt) erklärt.


Schritt 2
Terminal öffnen:
```
$ pdf2john
$ pdf2john Datei.pdf
```
- Ausgabe ist der *Hash* der Datei.


Schritt 3
- Speichern des *Hashes* in einer `Text` Datei:
```
$ pdf2john Datei.pdf > hash.txt
```


Schritt 4
- Passwort cracken:
```
$ john --format=pdf hash.txt
```


Beim erfolgreichen "cracken", erscheint das Passwort im Terminal.


----------------------------------------------------------------------------------------------------------------
