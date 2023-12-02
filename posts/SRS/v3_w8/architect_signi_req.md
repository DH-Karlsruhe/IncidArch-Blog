# Architecturally Significant Requirement (ASR)

> **F**: Was ist ein ASR, bzw. eine architektonisch bedeutsame Anforderung?  
> ***A***: Die **funktionalen** und **qualitativen Anforderungen** an eine Software-Architektur  
> **unter** der **Beachtung von Einschränkungen** (Constraints).  
> *Einschränkungen werden von Stakeholdern und der Erfüllungspflicht der [Erfolgskriterien](#erfolgskriterien-eines-systems) bestimmt.*

Die signifikanten Anforderungen werden in jedem Fall von (einzelnen) Stakeholdern bestimmt,  
wobei bei der Bewertung der Qualitätsfaktoren stets die Erfahrung der beteiligten Personen gefragt ist.  
Demnach bedarf es einer (kollaborativen) Erarbeitung dieser Individualanforderungen,  
die anschließend synthetisiert auf die Architecturally Significant Requirements (ASRs) abgebildet werden.  

Diese individuellen Anforderungen können in einem Qualitätsattribut-Workshop erfasst werden,  
wir haben [unseren erarbeiteten Utility-Baum](#utility-baum) in Markdown-Tabellen abgebildet..

## Erfolgskriterien eines Systems.

Nach McCall's Qualitätsfaktoren und der *ISO 9126 Qualitätsfaktoren* werden die folgenden Attribute  
als Grundlage für die Qualitätsbewertung eingesetzt:  

 - (Korrektheit, Funktionalität) ✅
 - Zuverlässigkeit 🦾
 - (Effizienz, Performanz) ⚡
 - (Integrität, (Code-)Ästhetik, Stil) 🦋
 - Wartbarkeit 🔧
 - Testbarkeit 💣
 - Bereitstellbarkeit 🦾 *und deren Sicherheit* 
 - Interoperabilität 🔌
 - SICHERHEIT. 🔏

Diese qualitativen Attribute werden um konkrete **Architektur-Lösungen/-Verschreibungen**  
und deren Komplementär, den **nicht-architektonischen Lösungen** ergänzt.  
Diese beschreiben zum einen den physischen Bauplan einer Architektur,  
wie diese in der Realität abgebildet wird  
und zum anderen, wie Menschen mit dieser interagieren sollen  
und wie die Architektur diesen nützt.


## Utility-Baum

Für die Spalten **Geschäftswert** und **technisches Risiko** haben wir folgende Skala festgelegt:  

 - **H**igh 🔥
 - **M**edium 💧
 - **L**ow ❄️


### Maintainability

| Konkret                                       | Qualitätsattributs-Szenarien                     | Geschäftswert | Technisches Risiko |
|-----------------------------------------------|-------------------------------------------------|---------------|--------------------|
| Deno als moderne Backend-Laufzeitumgebung      | Verbesserte Leistung und Skalierbarkeit          | Medium💧        | Niedrig❄️             |
| React Native und Expo als Frontend-Framework   | Effiziente Entwicklung plattformübergreifender mobiler Anwendungen | Hoch🔥 | Mittel💧 |
| Zod-OpenAPI zur API-Validierung                | Standardisierte und sichere API-Kommunikation   | Hoch 🔥         | Niedrig❄️             |

### Security

| Konkret                                       | Qualitätsattributs-Szenarien                     | Geschäftswert | Technisches Risiko |
|-----------------------------------------------|-------------------------------------------------|---------------|--------------------|
| Redundante Server und Lastenausgleich          | Hohe Serververfügbarkeit während Stoßzeiten     | Hoch🔥          | Mittel💧              |
| Automatische Fehlererkennung und -behebung     | Gewährleistung der Datenintegrität und minimale Ausfallzeiten | Hoch🔥 | Niedrig❄️ |
| Authentifizierung und Autorisierung            | Sicherstellung des Zugriffs nur für autorisierte Benutzer | Hoch🔥 | Hoch🔥 |

### Testability

| Konkret                                       | Qualitätsattributs-Szenarien                     | Geschäftswert | Technisches Risiko |
|-----------------------------------------------|-------------------------------------------------|---------------|--------------------|
| Umfassende Tests für wichtige Funktionen und Randfälle | Frühe Fehlererkennung und -behebung          | Hoch🔥          | Niedrig❄️             |
| Hohe Testabdeckung                            | Sicherstellung einer robusten und zuverlässigen Anwendung | Hoch🔥 | Niedrig❄️ |
## Architekturentscheidungen

*Warum haben wir das so gelöst?*
