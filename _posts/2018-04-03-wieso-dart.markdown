---
title: Wieso Dart
date: 2018-04-03 00:00:00 Z
categories:
- blog
author: adrian
---

Dart als Programmiersprache wird bereits seit 2010 von einem Team in Google entwickelt. In den
vergangen Jahren ist uns Dart immer wieder als Name über den Weg gelaufen aber es war nie die Zeit um sich mit der Sprache richtig zu beschäftigen.
Als Apple vor einigen Jahren Swift als die neue Programmiersprache für sein iOS
 Betriebssystem vorgestellt hat, war meine  Hoffnung, dass
Google Dart als die neue Sprache für Android einführen wird. Noch ist das nicht passiert, jedoch das neue [Flutter UI Framework](https://flutter.io) scheint hier den Weg zu ebnen, so dass schon heute native Apps für Android und sogar für
iOS in Dart geschrieben werden können.

Mit der Dart VM ist es heute möglich Serverseitige Programme zu entwickeln. Wie Faisal Abid in seinem [Vortrag auf dem Dart Developer Summit 2015](https://www.youtube.com/watch?v=NHsmiY0rFS8) zeigt, gibt es hier auf jeden Fall einige Vorteile gegenüber Node.js. 
Als Nutzer von Google Cloud Functions wünschen wir uns, dass bald auch Dart neben
TypeScript und JavaScript ebenfalls auf Cloud Functions laufen wird. Wir werden
im Rahmen von diesem Blog ein paar Beispiele zeigen, wie man dies auch mit Hilfe
von dart2js Compiler schon heute umsetzen kann, jedoch würde eine Dart VM auf Cloud Functions auf jeden Fall Sinn machen.

Und wie sieht es aus mit Dart im Web? Mit der Einführung von Dart 2 wurde der
native Support von Dart in Chrome/Dartium fallen gelassen. JavaScript dominiert
als Browsersprache den Markt, so dass dem Dart Team nichts anderes übrig blieb
als den Dart Code nach JavaScript zu compilieren. Genau das macht [AngularDart](https://webdev.dartlang.org/angular) und bietet damit eine optimale Lösung um seinen Code vom Backend im Web-Client wieder zu verwenden.

Ist Dart jetzt die beste Sprache für alle Anwendungsgebiete? Mobile, Backend und Web? Wir werden uns mit dieser Frage in unserem Blog beschäftigen und mit Beispielen Lösungen zeigen und die Entwicklung weiter verfolgen. 
