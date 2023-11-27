# Siebter Blogpost (KW48)

Hallihallo 👋  

Die 7. Woche hat ein paar Weiterentwicklungen mit sich gezogen,  
neben Features im Sicherheitsbereich, bis zu Optimierungen  
haben wir an allen Ecken und Enden etwas Fortschritt erarbeiten können.  

## Frontend

Im Frontend hat es einige Aufräumarbeiten gegeben  
und die unterschiedlichen Team-Mitglieder haben Design-Experimente durchgeführt,  
um sich zum einen erweiternd mit dem ReactNative Styling auseinanderzusetzen,  
das wir bislang mit purem CSS handhaben  
und zum anderen hat es Entwicklungen in der Formular-Logik gegeben,  
sodass nun ein Basis-Formular für eine Vorfalls-Erstellung angezeigt  
und im Hintergrund richtig auf ein JSON-Objekt gemapt wird.   

Eine Anbindung zum Backend steht noch aus,  
da sich hier die Datenbankanbindung aufgrund der Sicherheitsanforderungen weiter verzögert..

## Backend

Die Authorisierung und Mitteilung der JWTs ist soweit implementiert  
und wartet auf die Anbindung an die Datenbank.  
Hier gibt es aktuell noch ein Problem mit der Laufzeit,  
wonach es bislang noch nicht möglich ist auf die Remote-Postgre-Datenbank zuzugreifen.  

Die Anwendung ist zudem resillienter geworden,  
da alle Fehler nun mit einem unifizierten Handler für den gesamten Programmablauf behandelt werden.
  => Fehler werden im Backend ausgegeben und nur mittels standartisierten HTTP-Codes zum Benutzer weitergeleitet.
  => Validierungs-Fehler werden entsprechend von Zod übernommen, nur ohne die konkrete Kennzeichnung.  

Des Weiteren stehen mittlerweile die kryptographischen Schnittstellen mit der [WebCrypto-API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API) zur Verfügung,  
um diese u.a. zstl. zum Kyber-Kryptosystem auf die Datensicherung anzuwenden  
und um sichere Hashing-Implementierungen (vor allem des SHA3-256) bereitzustellen.  


### Aktuelle Hürden

Die größte Hürde im Backend ist nach wie vor die **sichere** Datenbankanbindung.  
Da Deno einige Sicherheitsfeatures implementiert hat, die es bei Node.js nicht gibt.
Demnach ist aktuell das Problem, dass der Verbindungsaufbau mit der entfernten Postgres-Datenbank  
mit einem `os error 111` abgebrochen wird.  

Im Frontend gilt es für einen einheitlichen Look&Feel noch eine finale Lösung zu finden,  
bislang arbeiten wir jedoch auf einen ersten, funktionalen Kandidaten hin  
und das Design lässt sich in einer späteren Phase erneut aufgreifen. 

---  
Letzte Woche: [Sechster Post _(KW47)_](06_Implementation.md)  
Nächste Woche: [Achter Post _(KW49)_]()

---

{% include kommentare.html %}
