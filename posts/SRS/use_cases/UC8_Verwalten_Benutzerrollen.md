# Use-Case Spezifikation: Verwalten von Benutzerrollen

# 1. Verwalten von Benutzerrollen

## 1.1 Kurzbeschreibung
Dieser Anwendungsfall ermöglicht es autorisierten Administratoren, Benutzerrollen in der Anwendung zu erstellen, zu bearbeiten, und zu löschen.

## 1.2 Mockup

### Work in Progress

# 2. Ablauf von Events

## 2.1 Grundablauf
- Der Administrator öffnet die Administrationsseite der Anwendung und navigiert zur Benutzerverwaltung.
- Der Administrator wählt die Option "Benutzerrollen verwalten".
- Die Liste der vorhandenen Benutzerrollen wird angezeigt.
- Der Administrator kann neue Benutzerrollen erstellen, bestehende Benutzerrollen bearbeiten oder löschen.
- Bei der Erstellung oder Bearbeitung einer Benutzerrolle werden Informationen wie Name, Berechtigungen und Beschreibung angegeben.
- Der Administrator bestätigt die Änderungen.
- Die Benutzerrollen werden entsprechend aktualisiert.

## 2.2 Alternativer Ablauf
- Wenn ein Administrator versucht, eine Rolle zu löschen, die noch Benutzer zugewiesen hat, wird eine Warnung angezeigt, und die Rolle wird nicht gelöscht, bis alle Zuweisungen entfernt sind.

# 3. Besondere Anforderungen
Die Verwaltung von Benutzerrollen sollte sicherstellen, dass autorisierte Benutzer die erforderlichen Berechtigungen erhalten und auf bestimmte Funktionen der Anwendung zugreifen können.

# 4. Vorbedingungen
Die Vorbedingungen für diesen Anwendungsfall sind:
1. Der Administrator ist in der Anwendung angemeldet und hat die erforderlichen Rechte für die Benutzerverwaltung.

# 5. Nachbedingungen
Die Benutzerrollen werden aktualisiert und die Änderungen haben Auswirkungen auf die Berechtigungen und Zugriffe der Benutzer in der Anwendung.

# 6. Aufwandsschätzung
Für die Implementierung der Benutzerverwaltung und Verwaltung von Benutzerrollen wird ein Aufwand von 14 Punkten geschätzt.
