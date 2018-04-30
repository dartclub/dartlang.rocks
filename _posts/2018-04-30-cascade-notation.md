---
title: 'DART: Cascade Notation und andere Besonderheiten'
date: 2018-04-30 12:20:46.024000000 Z
categories:
- blog
author: lukas
---

Dart liefert einige syntaktische Besonderheiten, die man von anderen Sprachen noch nicht kennt. Vorteile: Sobald man diese Features kennt, lässt sich besser lesbarer und kürzerer Code schreiben!

Eine dieser Alleinstellungsmerkmale von Dart ist die Cascade Notation. Eine Cascade wird mit zwei Punkten (`..`) eingeleitet. Durch sie kann auf ein Objekt mehrfach (in einer Sequenz) zugegriffen werden, ohne dass eine temporäre Variable gespeichert werden muss.

Erstmal ein Beispiel ohne die Cascade Notation.

<amp-gist data-gistid="b3c65d755e01bf79943d1ddc9496148b" data-file="normal.dart" layout="fixed-height" height="300" class="mb4"></amp-gist>

Und hier die Version mit der verkürzten Schreibweise. Zu beachten ist, dass am Ende der Zeilen kein Semikolon (`;`) stehen darf.

<amp-gist data-gistid="b3c65d755e01bf79943d1ddc9496148b" data-file="cascade.dart" layout="fixed-height" height="300" class="mb4"></amp-gist>

In diesem Beispiel wird die Cascade Notation auf ein zwischengespeichertes Objekt angewandt.

<amp-gist data-gistid="b3c65d755e01bf79943d1ddc9496148b" data-file="cascade2.dart" layout="fixed-height" height="300" class="mb4"></amp-gist>

Worauf aber geachtet werden muss ist, dass die Cascade Notation nur auf Objekte verwendet wird. Die Methode `.classes.add(...)` liefert ein bool zurück und nicht das gewünschte Objekt von button. Der folgende Code ist deshalb fehlerhaft.

<amp-gist data-gistid="b3c65d755e01bf79943d1ddc9496148b" data-file="cascade3.dart" layout="fixed-height" height="300" class="mb4"></amp-gist>

**So geht kompakt:**  
In Dart können ausufernde if-null-Abragen auf wenige Zeichen komprimiert werden.
- conditional member access:  
    anstatt  
    `if(element.foo != null){ element.foo(); }`  
    einfach  
    `element?.foo();`  
- Zuweisungen mit Abfrage:  
    `if(bar != null){ foo = bar; }`  
    wird zu  
    `foo ??= bar;`  
- und noch diese Schreibweise:  
    `if(foo != null){ return bar; }`
    wird zu  
    `return foo ?? bar;`
- Der allseits bekannte if-else-shortcut ist auch in Dart möglich:  
    `return (expr) ? foo : bar;`

Aus anderen Sprachen schon als Lambda-Functions bekannt, aber deswegen nicht weniger wichtig: Die Kurzschreibweise für Funktionen.

`square(x) { return x * x; }`

wird zu:

`suare(x) => x * x;`


**Komplett neu:**  
Type-casting ist nicht wie in C-ähnlichen Sprachen. Hierfür gibt es einen eigens dafür geschaffenen `as` Operator. Man schreibt nicht bspw. `foo = (int) bar;`, sondern: `foo = bar as int;`. 

Die Typenabfrage wird mit den Operatoren `is` und `is!` durchgeführt. Beispiele: `foo is int` oder `bar is! String`.

All diese Features von Dart werden auch hier erklärt: [dartlang.org > language tour](https://www.dartlang.org/guides/language/language-tour). Wer einen schnellen Einstieg in Dart braucht, ist dort richtig.

Mit seiner klaren, einfachen Syntax und vielen dieser Tricks ist Dart eine sehr kraftvolle, neue Technologie, mit der man sehr schnell für Browser, Mobil und das Backend entwickeln kann.