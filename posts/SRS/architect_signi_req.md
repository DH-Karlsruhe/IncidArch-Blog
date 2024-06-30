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
| Deno als moderne Backend-Laufzeitumgebung      | Verbesserte Leistung und Skalierbarkeit; Trägt zum "eine Sprache, ein Ökosystem" (TypeScript) Gedanken bei.          | Medium💧        | Niedrig❄️             |
| React Native und Expo als Frontend-Framework (auf TypeScript-Basis)   | Effiziente Entwicklung plattformübergreifender mobiler Anwendungen | Hoch🔥 | Mittel💧 |
| Zod-OpenAPI zur API-Validierung und Dokumentation                | Standardisierte und sicher getestete Schema-Validierung mit vollständiger Typisierung und teilautomatisierter API-Dokumentation.    | Hoch 🔥         | **M**edium 💧            |

### Security

| Konkret                                       | Qualitätsattributs-Szenarien                     | Geschäftswert | Technisches Risiko |
|-----------------------------------------------|-------------------------------------------------|---------------|--------------------|
| Redundante Server und Lastenausgleich          | Hohe Serververfügbarkeit während Stoßzeiten, dank zustandsloser Backend-API.     | Hoch🔥          | Mittel💧              |
| Authentifizierung und Autorisierung            | Sicherstellung des Zugriffs nur für autorisierte Benutzer mit gültigen JSON-Web-Tokens, welche standardmäßig mit einer maximalen Lebenszeit (akt. 2 Wochen) versehen werden. | Hoch🔥 | Hoch🔥 |
| Catchall Errors  | Durch das Middleware-zentrierte Backend werden alle möglichen Fehler von einer hierarchisch hoch angesiedelten Middleware abgefangen und von potentiellen Leaks befreit, indem generische Fehlermeldungen (HTTP-Errors) nur mit speziell angegebenen Nachrichten zurückgegeben werden.             | Mittel💧       | Hoch🔥             |
| Data Encryption  | Möglichst keine Klartext-Informationen in der Datenbank, sodass diese aktuell (noch) mit einem App-Key verschlüsselt werden *(und i.Zkt. wom. mit E2EE)*.              | Hoch🔥       | Hoch🔥             |

### Testability

| Konkret                                       | Qualitätsattributs-Szenarien                     | Geschäftswert | Technisches Risiko |
|-----------------------------------------------|-------------------------------------------------|---------------|--------------------|
| Anwenden des funktionalen Programmierstils | Funktionen haben genau eine Aufgabe mit begrenzten Ergebnissen, was die Komplexität auf kleinstmögliche Teile herunterbricht (Limit Complexity)          | **M**edium 💧          | Niedrig❄️             |
| Umfassende Tests für wichtige Funktionen und Randfälle | Frühe Fehlererkennung und -behebung          | Hoch🔥          | Niedrig❄️             |
| Hohe Testabdeckung                            | Sicherstellung einer robusten und zuverlässigen Anwendung | Hoch🔥 | Niedrig❄️ |
| Lose Kopplung                            | Frontend und Backend sind voneinander getrennt,  lediglich eine OpenAPI-Schnittstellen-Spezifikation verknüpft die beiden.  | **M**edium 💧 | **M**edium 💧 |


## Architekturentscheidungen

*Warum haben wir das so gelöst?*
### Architekturentscheidungen

#### **Wahl der Backend-Laufzeitumgebung (Deno):**
Die Entscheidung, Deno als moderne Backend-Laufzeitumgebung zu verwenden, basiert auf der Zielsetzung für verbesserte Leistung und Skalierbarkeit. Deno ermöglicht die Ausführung von TypeScript-Code im Backend und bietet dabei moderne Sicherheits-Features, sowie eine verbesserte Leistung im Vergleich zu traditionellen Laufzeitumgebungen.

#### **Frontend-Framework (React Native und Expo):**
Die Wahl von React Native und Expo als Frontend-Frameworks zielt darauf ab, eine effiziente Entwicklung plattformübergreifender mobiler Anwendungen zu ermöglichen. React Native ermöglicht die Entwicklung von nativen mobilen Apps mit TypeScript und React, während Expo zusätzliche Entwicklungs- und Bereitstellungstools bietet, um den Entwicklungsprozess zu optimieren.

#### **API-Validierung mit Zod-OpenAPI:**
Die Entscheidung, Zod-OpenAPI zur API-Validierung zu nutzen, wird getroffen, um eine standardisierte und sichere API-Kommunikation mit vollständiger Fehlerbehandlung zu gewährleisten. Zod-OpenAPI ermöglicht die Definition von Datenstrukturen und API-Schemas in TypeScript, was zu einer verbesserten Sicherheit und Robustheit der Anwendung beiträgt.

#### **Authentifizierung und Autorisierung:**
Die Architekturentscheidung für eine robuste Authentifizierung und Autorisierung stellt sicher, dass der Zugriff auf die Anwendung nur für autorisierte Benutzer gewährt wird. Dies erfolgt durch die Implementierung von sicheren Authentifizierungsmechanismen und rollenbasierten Zugriffskontrollen.

Diese Architekturentscheidungen sind darauf ausgerichtet, die Ziele der Leistung, Sicherheit und Benutzerfreundlichkeit zu erreichen und bilden die Grundlage für die Entwicklung einer skalierbaren und zuverlässigen Anwendung.
