============
Installation
============

So instalieren sie SSP Schritt für Schritt



1. Schritt: IIS einrichten
	1.1 Server Manager/Dashboard öffnen
	1.2 Rollen und Features auswählen
	1.3 Rollenbasierte oder featurebasierte Installation auswählen
	1.4 Einen Server aus dem Serverpool auswählen (hier den gewünschten Server auswählen
	1.5 Webserver (IIS) auswählen und Feature hinzufügen
	1.6 weiter auswählen
	1.7 Rollendienste auswählen
		1.7.1 Sicherheit --> Windows-Authenfizierung ein Haken setzen
	1.8 weiter auswählen
	1.9 Bestätigung --> dort installation auswählen
	1.10 IIS Server wird nun instaliert. Bitte haben sie Geduld
	1.11 schließen auswählen
	Hinweiese zu Schritt 1: Eventuell wird ein Neustart des Servers benötigt damit die Feature funktionieren

2.Schritt Host-Bundle
	2.1 folgenden Link bitte auswählen "https://download.visualstudio.microsoft.com/download/pr/633b17e5-a489-4da4-9713-5ddedf17a5f0/5c18f4203e837dd90ba3da59eee92b01/dotnet-hosting-2.1.15-win.exe" und das Host bundle herunterladen für Windows
	2.2 Host-Bundle instalieren

3.Schritt Site erstellen
	3.1 Öffnen Sie nun den Internetinformationsdienstserver
	3.2 Navigieren Sie in der Baumansicht auf Ihren Computernamen und klappen sie die untergeordnete Baumstruktur auf und führen ein Rechtsklick auf "Sites" aus um eine Website hinzu zu fügen
	3.3 Füllen Sie nun folgende Eingabefelder aus um eine Site zu erstellen:
		3.3.1 Sitename
		3.3.2 Physischer Pfad
		3.3.3 optional sind:
		3.3.3.1 Typ
		3.3.3.2 IP-Adresse 
		3.3.3.3 Port
		3.3.3.4 Hostname
	3.4 Bestätigen sie die Erstellung ihrer Website indem Sie Ok auswählen.
	
4.Schritt Zertifikat
	4.1 Ist ein Zertifikat vorhanden gehen sie zu Schritt 5
	4.2 Je nach Richtlinie wenden sie sich an ihren Systemadministrator und lassen sich ein Zertifikat anfertigen.
	4.3 sofern keine Richtline vorhanden sind wird ein SelfSignedCertificate erstellt.
	4.4 öffnen sie PowerShell ISE
	4.5 geben sie folgenden Command in PowerShell ISE ein:
	4.6 New-SelfSignedCertificate -DnsName "DomainName" -CertStoreLocation "Cert:\LocalMachine\My"
	4.7 sobald der Befehl ausgeführt wurde wird in der Konsole eine Ausgabe mit einem Thumbprint angezeigt
	4.8 Um das Zertifikat zu überprüfen, drücken Sie "R" +"Win-Taste" und geben Sie "mmc" Ein.
	4.9 Klicken Sie dort in sich öffnenden Fenster auf: Datei --> Snap-In hinzufügen/entfernen
	4.10 Nun fügen sie von den verfügbaren Snap-In`s Zertifikate aus und klicken Sie auf hinzufügen, dann erscheint ein Fenster bei dem Sie Computerkonto auswählen und klicken auf weiter.
	4.11 anschließend Lokalen Computer ausgewählt lassen und anschließend auf Fertig stellen drücken.
	4.12 Das Fenster mit OK bestätigen
	4.13 Nun haben Sie im Konsolenstamm Zertifikate hinzugefügt
	4.14 Navigieren Sie in der Baumansicht zu Konsolenstamm/Zertifikate/Eigene Zertifikate/Zertifikate
	4.15 Dort sehen sie nun ihr eben selbst erstelltes Zertifikat
	4.16 Führen Sie auf diesem Zertifikat ein Rechtsklick aus und zeigen Sie mit dem Mauszeiger auf Alle Aufgaben --> und klicken Sie auf Private Schlüssel verwalten
	4.17 Klicken Sie auf hinzufügen
	4.18 Dort geben in dem Eingabefeld folgendes ein: IIS AppPool\IhrApplicationspool name
	4.19 Überprüfen Sie ob der der Name richtig ist indem Sie auf "Name überprüfen" klicken.
	4.20 Sollte der Name richtig sein klicken Sie auf ok. Ist dies nicht der Fall wenden Sie sich an Ihren Systemadministrator.
	4.21 Klicken Sie auf übernehmen
	4.22 Mit OK bestätigen
	#4.16 mit einem Doppelklick öffnen sie die Zertifikatseigenschaften und navigieren sie zum Reiter "Details"
	#4.17 am Ende der Liste finden Sie nun den Fingerabdruck, welcher im Schritt XYZ benötigt wird.
	
5.Schritt Firewallregel einfügen
	5.1 Falls nötig richten Sie eine Windows-Firewallfreigabe ein für den von Ihnen genutzten Port.
	5.2 Wenn dies nicht benötigt wird Überspringen Sie den Schritt.
	5.3 Bei Fragen zu dem 5. Schritt wenden Sie sich an Ihren Systemadministrator

6.Schritt Datenbank Server anlegen
	6.1 Instalieren Sie ein Datenbank-Server
	6.2 Nehmen Sie zur hilfe folgenden Link: https://docs.microsoft.com/de-de/sql/database-engine/install-windows/install-sql-server?view=sql-server-ver15
	6.3 Falls eine Datenbank vorhanden ist überspringen Sie Schritt 6
	
7.Schritt Bereitstellung von SelfServicePortal
	7.1	SelfServicePortal herunterladen
	7.2 SelfServicePortal in den Applikationspool einfügen
	7.3 config.json im www.root Ordner anpassen.
	7.4 appsettings.json anpassen
	7.4.5 Thumbprint aus Schritt #4.16 einfügen in rsathumbprint
	7.5 web.config anpassen
	7.6 Einstellung im ISS überprüfen, sowie evtl. Veränderung auf der IIS-Site vornehmen
	7.6.1 Anonmye und Windows-Authenfizierung müssen aktiviert sein.
	
8.Schritt Website starten
	8.1 zu der von Ihnen angegeben Website navigieren und überprüfen ob Sie sich mit einem Windows-Nutzer der Domnäne anmelden können

9.Schritt FAQ
	9.1 Falls nötig den Windows-Server in eine vorhanden Domäne einfügen oder selbst den Server zu einen Domän-Controller aufwerten.
	

	
	
	
	
		
	
	
