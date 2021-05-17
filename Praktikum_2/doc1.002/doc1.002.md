---
author:
   name1: Abousobie, Youssef, 1312001. 1
   name2: Iliev, Ivaylo, 1287983. 2
title:
   main: Software Engineering SS 2021
   sub1: Praktikum Termin 
   sub2: Dokumentation Aufgabe 2
revision:
   doc: Dateiname
   level: 1, ab 0
   date: Datum der Version 11.05.2021
lang: de
cssextra: doc1.css
---

# TEIL I: Voruntersuchung {.unnumbered .clDocPartHeader}

# Schätzung des Aufwands

## Zusammenstellung und Klassifizierung der Elementarprozesse


### Ausgaben


+------------------------------------------------+------------------+
| Name                                           |Klassifizierung   |
+------------------------------------------------+------------------+
| Statistiken zu Stellenangeboten                |   niedrig        |             
+------------------------------------------------+------------------+
| Statistiken zu Stellengesuchen erzeugen        |   niedrig        |             
+------------------------------------------------+------------------+
| Eingang der Bewerbung wird durch eine          |  niedrig         |
| Kontaktaufnahme per EMail bestätigt            |                  |
+------------------------------------------------+------------------+
| Infromierung der OE über die Ablauf jedes      |  niedrig         |
|  Stellenangebot                                |                  |
+------------------------------------------------+------------------+
| Inforomierung der OE über die Ablauf jedes     | niedrig          |
|  Stellengesuche                                |                  |
+------------------------------------------------+------------------+
| Übergabe der Bewerbung an den ZPM              | mittel           |
+------------------------------------------------+------------------+
| Übergabe der initiative Bewerbung an den ZPM   | mittel           |
+------------------------------------------------+------------------+
| Benachrichtigung der Bewerber, dass die        | niedrig          |
| Bewerbung an der OE geleitet wird              |                  |
+------------------------------------------------+------------------+
| Übergabe der Bewerbung an den OE               | mittel           |
+------------------------------------------------+------------------+
| Übergabe der initiative Bewerbung an den OE    | mittel           |
+------------------------------------------------+------------------+
| ZPM weist die Bewerbung zurück mit einer       |  niedrig         |
| entsprechenden Benachrichtigung an den Bewerber|                  |
+------------------------------------------------+------------------+
| Einladung von OE                               | niedrig          |
+------------------------------------------------+------------------+
| bei Nichteignung wird dies per Benachrichtigung| niedrig          |
| mitgeteilt                                     |                  |
+------------------------------------------------+------------------+
| bei allen Benachrichtigungen wird auch das ZPM | niedrig          |
| informiert                                     |                  |
+------------------------------------------------+------------------+
| wenn die Bewerbung durch die OE erfolgreich    |  niedrig         |
| abgeschlossen wird, informiert die OE das ZPM  |                  |
+------------------------------------------------+------------------+
| das ZPM bietet der Person, die sich bewirbt,   | niedrig          |
| den Arbeitsplatzwechsel an                     |                  |
+------------------------------------------------+------------------+


                                          

### Abfragen
+------------------------------------------------+------------------+
| Name                                           |Klassifizierung   |
+------------------------------------------------+------------------+
| Stellengesuche recherchieren                   |    mittel        |
+------------------------------------------------+------------------+
| Stellenangebote recherchieren                  |   mittel         |
+------------------------------------------------+------------------+
| Bewerbungen recherchieren                      |   mittel         |
+------------------------------------------------+------------------+
| ZPM prüft/recherchiert für welche OE die       |  mittel          |
| initiative Bewerbung von Bedeutung sein könnte |                  |
+------------------------------------------------+------------------+


### Eingaben

+------------------------------------------------+------------------+
| Name                                           |Klassifizierung   |
+------------------------------------------------+------------------+
|  Mitarbeiter kann Stellengesuche einstellen    |   mittel         |
+------------------------------------------------+------------------+
|  Mitarbeiter kann Stellengesuche bearbeiten    |   mittel         |
+------------------------------------------------+------------------+
|  Mitarbeiter kann Stellengesuche entfernen     |   mittel         |
+------------------------------------------------+------------------+
| Bewerbung Eingeben                             |   mittel         |
+------------------------------------------------+------------------+
| Bestätigung der Arbeitswechselangebot          |   niedrig        |
+------------------------------------------------+------------------+
| Ablenhung der Arbeitswechselangebot            |   niedrig        |
+------------------------------------------------+------------------+
| Stellenangebot einstellen von OE               |   mittel         |
+------------------------------------------------+------------------+
| Stellenangebot bearbeiten von OE               |   mittel         |
+------------------------------------------------+------------------+
| Stellenangebot entfernen  von OE               |   mittel         |
+------------------------------------------------+------------------+
| nach Ablauf der Frist werden die Angebote      |   mittel         |
|  automatisch entfernt                          |                  |
+------------------------------------------------+------------------+
| nach Ablauf der Frist werden die Gesuche       |   mittel         |
|  automatisch entfernt                          |                  |
+------------------------------------------------+------------------+
| Mitarbeiter können Initiative Bewerbung        |   mittel         |
| einreichen                                     |                  |
+------------------------------------------------+------------------+
| passenden Arbeitsfeldern ermittelt für         |   mittel         |
|  initiative Bewerbung                          |                  |
+------------------------------------------------+------------------+
| erzeugt die ZPM Initiativausschreibungen       | niedrig          |
+------------------------------------------------+------------------+


## Daten

Benennen Sie Datenbestände und beschreiben Sie diese mit dem "Data-Dictionary"-Ansatz.

### Interne Datenbestände

1.Stellenangebote::=Standort/OE + #Identfikationsnummer + Arbeitsfeld +  Fachlicher Ansprechpartner + Erforderliche Abschlüsse + Erforderliche besondere Qualifikationen + Beschäftigungsumfang + tarifliche Vergütung + befristete Beschäftigung + Stellenbesetzung + Ablauf Bewerbungsfrist;

Standort/OE ::= 
	string;

Identfikationsnummer ::= 
	number;

Arbeitsfeld ::=
	 string + *Stellenbeschreibung*
	 boolean; *Führungsaufgabe*


Fachlicher Ansprechpartner  ::= 
	string + *Name* 
	string + *Funktion* 
	string;  *EMail-Adresse*



Erforderliche Abschlüsse ::= 
	{string}; *Abitur, Ausbildung, Bachelor, Master etc.*

Erforderliche Qualifikationen::=
	{string}; *Besondere Nachweise und Zertifikate*

Beschäftigungsumfang::=
	[
		number *Prozent*
		|
		number *Stunden*
	];

tarifliche Vergütung::=
	[
	number	*ja => Tarifgruppe*
	|
	string *Nein => Außertarifliche Angaben*
	];

befristete Beschäftigung ::=
	date + *Von*
	date; *Bis*


Stellenbesetzung_zum::=
	date;

Ablauf Bewerbungsfrist::=
	date; 



2.Bewerbungen::=Datum der Bewerbung + @Identifikationsnummer + Initiativbewerbung + Name + Vorname + Wohnort + Kontaktdaten + aktuelle Tätigkeit + Arbeitsfeld + Anschreiben + Lebenslauf + Zeugnisse / Abschlüsse + spezielle Qualifikationen;

	date + *Datum der Bewerbung
	number + *Identifikationsnummer*
	boolean + *Initiativbewerbung*
	string + *Name*
	string + *Vorname*
	string + *Wohnort*
	Kontaktdaten::=
		number + *Telefonnummer*
		string;  *EMail-Adresse*
	Telefon::=
		['privat'|'dienstlich'];

	aktuelle Tätigkeit::=
		string + *Standort* 
		string + *OE* 
		string;  *Arbeitsfeld*
	string + *Anschreiben*	
	string + * Lebenslauf*
	string + *Zeugnisse / Abschlüsse*
	string; *Spezielle Qualifikationen*


3.Stellengesuche::= #Identifikationsnummer + #Personalnummer + Befristung*Maximum 2 Monate* + Datum + Name + Vorname + Wohnort + Kontaktdaten + aktuelle Tätigkeit + gewünschte Tätigkeit + Abschlüsse + spezielle Qualifikationen;

	number + *Identifikationsnummer*
	number + *Personalnummer*
	date + *Befristung*
	date + *Datum*
	string + *Name*
	string + *Vorname*
	string + *Wohnort*
	Kontaktdaten::=
		number + *Telefonnummer*
		string;  *EMail-Adresse*
	Telefon::=
		['privat'|'dienstlich'];

aktuelle Tätigkeit::={Standort}+{OE}+{Arbeitsfeld}+{Beschäftigungsumfang}+{tarifliche Vergütung} + befristete Beschäftigung 
	string + *Standort*
	string + *OE*
	string + *Arbeitsfeld*
	number + *Beschäftigungsumfang*
	string + *Tarifliche Vergütung*
	date; *Befristete Beschäftigung*

gewünschte Tätigkeit::={Standort}+{OE}+{Arbeitsfeld}+{Beschäftigungsumfang}+{tarifliche Vergütung} +Beginn der Tätigkeit +Besondere Stellenwünsche
	string + *Standort*
	string + *OE*
	string + *Arbeitsfeld*
	number + *Beschäftigungsumfang*
	string + *Tarifliche Vergütung*
	string + *Abschlüsse*
	string; *Spezielle Qualifikationen*


### Referenzdaten


## Komplexität / Berechnung der unbewerteten FP

Wenden Sie die Zählregeln an und ermitteln Sie anhand der Tabelle die unbewertete Summe der FP.

+-----------------------+--------+----------------+------------+------+
| Kategorie             | Anzahl | Klassifzierung | Gewichtung | Wert |
+=======================+========+================+============+======+
| Eingaben              |   3    | einfach        |  3         | 9    |
+-----------------------+--------+----------------+------------+------+
| Eingaben              |   11   | mittel         |   4        | 44   |
+-----------------------+--------+----------------+------------+------+
| Eingaben              |   0    | komplex        |    6       | 0    |
+-----------------------+--------+----------------+------------+------+
| Ausgaben              |   12   | einfach        |    4       |  48  |
+-----------------------+--------+----------------+------------+------+
| Ausgaben              |   4    | mittel         |    5       |  20  |
+-----------------------+--------+----------------+------------+------+
| Ausgaben              |   0    |komplex         |    7       |  0   |
+-----------------------+--------+----------------+------------+------+
| Abfragen              |   0    | einfach        |    3       | 0    |
+-----------------------+--------+----------------+------------+------+
| Abfragen              |   4    | mittel         |   4        | 16   |
+-----------------------+--------+----------------+------------+------+
| Abfragen              |   0    | komplex        |  6         | 0    |
+-----------------------+--------+----------------+------------+------+
| Interne Datenbestände |   2    | einfach        |  7         | 14   |
+-----------------------+--------+----------------+------------+------+
| Interne Datenbestände |   1    | mittel         |  10        | 10   |
+-----------------------+--------+----------------+------------+------+
| Interne Datenbestände |   0    | komplex        |   15       | 0    |
+-----------------------+--------+----------------+------------+------+
| Referenzdaten         |   0    | einfach        |   5        | 0    |
+-----------------------+--------+----------------+------------+------+
| Referenzdaten         |   0    | mittel         |   7        | 0    |
+-----------------------+--------+----------------+------------+------+
| Referenzdaten         |   0    | komplex        |   10       | 0    |
+-----------------------+--------+----------------+------------+------+
| Summe                 |        |                |            | 161  |
+-----------------------+--------+----------------+------------+------+

## Berechnung der bewerteten FP

### Merkmale

(Standardwert 5, d.h. ohne Bedeutung / für alle Merkmale einen Wert zwischen 0 und 10 angeben)

+--------------------------------------------------------+----------+-----------------------------------------------+
| Merkmal                                                | Wert     |     Begründung                                |
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M1) Komplexe Verarbeitung                             |   5      |Die Funktionalität der Application ist nicht   | 
|                                                        |          |sehr hoch.Wegen der Größe des Unternehmens und |
|                                                        |          |die Anzahl der OEs                             | 
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M2) Begrenzte Kapazität                               |   9      |Die Kapazität muss nicht begrenzt werden.      |
|                                                        |          |                                               |
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M3) Transaktionsrate                                  |    8     |Die Anwendung muss von viele Benutzer          |
|                                                        |          |gleichzeitig benutzt werden.                   |
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M4) Benutzerfreundlichkeit                            |    10    |Das ist einer der wichtigste Aspekte. Die      |
|                                                        |          |DSB muss leicht von jedem Mitarbeiter in der   | 
|                                                        |          |Unternehmen genutzt werden                     |
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M5) Flexibilität                                      |    7     |Die Application muss auf verschidene Geräte wie|
|                                                        |          |Computern oder Händys verwendbar werden        |
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M6) verteilte Verarbeitung (Aufteilung der Anwendung) |    10    |Die verschieden Zielgruppen haben verschidene  |
|                                                        |          |Rechte bei dem Zugriff der DSB, deswegen ist der|
|                                                        |          |Aufwand hoch.                                  |
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M7) Datenkommunikation (mit Nachbarsystemen)          |    10    |Die DSB muss von verschidene Systeme und       |
|                                                        |          |Zielgruppen verwendet werden                   |
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M8) Portierbarkeit                                    |    1     |Die Application ist nur von den Server des     | 
|                                                        |          |Unternehmens abhängig und die Portierbarkeit ist 
|                                                        |          |gering.                                        |
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M9) Änderungsfreundlichkeit (Konstruktion auf A. hin) |    5     |Die Funktionalität der Anwendung ist nich sehr |
|                                                        |          |kompliziert.Es ist möglich Aktualisierungen des|
|                                                        |          |Systems zu machen, aber keine grunsetzlichen   |
|                                                        |          |Veränderungen werden gemacht.                  |
+--------------------------------------------------------+----------+-----------------------------------------------+
| (M10) Wiederverwendbarkeit                             |    4     |Die Anwendung muss immer zur Verfügung stehen. |
|                                                        |          |Trotzdem liegt der Fokus der DSB nicht im      |
|                                                        |          |Wiederverwendbarkeit                           |
+--------------------------------------------------------+----------+-----------------------------------------------+
| TDI = Summe der Werte                                  |    69    |
+--------------------------------------------------------+----------+




### VAF / bewertete Function-Points

VAF berechnen:

- VAF = (TDI * 0.01) + 0.5
VAF=(69 *0.01)+0.5= 1,19


bewertete Function-Points:

- bFP = VAF * FP
bfP=161 * 1,19= 191,59

## Ermittlung Personalaufwand, Bearbeitungsdauer, Kosten

Zur Abschätzung des Entwicklungsaufwands in Personenmonaten gibt es in der Literatur u.a. folgende Formel:

- Aufwand (Personenmonate) = bFP^1.4^ / 150 => 191,59 ^1.4^ / 150 = 10,45

1.Bearbeitungszeitraum

Wasserfallmodell:

Anforderung:1 Monate

Entwurf:5 Monate

Implementation:4 Monate

Überprüfung: 6 Monate

Wartung: 2 Monate

Die Überprüfung und der Entwurf werden die zeitaufwendigsten Phasen während der Bearbeitung sein. Der Grund dafür ist der große Aufwand bei der Benutzerfreunldichekeit, Datenkommunikation und verteilte Verarbeitung, was zur langsame Bearbeitung von viele Daten auf einmal führen kann. Bei dem Entwurf braucht man gute und effiziente Planung zu erstellen für den Datenaustausch und die Kommunikation zwischen DSB ,ZPM und OE. Falls Der Entwurf gut ist , werden die IT-Ingenieure nicht so viel Zeit bei der Implementation verschwenden , weil die Funktionalität der Stellenbörse nicht so kompliziert ist. Die geringste Zeitumfang haben die Anforderungen und die Wartung. 

2.Kosten
Kosten=Anzahl der OE * 3 Techniker jeder mit Gehalt von 5000 Euro.

Erstellung der Application:40 000 - 100 000 Euro.
Der Grund dafür ist die Größe des Unternehmens, die in verschiedenen
Standorten verteilt ist.Außerdem existieren zahlreiche OE pro Standort, was zur größere Datenbanken und langsame bearbeitung der Information führt.
Die Komplexität der Funktionalität der Stellenbörse kann man als niedrig Bezeichnet.Deswegen ist der obere Grenzung für den Budget 100 000 Euro.
Die meisten Kosten werden für die Erstellung der Ablauf Beziehung zwischen DBS,ZPM und OE in der verschiedenenen Standorten, was zur aufwendige Bearbeitung der Datenbanken führt.   

Gemeinsame Kosten:120 000 - 200 000 Euro.


# TEIL II: Anforderungsanalyse {.unnumbered .clDocPartHeader}

# Zielbestimmung

Ziel der Software ist es, die Erleichterung nicht nur für die Organisationseinheiten , sondern auch für die in der Untenhemen beschäftigte Mitarbeieter bei einem Arbeitsplatzwechsel. Für das Unternehmen bietet die Application die Möglichkeit nicht mit den selben Mitarbeiter ,deren Qualifizierungen schön bekannt sind, wiederzuarebiten. Auf diese Weise werden die Kosten und die Zeitaufwand bei der Suche nach neue Mitarbeiter verringert.Aus der Seite der Mitarbeiter bietet die digitale Stellenbörse auf die gewünschte Position in der Unternehmen zu arbeiten, was zur Zeitaufwand bei der einer Suche außer der Firma sparren kann.

# Produkt-Einsatz

## Anwendungsbereiche

Der in den Untenhemen beschäftigten Mitarbeiter kann sich , um eine Arbeitsstellen bewerben/initiativ bewereben und nach Stellengesuche recherchieren.

Die digitale Stellenbörse steht  auch zur Verfügung der zentralen Personalmanagement die einegehende Bewebungen zu Überprüfen.

Die Organisationseinheiten stellen Angeboten in der digitalen Stellenbörse ein. Sie können auch Benachrichtigungen bei einer Eignung oder Nichteignung einer Bewerbung zu den ZPM senden. 

## Zielgruppen

Die Zeilgruppen sind jeder in dem Unternehemen beschäftigten Mitarbeiter und die Organisationseinheiten.Die Akteure des Systems bestehen aus dem Zielgruppen und den zentralen Personalmanagament.

Für die Organisationseinheiten bietet die digitale Stellenbörse die Möglichkeit nach Mitarbeiter zu suchen ,indem sie Stellenangeboten in das Application eingeben.

Mit der Hilfe des Systems können die in der Unternehmen beschäftigte Mitarbeiter ihren Arbeitsplatzwechsel ermöglichen, indem sie nicht in einem anderen Unternehemen suchen müssen.

Die zentrale Personalmanagament führt zu einer Überprüfung der Bewerbung im Bezug darauf, ob eine Bewerbung den Kriterien entspricht und benachrichtigt der Bewerber mit dem Zustand der Bewerbung. 

## Betriebsbedingungen

Die Software muss zur Verfügung sein und kann viele Bewerbungen auf einmal zu bearbeiten/aufnehmen, indem das Datenbanksystem die benötige Einstellungen und Speicherkapazität hat. Der Grund dafür ist die Größe des Unternehmens,das in verschidenen Standorten verteilt ist. 

Nicht alle in dem Unternehmen beschäftigten Mitarbiter haben zu jeder Information Zugriff. Zum Beispiel nur ZPM beschäftigten Personen können Statistiken zu Stellenangeboten und Stellengesuchen erzeugen. Das bedeutet ,dass für jede Nutzergruppe eine benutzerfreundliche Application-Software mit dem bestimmten Zugriffsrechte vorgesehen wird.

# Produkt-Umgebung

## Software

Die Software muss eine benutzerfreundlichen Frontend für die Nutzer haben, damit die verschiedene Nutzergruppen leichtere Zugriff auf die Funktionalitäten der digitalen Stellenbörse haben können.Die Application muss nicht nur auf einem Computer, sondern auch auf einem Handy funktionieren. Alle Nutzern des digitalen Stellenbörse müssen ein Account und Zugriff auf dem  Intranet des Unternehmens besitzen. Für die Realisierung wird eine NoSQL-Datenbank, was die im Vergleich zu den SQL-Datenbank größere Performance,Skalierbarkeit und Flexibilität bietet.

## Hardware

Zum Speicherung der verschiedene Informationsarten muss ein Datenbankserver vorhanden sein. Datenbankserver ist ein zu dem Netzwerk des Unternehmens vernetzte Computer , das für die Speicherung von Datenbanken und das Abrufen von Daten aus der Datenbank vorgesehen ist. Für jeden Standort des Untenehmens werden  mindestens ein Server ist vorgesehen.Die Gründe dafür sind sowohl die Größe des Untenehmens als auch die Verwendung von NoSQL-Datenbank ,was mehere Datenbaken benötigt.Jeder von der Nutzergruppen muss ein PC zur Verfügung haben, der nicht nur zu dem Intranet des Untenhemens angeschlossen ist, sondern auch genug Leistungsfähigkeiten für die Ausführung der veschiedene Funktionalitäten hat.

# Funktionale Produkt-Anforderungen



## Anwendungsfälle

![Alt text](C:/Users/ivayl/Desktop/4.Semester/SWE/Praktikum_2/Use_case(1.4).jpg?raw=true "Title")


&nbsp;
&nbsp;



+----------------------+-----------------------------------------------------------------------------+
|     Bezeichnung      |                        Stellenangebote recherchieren                        |
+======================+=============================================================================+
| Ziel                 | Aussuche nach Stellenangebote                                               |
+----------------------+-----------------------------------------------------------------------------+
| Akteure              | In dem Unternehmen beschäftigte Person, ZPM                                 |
+----------------------+-----------------------------------------------------------------------------+
| Auslösendes Ereignis | Suchen nach Stellenangebote von Mitarbeiter in der Untenehmen wegen Wunsch  |
|                      |  nach Arbeitsplatzwechsel                                                   |
+----------------------+-----------------------------------------------------------------------------+
| Vorbedingung         | Stellenangebote müssen schon von OE in der DSB eingestellt werden           |
+----------------------+-----------------------------------------------------------------------------+
| Nachbedingung        | keine                                                                       |
+----------------------+-----------------------------------------------------------------------------+
| Kategorie            | optional                                                                    |
+----------------------+-----------------------------------------------------------------------------+
| Beschreibung         | In dem Unternehmen beschäftigte Person sucht nach Stellenangebot            |
+----------------------+-----------------------------------------------------------------------------+

&nbsp;
&nbsp;




+----------------------+-----------------------------------------------------------------------------+
|     Bezeichnung      |                        Bewerben/initiative Bewerbung einreichen             |
+======================+=============================================================================+
| Ziel                 | Eine  Bewerbung in DSB schicken                                             |
+----------------------+-----------------------------------------------------------------------------+
| Akteure              | In dem Unternehmen beschäftigte Person                                      |
+----------------------+-----------------------------------------------------------------------------+
| Auslösendes Ereignis | Bewerber veruscht seine Arbeitsposition in dem Unternehmen zu wechseln durch| 
|                      | Bewerbung für bestimmte Stellenangebot in der digitalen Stellenbörse        |
+----------------------+-----------------------------------------------------------------------------+
| Vorbedingung         |  Stellenangebot für die bestimmte Arbeitsplatz muss schon in DSB eingestellt|
|                      |  sein                                                                       |
+----------------------+-----------------------------------------------------------------------------+
| Nachbedingung        | Anzahl der Bewerbung in der digitale Stellenbörße nimmt zu.                 |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Kategorie            | primär                                                                      |
+----------------------+-----------------------------------------------------------------------------+
| Beschreibung         | In dem Unternehmen beschäftigte Person schickt eine Bewerbung in der DSB    |
+----------------------+-----------------------------------------------------------------------------+
&nbsp;
&nbsp;








+----------------------+-----------------------------------------------------------------------------+
|     Bezeichnung      |                        Stellengesuche recherchieren                         |
+======================+=============================================================================+
| Ziel                 | Suche von Stellengesuche                                                    |
+----------------------+-----------------------------------------------------------------------------+
| Akteure              | In dem Unternehmen beschäftigte Person                                      |
+----------------------+-----------------------------------------------------------------------------+
| Auslösendes Ereignis | Ausgabe den Stellengesuche ,die den Kriterien der Suchende entsprechen      | 
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Vorbedingung         | Stellenangebote müssen schön von OE in der DSB eingestellt werden           |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Nachbedingung        | keine                                                                       |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Kategorie            | sekundär                                                                    |
+----------------------+-----------------------------------------------------------------------------+
| Beschreibung         | In der Unternehmen beschäftigte Person such nach eine Stellengesuche in der |
|                      |  DSB                                                                        |
+----------------------+-----------------------------------------------------------------------------+
&nbsp;
&nbsp;








+----------------------+-----------------------------------------------------------------------------+
|     Bezeichnung      |                        formalen Prüfung leiten                              |
+======================+=============================================================================+
| Ziel                 | Betsätigung, ob eine Bewerbung passend zu bestimmtem Stellenangebot ist.    |
+----------------------+-----------------------------------------------------------------------------+
| Akteure              | ZPM,OE                                                                      |
+----------------------+-----------------------------------------------------------------------------+
| Auslösendes Ereignis | Die Bestätigung für den Eingang der Bewerbung bei ZPM                       |
+----------------------+-----------------------------------------------------------------------------+
| Vorbedingung         | Eine Bewerbung mussen schön in der DSB geschickt werden.                    |
+----------------------+-----------------------------------------------------------------------------+
| Nachbedingung        | Anzahl der abgeschlossene Bewerbungen in der digitalen Stellenbörße steigt. |
+----------------------+-----------------------------------------------------------------------------+
| Kategorie            | primär                                                                      |
+----------------------+-----------------------------------------------------------------------------+
| Beschreibung         | Die ZPM und/oder OE überprüft ob eine Bewerbung passend zu den              |
|                      | Stellenangebot ist                                                          |
+----------------------+-----------------------------------------------------------------------------+

&nbsp;
&nbsp;






+----------------------+-----------------------------------------------------------------------------+
|     Bezeichnung      |                        Benachritigung schicken                              |
+======================+=============================================================================+
| Ziel                 | Bewerber,OE oder ZPM wird für den Status einer Bewerbung informiert         |
+----------------------+-----------------------------------------------------------------------------+
| Akteure              | ZPM,OE,in der Untenhemen beschäftigte Person                                |
+----------------------+-----------------------------------------------------------------------------+
| Auslösendes Ereignis |Aktualisierung über Status einer Bewerbung                                   |
+----------------------+-----------------------------------------------------------------------------+
| Vorbedingung         | Eine Bewerbung mussen schön in der DSB geschickt                            |
+----------------------+-----------------------------------------------------------------------------+
| Nachbedingung        | keine                                                                       |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Kategorie            | primär                                                                      |
+----------------------+-----------------------------------------------------------------------------+
| Beschreibung         |Nach jede Aktualisierung über Status einer Bewerbung(z.B der Eingang oder    |
|                      |Einladung) werden Benachrichtungen zwischen die Akteure ausgetauscht         |
+----------------------+-----------------------------------------------------------------------------+


&nbsp;
&nbsp;







+----------------------+-----------------------------------------------------------------------------+
|     Bezeichnung      |                      Stelleneingebote verwalten                             |
+======================+=============================================================================+
| Ziel                 |Stellenangebot wird eingestellt ,bearbeitet oder entfernt                    |
+----------------------+-----------------------------------------------------------------------------+
| Akteure              | OE                                                                          |
+----------------------+-----------------------------------------------------------------------------+
| Auslösendes Ereignis |OE kann Status und Anzahl der Stellenangeboten beeinflussen                  |
+----------------------+-----------------------------------------------------------------------------+
| Vorbedingung         |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Nachbedingung        | Die Anzahl der Stellenangeboten in DSB nimmt zu/ab oder Status              |
|                      | wird aktualisiert                                                           |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Kategorie            | primär                                                                      |
+----------------------+-----------------------------------------------------------------------------+
| Beschreibung         | Verwaltung der Setllenangebote im Bezug auf die Kriterien und Interessen    |
|                      | der Organisationseinheit                                                    |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+



&nbsp;
&nbsp;






+----------------------+-----------------------------------------------------------------------------+
|     Bezeichnung      |  Statistiken zu Stellenangeboten und Stellengesuchen zugreifen               |
+======================+=============================================================================+
| Ziel                 |Erzeugung von graphische Darstellungen der Stellenangeboten und Stellengesuchen|
+----------------------+-----------------------------------------------------------------------------+
| Akteure              | ZPM                                                                         |
+----------------------+-----------------------------------------------------------------------------+
| Auslösendes Ereignis | Personen,die im ZPM arbeiten,suchen nach graphische Darstellungen der       |
|                      | Stellenangeboten und Stellengesuche sehen.                                  | 
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Vorbedingung         | Stellenangebote und Stellengesuche müssen schön in DSB vorhanden sein       |
+----------------------+-----------------------------------------------------------------------------+
| Nachbedingung        | keine                                                                       |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Kategorie            | sekundär                                                                     |
+----------------------+-----------------------------------------------------------------------------+
| Beschreibung         | Statistiken und graphische Darstellung zur Veranschaulichung von der        |
|                      | Stellenangeboten und Stellengesuchen in Unternehme der Ergebnisse werden    |
|                      | erzeugt.                                                                    |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+

&nbsp;
&nbsp;


+----------------------+-----------------------------------------------------------------------------+
|     Bezeichnung      |  Bewerbungen recherchieren                                                  |
+======================+=============================================================================+
| Ziel                 | Suchen von Bewerbungen                                                      | 
+----------------------+-----------------------------------------------------------------------------+
| Akteure              | ZPM                                                                         |
+----------------------+-----------------------------------------------------------------------------+
| Auslösendes Ereignis | Information über die Zustand von den                                        |
|                      | Bewerbungen in der DSB kriegen                                              | 
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Vorbedingung         | Bewerbungen müssen schön im DSB vorhanden sein                              |
+----------------------+-----------------------------------------------------------------------------+
| Nachbedingung        | keine                                                                       |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
| Kategorie            | primär                                                                      |
+----------------------+-----------------------------------------------------------------------------+
| Beschreibung         | Mitarbeiter der ZPM informieren sich über die Zustand der verschieden       |
|                      | Bewerbungen                                                                 |
|                      |                                                                             |
+----------------------+-----------------------------------------------------------------------------+
&nbsp;
&nbsp;







## Sonstige Anforderungen

Nach bestimmte Zeit müssen die Stellenangeboten und die Stellengesuche automatisch aus der digitalen Stellenbörse entfernt werden.

Alle in dem Untenehmen beschäftigten Personen müssen Zugriff auf die digitale Stellenbörse haben.

