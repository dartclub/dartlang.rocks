---
title: Moment JS in Dart? Arbeiten mit Zeit
date: 2018-04-25 20:20:46.024000000 Z
categories:
- blog
author: lukas
---

Moment.js ist *die* Bibliothek für alles, was man mit Zeiträumen und Daten in Javascript anstellen möchte.

Wie sieht es in Dart aus?

In Dart braucht man gar keine extra Library. Die Standard-Klassen DateTime, Duration und DateFormat decken das meiste ab.

Ein Vergleich zwischen moment.js und dem Dart-Äquivalent:

- date parsing: https://api.dartlang.org/stable/1.24.3/dart-core/DateTime/parse.html https://momentjs.com/docs/#/parsing/
- DateFormat: https://www.dartdocs.org/documentation/intl/latest/intl/DateFormat-class.html
- add / subtract https://api.dartlang.org/stable/1.24.3/dart-core/DateTime/subtract.html
- Zeiträume mit Duration https://api.dartlang.org/stable/1.24.3/dart-core/Duration-class.html
- Relative Time: "Wie lange her"... Bsp: Duration = (Now - Then)
- Date comparison: isBefore, isAfter
- einzelne Attribute von DateTime Klasse (wie hours, month, usw.)
- Zeitzonen
- quiver https://www.dartdocs.org/documentation/quiver/latest/quiver.time/quiver.time-library.html
