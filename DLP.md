1. Aufrufen des Microsoft 365 Security & Compliance Centers
Melde dich im Microsoft 365 Admin Center an: https://admin.microsoft.com.
Navigiere zum Compliance Center (oder suche nach Microsoft Purview Compliance Portal).

2. Zugriff auf die DLP-Richtlinienverwaltung
Im Menü links wähle Lösungen > Datenverlustverhinderung.
Klicke auf Richtlinien.
Wähle + Richtlinie erstellen, um den DLP-Richtlinien-Assistenten zu starten.

3. Auswahl des Typs der Richtlinie
Wähle die Vorlage Kreditkartennummern aus der Liste von vorkonfigurierten Vorlagen. Diese Vorlage enthält bereits Regeln zum Schutz von Kreditkartendaten.
Klicke auf Weiter.

4. Definition des Geltungsbereichs
Lege fest, wo die DLP-Richtlinie angewendet werden soll:
E-Mail (Exchange Online)
OneDrive for Business
SharePoint Online
Microsoft Teams
In dieser Aufgabe soll die Richtlinie nur auf Exchange Online (E-Mails) angewendet werden. Wähle daher Exchange E-Mail aus.

5. Definition der Bedingungen
Überprüfe die vorgegebenen Bedingungen für die DLP-Richtlinie:
Die Bedingung „Wenn die Nachricht eine Kreditkartennummer enthält“ ist bereits eingestellt.
Klicke auf Weiter, um diese Bedingung zu akzeptieren.

6. Aktion festlegen
Lege fest, welche Aktion ausgeführt werden soll, wenn die Bedingung erfüllt ist:
Wähle die Option E-Mail blockieren aus, um E-Mails zu verhindern, die Kreditkartennummern enthalten.
Aktiviere die Option, den Absender zu benachrichtigen, damit dieser weiß, warum die Nachricht blockiert wurde.

7. Anpassung der Benachrichtigungen (optional)
Du kannst die Benachrichtigung anpassen, die Benutzer erhalten, wenn eine Nachricht blockiert wird. Füge eine Nachricht hinzu, die erklärt, dass E-Mails mit Kreditkartennummern nicht gesendet werden dürfen.

Beispiel: „Ihre E-Mail wurde blockiert, weil sie sensible Kreditkartendaten enthält.“

8. Festlegung von Ausnahmen (optional)
Füge Ausnahmen hinzu, falls bestimmte Benutzer, Gruppen oder Domains von der DLP-Regel ausgeschlossen werden sollen.
 Diese Option ist optional und muss für diese Übung nicht zwingend verwendet werden.

9. Überprüfung und Aktivierung
Überprüfe die Einstellungen der Richtlinie und aktiviere die Richtlinie sofort, oder wähle die Option, sie später zu aktivieren.
Klicke auf Erstellen, um die DLP-Richtlinie zu implementieren.

10. Überwachung der Richtlinie
Nachdem die Richtlinie aktiviert wurde, kehre zum Dashboard zurück.
Unter Datenverlustverhinderung kannst du sehen, ob die Richtlinie Verstöße erkannt hat. Überwache, ob Nachrichten blockiert wurden, und überprüfe Berichte.
Bonus-Aufgabe (optional): Test der Richtlinie
Sende eine E-Mail mit einer simulierten Kreditkartennummer (z. B. 4111 1111 1111 1111) an ein anderes Postfach innerhalb deiner Organisation.
Überprüfe, ob die DLP-Richtlinie die Nachricht blockiert und eine Benachrichtigung sendet.