---
description: Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.
seo-description: Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.
seo-title: Opt-in-Nutzungsszenarios
title: Opt-in-Nutzungsszenarios
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Opt-in-Nutzungsszenarios {#opt-in-use-cases}

Beispiele für Nutzungsszenarios und Lösungen zur Verwaltung des Opt-in-Dienstes.

## Tipps und Fehlerbehebung {#section-5c566366410f4a8f89eca0d3f556d99f}

* Die Visitor JS-Initialisierung wird synchron ausgeführt, während die Seite geladen wird. Wenn Sie eine CMP oder Lösung zum Speichern von Berechtigungen mit hoher Latenzzeit verwenden, ist es möglicherweise sinnvoller, die unter [Einrichten des Opt-in-Objekts](../../mcvid-implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047) beschriebenen asynchronen Funktionen zu verwenden.
* Opt-in wird pro Domäne implementiert. Es kann nicht für domänenübergreifende Implementierungen verwendet werden.
* Um Drittanbieter-Aufrufe für eine bestimmte Bibliothek zu deaktivieren, müssen Sie diese Voreinstellung in jeder Bibliothek separat konfigurieren.

## Opt-in-Szenarios {#section-1178053c065c430bba26f82ef383a71c}

Diese Nutzungsszenarios sind Beispiele für die Verwendung des Opt-in-Dienstes.

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Anforderung </th> 
   <th colname="col2" class="entry"> „Lösungen“ </th> 
   <th colname="col3" class="entry"> Wirkung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analytics kann im Status vor der Zustimmung geladen werden, alle anderen Bibliotheken können jedoch erst geladen werden, nachdem die Zustimmung erteilt wurde. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie Opt-in, um die Kategorie „Analytics“ im Status vor der Zustimmung zu aktivieren. </p> </td> 
   <td colname="col3"> <p>Im Status vor der Zustimmung verwendet Analytics zur Erfassung die Analytics-Kennung statt ECID. Sobald ECID genehmigt wurde, wird eine neue Kennung verwendet und der Besucher erhält eine ECID, die zur Aktivierung und Integration genutzt werden kann. </p> <p>Die Besucherfragmentierung im Status vor und nach der Zustimmung wird erwartet. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Erstanbieter-Messwerte können im Status vor der Zustimmung erfasst werden. Alle anderen Arten der Datenverwendung werden verhindert, bis die Zustimmung erteilt wird. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie Opt-in, um Analytics- und ECID-Bibliotheken im Status vor der Zustimmung zu aktivieren. </p> <p>Fügen Sie die Konfiguration „disablethirdpartycookies“ der ECID-Bibliothek hinzu, um Drittanbieter-Cookies und ID-Synchronisationen im Status vor der Zustimmung zu blockieren. </p> </td> 
   <td colname="col3"> <p>Ein Adobe Demdex-Aufruf wird zum Abrufen der ECID ausgelöst, es sind jedoch keine Demdex-Cookies, andere Drittanbieter-Cookies oder ID-Synchronisationen vorhanden. </p> <p>Der Besucher bleibt im Status vor/nach der Zustimmung für Analytics konsistent. Die Erfassung im Status vor der Zustimmung ist an die Datenerfassung nach der Zustimmung gebunden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Erstanbieter-Messwerte und Targeting können im Status vor der Zustimmung erfasst werden. Alle anderen Arten der Datenverwendung werden verhindert, bis die Zustimmung erteilt wird. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie Opt-in, um Analytics-, ECID- und Target-Bibliotheken im Status vor der Zustimmung zu aktivieren. </p> <p>Fügen Sie die Konfiguration <span class="codeph">isablethirdpartycookies</span> der ECID-Bibliothek hinzu, um Drittanbieter-Cookies und ID-Synchronisationen im Status vor der Zustimmung zu blockieren. Entfernen Sie die Kennzeichnung im Status nach der Zustimmung. </p> </td> 
   <td colname="col3"> <p>Ein Adobe Demdex-Aufruf wird zum Abrufen der ECID ausgelöst, es sind jedoch keine Demdex-Cookies, andere Drittanbieter-Cookies oder ID-Synchronisationen vorhanden. </p> <p>Der Besucher bleibt im Status vor/nach der Zustimmung für Erstanbieter-Lösungen konsistent. Die Erfassung im Status vor der Zustimmung ist an die Datenerfassung nach der Zustimmung gebunden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Im Status vor der Zustimmung dürfen keine Cookies erstellt werden. </p> </td> 
   <td colname="col2"> <p>Verwenden Sie Opt-in, um das Laden aller Bibliotheken zu verhindern, bis eine Zustimmung erteilt wird. </p> </td> 
   <td colname="col3"> <p>Die Implementierung funktioniert wie erwartet und alle Bibliotheken, einschließlich der ECID, werden im Status nach der Zustimmung in der richtigen Reihenfolge geladen. </p> <p>Datenverlust für Kunden, die dem Tracking niemals zustimmen. </p> </td> 
  </tr> 
 </tbody> 
</table>

