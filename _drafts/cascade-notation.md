---
title: "DART: Cascade Notation und andere Besonderheiten"
author: lukas
categories:
- blog
---

Wer in Dart geschriebenen Code zum ersten Mal sieht, wird feststellen, dass im Vergleich zu anderen Sprachen einige Neuerungen der Sprachsyntax festzustellen sind, die man so noch nicht kennt. In diesem Post werde ich einige dieser Schreibweisen erläutern.

1. Cascade Notation
2. conditional member access ?.
3. ??= assign if not null
4. foo ?? bar -> return bar if foo not null
5. Vgl. normale if Kurzform: expr ? : ;
6. Lambda functions () =>
7. type casting & testing mit is is! as
8. assert
9. -> neuer Post über webdev

### Cascade Notation

Cascade Notations ist eine Schreibweise, die öfters in Dart verwendet wird. Cascade Notations werden mit zwei Punkten eingeleitet (`..`), die vor einem Funktionsaufruf oder einer Zuweisung stehen. Mit ihr können mehrere Operationen an dem gleichen Objekt durchgeführt werden, ohne das Objekt zwischenspeichern zu müssen, oder zumindest den Namen nicht bei jeder Operation ausschreiben zu müssen.

Erstmal ein Beispiel ohne die Cascade Notation.

<amp-gist data-gistid="b3c65d755e01bf79943d1ddc9496148b" data-file="normal.dart" layout="fixed-height" height="300" class="mb4"></amp-gist>

Und hier die Version mit der verkürzten Schreibweise. Zu beachten ist, dass am Ende der Zeilen kein Semikolon (`;`) stehen darf.

<amp-gist data-gistid="b3c65d755e01bf79943d1ddc9496148b" data-file="cascade.dart" layout="fixed-height" height="300" class="mb4"></amp-gist>

In diesem Beispiel wird die Cascade Notation auf ein zwischengespeichertes Objekt angewandt.

<amp-gist data-gistid="b3c65d755e01bf79943d1ddc9496148b" data-file="cascade2.dart" layout="fixed-height" height="300" class="mb4"></amp-gist>

Worauf aber geachtet werden muss ist, dass die Cascade Notation nur auf Objekte verwendet wird. Die Methode `.classes.add(...)` liefert ein bool zurück und nicht das gewünschte Objekt von button.

<amp-gist data-gistid="b3c65d755e01bf79943d1ddc9496148b" data-file="cascade3.dart" layout="fixed-height" height="300" class="mb4"></amp-gist>

Die Cascade Notation wird in der Language Tour erläutert. [dartlang.org > language tour > cascade-notation](https://www.dartlang.org/guides/language/language-tour#cascade-notation-)