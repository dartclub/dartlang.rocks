---
title: 'DART: Cascade Notation und andere Besonderheiten'
date: 2018-04-25 20:20:46.024000000 Z
categories:
- blog
author: lukas
---

Dart liefert einige syntaktische Besonderheiten, die man von anderen Sprachen noch nicht kennt. Vorteile: Sobald man diese Features kennt, lässt sich besser lesbarer und kürzerer Code schreiben!

Eine dieser Alleinstellungsmerkmale von Dart ist die Cascade Notation. Eine Cascade wird mit zwei Punkten (`..`) eingeleitet. Durch sie kann auf ein Objekt mehrfach (in einer Sequenz) zugegriffen werden, ohne dass eine temporäre Variable gespeichert werden muss.

...

So geht kompakt: In Dart können ausufernde if-null-Abragen auf wenige Zeichen komprimiert werden.
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
    `if(foo!=null){ return bar; }`
    wird zu  
    `return foo ?? bar;`
- Der allseits bekannte if-else-shortcut ist auch in Dart möglich:  
    `return (expr) ? foo : bar;`

Aus anderen Sprachen schon als Lambda-Functions bekannt, aber deswegen nicht weniger wichtig: Die Kurzschreibweise für Funktionen.

`square(x) { return x * x; }`

wird zu:

`suare(x) => x * x;`

Komplett neu:  
Type-casting ist nicht wie in C-ähnlichen Sprachen. Hierfür gibt es einen eigens dafür geschaffenen `as` Operator. Man schreibt nicht bspw. `foo = (int) bar;`, sondern: `foo = bar as int;`. 

Die Typenabfrage wird mit den Operatoren `is` und `is!` durchgeführt. Beispiele: `foo is int` oder `bar is! String`.

Diese Features und die Tatsachr,  dass man mit Dart für das Backend, das Web und nativ für Mobil entwickeln kann, machen Dart zu einer Sprache, bei der man sich überlegen sollte, ob man sihch das nicht mal genauer anschaut...