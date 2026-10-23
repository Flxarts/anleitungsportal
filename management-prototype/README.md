# DIANA – Verwaltungsprototyp

Interaktiver, buildfreier Entwurf mit ausschließlich fiktiven Daten. `index.html` im Browser öffnen. Für die vorhandenen Fachinhalte führt „Anleitungsportal“ zur unveränderten, passwortgeschützten Hauptseite.

## Ausprobieren

1. Als Praxiskoordinator unter „Dokumente“ die eingereichte Unterlage von Mia Beispiel öffnen.
2. Rückmeldung eintragen und „Korrektur anfordern“ auswählen.
3. Oben zur Demo-Rolle „Schüler“ wechseln, Unterlage bearbeiten und einreichen.
4. Als Praxiskoordinator erneut öffnen und als geprüft markieren.
5. Unter „Einsatzplanung“ einen Einsatz anlegen, ändern oder einen neuen Einsatz ohne Dokumente löschen.
6. Unter „Fehlzeiten“ Stunden erfassen.

Daten bleiben im localStorage-Schlüssel `diana-management-demo-v1` dieses Browsers. Zum Zurücksetzen diesen Schlüssel in den Browser-Entwicklerwerkzeugen entfernen. Originalportal und Verwaltungsprototyp speichern getrennt.

## Vorhandene Basis

Das geprüfte Original enthält 460 Anleitungsthemen, acht Kurspläne, 106 Module und zwölf eingebettete Vorlagen. Digitale Formulare, Dienstplan, Fehlzeiten und lokale Nachweise sind bereits vorhanden. Die Versandfunktion bereitet E-Mails vor; sie ist noch keine serverseitige Dokumentenabgabe.

## Stand und Grenzen

- Sieben Demo-Rollen mit fester Berechtigungsmatrix; Schüler sieht Mia Beispiel, Praxisanleitung ist Mia Beispiel zugeordnet, Lehrer sieht Kurs 26 F.
- Ein beispielhafter Lehrgang mit zwei Kursen und drei Teilnehmenden. Lehrgänge, Kurse und Benutzer sind noch nicht administrierbar.
- Einsätze erstellen, bearbeiten und löschen; zugeordnete Dokumente verhindern das Löschen.
- Dokumente anfordern, als Textentwurf ausfüllen, einreichen, prüfen und zur Korrektur zurückgeben.
- Fehlzeiten erfassen und im Zuständigkeitsbereich anzeigen.
- Rollenwechsel ist ausschließlich eine Simulation. Es gibt keine echte Authentifizierung und keine serverseitige Autorisierung.
- Keine Datei-Uploads, gemeinsame Speicherung, tatsächlichen Benachrichtigungen oder rechtsverbindlichen Unterschriften. Bestehende Formulardaten werden noch nicht importiert.
- Der lokale Aktivitätsverlauf ist kein revisionssicheres Auditprotokoll. Er wird für eingeschränkte Demo-Rollen ausgeblendet.
- Keine Echtdaten verwenden.

## Nächster Umsetzungsschritt mit Supabase und Vercel

1. Persönliche Konten und Einladungen über Supabase Auth.
2. Datenmodell: Organisation → Lehrgang → Kurs → Teilnehmer → Einsatz; zusätzlich Rollen, Einzelrechte und zeitlich begrenzte Kurs-/Schüler-/Einsatzzuordnungen.
3. Tabellen für Dokumentenanforderungen, versionierte Abgaben, Prüfungen, Rückmeldungen und Fehlzeiten. Private Dateispeicherung mit denselben Zugriffskriterien.
4. Rechte pro Aktion und Zuständigkeit serverseitig und durch Row Level Security absichern; Benutzer dürfen eigene Rollen nicht ändern.
5. Formularbibliothek aus dem Original anbinden. Inhalte und persönliche Abgaben getrennt behandeln.
6. Rollenänderungen, Prüfungen und Abgaben mit unveränderbarer Historie protokollieren. Medizinische Fehlzeitengründe gesondert begrenzen.
7. Tests mit mehreren Konten für erlaubte und verbotene Zugriffe; anschließend Preview auf Vercel.

Die berechnete Nachweisquote zeigt geprüfte Dokumente / angeforderte Dokumente, keine fachliche Kompetenzbewertung. Die Rollenmatrix ist ein fachlicher Vorschlag und muss vor Produktivbetrieb abgestimmt werden.

## Prüfung

JavaScript-Syntax geprüft. Modellprüfung für alle 49 Kombinationen aus Rolle und Seite, Zuständigkeitsfilter, Planungsrechte und lokale Speicherung erfolgreich. Ein echter Browserlauf war durch die Socket-Beschränkungen der Arbeitsumgebung blockiert. Daher noch keine bestätigte visuelle oder vollständige Ende-zu-Ende-Prüfung.
