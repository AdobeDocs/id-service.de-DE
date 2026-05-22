---
description: Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.
title: Opt-in-Nutzungsszenarios
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
TQID: https://experienceleague.adobe.com/ssSKMn1pEhduempV4zjCqi4Pol1U0oEBU6l36SkUTH4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 460
ht-degree: 91%

---

# Opt-in-Nutzungsszenarios {#opt-in-use-cases}

Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.

## Tipps und Fehlerbehebung {#section-5c566366410f4a8f89eca0d3f556d99f}

* „Visitor JS initialize“ ist synchron und wird während des Seitenladevorgangs ausgeführt. Wenn Sie mit einer CMP- oder Berechtigungspersistenz mit hoher Latenz interagieren, sollten Sie die asynchronen Funktionen verwenden, die unter [Opt-in-Setup](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047) beschrieben werden.
* Bei Opt-in handelt es sich um eine Implementierung pro Domain. Domain-übergreifende Implementierungen werden nicht verarbeitet.
* Um Aufrufe von Drittanbietern für eine bestimmte Bibliothek zu deaktivieren, müssen Sie diese Voreinstellung in jeder Bibliothek separat konfigurieren.

## Opt-in-Szenarios {#section-1178053c065c430bba26f82ef383a71c}

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
   <td colname="col1"> <p>Analytics kann im Status vor dem Einverständnis erfasst werden, aber alle anderen Bibliotheken können erst geladen werden, wenn das Einverständnis eingeht </p> </td> 
   <td colname="col2"> <p>Verwenden Sie Opt-in zur Aktivierung der Analytics-Kategorie vor dem Einverständnis </p> </td> 
   <td colname="col3"> <p>Analytics verwendet die Analytics-ID anstelle der ECID bei einer Erfassung vor dem Einverständnis. Nach der Genehmigung der ECID wird eine neue ID verwendet, und der Besucher erhält eine ECID, die für Aktivierungen und Integrationen verwendet werden kann. </p> <p>Im Zustand vor und nach dem Einverständnis ist eine Besucherfragmentierung zu erwarten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Für eine Erfassung vor dem Einverständnis ist Erstanbietermessung zulässig. Jegliche andere Art von Datennutzung wird verhindert, bis das Einverständnis eingeht. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie Opt-in zur Aktivierung von Analytics+ ECID-Bibliotheken vor dem Einverständnis. </p> <p>Fügen Sie die Konfiguration „disableThirdPartyCookies“ zur ECID-Bibliothek hinzu, um die Synchronisierung von Drittanbieter-Cookie und IDs im Status vor der Zustimmung zu blockieren </p> </td> 
   <td colname="col3"> <p>Adobe Demdex-Aufrufe lösen zwar einen ECID-Abruf aus, jedoch sind keine Demdex-Cookies, andere Drittanbieter-Cookies oder ID-Synchronisierungen vorhanden. </p> <p>Der Besucher bleibt im Status vor/nach der Zustimmung für Analytics konsistent. Die Erfassung vor dem Einverständnis ist an die Datenerfassung nach dem Einverständnis gebunden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Erstanbieter-Messwerte und Targeting können im Status vor der Zustimmung erfasst werden. Jegliche andere Art von Datennutzung wird verhindert, bis das Einverständnis eingeht. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie Opt-in zur Aktivierung von Analytics- + ECID- + Target-Bibliotheken vor dem Einverständnis. </p> <p>Fügen Sie die Konfiguration <span class="codeph">isablethirdpartycookies</span> der ECID-Bibliothek hinzu, um Drittanbieter-Cookies und ID-Synchronisationen im Status vor der Zustimmung zu blockieren. Entfernen Sie die Kennzeichnung nach dem Einverständnis. </p> </td> 
   <td colname="col3"> <p>Adobe Demdex-Aufrufe lösen zwar einen ECID-Abruf aus, jedoch sind keine Demdex-Cookies, andere Drittanbieter-Cookies oder ID-Synchronisierungen vorhanden. </p> <p>Der Besucher bleibt im Status vor/nach der Zustimmung für Erstanbieter-Lösungen konsistent. Die Erfassung vor dem Einverständnis ist an die Datenerfassung nach dem Einverständnis gebunden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Es darf für keine Cookies ein Einverständnis voreingestellt werden. </p> </td> 
   <td colname="col2"> <p>Mit Opt-in verhinden Sie das Ladens aller Bibliotheken bis zum Erhalt des Einverständnisses. </p> </td> 
   <td colname="col3"> <p>Die Implementierung erfolgt wie erwartet und alle Bibliotheken, einschließlich ECID, werden nach dem Einverständnis in der richtigen Reihenfolge geladen. </p> <p>Datenverlust für Kunden, die für die Verfolgung nie ein Einverständnis geben. </p> </td> 
  </tr> 
 </tbody> 
</table>

