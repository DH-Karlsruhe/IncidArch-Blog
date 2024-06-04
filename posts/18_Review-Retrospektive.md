# Review, Retrospektive & Code-Analyse

## Review 👀 & Retrospektive 📰

## Code-Analyse mit SonarQube 🪼

Besser spät als nie, nun zum 18. Blogbeitrag hier die Ergebnisse unserer ersten statischen Code-Analyse mit SonarQube
und dem SonarScanner:

![SonarQube-Score](../images/sonarqube_040624.png)


Grob zusammengefasst sagt der Score aus,
dass unsere Code-Qualität einen akzeptablen Zustand erreicht hat.
Zwei der angegebenen "Security-Hotspots" entstehen aus einer Test-Datei zu der `RegisterComponent.ts`,
da diese bei Beginn in die Auswertung gerutscht ist, weshalb SonarQube hier fälschlicherweise zwei High priority `potentially hardcoded credential` angibt.

Eine weitere tritt in der `HomeScreen.tsx` Datei auf, wo wir bis dato
noch Zufallszahlen als Statistik-Werte verwenden,
wobei SonarCube diese mit einem `pseudorandom number` Fehler unter Medium priority versieht.

Der einzig ernst zu nehmende Security-Hotspot mit low priority scheinen somit
die Wildcard-CORS Angabe der Backend-Funktionen, sowie die Auto-Generierten Berechtigungs-Anfragen von Expo im Android-Kontext zu sein,
bei letzterem werden Berechtigungen für `WRITE_EXTERNAL_STORAGE` und `RECORD_AUDIO` angefragt,
zumal wir maximal für ersteres im Storage-Kontext einen nutzen haben.

Die Code-Smells bewegen sich größtenteils im Minor-Bereich,
dennoch haben wir 8 kritische Code Smells, wobei fünf auf noch nicht implementierte,
aber deklarierte Funktionen zurückzuführen sind,
sowie zwei durchzuführende Refactors zwecks zu hoher Komplexität der Funktionen
und eine bezüglich eines Duplikats in einer TS-Typendeklaration,
die wohl durch den Linter nicht dedupliziert worden ist.

Da diese Probleme für uns vorerst keine Priorität haben und diese unsere Demo nicht weiter einschränken oder im Endeffekt unsicherer machen, ist es dennoch gut über deren Existenz informiert zu sein,
um in Zukunft mögliche Maßnahmen treffen zu können.


---

Letzte Woche: [Neue Woche: Fortschritte und Optimierungen](17-CI-CD-Pipeline.md)

Nächste Woche: [Upcoming]()

---

{% include kommentare.html %}
