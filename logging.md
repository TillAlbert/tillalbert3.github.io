---
layout: default
published: true
---



## General

Logger is a PL/SQL logging and debugging framework.

## Step-by-step guideDownload der Software
https://github.com/OraOpenSource/Logger/tree/master/releases
Download the latest Version and unzip the file.


Installation via SQL*plus
Startet die Eingabeaufforderung (console) bei Windows oder den Terminal bei Linux/Mac.

img1

Navigiert euch mit dem Kommando "cd" (Change Directory) zu der entpackten Datei.
z.B.: cd Users\<username>\Downloads\logger_3.1.0 


Verbinden mit SQL*plus als sysdba oder als User mit sysdba-Rechten, in welcher das Framework installiert werden soll.
z.B.: sqlplus usr/pass@hostname.network:port/remote_service_name



In diesem How-To wird die sichere Variante (sicher = extra Schema) bevorzugt.
1.Es ist später einfacher zu warten für die DBAs
2.Das Schema einfach gesperrt werden und das Framework ist nicht mehr aktiv
 (alter user <username> account lock;)


Ausführen des create_user.sql script. Dies legt ein neues Schema für das Framework an.
@create_user.sql
(Diese direkte Ausführung des Scripts ist nur möglich, wenn man SQL*plus direkt aus dem gleichen Ordner aufruft.)

In den Klammern stehen die Default Werte.  !! Das Passwort wird bei Eingabe nicht angezeigt
Automatischer Disconnect erfolgt.


Einloggen im erstellten Schema.


Ausführen des logger_install.sql script.
Mit der Ausführung hat man die Tabellen für das Speichern der Logs installiert.




Für die Nutzung des Loggers in anderen Schema müssen Grants verteilt werden.
Dafür wird das Script grant_logger_to_user.sql benutzt.
(Dies findet ihr im Unterordner /Scripts)


Enter value for 1: User angeben, der das Framework Logger benutzen darf/soll


Verbindung trennen und mit dem User aufbauen an den der Grant aus dem oberen Schritt vergeben wurde.
Ausführen des create_logger_synonyms.sql script.
@scripts/create_logger_synonyms.sql

Enter value for 1: !!! Schema wo der Logger installiert ist


!! Der Logger ist installiert !!

Logger Installiert?
Einloggen mit dem User der Grant vom Logger hat.

SELECT * FROM logger_logs;

Ihr solltet 2 Eintrage haben wie im Bild



Logger API Manual 
Developer Guide

Best practices

Code examples

Links for further information and details:
...
