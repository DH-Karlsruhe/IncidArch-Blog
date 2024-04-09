# 4. Semester Start _(KW15/24)_

In der Welt der Softwareentwicklung ist eines gewiss: Fehler gehören dazu. 
Doch was zählt, ist nicht nur das Eingeständnis dieser Fehler, sondern vor 
allem das Lernen aus ihnen und die Integration dieser Erfahrungen in zukünftige Projekte.

Zum Beginn des vierten Semesters haben wir diese Lektion auf eine etwas harte Tour gelernt.
Ursprünglich hatten wir uns vorgenommen, eine umfangreiche Liste von Funktionen 
für die erste Version unserer Software zu implementieren. Unsere Ambitionen waren hoch, 
und wir waren entschlossen, eine perfekte erste Version zu liefern.
Die Realität der Softwareentwicklung ist oft komplexer als erwartet, 
und so stießen wir auf zahlreiche unvorhergesehene Herausforderungen. 
Die Zeit, die wir für die Implementierung dieser umfangreichen Funktionsliste benötigten,
erwies sich als viel länger als erwartet. Wir mussten uns eingestehen, dass ein pünktlicher 
Release der ersten Version in Gefahr geriet.
Wir haben uns dazu entschieden das Backend als Teilprojekt fallen zu lassen,  
um in naher Zukunft als Team primär an dem Frontend, der App, arbeiten zu können.  


## Frontend-Änderungen

Zunächst einmal liegt unser Hauptaugenmerk darauf, es dem Benutzer zu ermöglichen, das Produkt zu kaufen. Dazu gehört die Implementierung eines einfachen und benutzerfreundlichen Kaufprozesses, der es dem Nutzer ermöglicht, seine gewünschten Artikel schnell und unkompliziert zu erwerben.

Darüber hinaus legen wir großen Wert darauf, dass sich die Benutzer in der App anmelden können und entsprechende Benutzerprofile erstellt werden. 

Der private Bereich ist ein weiterer Schwerpunkt unserer aktuellen Entwicklungsbemühungen. Hier können die Benutzer auf eine Liste von Unfallberichten zugreifen, die für sie relevant sind. Dieser Bereich wird sorgfältig gestaltet, um sicherzustellen, dass die Benutzer die benötigten Informationen schnell und einfach finden können.

Schließlich, wenn es unsere Zeit erlaubt, planen wir die Implementierung einer Hierarchie der Vorgesetzten, die die gemeldeten Unfälle einsehen können. Dieser Bereich ist zwar nicht unbedingt für die erste Version unserer App erforderlich, aber wir erkennen die Bedeutung einer solchen Funktion für die langfristige Benutzerzufriedenheit und Sicherheit.

## Backend-Änderungen

Die Arbeit an zwei unterschiedlichen Teilprojekten hat sich als äußerst schwierig herausgestellt,  
da uns die Versiertheit von Sprints gefehlt hat, 
um möglichst schnell einen ersten funktionalen Kandidaten zu liefern.  

Daher haben wir als Team entschieden, keine weiteren Anstrengungen auf die Backend-Entwicklung zu verschwenden  
und uns primär mit dem Frontend auseinanderzusetzen.


### Supabase

[Supabase](https://supabase.com/) ist eine open-source Firebase-Alternative,  
die als ausgereifte Administrations-Plattform für eine PostgresSQL-Datenbank auftritt.  

Unser bereits erstelltes Entity-Relationship-Model, das wir nach dessen Finalisierung freigeben werden,  
ist einfach über den Datenbank-Editor einzubinden gewesen.

#### Row Level Security

Ein weiteres Feature, seit PostgresSQL v12, sind die **Row Security Policies**,  
die mithilfe von vorgeschalteten SQL-Abfragen wie der folgenden,
um allen Personen innerhalb einer Organisation den Zugriff auf eine Zeile zu ermöglichen:

```postgres
auth.uid() in (
    select authUserId
    from organization o
    right outer join persons p
    on o.id = p.organization_id
)
```
_Wir differenzieren zwischen authentifizierten und Gast-Benutzern (Zeugen), deshalb eine "persons"-Tabelle nebst der standardmäßigen auth>users Tabelle._

Standardmäßig ist bei diesem Feature alles gesperrt.
Eine Anfrage liefert immer ein leeres Ergebnis, bis eine entsprechende Policy (Bedingung) einem Benutzenden oder einem Schlüssel die Freigabe für einen speziellen Vorgang (Select/Insert/Update/Delete) erteilt.
Dieses Black-List-Feature ermöglicht es uns auf ein zwischengeschaltete Controller,
die in einem dedizierten Backend abgebildet werden müssten zu verzichten.  

Komplexere Vorgänge, die womöglich Umsysteme einbeziehen, können nach wie vor über die Edge-Funktionen von Supabase in Java-/ TypeScript abgebildet werden.


---  
Ende letztes Semester: [Zehnter Post _(KW51)_](10_Semesterabschluss.md)  
Nächste Woche: [...]()

---

{% include kommentare.html %}
