# Projekt-Update: Migration, Tests und Fortschritte

Hallo zusammen,

seit unserem letzten Blogbeitrag hat sich einiges getan. Hier sind die neuesten Updates zu unserem Softwareprojekt:

## Migration zu Expo SDK 51

Wir mussten von Expo SDK 49 auf Expo SDK 51 migrieren, da die Expo Go App, die wir benutzen, nun nur mit der neuesten Expo SDK 51 funktioniert. Diese Migration führte zu einigen Herausforderungen, da einige Funktionen nach der Umstellung nicht mehr wie gewohnt arbeiteten. Wir haben intensiv daran gearbeitet, diese Probleme zu beheben und die Funktionalität wiederherzustellen.

## Testplan

Beim Testplan hat sich seit dem letzten Mal nichts Wesentliches geändert. Wir haben jedoch einige neue Tests hinzugefügt, die wir euch im Folgenden kurz vorstellen möchten.

### Neue Tests

Wir haben verschiedene End-to-End-Tests (E2E) und Komponententests integriert, um die Stabilität und Zuverlässigkeit unserer Anwendung weiter zu verbessern. Hier sind einige der Highlights:

1. **End-to-End-Test zur Initialisierung einer neuen Benutzerorganisation**
    - Dieser Test prüft, ob ein neuer Benutzer korrekt registriert wird und ob automatisch eine neue Organisation für diesen Benutzer erstellt wird. Dabei werden Schritte wie die Registrierung des Benutzers, die Bestätigung der E-Mail und die automatische Erstellung der Organisation durchlaufen.

2. **Testen der ExploreHeader-Komponente**
    - Hier überprüfen wir, ob die ExploreHeader-Komponente mit den richtigen Daten gerendert wird und ob sie auf Benutzereingaben korrekt reagiert. Wir stellen sicher, dass alle Kategorien und Buttons richtig angezeigt und funktionsfähig sind.

3. **Testen der InfoSection-Komponente**
    - Dieser Test prüft, ob die InfoSection-Komponente mit den gegebenen Titel-, Beschreibungs- und Icon-Daten korrekt dargestellt wird.

4. **Testen der RegisterComponent-Komponente**
    - Wir simulieren die Eingaben eines Benutzers in der Registrierungsmaske und überprüfen, ob die Registrierung korrekt verarbeitet wird. Dabei wird auch sichergestellt, dass alle eingegebenen Daten richtig übernommen werden.

5. **Testen der Section-Komponente**
    - Hier wird überprüft, ob die Section-Komponente mit den richtigen Daten gerendert wird und ob der Navigationsbutton korrekt funktioniert.

6. **Testen der SplashComponent-Komponente**
    - Dieser Test stellt sicher, dass der Startbildschirm unserer Anwendung korrekt gerendert wird und dass alle visuellen Elemente richtig angezeigt werden.

Diese Tests helfen uns dabei, die verschiedenen Komponenten und Funktionalitäten unserer Anwendung gründlich zu überprüfen und potenzielle Probleme frühzeitig zu identifizieren.

---  

Letzte Woche: [Testplan](14_Testplan.md)
Nächste Woche: [Upcoming]()  

---

{% include kommentare.html %}
