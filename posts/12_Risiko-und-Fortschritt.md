# Update zu unserem Risikomanagement

Wir arbeiten kontinuierlich daran, unsere Software sicherer und effizienter zu gestalten. Heute möchten wir euch unsere neueste Risk Mitigation, Monitoring and Management (RMMM) Tabelle vorstellen und das größte technische Risiko erläutern, das wir identifiziert haben, sowie unsere Pläne, dieses zu adressieren.

## RMMM-Tabelle (Version 1.0)

[RMMM Tabelle](RMMM/v1_w12/RMMM.md)

## Fokus auf das größte technische Risiko: Unzureichende Sicherung sensibler Daten (T1)

### Risikobeschreibung

Es besteht das Risiko, dass persönliche und wichtige Geschäftsdaten durch Sicherheitslücken gefährdet werden. Da wir uns an strenge Datenschutzgesetze wie die DSGVO halten müssen, ist dieses Risiko besonders ernst zu nehmen.

### Geplante Strategie zur Risikominderung

Wir planen, fortschrittliche Verschlüsselungstechniken einzuführen, um dieses Risiko zu reduzieren. Alle Daten sollen während der Übertragung und Speicherung verschlüsselt werden. Während der Übertragung ist stets auf den neusten TLS-Standard (1.3) zu setzen, wobei wir für die Speicherung in einer späteren Iteration mit [pgsodium](https://www.postgresql.org/about/news/pgsodium-200-modern-cryptography-for-postgresql-2389/) als offiziell anerkannte PostgresSQL-Erweiterung eine Column-Level-Encryption einführen möchten, die zudem ab Werk Schlüssel-Ringe und Recovery-Optionen bereitstellen soll. Zudem sind in unserer Postgres-Datenbank die Row-Level-Security Policies nahezu vollständig eingeführt, sodass nur authentifizierte Personen auf sensible Daten zugreifen können.

### Notfallplan

Für den Fall einer Datenpanne bereiten wir einen Notfallplan vor. Dieser Plan wird sofortige Maßnahmen zur Eindämmung der Situation umfassen, wie Benutzer-Zugänge einzufrieren, Organisationen zu sperren oder im äußersten die Supabase-Instanz für externe "offline" zu nehmen.  
Die Benachrichtigung aller Betroffenen gemäß gesetzlichen Vorgaben sowie eine gründliche Untersuchung, um die Ursache zu finden und zukünftige Probleme zu verhindern sind unabdingbar.  



## Projektfortschritt seit der Halbzeitpräsentation

Seit unserer Halbzeitpräsentation haben wir das Projekt nahezu komplett umgekrempelt.  

Das Backend ist nun eine Supabase-Instanz, wobei der wahre Fokus im Backend nun auf PostgresSQL und dessen Features liegt.  
Unser Datenbank-Schema ist entsprechend eingebunden und um die RLS-Policies erweitert worden,  
sodass nun zuverlässig die Organisations-Struktur in SQL-Tabellen abgebildet und entsprechend der Benutzerberechtigungen über Policies in implizite Rollen (Organisations-Eigentümer -darf alles- und Sachbearbeitende -darf alles lesen und eigenes bearbeiten-) übertragen worden ist.  

Aktuell wird die Logik für die Organisations-Anlage mit Beispiel-Vorfällen über Supabase-Edge-Functions abgebildet.

Im Frontend ist zudem erstmals die Anmelde-/ und Registrierungs-Logik im Einsatz.
Weitere Entwicklungsstellen sind eine verbesserte Navigation,
dank angepasster Router-Konfiguration, verbessertes manuelles CSS-Styling und natürlich die Klickstrecke bei der Vorfalls-Erstellung.

*Zusammengefasst geht es voran und wir sind zuversichtlich. 🚀*

---
Letzte Woche: [4. Semester Start _(KW15/24)_](./11_4-Semester-Initialisierung.md)

---

{% include kommentare.html %}
