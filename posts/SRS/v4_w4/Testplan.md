# Testplan

## Arten von Tests

Unsere Teststrategie umfasst folgende Arten von Tests, ausgewählt aufgrund ihrer Bedeutung für die Qualitätssicherung unserer Expo-basierten JavaScript-Anwendung:

- **Unit-Tests:** Diese Tests sind entscheidend, um sicherzustellen, dass einzelne Funktionen und Module unserer JavaScript-Anwendung korrekt funktionieren. Unit-Tests ermöglichen es uns, Code isoliert zu testen und potenzielle Fehler frühzeitig zu erkennen, was zu einer verbesserten Codequalität und Wartbarkeit führt.

- **UI-Tests:** Da die Benutzeroberfläche einer Anwendung oft der erste Berührungspunkt für Benutzer ist, sind UI-Tests von entscheidender Bedeutung, um sicherzustellen, dass die Benutzeroberfläche unserer mobilen Anwendung ordnungsgemäß funktioniert und eine optimale Benutzererfahrung bietet

- **End-to-End-Tests:** End-to-End-Tests sind wichtig, um sicherzustellen, dass alle Komponenten unserer Anwendung ordnungsgemäß zusammenarbeiten und der gesamte Anwendungsfluss korrekt funktioniert. Diese Tests simulieren reale Benutzerinteraktionen und ermöglichen es uns, potenzielle Probleme in der Anwendungsumgebung zu identifizieren, bevor sie von den Benutzern festgestellt werden.

## Zielwert für Testabdeckung

Unser Zielwert für die Testabdeckung beträgt mindestens 80%. Dies bedeutet, dass mindestens 80% des JavaScript-Quellcodes unserer Expo-Anwendung durch Tests abgedeckt werden sollen, um eine ausreichende Testqualität und -abdeckung zu gewährleisten.

## Automatische Testwerkzeuge

Wir verwenden GitHub Actions zur Automatisierung unserer Testprozesse. GitHub Actions ermöglicht es uns, automatisch Tests auszuführen, wenn Änderungen am Quellcode vorgenommen werden, und Rückmeldungen über den Status der Tests in unserem GitHub-Repository zu erhalten.

Für die einzelnen Testarten verwenden wir folgende Werkzeuge:

- **Unit-Tests:** Jest ist ein beliebtes Testframework für JavaScript-Anwendungen, das wir verwenden, um unsere Unit-Tests zu automatisieren.
- **UI-Tests:** Wir verwenden Detox, um UI-Tests in unseren React Native-Anwendungen durchzuführen. Detox bietet eine spezielle Unterstützung für React Native und ermöglicht es uns, die Benutzeroberfläche und die Interaktionen auf mobilen Geräten zu testen.
- **End-to-End-Tests:** Wir verwenden ebenfalls Detox, um End-to-End-Tests durchzuführen und sicherzustellen, dass unsere gesamte Anwendung wie erwartet funktioniert.

## Verwaltung von Testfällen

Die Verwaltung unserer Testfälle erfolgt direkt über GitHub Actions in Verbindung mit unserem GitHub-Repository. Wir organisieren unsere Testfälle in speziellen Verzeichnissen innerhalb unseres Repositorys und führen sie automatisch aus, wenn bestimmte Ereignisse, wie z. B. ein Push oder ein Pull Request, auftreten. Durch die Integration mit unserem Versionskontrollsystem können wir den Status bestandener und fehlgeschlagener Tests genau verfolgen und die Testergebnisse mit den entsprechenden Codeänderungen verknüpfen.

