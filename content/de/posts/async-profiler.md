+++
title = 'Java Async Profiler'
date = 2024-06-01T21:49:27+01:00
draft = true
+++

# Java Async Profiler

## Profiling - jagen wir jetzt Verbrecher?

- was ist Profiling?
- wieso wird das Profiling angewandt?
- welche Profiler gibt es?

Fängt ein Mensch mit der Entwicklung von Software an, werden in der Regel in den ersten Projekten
kleine Tools geschrieben,
wie das klassische "Hello-World"-Program oder einfaches Einlesen von Nutzer-Eingaben über die
Konsole.
Das Ziel dieser Anwendungen ist klar: Die Funktionsweise und Semantik einer Programmiersprache soll
kennengelernt werden.
In den seltensten Fällen werden sich hierbei Gedanken, wie "Wie genau wird der Code von der CPU
verarbeitet?" oder
"Wie viel Speicher wird meine Anwendung verbrauchen?", gemacht. Java lebt, wie viele andere
Programmiersprachen auch,
von unzählig vielen Frameworks und Modulen, welche mit mehr oder weniger viel Aufwand in das eigene
Projekt integriert werden können
und dabei viele nützliche Dinge abnehmen. Und langsam aber sicher wird aus einem kleinem,
überschaubaren Projekt ein großer Berg von Code mit
komplexen Prozessen. Und ehe mensch sich versieht, wird die eigene noch eben so kleine Anwendung
langsamer und
ein Blick in den Speicherverbrauch verrät "Oh, der Speicher ist voll". Und jetzt? Wie finden wir
"den Verbrecher"?

### Was ist Profiling?

Um diese Frage zu beantworten, bediene ich mich gerne zuerst an einer allgemeinen Definition aus dem
*Duden*[[1]]({{< ref "#duden" >}}).
Hiernach wird unter Profiling eine

> für bestimmte Zwecke (z. B. zur Arbeitsvermittlung oder bei der Tätersuche) nutzbare Erstellung
> des Gesamtbildes einer Persönlichkeit

verstanden. Auch wenn bei dem oben beschriebenen Problem nicht zwingend eine menschliche
Persönlichkeit gesucht wird, kann das "Erstellen eines Gesamtbildes" der Anwendung gewinnbringende
Informationen über das Verhalten ("die Persönlichkeit") eines Stückes Software bringen. Fragen,
wie "Wie verhält
sich die Anwendung bei dieser oder jener Eingabe?", lassen sich durchaus vergleichen mit "Wie
verhält
sich eine Person in dieser oder jener Situation?".

### Wieso wird Profiling in der Software-Entwicklung angewandt?

In der Welt der Software-Entwicklung wird der Prozess des Profilings als das Sammeln und Auswerten
von verschiedenen Metriken
einer laufenden Anwendung verstanden. In der Regel geben diese Werte Einblicke unter die Motorhaube
einer Applikation,
welche bei dem normalen Betrachten einer Anwendung nicht sofort ersichtlich sind. Gerade wenn es um
Funktionen geht, welche von der zugrunde liegende Runtime oder Framework ausgeführt werden und somit
weiter von der Anwendungs-Entwicklung entfernt sind, können somit zum Vorschein gebracht werden.
In den meisten Fällen interessieren Messungen im Kontext von Ressourcennutzungen:

- Welche Methode benötigt wie viel CPU Zeit zum Durchlaufen?
- Wie lange ist die Durchlaufzeit einer Funktion?
- Welche Methode belegt besonders viel Speicher?

### Welche Profiler gibt es?

Um eine laufende Java Anwendung zu "profilen" wird an diese ein sogenannter *Java Agent*[[2]]({{<
ref "#agent" >}})
"eingehängt". Dies kann sowohl beim Starten einer Applikation geschehen

```shell
java -javaagent:agent.jar -jar application.jar
```

als auch während ein Program schon läuft. Die Logik des Profilers steckt in dem `agent.jar` Archiv.
Dieser wird mittels des *Instrumentation*[[3]]({{< ref "#instrumation" >}}) Interfaces von der
laufenden JVM eingehängt.

## Save-Point vs Async Profiling

- was ist ein Java Savepoint?

## Grundlegende Nutzung des Async Profilers

- was kann gemessen wird?
- welche Ergebnisse gibt es?

## Referenzen

- <span id="duden">[1][https://www.duden.de/rechtschreibung/Profiling](https://www.duden.de/rechtschreibung/Profiling)
- <span id="agent">[2][https://medium.com/nerd-for-tech/what-is-a-java-agent-and-what-is-it-for-7a7896729c76](https://medium.com/nerd-for-tech/what-is-a-java-agent-and-what-is-it-for-7a7896729c76)
- <span id="instrumation">[3][https://docs.oracle.com/en/java/javase/21/docs/api/java.instrument/java/lang/instrument/Instrumentation.html](https://docs.oracle.com/en/java/javase/21/docs/api/java.instrument/java/lang/instrument/Instrumentation.html)

