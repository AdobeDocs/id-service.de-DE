---
description: Nach der Bereitstellung des Besucher-ID-Diensts gibt es fünf Möglichkeiten zum Ermitteln eines Besuchers in Analytics.
keywords: ID-Dienst
seo-description: Nach der Bereitstellung des Besucher-ID-Diensts gibt es fünf Möglichkeiten zum Ermitteln eines Besuchers in Analytics.
seo-title: Reihenfolge der Befehle für Analytics-IDs
title: Reihenfolge der Befehle für Analytics-IDs
uuid: cb 1 d 136 e -093 f -43 b 0-a 7 e 1-96 f 1 e 61 fdad 0
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Reihenfolge der Befehle für Analytics-IDs{#order-of-operations-for-analytics-ids}

Nach der Bereitstellung des Besucher-ID-Diensts gibt es fünf Möglichkeiten zum Ermitteln eines Besuchers in Analytics.

In vielen Szenarios können für einen Aufruf zwei oder drei verschiedene IDs vorliegen. Analytics verwendet jedoch die erste ID in der Liste als offizielle [!DNL Experience Cloud] ID. Wenn Sie zum Beispiel eine benutzerdefinierte Besucher-ID (im Abfrageparameter `vid` enthalten) festlegen, wird diese ID vor anderen IDs verwendet, die möglicherweise bei dem gleichen Treffer vorhanden sind. Weitere Informationen finden Sie unter [Einstellen von Analytics- und Experience Cloud-IDs](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) .

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Reihenfolge </th> 
   <th colname="col2" class="entry"> Anfrageparameter (Erfassungsmethode) </th> 
   <th colname="col3" class="entry"> Vorhanden, wenn </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>1.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>die <span class="codeph">s.visitorID</span> festgelegt wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (s_vi-Cookie)</a> </p> </td> 
   <td colname="col3"> <p>Der Besucher hatte bereits ein s_ vi-Cookie, bevor Sie den <span class="keyword"> Experience Cloud</span> ID-Dienst bereitgestellt haben oder eine <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md" format="dita" scope="local"> Übergangsphase</a> konfiguriert haben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../mcvid-introduction/mcvid-cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>der Browser des Besuchers Erstanbieter-Cookies akzeptiert. Dies wird durch das AMCV-Cookie festgelegt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (Ausweichcookie für H.25.3 oder AppMeasurement für JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Ein Browser akzeptiert keine Drittanbietercookies, und der Analytics-Tracking-Server ist als ein Drittanbieter-Tracking-Server eingerichtet. </p> <p> <p>Hinweis: Das Ausweichcookie <span class="codeph">fid</span> ist eine Legacy-ID und wird nicht verwendet, wenn Sie den ID-Dienst auf Ihrer Website implementiert haben. In diesem Fall ist die <span class="codeph"> FID-Datei</span> nicht erforderlich, da das <a href="../../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local"> AMCV-Cookie</a> vom Erstanbieter veraltet ist. Es wurde für die Unterstützung von altem Code und aus Verlaufsgründen beibehalten. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5.<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> IP-Adresse, Benutzeragent, Gateway-IP-Adresse</a> </p> </td> 
   <td colname="col3"> <p>der Browser des Besuchers keine Cookies akzeptiert. </p> </td> 
  </tr> 
 </tbody> 
</table>

