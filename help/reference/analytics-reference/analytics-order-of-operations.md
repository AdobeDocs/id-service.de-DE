---
description: Nach der Bereitstellung des Besucher-ID-Services gibt es in Analytics fünf Möglichkeiten zum Ermitteln eines Besuchers.
keywords: ID-Dienst
title: Reihenfolge der Befehle für Analytics-IDs
exl-id: 8ee340fe-ef3b-40e6-9441-7ee0c9e20357
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 100%

---

# Reihenfolge der Befehle für Analytics-IDs{#order-of-operations-for-analytics-ids}

Nach der Bereitstellung des Besucher-ID-Services gibt es in Analytics fünf Möglichkeiten zum Ermitteln eines Besuchers.

In vielen Szenarios können für einen Aufruf zwei oder drei verschiedene IDs vorliegen. Analytics verwendet jedoch die erste ID in der Liste als offizielle [!DNL Experience Cloud] ID. Wenn Sie zum Beispiel eine benutzerdefinierte Besucher-ID (im `vid` Abfrageparameter enthalten) festlegen, wird diese ID vor anderen IDs verwendet, die möglicherweise bei dem gleichen Treffer vorhanden sind. Weitere Informationen finden Sie unter [Einrichten von Analytics und Experience Cloud IDs](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Verwendete Reihenfolge </th> 
   <th colname="col2" class="entry"> Abfrageparameter (Erfassungsmethode) </th> 
   <th colname="col3" class="entry"> Vorhanden, wenn </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>1.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=de" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>die <span class="codeph">s.visitorID</span> festgelegt wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=de" format="http" scope="external"> aid (s_vi-Cookie)</a> </p> </td> 
   <td colname="col3"> <p>der Besucher bereits über ein s_vi-Cookie verfügte, bevor Sie den <span class="keyword">Experience Cloud</span> ID-Dienst einsetzten, oder Sie haben eine <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">Übergangsphase</a> konfiguriert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>Der Browser des Besuchers akzeptiert Erstanbieter-Cookies. Dies wird durch das AMCV-Cookie festgelegt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/analytics-ids.html?lang=de" format="http" scope="external"> fid (Ausweichcookie für H.25.3 oder AppMeasurement für JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Ein Browser akzeptiert keine Drittanbietercookies, und der Analytics-Tracking-Server ist als ein Drittanbieter-Tracking-Server eingerichtet. </p> <p> <p>Hinweis: Das <span class="codeph">fid</span> ist eine Legacy-ID und wird nicht verwendet, wenn Sie den ID-Dienst auf Ihrer Website implementiert haben. In diesem Fall wird <span class="codeph">fid</span> nicht benötigt, da das Erstanbieter-<a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV-Cookie</a> es obsolet macht. Es wurde für die Unterstützung von altem Code und aus Verlaufsgründen beibehalten. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/technotes/visitor-identification.html?lang=de" format="http" scope="external"> IP-Adresse, Benutzeragent, Gateway-IP-Adresse</a> </p> </td> 
   <td colname="col3"> <p>der Browser des Besuchers keine Cookies akzeptiert. </p> </td> 
  </tr> 
 </tbody> 
</table>
