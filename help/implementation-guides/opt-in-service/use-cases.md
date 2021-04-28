---
description: Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.
seo-description: Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.
seo-title: Opt-in-Nutzungsszenarios
title: Opt-in-Nutzungsszenarios
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '437'
ht-degree: 100%

---

# Opt-in-Nutzungsszenarios {#opt-in-use-cases}

Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.

## Tipps und Fehlerbehebung {#section-5c566366410f4a8f89eca0d3f556d99f}

* „Visitor JS initialize“ ist synchron und wird während des Seitenladevorgangs ausgeführt. Wenn Sie mit einer CMP- oder Berechtigungspersistenz mit hoher Latenz interagieren, sollten Sie die asynchronen Funktionen verwenden, die unter [Opt-in-Setup](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047) beschrieben werden.
* Bei Opt-in handelt es sich um eine Implementierung pro Domain. Domain-übergreifende Implementierungen werden nicht verarbeitet.
* Um Aufrufe von Drittanbietern für eine bestimmte Bibliothek zu deaktivieren, müssen Sie diese Voreinstellung in jeder Bibliothek separat konfigurieren.

## Opt-in-Szenarios   {#section-1178053c065c430bba26f82ef383a71c}

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
   <td colname="col1"> <p>Analytics kann zwar eine Erfassung vor einem Einverständnis durchführen, aber alle anderen Bibliotheken können erst dann geladen werden, wenn das Einverständnis eingegangen ist. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie Opt-in zur Aktivierung der Analytics-Kategorie vor dem Einverständnis </p> </td> 
   <td colname="col3"> <p>Analytics verwendet die Analytics-ID anstelle der ECID bei einer Erfassung vor dem Einverständnis. Nach der Genehmigung der ECID wird eine neue ID verwendet, und der Besucher erhält eine ECID, die für Aktivierungen und Integrationen verwendet werden kann. </p> <p>Im Zustand vor und nach dem Einverständnis ist eine Besucherfragmentierung zu erwarten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Für eine Erfassung vor dem Einverständnis ist Erstanbietermessung zulässig. Jegliche andere Art von Datennutzung wird verhindert, bis das Einverständnis eingeht. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie Opt-in zur Aktivierung von Analytics+ ECID-Bibliotheken vor dem Einverständnis. </p> <p>Fügen Sie der ECID-Bibliothek die Konfiguration „disablethirdpartycookies“ hinzu, um Drittanbieter-Cookies und ID-Synchronisierungen vor dem Einverständnis zu blockieren. </p> </td> 
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
