---
title: Firebase Cloud Functions mit Dart
date: 2018-04-04 00:00:00 Z
categories:
- cloudfunctions
author: adrian
---

Ähnlich wie TypeScript unterstützt auch Dart das Compilieren nach JavaScript.
Dies ermöglicht mit einigen Umwegen das Ausführen von Dart Programmen auf Googles Firebase Cloud Functions. Da wir Cloud Functions und andere Firebase-Dienste, wie die Realtime Database häufig in
unseren Projekten verwenden, war es für uns sehr wichtig auch mit Dart Cloud Functions nutzen zu können.

Wenn ihr das Projekt, was wir hier beschreiben schon mal anschauen wollt, so haben wir es 
als [Beispiel bei GitHub](https://github.com/dartclub/dart-cloud-functions) abgelegt.

[Anatoly Pulyaesvkiy](https://github.com/pulyaevskiy) hat Interop Libraries für Node.js und [Cloud Functions](https://github.com/pulyaevskiy/firebase-functions-interop) geschrieben mit denen man die entsprechenden JavaScript Libraries unter Dart nutzen kann. Damit ist es dann mit minimalem Aufwand
möglich seine Dart Programme so in JavaScript zu konvertieren, dass sie mit den Cloud Functions laufen.

Um ein Cloud Functions Projekt zu starten erzeugt man zuerst ein leeres 
Verzeichnis und initialisiert darin ein neues Firebase Projekt:

<amp-gist data-gistid="fe1f34d201a464d4235d8875bb017d1b" data-file="init.sh" layout="fixed-height" height="200" class="mb4"></amp-gist>

Danach existiert in dem Unterordner **functions** eine standard Node.js Package Struktur. Um jetzt darin ein
Dart Projekt einzurichten muss man eine **pubspec.yaml** erstellen. Ein Beispiel findet man [hier](https://github.com/pulyaevskiy/firebase-functions-interop#2-initialize-dart-project).

Mit `pub get` werden jetzt die entsprechenden Abhängigkeiten installiert.

Im nächsten Schritt kann dann das Dart Programm erstellt werden. Hierzu bitte einfach in einem Unterordner mit dem
Namen **node** im functions Verzeichnis die Datei **index.dart** anlegen. Das folgende Beispiel liefert einfach 
eine JSON Datenstruktur zurück.

<amp-gist data-gistid="fe1f34d201a464d4235d8875bb017d1b" data-file="index.dart" layout="fixed-height" height="400" class="mb4"></amp-gist>

Jetzt fehlt noch das Compilieren der Dart Dateien nach JavaScript. Hierzu kann man den dart2js Compiler verwenden.
Im Zusammenhang mit dem neuen [build_runner](https://github.com/dart-lang/build/blob/master/docs/getting_started.md) kann das ganze nun entsprechend konfiguriert werden. Dazu wird eine Config-Datei mit dem Namen **build.yaml** benötigt, die im functions Verzeichnis abgelegt wird:

<amp-gist data-gistid="fe1f34d201a464d4235d8875bb017d1b" data-file="build.yaml" layout="fixed-height" height="400" class="mb4"></amp-gist>

Der build_runner wird nun mit dem folgenden Befehl im functions Verzeichnis ausgeführt:

```bash
pub run build_runner build --output=build
```

Als letzter Schritt fehlt noch das Deployment. Das Start-Skript für Cloud Functions ist immer die index.js, die
jetzt build/node/index.dart.js heisst. Dies muss den function tools mitgeteilt werden, indem man in der package.json
einen entsprechenden Key mit dem Namen **main** einfügt:

```json 
"main" : "build/node/index.dart.js"
```

Damit ist die komplette Konfiguration abgeschlossen und die Funktion kann jetzt deployed werden.
Falls das Projekt mit dem eslint Tool eingerichtet wurde, dann muss es deaktiviert werden, da
der generierte Code sehr lange zum Prüfen braucht und Warnungen und Fehler von eslint generiert. 

Hierzu muss der Eintrag **npm --prefix $RESOURCE_DIR run lint** in der firebase.json 
aus der predeploy Liste entfernt werden.

Jetzt kann das Projekt zu Cloud Functions deployed werden:

```bash
firebase deploy --only functions
```

Nachdem das Deployment erfolgreich abgeschlossen wurde, kann die neue Funktion 
direkt aufgerufen werden. Der Link dazu wird normalerweise nach dem Deployment 
in der Console angezeigt.

### Live Development

Obwohl das Deployment zu Cloud Functions im Moment noch sehr lange 
dauert, kann man den ganzen Prozess doch sehr beschleunigt, wenn man die Cloud Functions lokal ausführt.
Dazu wird das Projekt nicht zu Cloud Functions hochgeladen sondern ein lokaler Server gestartet.
Dies geht mit dem folgenden Befehl:

```bash
firebase serve --only functions
```

Diese Konfiguration erlaubt es, dass bei Änderungen vom JavaScript Code die Cloud Functions sofort
neugestartet werden und man kann den neuen Code sofort ausprobieren kann. 

Der Dart-Code ist davon jedoch nicht betroffen und so müsste man bei jeder Änderung vom Dart-Code
den build_runner ausführen, damit sich die Cloud Functions aktualisieren. Sinnvollerweise
bietet der build_runner eine **watch** Option an, die genau das macht, was wir wollen: bei Änderungen
vom Dart-Code den Build Prozess neu starten und JavaScript Code erstellen.

Hierzu startet man (in einer zweiten Console) den build_runner mit:

```bash
pub run build_runner watch --output=build
```

Jetzt kann man ganz normal an dem Dart-Code arbeiten und sobald eine 
Änderung vom build_runner festgestellt wird, erzeugt er einen neuen JavaScript Code, der
dann von dem lokalen Cloud Functions Server erkannt wird 
und die entsprechend Funktion aktualisiert. Das ganze kann unter Umständen 2-3 Sekunden 
dauern, so dass man nicht zu schnell den HTTP-Request ausführen sollte. 
Jedoch ist das immerhin schneller und einfacher, als die Skripte immer 
wieder von Hand auszuführen.

### Ausblick

Das Setup zeigt schon mal das Potential von Dart auf dem Server. Es bleibt die Hoffnung,
dass Google in der nächsten Zeit Cloud Functions so erweitert, dass Dart 
direkt und ohne Umwandlung nach JavaScript dort ausgeführt werden kann.