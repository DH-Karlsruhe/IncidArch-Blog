# Software Architecture Document

## Inhaltsverzeichnis
- [Software Architecture Document](#software-architecture-document)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [1. Einführung](#1-einführung)
    - [1.1 Zweck](#11-zweck)
    - [1.2 Akronyme](#12-akronyme)
    - [1.3 Referenzen](#13-referenzen)
  - [2 Architektonische Darstellung](#2-architektonische-darstellung)
  - [3 Architektonische Ziele und Einschränkungen](#3-architektonische-ziele-und-einschränkungen)
    - [Sicherheit gemäß DSGVO](#sicherheit-gemäß-dsgvo)
    - [Wiederverwendbarkeit](#wiederverwendbarkeit)
  - [5 Logische Ansicht](#5-logische-ansicht)
  - [6 Prozess-Ansicht](#6-prozess-ansicht)
    - [6.1 Registrierung \& Initialisierung](#61-registrierung--initialisierung)
    - [6.2 Vorfall-Handling](#62-vorfall-handling)
    - [6.3 Intra-Organisationelle Administration](#63-intra-organisationelle-administration)
  - [7 Bereitstellungs-Ansicht](#7-bereitstellungs-ansicht)
    - [7.1 Frontend](#71-frontend)
    - [7.2 Backend](#72-backend)
  - [8 Implementierungs-Ansicht](#8-implementierungs-ansicht)
  - [9 Daten-Ansicht](#9-daten-ansicht)
  - [11 Qualität und Performance](#11-qualität-und-performance)
    - [Performance\*](#performance)
    - [Qualität](#qualität)

## 1. Einführung

### 1.1 Zweck
Das Software Architecture Document (SAD) dient der Beschreibung der Software-Architektur(-Anforderungen).  
Es schlüsselt stellenweise die Entscheidungsgrundlagen für getroffene Entscheidungen auf 
und gibt Einsichten in Bezug auf die Logik, Prozesse, Bereitstellung, Implementierung, Daten, Qualität und Performance.

### 1.2 Akronyme  

| Akronym | Beschreibung | 
|---------|--------------|
| RLS     | Row-Level-Security | 

### 1.3 Referenzen

| Beschreibung | Link |
|--------------|------|
| Supabase CLI für Backend-Entwicklung & Bereitstellung | https://supabase.com/docs/guides/cli/getting-started |

## 2 Architektonische Darstellung 

## 3 Architektonische Ziele und Einschränkungen

Unser Hauptziel ist es ein Vorfalls-Archiv auf Enterprise-Niveau bereitzustellen.
Dabei sind folgende Aspekte von Relevanz..

### Sicherheit gemäß DSGVO

Es soll und darf nicht möglich sein im Kontext einer Organisation auf etwaige Inhalte einer anderen Organisation zuzugreifen. Daher..

- werden getestete RLS-Policies eingesetzt, um den Zugang zeilenweise permissiv unter bestimmten Bedingungen freizugeben und ermöglichen zudem den Wegfall eines dedizierten Controllers. 
  - _Etwaige Fehlkonfigurationen fallen, sofern sie das während dem Testen tun, in dem Supabase-Security-Advisor auf._
- werden Berechtigungen zentral von dem Organisations-Eigentümer vergeben und alle Benutzer können in erster Linie nur eigens erstellte Vorfälle erweitern (nicht manipulieren/löschen!).
- kann das Backend in Einzelfällen mithilfe einer Schema-Migration gezielt für einzelne Organisationen bereitgestellt werden, um beispielsweise Air-Gapped-Systeme zu ermöglichen.

### Wiederverwendbarkeit

Im Sinne der Wiederverwendbarkeit wird in allen Instanzen das Atomic-Schema,
beziehungsweise ein funktionaler Ansatz verfolgt, sodass verschiedene Komponenten
an verschiedenen Stellen mit sicherem Gewissen wiederverwendet werden können.  

## 5 Logische Ansicht

Aus logischer Sicht findet in jedem Fall am Frontend eine Vor-Validierung statt,  
die anschließend vom Backend legitimiert wird, bevor tatsächliche Änderungen vorgenommen, darauf basierende Aktionen ausgeführt werden.  
Ziel ist es zumindest für die Vorfälle als Kern eine git-ähnliche Historie aufbauen,  
wobei lediglich das Anhängen von Änderungen möglich sein soll, um dem Verfälschen von Berichten vorzubeugen.  

## 6 Prozess-Ansicht

Wir setzen auf transaktionselle Abläufe, 
die von unserem Backend verarbeitet werden.  
Diese richten sich nach den Use-Cases und sind im SRS entsprechend in der Ablaufbeschreibung dokumentiert.
Ein großer Vorteil der zustandslosen Verarbeitung ist die einfache Skalierung.

### 6.1 Registrierung & Initialisierung

Neue Benutzende können sich über das Frontend registrieren,
wobei in demselben Formular ein optionales Feld für einen Organisations-Namen vorgehalten wird.
Nachdem der Benutzer die Bestätigungsmail bestätigt hat,
wird im Hintergrund eine Edge-Funktion ausgelöst, 
welche die Organisations-Initialisierung anstößt
und mit den Parametern der Registrierung eine neue Organisation anlegt.

### 6.2 Vorfall-Handling

Ein neuer Vorfall kann mit der Organisations-Eigentümer-/ oder Verwalter-Berechtigung angelegt werden.  

Bestehende Vorfälle können von dem Eigentümer und dem Autor des Vorfalls bearbeitet werden,
was das Hinzufügen von Betroffenen, Ersthelfenden, Zeugen und deren Berichten ermöglicht.  

Bestehende und archivierte Vorfälle können lediglich von dem Eigentümer der Organisation gelöscht werden.

### 6.3 Intra-Organisationelle Administration

Die Administration innerhalb einer Organisation ermöglicht die Anlage für etwaige Personen,
die im Kontext der Organisation die aktive Rolle einer verwaltenden Person einnehmen können, 
sofern sie als authentifizierte Benutzer angelegt werden.

Alternativ können Personen innerhalb der Organisation in passive Rollen als von Vorfällen Betroffene, Ersthelfende oder Zeugen zugeordnet werden. Es ist des weiteren möglich beliebige Personen anzulegen,
selbst wenn diese keine der genannten Rollen erfüllen, da in der Zukunft ein potential auf solch eine Rolle besteht. 
_In der Praxis kann so beispielsweise eine Synchronisation zu einem Active-Directory eingerichtet werden, um die Angehörigen einer Organisation aktuell zu halten._


## 7 Bereitstellungs-Ansicht

Die Bereitstellung muss in zwei Sparten unterteilt werden.  
Jene für das Frontend und für das Backend.

### 7.1 Frontend

Das Deployment der Apps erfolgt im Fall über die beiden marktführenden App-Stores,
den Google Play-Store und den Apple App-Store. Mit etwaigen Entwickler-Lizenz-Kosten muss gerechnet werden.  
Die Web-App werden wir über ein CDN statisch bereitstellen,  
was sich aufgrund der losen Kopplung zum Backend anbietet.  
Ein klassischer Anbieter ist hier Cloudflare mit Cloudflare-Pages  
und deren CDN, mit Edge-Nodes in allen großen Rechenzentren.  

Die eigentliche Bereitstellung (Deployment) wird,  
über Github Actions oder einen vergleichbaren Automatisierungs-Services konfiguriert.  
Nicht zuletzt wegen bereits existierenden Workflow-Vorlagen.  

### 7.2 Backend

Das Backend kann und wird zentral über das supabase Dashboard gewartet,
zumal das Bereitstellen von Edge-Funktionen und die Migration von Datenbank-Schemata
über die Supabase CLI von statten gehen, an der sich ausschließlich berechtigte Plattform-Administratoren authentifizieren können.  

Etwaige Änderungen an dem Backend werden in dem IncidArch Monorepo festgehalten.


## 8 Implementierungs-Ansicht

## 9 Daten-Ansicht

Das tatsächliche Datenbankschema mit vollständiger RLS-Policy-Absicherung:

![IncidArch-DB-Scheme](./IncidArchScheme.png)

## 11 Qualität und Performance

### Performance*

Um die Performance von Anfang an hoch zu halten orientieren wir uns an den Best-Practices der jeweiligen Ökosysteme.  

Die Größe der Apps spielt eine große Rolle kann bei React Native eine Hürde darstellen.  
Mit dem in Expo vorkonfigurierten Webpack-Bundler ist jedoch eine ausreichende Komprimierung möglich,  
sodass das Frontend auch als relativ leichtgewichtige WebApp bereitgestellt werden kann.  

Der Zeitaspekt spielt zumindest während dem Onboarding neuer Benutzenden eine große Rolle.
App-Seiten sollten möglichst instantan an Benutzereingaben geladen werden,
weshalb in Einzelfällen bei spürbaren Wartezeiten mit einem vorgelagerten Cache/Storage zu arbeiten ist (wie es bei Vorfällen direkt nach der Authentisierung der Fall ist).

Im Backend ist die Größe von Edge-Funktionen zunächst trivial. 
Es sollte jedoch nur ein konkreter Kontext im Kontext einer Funktion abgehandelt werden,  
wodurch die Größe implizit limitiert sein sollte.
Etwaig lange Ladezeiten (bspw. bei Kaltstarts) sind in Einzelfällen zu untersuchen.

Bezüglich der Zeit können wir im Backend lediglich auf die Edge-Funktionen einfluss nehmen,  
indem wir diese möglichst einfach halten.

### Qualität

Im Sinne einer besseren Qualität setzen wir auf einfache Ausgangsbedingungen.  
Wir verwenden nur TypeScript mit den minimal nötigen Bibliotheken.
Die Wahl von TypeScript als einzige Entwicklungssprache haben wir ebenfalls im Sinne der Einfachheit getroffen,    
aufgesattelt auf die V8-JavaScript-Engine im Frontend, wie Backend,  
war naheliegend, da wir so eine typsichere und dennoch möglichst agile Entwicklung erzielen,
da immer in demselben Sprachkontext gearbeitet werden kann.
