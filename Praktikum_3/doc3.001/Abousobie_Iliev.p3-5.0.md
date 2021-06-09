---
author:
   name1: Abousobie, Youssef, 1312001. 1
   name2: Iliev, Ivaylo, 1287983. 2
title:
   main: Software Engineering SS 2021
   sub1: Praktikum Termin 
   sub2: Dokumentation Aufgabe 3
revision:
   doc: Dateiname
   level: 1, ab 0
   date: Datum der Version 07.06.2021
lang: de
cssextra: doc1.css
---

**Beachten Sie die Anforderungen an die Dokumentation in der Aufgabenstellung**

# Allgemeine Beschreibung

Für die Implementation der digitalen Stellenbörße wird eine REST API Application aufgebaut. REST API bietet die Verwendung von den HTTP Portocol. Dies bedeutet, dass Entwickler beim Erstellen einer REST-API keine zusätzliche Software oder Bibliotheken installieren müssen.Danach wird eine Antwort vom Server in Form einer Ressource zurückgegeben, die etwas wie HTML, XML, Image oder JSON sein kann.Im bezug darauf sind verschiedenen Komponenten vorgesehen. Die Frontend Komponente besteht aus drei Unterkomponenten: Mitarbeiter, ZPM und OE,die auch als Akteuere bezeichnet werden können. Nachher kommt de Komponent API der aus der unterkomponenten Export und Impoer besteht. Dieser Komponent dient , als Schnittstelle zwischen den Backend und Frontend. Dann wird die Information an den Datenbank Komponent übergeben, der aus OE_DB,ZPM_DB,Mitarbeiter_DB,Bewerbungen,Stellengesuche und Stellenangebote besteht.  

# Systemstruktur

## Komponentendiagramm

![Alt text](C:/Users/ivayl/Desktop/4.Semester/SWE/Praktikum_3/Component_diagram(1).jpg?raw=true "Title")



Die Komponente OE,ZPM und Mitarbeiter werden als den Frontend des Systems bezeichnet. Die Api ist aufgebaut aus zwei Hauptkomponenten: Eingaben und Ausgaben, die die internen bzw. externen Schnittstellen representieren. Für die Export-Schnittstellen werden GET-Abfragen verwendet. Die Internne-Schnittstellen werden durch die POST-Request implementiert. Damit jede Abfragen die eine bestimmete Funktionalität ausführen kann wird in der Server Method-Dispatching implementiert. Die Abgfragen werden nachcher nach dem geignete Klasse überleitet ,wo sie auch bearbeitet wird. Nach der Bearbeitung werden entweder Information in der Datenbank gespeichert ,oder Information entnohmen.

## Komponenten

![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\bewerbung_class.jpg?raw=true "Title")

&nbsp;

### class Bewerbung

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|listeBewerbungenDB()                     | list listeBewerbungenDB(BewerbungForm b)| Liste mit den Bewerbungen zurückgeben                      |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungEingebenDB(Partner)             |void bewerbungEingebenDB(Partner p)      | Bewerbung(Form) einfügen                                   |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|ermittlungPassendeArbeitsfeldernfürInitia| string ermittlungPassendeArbeitsfelder  |Ermittlung von Arbeitsfledern für Initiative Bewerbung      |
|tiveBewerbungDB(BewerbungForm b)         |nfürInitiativeBewerbungDB(BewerbungForm  |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|initiativausschreibungenErzeugenDB       |string initiativausschreibungenErzeugenDB| Ermittlung initiative Ausschrebungen erzeugen              |
| (BewerbungForm):string                  |(BewerbungForm)                          |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungZustandAktualisieren            |void bewerbungZustandAktualisieren       | Zustand der Bewerbung aktualisieren                        |
|(BewerbungForm)                          |(BewerbungForm)                          |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| benachrichtigungZustand                 | string benachrichtigungZustand          | Benachrichtigung über den Zustand von Bewerbung            |                     
|(benachrichtigung:string)                |(benachrichtigung:string)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+                 
 
&nbsp;
     
### struct Bewerbung
                                                                                         
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|bewerbungEingeben                        | void bewerbungEingeben(Atribute a)      | Eingabe der Bewerbungsform und ihre Atributte              |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungZustandAktualisieren            |void bewerbungZustandAktualisieren       | Zustand der Bewerbung aktualisieren                        |
|                                         |(zustand:string)                         |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+

&nbsp;

Atribute a={
datum:date,
indnum:int,
initiativbew:boolean,
name:string,vorname:string,
wohnort:string,
telefondienst:int,
telefonpriv:int,
emailDienst:string,
emailPriv:string,
standort:string,
oe:string,
arbeitsfeld:string,
anschreiben:string,
lebenslauf:string,
zeugnise:string,
abschlüsse:
string,
spezQualifikationen:string
}

![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\stellengesuche_class.jpg?raw=true "Title")

### class Stellengesuche
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|listeStellengesucheDB                    |list listeStellengesucheDB               |                                                            |
|                                         |(BewerbungForm b)                        | Liste mit den Stellengesuche zurückgeben                   |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|erzeugenStatistikenStellengeuscheDB      |list<Integer>                            | Statistiken für Stellengesuche erzeugen                    |
|                                         |erzeugenStatistikenStellengeuscheDB      |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellengesucheZustandAktualisieren       |void stellengesucheZustandAktualisieren  | Zustand der Stellengesuche aktualisieren                   |
|                                         |(StellengesucheFrom)                     |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellengesucheEinstellenDB               | void stellengesucheEinstellenDB         | Stellengesuche(Form) einfügen
|                                         | (StellengesuchForm)                     |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellengesucheEntfernenDB                | void stellengesucheEntfernenDB          | Stellengesuche löschen                                     |
|                                         | (StellengesucheForm)                    |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellengesucheBearbeitenDB               | void stellengesucheBearbeitenDB         | Stellengesuche bearbeiten/aktuelisieren                    |
|                                         | (StellengesucheForm)                    |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| benachrichtigungZustand                 | string benachrichtigungZustand          | Benachrichtigung über den Zustand von Stellengesuche       |                     
|(benachrichtigung:string)                |(benachrichtigung:string)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+       

&nbsp;

### struct Stellengesuche
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|stellengesucheEinstellen                 | void stellengesucheEinstelle(Atribute a)| Eingabe der Stellungsgesucheform und ihre Atributte        |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangesucheEntfernen()              |void stellenangesucheEntfernen()         | Entfernung der einzelnen Stellengesuche                    |
|                                         |                                         |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangesucheBearbeiten               |void stellenangesucheBearbeiten          | Bearbeitung der einzelnen Stellengesuche                   |
|                                         |(Atribute a)                             |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangesucheZustandAktualisieren     |void stellenangesucheZustandAktualisieren| Zustand der einzelnen Stellengesuche aktualisieren         |
|                                         |(string zustand)                         |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+

Atribut a={

standort:string,
oe:string,
indnummmer:int,
stellenbeschreibung:sting,
führungsaufgabe:boolean,
ansprechpartnerName:string ,
ansprechpartnerFunktion:string,
ansprechpartnerEmail:string,
erforderlicheAbschlüsse:string,
erfolgreicheQualifikationen:string,
bschäftigungsUmfang:date,
tariflicheVergütung:boolean,
befristiteBeshcäftigungVon:date,
befristiteBeshcäftigungBis:date,
#stellenBesetzung:date,
ablaufBewerbefrist:date

}


![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\stellenangebot_class.jpg?raw=true "Title")


### class Stellenangebot

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|listeStellenangebotDB                    |list listeStellenangebotDB               |                                                            |
|                                         |(BewerbungForm b)                        | Liste mit den Stellenangebot zurückgeben                   |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|erzeugenStatistikenStellenangebotDB      |list<Integer>                            | Statistiken für Stellenangebot erzeugen                    |
|                                         |erzeugenStatistikenStellenangebotDB      |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangebotZustandAktualisieren       |void stellenangebotZustandAktualisieren  | Zustand der Stellenangebot aktualisieren                   |
|                                         |(StellengesucheFrom)                     |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangebotEinstellenDB               | void stellenangebotEinstellenDB         | Stellenangebot(Form) einfügen                              |
|                                         | (StellengesuchForm)                     |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangebotEntfernenDB                | void stellenangebotEntfernenDB          | Stellenangebot löschen                                     |
|                                         | (StellengesucheForm)                    |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangebotBearbeitenDB               | void stellenangebotBearbeitenDB         | Stellenangebot bearbeiten/aktuelisieren                    |
|                                         | (StellengesucheForm)                    |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| benachrichtigungZustand                 | string benachrichtigungZustand          | Benachrichtigung über den Zustand von Stellenangebot       |                     
|(benachrichtigung:string)                |(benachrichtigung:string)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+       

&nbsp;

### class Stellenangebot

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|stellenangebotEinstellen                 | void stellenangebotEinstelle(Atribute a)| Eingabe der Stellungsangebot form und ihre Atributte       |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenanangebotEntfernen()              |void stellenangebotEntfernen()           | Entfernung der einzelnen Stellenangebot                    |
|                                         |                                         |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangebotBearbeiten                 |void stellenangebotBearbeiten            | Bearbeitung der einzelnen Stellenangebot                   |
|                                         |(Atribute a)                             |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangebotZustandAktualisieren       |void stellenangebotZustandAktualisieren  | Zustand der einzelnen Stellenangebot aktualisieren         |
|                                         |(string zustand)                         |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+



![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\mitarbeiter_class.jpg?raw=true "Title")


### class Mitarbeiter

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|stellenangeboteRecherschieren            |list<Stellenangebot>                     | Rechersche von Stellenangebote durch Eingabe einer Form    |
|                                         |stellenangeboteRecherschieren(           |                                                            |
|                                         | StellenangebotForm)                     |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungÜbergabe                        | BewerbungForm bewerbungÜbergabe         | Bewerbung(Form) übergeben                                  |
|                                         |(BewerbunfForm)                          |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungRecherschieren                  | list<BewerbungFrom>                     | Rechersche von Bewerbungen durch Eingabe einer Form        |                                                   |
|                                         | bewerbungRecherschieren                 |                                                            |
|                                         | (BewerbungForm)                         |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungEingeben                        |void bewerbungEingeben(BewerbungForm)    | Eingabe der Bewerbung                                      |
|                                         |                                         |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|verwaltungStellenangesuche               |void verwaltungStellenangesuche          | Eingeben,bearbeiten oder löschen von Stellengesuche        |
|                                         |(string verwaltungTyp)                   |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+



![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\zpm_class.jpg?raw=true "Title")

### class ZPM

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|statistikenStellenangeboteErzeugen       |list<Integer>                            | Statistiken für Stellenangebote erzeugen                   |
|                                         |statistikenStellenangeboteErzeugen()     |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|statistikenStellengesucheErzeugen        |list<Integer>                            | Statistiken für Stellengesuche erzeugen                    |
|                                         |statistikenStellenangesucheErzeugen()    |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellengesucheRecherschieren             |list<StellengeuscheForm>                 | Rechersche von Stellengeusche durch Eingabe einer Form     |
|                                         |stellengesucheRecherschieren(            |                                                            |
|                                         | StellengesucheForm)                     |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|benachrichtigungZustand                  |string benachrichtigungZustand           | benachrichtigung über den Zustand der Bewerbung            |
|                                         |(benachrichtigung:string)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungÜbergabe                        | BewerbungForm bewerbungÜbergabe         | Bewerbung(Form) übergeben                                  |
|                                         |(BewerbunfForm)                          |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|zurückweisenBewerbung                    |string zurückweisenBewerbung             | Zuruckweißen von Bewerbung                                 |
|                                         |(string zustand)                         |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|ermittlungPassendeArbeitsfeldernfür      |string ermittlungPassendeArbeitsfeldernfü|Passende Arbeitsfelder für Initiative Bewerbung ermittln    |
| InitiativeBewerbung                     |rInitiativeBewerbung(Bewerbung b)        |                                                            |                                                  
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|initiativausschreibungenErzeugen         | string initiativausschreibungenErzeugen | Aussscherbungen für initiative Bewerbung erzeugen          |
|                                         | (Bewerbung b)                           |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bestätigungEingangBewerbung(Bewerbung)   |string bestätigungEingangBewerbung       | Der Eingang eine Bewerbuung wird duch nachricht bestätigt  |
|                                         |(Bewerbung b)                            |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|arbeitplatzAngebot                       | string arbeitplatzAngebot               | Benachrichtigung/Angebot für Arbeitzplatz                  |
|                                         | (string benchrichtigung)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|verwaltungStellenangebot                 |void verwaltungStellenangebot            | Eingeben,bearbeiten oder löschen von Stellenangebot        |
|                                         |(string verwaltungTyp)                   |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+




![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\oe_class.jpg?raw=true "Title")


### class OE

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|nichteignungBewerbung                    |string nichteignungBewerbung             |Benachrichtigung daüber ,dass die OE keine Eignung für die  |
|                                         |rInitiativeBewerbung(string              |Bewerbung hat                                               |
|                                         | benachrichtigung)                       |                                                            |                                                  
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|eignungBewerbung                         | string eignungBewerbung                 | Benachrichtigung daüber ,dass die OE keine Eignung für die |
|                                         | (string benachrichtigung)               | Bewerbung hat                                              |             |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|benachrichtigungZustand                  |string benachrichtigungZustand           | benachrichtigung über den Zustand der Bewerbung            |
|                                         |(benachrichtigung:string)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungÜbergabe                        | BewerbungForm bewerbungÜbergabe         | Bewerbung(Form) übergeben                                  |
|                                         |(BewerbunfForm)                          |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bestätigung/ablehnungVon                 |string bestätigung/ablehnungVon          |Bestätigung oder Ablehnung einer Arbeitsplatzwechel         |
| Arbeitsplatzwechsel                     |Arbeitsplatzwechsel                      |                                                            |
|                                         |(string benachrichtigung)                |                                                            |                                              
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+


&nbsp;


![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\export_class.jpg?raw=true "Title")

### class Export

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|bestätigungEingangBewerbung(Bewerbung)   |string bestätigungEingangBewerbung       | Der Eingang eine Bewerbuung wird duch nachricht bestätigt  |
|                                         |(Bewerbung b)                            |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellenangeboteRecherschieren            |list<Stellenangebot>                     | Rechersche von Stellenangebote durch Eingabe einer Form    |
|                                         |stellenangeboteRecherschieren(           |                                                            |
|                                         | StellenangebotForm)                     |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|benachrichtigungZustand                  |string benachrichtigungZustand           | benachrichtigung über den Zustand der Bewerbung            |
|                                         |(benachrichtigung:string)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungÜbergabe                        | BewerbungForm bewerbungÜbergabe         | Bewerbung(Form) übergeben                                  |
|                                         |(BewerbunfForm)                          |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bewerbungRecherschieren                  | list<BewerbungFrom>                     | Rechersche von Bewerbungen durch Eingabe einer Form        |                                                   |
|                                         | bewerbungRecherschieren                 |                                                            |
|                                         | (BewerbungForm)                         |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|arbeitplatzAngebot                       | string arbeitplatzAngebot               | Benachrichtigung/Angebot für Arbeitzplatz                  |
|                                         | (string benchrichtigung)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|statistikenStellenangeboteErzeugen       |list<Integer>                            | Statistiken für Stellenangebote erzeugen                   |
|                                         |statistikenStellenangeboteErzeugen()     |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|statistikenStellengesucheErzeugen        |list<Integer>                            | Statistiken für Stellengesuche erzeugen                    |
|                                         |statistikenStellenangesucheErzeugen()    |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|stellengesucheRecherschieren             |list<StellengeuscheForm>                 | Rechersche von Stellengeusche durch Eingabe einer Form     |
|                                         |stellengesucheRecherschieren(            |                                                            |
|                                         | StellengesucheForm)                     |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|zurückweisenBewerbung                    |string zurückweisenBewerbung             | Zuruckweißen von Bewerbung                                 |
|                                         |(string zustand)                         |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|ermittlungPassendeArbeitsfeldernfür      |string ermittlungPassendeArbeitsfeldernfü|Passende Arbeitsfelder für Initiative Bewerbung ermittln    |
| InitiativeBewerbung                     |rInitiativeBewerbung(Bewerbung b)        |                                                            |                                                  
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|initiativausschreibungenErzeugen         | string initiativausschreibungenErzeugen | Aussscherbungen für initiative Bewerbung erzeugen          |
|                                         | (Bewerbung b)                           |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|nichteignungBewerbung                    |string nichteignungBewerbung             |Benachrichtigung daüber ,dass die OE keine Eignung für die  |
|                                         |rInitiativeBewerbung(string              |Bewerbung hat                                               |
|                                         | benachrichtigung)                       |                                                            |                                                  
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|eignungBewerbung                         | string eignungBewerbung                 | Benachrichtigung daüber ,dass die OE keine Eignung für die |
|                                         | (string benachrichtigung)               | Bewerbung hat                                              |             |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+



![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\import_class.jpg?raw=true "Title")

### class Import

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
|bewerbungEingeben                        |void bewerbungEingeben(BewerbungForm)    | Eingabe der Bewerbung                                      |
|                                         |                                         |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|verwaltungStellenangesuche               |void verwaltungStellenangesuche          | Eingeben,bearbeiten oder löschen von Stellengesuche        |
|                                         |(string verwaltungTyp)                   |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|verwaltungStellenangebot                 |void verwaltungStellenangebot            | Eingeben,bearbeiten oder löschen von Stellenangebot        |
|                                         |(string verwaltungTyp)                   |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|bestätigung/ablehnungVon                 |string bestätigung/ablehnungVon          |Bestätigung oder Ablehnung einer Arbeitsplatzwechel         |
| Arbeitsplatzwechsel                     |Arbeitsplatzwechsel                      |                                                            |
|                                         |(string benachrichtigung)                |                                                            |                                              
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
|anmelden                                 |void anmelden                            | Eingabe der Anmeldedaten einer Mitarbeiter                 |
|                                         |(name:string,indnummer:int)              |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+


![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\mitarbeiterDB_class.jpg?raw=true "Title")

### class MitarbeiterDB

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
| benachrichtigungZustand                 | string benachrichtigungZustand          | Benachrichtigung über den Zustand einer der Dokumenten     |                     
|(benachrichtigung:string)                |(benachrichtigung:string)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+ 
|anmelden                                 |void anmelden                            | Eingabe der Anmeldedaten einer Mitarbeiter                 |
|                                         |(name:string,indnummer:int)              |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+

![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\zpm_DB_class.jpg?raw=true "Title")



### class ZPM_DB

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
| benachrichtigungZustand                 | string benachrichtigungZustand          | Benachrichtigung über den Zustand einer der Dokumenten     |                     
|(benachrichtigung:string)                |(benachrichtigung:string)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+ 
|anmelden                                 |void anmelden                            | Eingabe der Anmeldedaten einer Mitarbeiter                 |
|                                         |(name:string,indnummer:int)              |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+



![Alt text](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Komponenten\oe_DB_class.jpg?raw=true "Title")



### class OE_DB

+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+
| Methode                                 |  Signatur                               |     Beschreibung                                           |
+=========================================+=========================================+============================================================+
| benachrichtigungZustand                 | string benachrichtigungZustand          | Benachrichtigung über den Zustand einer der Dokumenten     |                     
|(benachrichtigung:string)                |(benachrichtigung:string)                |                                                            |
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+ 
|anmelden                                 |void anmelden                            | Eingabe der Anmeldedaten einer Mitarbeiter                 |
|                                         |(name:string,indnummer:int)              |                                                            |        
+-----------------------------------------+-----------------------------------------+------------------------------------------------------------+



## Benutzungsschnittstelle


![Hier kann man sich einloggen entweder mit einem Mitarbeiter ID oder ein Manager ID.](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Wireframes\loginpage-1.jpg?raw=true "Title")

&nbsp;

![Die Startseite nach dem Login](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Wireframes\afterlogindirekt-1.jpg?raw=true "Title")

&nbsp;

![Hier kann man die Stelle suchen, die er haben wollte und sich darum bewerben.](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Wireframes\buttoneingereichebewerbungen-1.png?raw=true "Title")

&nbsp;

![Hier sind die Daten, die eingegeben sollten, um die Bewerbung einreichen zu können und dann die Bewerbung einreichen mit der Taste "Bewerbung einreichen".](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Wireframes\Bewerbungeinreichen-1.jpg?raw=true "Title")

&nbsp;

![Liste mit allen eingereichte Bewerbungen](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Wireframes\listedereingereichtebewerbungen-1.png?raw=true "Title")

&nbsp;

![Hier könnte eine Stellengesuche benatragt werden, indem man bestimmte Suckkriterien eingibt und dann wird die suche Automatisch gestellt und passende Jobs werden dann angezeigt.](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Wireframes\stellengeusche-1.jpg?raw=true "Title")

&nbsp;

![Liste der Stellengesuchen mit Optionen zum Löschen und Bearbeiten](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Wireframes\stellengesuchemitentfernen-1.png?raw=true "Title")

&nbsp;

![Liste mit allen Stellenangebote mit dem Optionen zu bearbeiten und löschen](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Wireframes\stellenabietenmitentfernen-1.png?raw=true "Title")

&nbsp;

![Auf die Seite können nur Leute mit Manager ID zugreifen, damit sie freie Stellen im Intranet anbieten.](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Wireframes\stellenanbieten-page.pdf-1.jpg?raw=true "Title")




## Systemverhalten


![Beschreibung der Kommunikation der einzelnen Komponenten während der Process der Speicherung einer Stellenangebot](C:/Users/ivayl/Desktop/4.Semester/SWE/Praktikum_3/sequence_stellenangebot.jpg?raw=true "Title")

![Beschreibung der Kommunikation der einzelnen Komponenten während der Process der Eingabe einer Bewerbung](C:/Users/ivayl/Desktop/4.Semester/SWE/Praktikum_3/sequence_bewerbung.jpg?raw=true "Title")

## Datenbasis

### Klassenmodell

![Beziehung zwischen der einzelnen Komponenten in den Datenbanksystem.](C:\Users\ivayl\Desktop\4.Semester\SWE\Praktikum_3\Class_diagram(1).jpg?raw=true "Title")



Table: (Bezeichnung der Klasse) - Zusammenstellung Attribute



(BewerbungsForm) - Zusammenstellung Attribute


+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| datum                | date  | Datum der Eingabe der Bewerbung                            |
+----------------------+-------+------------------------------------------------------------+
| indnum               | int   | Identifikationsnummer                                      |
+----------------------+-------+------------------------------------------------------------+
|initiativbew          | int   | Identifikationsnummer                                      |
+----------------------+-------+------------------------------------------------------------+
|name                  | string| Name der Bewerber                                          |
+----------------------+-------+------------------------------------------------------------+
|vorname               | string| Name der Bewerber                                          |
+----------------------+-------+------------------------------------------------------------+
|wohnort               | string| Wohnort der Bewerber                                       |
+----------------------+-------+------------------------------------------------------------+
|telefondienst         |int    | dienstliche Telefeonnummer                                 |
+----------------------+-------+------------------------------------------------------------+
|telefonpriv           |int    | private Telefeonnummer                                     |
+----------------------+-------+------------------------------------------------------------+
|emailDienst           |string | dienstliche Email                                          |
+----------------------+-------+------------------------------------------------------------+
|emailPriv             |string | private Email                                              |
+----------------------+-------+------------------------------------------------------------+
|standort              |string | Standort der OE                                            |
+----------------------+-------+------------------------------------------------------------+
|oe                    |string | Organisationseinheit                                       |
+----------------------+-------+------------------------------------------------------------+
|arbeitsfeld           |string | Arbeitsfeld ,um dem sich die Bewerbung bezieht             |
+----------------------+-------+------------------------------------------------------------+
|anschreiben           |string | Anschreiben ,um dem sich die Bewerbung bezieht             |
+----------------------+-------+------------------------------------------------------------+
|lebenslauf            |string | Lebenslauf der Bewerber                                    |
+----------------------+-------+------------------------------------------------------------+
|zeugnise              |string | Zeugnisse der Bewerber                                     |
+----------------------+-------+------------------------------------------------------------+
|abschlüsse            |string | Abschlüsse der Bewerber                                    |
+----------------------+-------+------------------------------------------------------------+
|spezQualifikationen   |string | spezielle Qualifikationen der Bewerber                     |
+----------------------+-------+------------------------------------------------------------+


&nbsp;


(StellenangebotForm)- Zusammenstellung Attribute

+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| datum                | date  | Datum der Eingabe der Stellenangebot                       |
+----------------------+-------+------------------------------------------------------------+
| indnum               | int   | Identifikationsnummer                                      |
+----------------------+-------+------------------------------------------------------------+
|funktion              |string | Funktion der Stelle                                        |
+----------------------+-------+------------------------------------------------------------+
|stellenbeschreibung   | string| Beschreibung der Stelle                                    |
+----------------------+-------+------------------------------------------------------------+
|führungsaufgaben      |boolean| Ob Führungsaufgaben erforderlich sind                      |
+----------------------+-------+------------------------------------------------------------+
|ansprechpartnerName   | string| Name der Ansprechspartner                                  |
+----------------------+-------+------------------------------------------------------------+
|ansprechpartnerFunktion|string| Funktion der Ansprechspartner                              |
+----------------------+-------+------------------------------------------------------------+
|ansprechpartnerEmail  |string | Email der Ansprechspartner                                 |
+----------------------+-------+------------------------------------------------------------+
|erforderlicheAbschlüsse|string |Erforderliche Abschlüsse                                   |
+----------------------+-------+------------------------------------------------------------+
|erforderlicheQualifik |       | Qualifikationen, die von den OE als erforderlich beziechnet|
| ationen              |string | werden                                                     |
+----------------------+-------+------------------------------------------------------------+
|beschäftigungsUmfang  |date   | Dauer der Beschäftigung                                    |
+----------------------+-------+------------------------------------------------------------+
|tariflicheVergütung   |boolean| Ob die Vergütung tariflich ist oder nich                   |
+----------------------+-------+------------------------------------------------------------+
|befristeteBeschäftigung|date | Befristigung der Beshcäftigung                            |
+----------------------+-------+------------------------------------------------------------+
|stellenbestzungZum    |date   | Anschreiben ,um dem sich die Bewerbung bezieht             |
+----------------------+-------+------------------------------------------------------------+
|ablaufBewerbungfrist  |string | Frist der Bewerbung                                        |
+----------------------+-------+------------------------------------------------------------+
|sonstigeHinweise      |string | zusätzlichen Hinweise                                      |
+----------------------+-------+------------------------------------------------------------+




&nbsp;


(StellengesucheForm)- Zusammenstellung Attribute

+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| standort             | string| Standort der OE                                            |
+----------------------+-------+------------------------------------------------------------+
|oe                    |string | Organisationseinheit                                       |
+----------------------+-------+------------------------------------------------------------+
| indnum               | int   | Identifikationsnummer                                      |
+----------------------+-------+------------------------------------------------------------+
|stellenbeschreibung   | string| Beschreibung der Stelle                                    |
+----------------------+-------+------------------------------------------------------------+
|führungsaufgaben      |boolean| Ob Führungsaufgaben erforderlich sind                      |
+----------------------+-------+------------------------------------------------------------+
|ansprechpartnerName   | string| Name der Ansprechspartner                                  |
+----------------------+-------+------------------------------------------------------------+
|ansprechpartnerFunktion|string| Funktion der Ansprechspartner                              |
+----------------------+-------+------------------------------------------------------------+
|ansprechpartnerEmail  |string | Email der Ansprechspartner                                 |
+----------------------+-------+------------------------------------------------------------+
|erforderlicheAbschlüsse|string |Erforderliche Abschlüsse                                   |
+----------------------+-------+------------------------------------------------------------+
|erforderlicheQualifik |       | Qualifikationen, die von den OE als erforderlich beziechnet|
| ationen              |string | werden                                                     |
+----------------------+-------+------------------------------------------------------------+
|beschäftigungsUmfang  |date   | Dauer der Beschäftigung                                    |
+----------------------+-------+------------------------------------------------------------+
|tariflicheVergütung   |boolean| Ob die Vergütung tariflich ist oder nich                   |
+----------------------+-------+------------------------------------------------------------+
|befristeteBeschäftigung|date | Befristigung der Beshcäftigung                              |
+----------------------+-------+------------------------------------------------------------+
|stellenbestzungZum    |date   | Anschreiben ,um dem sich die Bewerbung bezieht             |
+----------------------+-------+------------------------------------------------------------+
|ablaufBewerbungfrist  |date | Frist der Bewerbung                                          |
+----------------------+-------+------------------------------------------------------------+


&nbsp;

(MitarbeiterDB)- Zusammenstellung Attribute

+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| name                 | string| Name der Mitaarbeiter                                      |
+----------------------+-------+------------------------------------------------------------+
|vorname               |string | Vorname der Mitarbeiter                                    |
+----------------------+-------+------------------------------------------------------------+
| indnum               | int   | Identifikationsnummer                                      |
+----------------------+-------+------------------------------------------------------------+

&nbsp;

(Benachrichtigung)- Zusammenstellung Attribute

+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| benachrichtigung     | string| Nachricht ,dass von einer der Akteure gesndet wird         |
+----------------------+-------+------------------------------------------------------------+


&nbsp;

(ZPM_DB)- Zusammenstellung Attribute

+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| list<Mirarbeiter>    | list  | Liste mit allen Mitarbeiter in ZPM                         |
+----------------------+-------+------------------------------------------------------------+
|zustand               |string | Nachricht über Veränderung der Zustand                     |
+----------------------+-------+------------------------------------------------------------+


&nbsp;

(OE_DB)- Zusammenstellung Attribute

+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| list<Mirarbeiter>    | list  | Liste mit allen Mitarbeiter in OE                          |
+----------------------+-------+------------------------------------------------------------+
|zustand               |string | Nachricht über Veränderung der Zustand                     |
+----------------------+-------+------------------------------------------------------------+


&nbsp;
(Stellengesuche)- Zusammenstellung Attribute

+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| list<StellengesucheForm> list  | Liste der alle einzelnen Stellengeuschen                 |
+----------------------+-------+------------------------------------------------------------+


&nbsp;
(Stellenangebote)- Zusammenstellung Attribute

+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| list<StellenangebotForm> list  | Liste der alle einzelnen Stellenangebote                 |
+----------------------+-------+------------------------------------------------------------+


&nbsp;
(Bewerbungen)- Zusammenstellung Attribute

+----------------------+-------+------------------------------------------------------------+
| Attribut             |  Typ  |     Beschreibung                                           |
+======================+=======+============================================================+
| list<BewerbungsForm>   list  | Liste der alle einzelnen Bewerbungen                       |
+----------------------+-------+------------------------------------------------------------+








_Ersetzen Sie die Platzhalter durch sinnvolle Angaben. Achten Sie bei der Benennung der Klassen auf Konsistenz zum Klassendiagramm. Geben Sie die Signaturen in Form einer Aufzählung von Parametern (Name und Typ) an, soweit das möglich und sinnvoll ist._