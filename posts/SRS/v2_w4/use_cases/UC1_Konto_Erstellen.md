# Use-Case Spezifikation: Konto Erstellen

# 1. Konto Erstellen

## 1.1 Kurzbeschreibung
Dieser Anwendungsfall ermöglicht es jedem, sich zu registrieren und ein Konto zu erstellen. Die Daten werden sicher in unserer Datenbank gespeichert.

## 1.2 Mockup
![Registrierung](./mockups/UC1_Registrieren.png)


## 1.3 UML-Diagramm
![UML-Registrierung](./uml_diagramme/uml_registrieren.png)

# 2. Ablauf von Events

## 2.1 Grundablauf
- Benutzer klickt auf "Registrieren".
- Das Registrierungsfenster wird geöffnet.
- Der Benutzer gibt seine Daten ein.
- Der Benutzer klickt auf "Senden".
- Die Daten werden validiert und an die Datenbank gesendet.
- Der Benutzer erhält eine Bestätigungs-Mail mit einem Code für die App.
- Besagter Code kann entweder auf Screen für die nächste 

## 2.2 Sequenzdiagramm

```mermaid
sequenceDiagram
  participant User
  participant AppReact
  participant Server
  participant MailServer

  User->>AppReact: Öffnet die React-App
  AppReact->>User: Zeigt Registrierungsformular (React-Komponente) an

User->>AppReact: Füllt Registrierungsformular aus
  AppReact->>Server: Sendet Anfrage zur Benutzerregistrierung

  Server-->>AppReact: Benutzerkonto erstellt, E-Mail-Bestätigung ausstehend
  AppReact-->>User: Zeigt Erfolgsmeldung an

  Server-->>MailServer: Sendet Bestätigungs-E-Mail an Benutzer
  alt E-Mail erfolgreich gesendet
    MailServer-->>Server: Bestätigungs-E-Mail gesendet
    Server-->>User: Anweisungen zur E-Mail-Bestätigung
  else E-Mail konnte nicht gesendet werden
    MailServer--x Server: Fehler beim Senden der E-Mail
    Server-->>User: Zeigt Fehlermeldung an
  end
```

# 3. Besondere Anforderungen
Der Benutzer benötigt eine E-Mail-Adresse, um sich zu registrieren.

# 4. Vorbedingungen
Die Vorbedingungen für diesen Anwendungsfall sind:
1. Der Benutzer hat die App gestartet.
2. Der Benutzer klickt auf "Registrieren".

# 5. Nachbedingungen

Der Benutzer wird für die jeweilige Organisation > Abteilung > Team von einem Administrator freigegeben,
damit es nicht zu Datenlecks kommt.

# 6. Aufwandsschätzung
Für diese Funktionalität wird ein Aufwand von 7 Punkten geschätzt
