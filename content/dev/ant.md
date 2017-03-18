---
tags:
- java
- programming
- compile
created: 1199546488
date: 2008-01-05T16:21:28Z
title: ANT
aliases: /wiki/ANT
project2030: migrated
webarchive: http://web.archive.org/web/20120725134635/http://www.2030.tk/wiki/ANT
---
Notizen zum Thema wie ANT files aufgebaut sind.

<!--more-->

## Aufbau von Ant-Files
Das Ant File heisst immer: `build.xml`

Hällt man sich daran braucht man kein AntFile anzugeben.

Tag | Beschreibung
---- | ----
project | Ant Files beginnen immer mit dem `<project>` Tag. Dieser geht über das ganze File und hat den Parameter default. Wird nichts anderes angegeben führt er das Target mit dem im default Parameter angegebenen Namen aus.
target | Der Target Tag ist im Projet enthalten. Er hat den Parameter name. Dieser Wert ist frei wählbar.
echo | Gibt die Message im Parameter message aus.


{{< highlight xml "style=emacs" >}}
<project default="nina">
  <target name="franziska">
   <echo message="Hello Franziska"/>
  </target>
  <target name="nina">
   <echo message="Hallo Nina"/>
  </target>
</project>
{{< /highlight >}}

## Abhängikeit
Ist ein Taget vom andern abhängig, so kann das in der Folgenden weise bekundet werden:
{{< highlight xml "style=emacs" >}}<target name="ich" depends="du,ihr">{{< /highlight >}}
Dann werden beim aufruf von "ich" immer erst "du" und "ihr" aufgerufen.

## Variabeln
Variabeln können mit dem Folgenden Befehl definiert werden:
{{< highlight xml "style=emacs" >}}<property name="location" location="/home/noah" />{{< /highlight >}}
Eingesetzt werden können die Variabeln mit:
{{< highlight xml "style=emacs" >}}${obj-dir}{{< /highlight >}}

## Java Compilieren
Zum übersetzen von java kann in einem `<target>` einfach der `<javac>` Tag verwendet werden. Wird der Parameter "srcdir" angegeben, so werden alle .java Files in diesem Verzeichnis übersetzt.
{{< highlight xml "style=emacs" >}}<javac srcdir="." />{{< /highlight >}}

## Jar File erstellen
Um ein Jar File zu erstellen kann innerhalb eines Targets der `<jar>` Tag verwendet werden. Ein jar kann sich selber natürlich nicht enthalten. Im Beispiel werden alle .class Files in allen Unterordnern von basedir zum jar hallo.jar hinzugefügt.
Welches die Mainclass ist kann nicht direkt angegeben werden.
{{< highlight xml "style=emacs" >}}<jar destfile="hello.jar" basedir="." includes="**/*.class" />{{< /highlight >}}

## Ausführen von Java Code
{{< highlight xml "style=emacs" >}}<java classname="hello" classpath="hello.jar" fork="true" />{{< /highlight >}}
Damit wird ein neuer Prozess erstellt der die Klasse "hello" aus im Jar hello.jar ausführt.

## Erstellen von Ordnern
{{< highlight xml "style=emacs" >}}<mkdir dir="/home/noah/myproject" />{{< /highlight >}}

## Löschen von Ordnern und Dateien
{{< highlight xml "style=emacs" >}}
<delete dir="/home/noah/myproject" />
<delete file="/tmp/huj" />
<delete>
<fileset dir="/home/noah/myproject" includes="**/*.class" />
</delete>
{{< /highlight >}}

## JUnit Tests
Unitests können auch ausgeführt werden. Oft gibt es Probleme weil junit.jar nicht im Class-Path ist.
{{< highlight xml "style=emacs" >}}
<junit>
  <test name="ExampleTest" />
</junit>
{{< /highlight >}}

## Classpath definieren
Direkt im `<project>` Tag:
{{< highlight xml "style=emacs" >}}
  <path id="classpath.base">
  </path>
  <path id="classpath.test">
    <pathelement location="/usr/lib/java/junit.jar" />
    <pathelement location="." />
    <path refid="classpath.base" />
  </path>
{{< /highlight >}}

Später kann mit
{{< highlight xml "style=emacs" >}}<classpath refid="classpath.test" />{{< /highlight >}}
darauf zugegriffen werden. Z.B. innerhalbe eines JUnit-Tags.
