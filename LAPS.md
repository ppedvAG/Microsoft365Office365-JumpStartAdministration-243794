
1. Schema-Erweiterung:
Öffnen Sie eine PowerShell-Sitzung als Administrator auf einem Domain Controller.
Navigieren Sie zum LAPS-Installationsordner (in der Regel C:\Program Files\LAPS).

Führen Sie das Schema-Erweiterungsskript aus:
Import-Module AdmPwd.PS
Update-AdmPwdADSchema

Dies fügt das Attribut ms-Mcs-AdmPwd zu den Computerobjekten in Active Directory hinzu, das für die Speicherung der Passwörter verwendet wird.

2. LAPS-Client und Verwaltungstools installieren
Aufgabe:
Installieren Sie die LAPS-Clientsoftware und die Verwaltungstools auf den entsprechenden Systemen.

LAPS auf Domain Controller:

Führen Sie das LAPS-Setup auf einem Domain Controller aus.
Wählen Sie während der Installation die Komponenten:
AdmPwd GPO Extension (Client-Software).
LAPS Management Tools (Verwaltungstools).
LAPS auf Clients installieren:

Installieren Sie auf den Clients, die Sie verwalten möchten, die LAPS-Client-Software.
Dies kann manuell oder automatisiert (z. B. über SCCM) erfolgen.

3. Berechtigungen konfigurieren
Aufgabe:
Richten Sie die Berechtigungen für das Lesen und Ändern der LAPS-Passwörter in Active Directory ein.

Schritte:
Zugriffsrechte festlegen:

Stellen Sie sicher, dass nur autorisierte Benutzer oder Gruppen die LAPS-Passwörter lesen können.
In PowerShell führen Sie folgenden Befehl aus, um einer Sicherheitsgruppe Zugriff auf das ms-Mcs-AdmPwd-Attribut zu gewähren:


Set-AdmPwdReadPasswordPermission -OrgUnit "OU=Computers,DC=deinunternehmen,DC=com" -AllowedPrincipals "Domain Admins"
Passwortänderung zulassen:

Erlauben Sie den Computern, das Passwort in AD zu ändern:
n
Set-AdmPwdComputerSelfPermission -OrgUnit "OU=Computers,DC=deinunternehmen,DC=com"

4. Gruppenrichtlinie (GPO) einrichten
Aufgabe:
Erstellen Sie eine Gruppenrichtlinie, um die LAPS-Konfiguration auf die verwalteten Computer anzuwenden.

Gruppenrichtlinien-Management:

Öffnen Sie das Gruppenrichtlinien-Verwaltungstool (GPMC).
Erstellen Sie eine neue GPO (z. B. LAPS-Policy) oder bearbeiten Sie eine bestehende GPO.
Verknüpfen Sie die GPO mit der OU, die die Computer enthält, auf denen LAPS aktiv werden soll.
LAPS-Konfiguration:

Navigieren Sie zu: Computerkonfiguration > Richtlinien > Administrative Vorlagen > LAPS.
Aktivieren und konfigurieren Sie die folgenden Richtlinien:
Password Settings: Legen Sie die Passwortkomplexität und Länge fest (z. B. 12 Zeichen).
Name of administrator account to manage: Definieren Sie das lokale Konto, dessen Passwort verwaltet werden soll (standardmäßig Administrator).
Passwortrotation festlegen:

In der Gruppenrichtlinie können Sie auch die Häufigkeit der Passwortänderung festlegen (z. B. alle 30 Tage).
Gruppenrichtlinie aktualisieren:

Auf den Clients führen Sie einen GPO-Refresh aus:
gpupdate /force

5. Test und Verifizierung
Aufgabe:
Überprüfen Sie, ob LAPS korrekt konfiguriert ist und die lokalen Administratorpasswörter auf den Clients geändert wurden.


Überprüfung per PowerShell:

Verbinden Sie sich mit AD und führen Sie folgenden Befehl aus, um das Passwort eines bestimmten Computers abzurufen (nur für autorisierte Benutzer):

Get-AdmPwdPassword -ComputerName "Client-Computer"

Hier sollte das zufällig generierte Passwort angezeigt werden.

Lokale Passwortprüfung:
Melden Sie sich an einem Client-Computer an und prüfen Sie, ob das lokale Administratorpasswort mit dem in AD gespeicherten übereinstimmt.