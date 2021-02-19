---
description: Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.
seo-description: Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.
seo-title: Opt-in-Nutzungsszenarios
title: Opt-in-Nutzungsszenarios
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 23%

---


# Opt-in-Nutzungsszenarios {#opt-in-use-cases}

Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.

## Tipps und Fehlerbehebung {#section-5c566366410f4a8f89eca0d3f556d99f}

* Besucher JS initialize ist synchron und wird während des Seitenladevorgangs ausgeführt. Wenn Sie mit einer CMP- oder Berechtigungspersistenz mit hoher Latenz interagieren, sollten Sie die asynchronen Funktionen verwenden, die unter [Einwahleinrichtung](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047) beschrieben werden.
* Bei der Teilnahme handelt es sich um eine Implementierung pro Domäne. Domänenübergreifende Implementierungen werden nicht behandelt.
* Um Aufrufe von Drittanbietern für eine bestimmte Bibliothek zu deaktivieren, müssen Sie diese Voreinstellung in jeder Bibliothek separat konfigurieren.

## Opt-in-Szenarios  {#section-1178053c065c430bba26f82ef383a71c}

Diese Nutzungsszenarios sind Beispiele für die Verwendung des Opt-in-Dienstes.

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Anforderung </th> 
   <th colname="col2" class="entry"> Lösungen </th> 
   <th colname="col3" class="entry"> Wirkung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analytics ist in der Lage, vor der Zustimmung zu sammeln, aber alle anderen Bibliotheken können erst geladen werden, wenn die Zustimmung eingegangen ist </p> </td> 
   <td colname="col2"> <p>Verwenden Sie die Option zur Aktivierung der Analytics-Kategorie im Status vor der Zustimmung </p> </td> 
   <td colname="col3"> <p>Analytics verwendet die Analytics-ID anstelle der ECID bei der Erfassung vor der Zustimmung. Nach der Genehmigung der ECID wird eine neue ID verwendet, und der Besucher erhält eine ECID, die für Aktivierungen und Integrationen verwendet werden kann. </p> <p>Eine Fragmentierung des Besuchers im Status vor/nach der Zustimmung ist zu erwarten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Die Erstanbieter-Messung ist in der Lage, die Daten vor der Zustimmung zu sammeln. Alle anderen Arten der Datennutzung verhindert, bis die Zustimmung eingeht. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie die Option zur Aktivierung von Analytics- und ECID-Bibliotheken im Status vor der Genehmigung. </p> <p>hinzufügen der Konfiguration "Deaktivieren von Drittanbieter-Cookies"in der ECID-Bibliothek, um Drittanbieter-Cookie- und ID-Syncs im Status vor der Zustimmung zu blockieren </p> </td> 
   <td colname="col3"> <p>Adobe Demdex-Aufruf wird für den ECID-Abruf Trigger, es werden jedoch kein Demdex-Cookie, kein Drittanbieter-Cookie oder keine ID-Syncs vorhanden sein. </p> <p>Der Besucher bleibt im Status vor/nach der Zustimmung für Analytics konsistent. Die Erfassung im Vorhinein wird an die Datenerfassung nach der Zustimmung gebunden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Erstanbieter-Messwerte und Targeting können im Status vor der Zustimmung erfasst werden. Alle anderen Arten der Datennutzung verhindert, bis die Zustimmung eingeht. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie die Option zur Aktivierung von Analytics- + ECID- + Zielgruppe-Bibliotheken im Vorab-Status. </p> <p>Fügen Sie die Konfiguration <span class="codeph">isablethirdpartycookies</span> der ECID-Bibliothek hinzu, um Drittanbieter-Cookies und ID-Synchronisationen im Status vor der Zustimmung zu blockieren. Entfernen Sie die Flagge im Status nach der Zustimmung. </p> </td> 
   <td colname="col3"> <p>Adobe Demdex-Aufruf wird für den ECID-Abruf Trigger, es werden jedoch kein Demdex-Cookie, kein Drittanbieter-Cookie oder keine ID-Syncs vorhanden sein. </p> <p>Der Besucher bleibt im Status vor/nach der Zustimmung für Erstanbieter-Lösungen konsistent. Die Erfassung im Vorhinein wird an die Datenerfassung nach der Zustimmung gebunden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Es sind keine Cookies zulässig, die vor der Genehmigung eingestellt werden </p> </td> 
   <td colname="col2"> <p>Verwenden Sie die Option zum Blockieren des Ladens aller Bibliotheken bis zum Erhalt der Zustimmung </p> </td> 
   <td colname="col3"> <p>Die Implementierung erfolgt wie erwartet und alle Bibliotheken, einschließlich ECID, werden nach der Genehmigung in der richtigen Reihenfolge geladen. </p> <p>Datenverlust für Kunden, die nie zustimmen, verfolgt zu werden. </p> </td> 
  </tr> 
 </tbody> 
</table>

