# Metriken & Clean Code Ergänzungen


## Gewählte Metriken

Um die Qualität und Zuverlässigkeit unseres Codes zu gewährleisten, nutzen wir verschiedene Metriken. Eine der wichtigsten ist die Code Coverage, die wir mit `jest --coverage` messen. Diese Metrik gibt an, wie viel Prozent des Codes durch unsere Tests abgedeckt sind und hilft uns dabei, ungetestete Teile des Codes zu identifizieren und zu verbessern.

![Code Coverage](../images/code_coverage.jpg)

Die Abdeckung umfasst die folgenden Bereiche:

- **Statements**: Misst den Anteil der Code-Anweisungen, die durch Tests abgedeckt sind.
- **Branches**: Bezieht sich auf die bedingten Verzweigungen (wie if-else) im Code.
- **Functions**: Deckt die Funktionen und Methoden ab, die getestet wurden.
- **Lines**: Zählt die tatsächlich ausgeführten Codezeilen während der Tests.

Eine hohe Code Coverage ist ein Indikator für eine solide Testabdeckung und erhöht das Vertrauen in die Stabilität und Wartbarkeit des Codes. Es ist jedoch wichtig zu beachten, dass eine hohe Abdeckung alleine nicht ausreicht. Qualität und Aussagekraft der Tests sind ebenso entscheidend.

Durch die Verwendung von `jest --coverage` stellen wir sicher, dass wir kontinuierlich die Abdeckung überprüfen und gezielt Bereiche verbessern können, die unterdurchschnittlich abgedeckt sind.

---

# Ergänzungen zu Clean Code

<!-- Orientierung: https://dev.to/drruvari/mastering-solid-principles-in-react-easy-examples-and-best-practices-142b -->

Erweiternd zu dem [Clean-Code Blog-Beitrag](13_CleanCode.md) haben wir uns im Rahmen der letzten Migration auf das expo SDK 51
die SOLID-Prinzipien näher angeschaut und auf das funktionale Paradigma von JS/TS 
(und somit von React Native) angewendet.

Dabei haben wir folgende Grundsätze synthetisiert, nach denen wir nun Stück für Stück unsere Code-Base anpassen:

1. Single Responsibility 
   - "Eine Funktion, eine Verantwortung"
   - Das Template einer Komponente muss strikt von der Logik getrennt werden!
     - Bedeutet: Fetch-Funktionen für Stores, das Backend oder etwaige Geschäftslogik (wie Validierungs-Funktionen der Formular-Elemente) werden in dedizierte Funktionen ausgelagert.
2. Open-Closed
   - "Offen für Erweiterung, geschlossen für Modifikation"
   - Dieses Prinzip folgt inheränt bei sauberer Einhaltung des Atomic-Schemas, hier haben wir nachgebessert, sodass beispielsweise die verschiedenen Text-Eingabe-Formular-Felder in einem `LabeledTextInputs` Atom gebündelt werden und die EmailInput-/PasswordInput-/UsernameInput-Textfelder dieses Atom erweitern.
3. Liskov Substitution
   - "Subtypen verhalten sich wie ihre Basistypen"
   - Analog zu dem Beispiel aus dem Open-Closed-Prinzip ist die Typen-Abstraktion auf das Interface `InputProps` genormt, wobei die unterschiedlichen Moleküle zwar Standardwerte für ein Label annehmen, diese jedoch mit einem entsprechend explizit gesetzten Parameter überschrieben werden können.
4. Interface Segregation
   - "Keine Komponente sollte dazu gezwungen werden, Abhängigkeiten einer benötigten Funktion zu erfüllen, die in dem Kontext nicht relevant sind"
   - Als Nebenbedingung zu dem bereits genannten Single-Responsibility-Prinzip, ist die Trennung nach Eingabearten erneut ein gutes Beispiel, da zwar alle von einem Stamm, dem `LabeledTextInputs` Atom ausgehen, wobei das Atom keine Validierungen, wie die Passwort-Länge implementiert. Seine Schnittstelle ist eben atomar für den Kontext.
5. Dependency Inversion
   - Im Sinne der losen Kopplung Abstraktionen auf Bibliotheken zu legen.
   - Konkret bedeutet das unter anderem erweiternd zu dem Single-Responsibility-Prinzip, das fetchen von Backend-Informationen auf dedizierte Funktionen mit dem umzulegen, welche widerrum den Zustand der Daten mit `useState` halten, Aktualisierungen mit `useEffect` in dem Kontext der abstrahierten Funktion vornehmen und letztlich nur die sich aktualisierende Referenz auf den Datensatz zurückzugeben, sodass dieser in einem Template verwendet werden kann.

Der zu dem genannten Beispiel zugehörige [Clean-Code-Refactor-Commit](https://github.com/DH-Karlsruhe/IncidArch-FrontEnd/commit/2ace01d56bdd9fd7a8b5105a1ad32741e8748081) ist hier zu finden.  

Premature Optimization und besonders die Optimierung der Entwickler-Erfahrung haben uns im ersten Semester sehr viele, wertvolle Arbeitsstunden gekostet.  
In diesem Semester haben wir nicht zuletzt durch gemeinsam getroffene Entscheidungen
unsere Agilität verbessert und sind mittlerweile auf einem guten Weg für unser Projekt das Minimum Viable Product, entsprechend unserer geplanten Anforderungen aufzubauen.

Vielen Dank für's Lesen!

---  

Letzte Woche: [Framework Migration und Tests](15_Framework-migration-und-Tests.md)

Nächste Woche: [CI/CD Pipeline](17-CI-CD-Pipeline.md)

---

{% include kommentare.html %}
