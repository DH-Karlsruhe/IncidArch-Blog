# 4. Semester Start _(KW15/24)_

Zum Beginn des vierten Semesters ändert sich einiges an unserem Projekt.  
Wir haben uns dazu entschieden das Backend als Teilprojekt fallen zu lassen,  
um in naher Zukunft als Team primär an dem Frontend, der App, arbeiten zu können.  


## Frontend-Änderungen

TODO

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
    select unique_person_id
    from organization o
    right outer join persons p
    on o.id = p.organization_id
)
```

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
