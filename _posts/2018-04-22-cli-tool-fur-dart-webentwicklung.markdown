---
title: CLI Tool für Dart Webentwicklung
date: 2018-04-22 15:22:00 Z
author: lukas
---

Für alle Dart-Entwickler, die für das Web entwickeln, gibt es ein neues Kommandozeilen-Tool: webdev.

Das kann webdev:  
- Es vereinfacht das kompilieren und deployen von Dart-Webanwendungen
- `webdev build` Baut aus dem Quellcode eine für das Deployment fertige Package
- `webdev serve` Startet einen lokalen Server zur Entwicklung mit eingebautem File-Watcher

Beachtet werden muss, dass eine `pubspec.yaml`-Datei vorhanden ist.

**Wo kriegt man webdev her?**  
einfach über den Paket-Manager installieren:  
`pub global activate webdev`

Github:
[dart-lang/webdev](https://github.com/dart-lang/webdev)