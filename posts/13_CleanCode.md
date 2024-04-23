# Clean Code 🧹

Aufräumen muss (leider :) manchmal sein,  
so auch in Software-Projekten und in der Folge bei IncidArch.  

Als Standard-Leitfaden haben wir das in React (-Native) gängige Atomic-Schema angewendet,  
um unsere Komponenten-Bauweise strukturiert anzugehen.

![[Atomic-Schema - Quelle: Orionic](https://oroinc.com/b2b-ecommerce/blog/introducing-the-orocommerce-storefront-style-guide-for-b2b-ecommerce-brands/)](../images/atomic-schema.webp)

Dem Atomic-Schema nach ist unsere lebendige App-Struktur in dem `/app/` Verzeichnis abgelegt,  
die zudem auf jeder App-Ebene, abgebildet durch die Verzeichnis-Hierachie, eine `_layout.tsx`-Datei enthält.  
In dieser werden die unterschiedlichen Pages und deren Header zusammengeführt,
die für die aktuelle App-Ebene relevant sind.

Die eigentlichen Ansichten (Pages) werden in jeweils eigene Dateien ausgelagert (`form.tsx`, `home.tsx`, `profile.tsx`, etc.) und enthalten die Page.  
In (fast) allen Fällen ist das zugehörige Template in das `/src/screens/`-Verzeichnis ausgelagert,  
um die Hydration der konkreten Benutzer-Daten von dem unterliegenden App-Aufbau zu trennen.  

Die kompositionierten Komponenten der Screens (Templates) werden größtenteils in das `/src/components` ausgelagert.  

Die eigentlichen Benutzer-Daten werden über `/src/stores/`
mit dem Supabase-Client aus der PostgresSQL-Datenbank abgerufen und eingelagert (WiP).

In Kombination mit den [Expo-Best-Practices]().


https://reactnative.dev/docs/next/gesture-responder-system#best-practices

## Prettier & ESLint

Für die Formattierung und 



---
Letzte Woche: [RMMM Tabelle und Fortschritt _(KW16/24)_](12_Risiko-und-Fortschritt.md)  
Nächste Woche: [Upcoming]()  
---

{% include kommentare.html %}
