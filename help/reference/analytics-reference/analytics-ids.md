---
description: Der Experience Cloud Identity-Dienst ersetzt die Legacy ID-Methoden für Analytics.
keywords: ID-Dienst
title: Einrichten von Analytics- und Experience Cloud IDs
exl-id: 7399ea16-d13e-452c-b8d9-8d0699566aa2
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '917'
ht-degree: 100%

---

# Einrichten von Analytics- und Experience Cloud IDs{#setting-analytics-and-experience-cloud-ids}

Der Experience Cloud Identity-Dienst ersetzt die Legacy ID-Methoden für Analytics.

Nach der Implementierung des ID-Diensts wird dieser Code vor AppMeasurement ausgeführt. Der ID-Dienst ruft die Experience Cloud IDs und Analytics-IDs ab, damit diese Werte beim Laden von AppMeasurement verfügbar sind.

Beim Laden von AppMeasurement werden die Werte für Experience Cloud IDs und Analytics-IDs vom ID-Dienst angefordert und mit jedem Server-Aufruf an die Datenerfassung gesendet. Da der ID-Dienst die Besucher-ID bestimmt und sie einfach an AppMeasurement übergibt, muss der ID-Dienst auf jeder Seite vor Ihrer AppMeasurement-JavaScript-Datei eingebunden und implementiert werden.

## Änderungen beim ID-Vorgang für Analytics  {#section-79bb86ae63f546419bb1a7ef5e710462}

Die wesentliche Änderung bei der Migration auf den [!DNL Experience Cloud] ID-Dienst besteht darin, dass das ID-Cookie nun mit JavaScript gesetzt wird und nicht mehr im HTTP-Header, der vom Datenerfassungs-Webserver zurückgegeben wird. Um diese Änderung zu verstehen, wird in den folgenden Abschnitten beschrieben, wie Cookies mithilfe dieser beiden Methoden gesetzt werden.

**HTTP-Header**

Eine HTTP-Antwort eines Webservers setzt Cookies in einem Browser. So wird das `s_vi`-Cookie gesetzt. Mit dem `s_vi`-Cookie werden Analytics-Besucher identifiziert. Nachdem ein Cookie gesetzt wurde, wird es mit allen nachfolgenden HTTP-Anforderungen an den Server gesendet.

Wenn eine Anforderung an den Adobe-Datenerfassungsserver gesendet wird, wird geprüft, ob der Header einen `s_vi`-Cookie enthält. Wenn der Cookie in der Anforderung enthalten ist, wird er zur Identifizierung des Besuchers verwendet. Wenn der Cookie nicht in der Anforderung enthalten ist, generiert der Server eine eindeutige [!DNL Experience Cloud] ID, setzt sie als Cookie im HTTP-Antwort-Header und sendet diesen mit der Anforderung zurück. Das Cookie wird im Browser gespeichert und bei nachfolgenden Besuchen der Site an den Datenerfassungs-Server zurückgesendet. Dadurch kann der Besucher besuchsübergreifend identifiziert werden.

Einige Browser wie Apple Safari akzeptieren jedoch keine Drittanbieter-Cookies. Hierbei handelt es sich um Cookies, die im Browser von anderen Domänen als der aktuellen Website gesetzt werden. Zusätzlich blockiert Safari Cookies auf Drittanbieterdomänen, wenn ein Besucher diese Domäne noch nie zuvor besucht hat. Wenn Ihre Domäne z. B. `mysite.com` ist und sich Ihr Datenerfassungsserver unter der Domäne `mysite.omtrdc.net` befindet, wird der von `mysite.omtrdc.net` im HTTP-Header zurückgegebene Cookie möglicherweise vom Browser abgewiesen.

Damit dies umgangen werden kann, haben viele Kunden CNAME-Einträge für ihre Datenerfassungsserver implementiert. Dies kann ein effektiver Bestandteil einer [Erstanbieter-Cookie-Implementierungsstrategie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-first-party.html?lang=de) sein. Wenn ein CNAME-Eintrag so konfiguriert wurde, dass ein Hostname unter der Domäne des Kunden einem Datenerfassungsserver zugeordnet wird (z. B. die Zuordnung von `metrics.mysite.com` zu `mysite.omtrdc.net`), wird das [!DNL Experience Cloud] ID-Cookie gespeichert, da die Datenerfassungsdomäne nun mit der Domäne der Website übereinstimmt. Somit erhöht sich die Wahrscheinlicheit, dass das Cookie des ID-Diensts gespeichert wird. Auf der anderen Seite verursacht diese Strategie Zusatzaufwand, da CNAME-Einträge erstellt und SSL-Zertifikate der Datenerfassungsserver gepflegt werden müssen.

**JavaScript**

JavaScript kann in der Erstanbieterdomäne (der Domäne der aktuellen Website) gesetzte Cookies lesen und schreiben. Der [!DNL Experience Cloud] ID-Dienst verwendet diese Methode, um den Cookie `AMCV_###@AdobeOrg` zu setzen, der sämtliche Besucher-IDs enthält. Die Domäne des Tracking-Servers muss dabei nicht mehr mit der Domäne der Website übereinstimmen, damit der Besucher-ID-Cookie gespeichert wird. In den meisten Fällen ist dies die bevorzugte Methode zum Setzen des ID-Dienst-Cookies, da dadurch der Mehraufwand für CNAME-Einträge und SSL-Zertifikate entfällt.

<!---However, there are a few situations where setting the cookie in the HTTP header is beneficial for cross-domain tracking, which is described in [Data Collection CNAMEs and Cross-Domain Tracking](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).-->

## Benutzerdefinierte ID für Analytics  {#section-b6a7bd19e9ff432390010062450808f6}

In Analytics können Besucher identifiziert werden, indem eine Kunden-ID mit `s.visitorID` festgelegt wird. Integrationen jedoch, bei denen Daten mithilfe des ID-Dienstes aus Analytics exportiert oder in die Anwendung importiert werden, funktionieren nicht, wenn ein Besucher mithilfe von `s.visitorID`.

Hierzu gehören unter anderem gemeinsam genutzte Zielgruppen, Analytics for Target (A4T) und Kundenattribute. Bei diesen Integrationen wird die Festlegung einer benutzerdefinierten Analytics ID nicht unterstützt.

## Reihenfolge für Analytics-Besucher-IDs {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

Nach der Bereitstellung des Besucher-ID-Diensts gibt es fünf Möglichkeiten, einen Besucher in Analytics zu identifizieren (in der folgenden Tabelle in der bevorzugten Reihenfolge aufgeführt):

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
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=de" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>s.visitorID festgelegt ist. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=de" format="http" scope="external"> aid (s_vi-Cookie)</a> </p> </td> 
   <td colname="col3"> <p>der Besucher bereits über ein s_vi-Cookie verfügte, bevor Sie den <span class="keyword">Experience Cloud</span> ID-Dienst einsetzten, oder Sie haben eine <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">Übergangsphase</a> konfiguriert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (AMCV_-Cookie, das vom Experience Cloud-Besucher-ID-Dienst gesetzt wird) </p> </td> 
   <td colname="col3"> <p>der Browser des Besuchers Erstanbieter-Cookies akzeptiert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/analytics-ids.html?lang=de" format="http" scope="external"> fid (Ausweichcookie für H.25.3 oder AppMeasurement für JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Ein Browser akzeptiert keine Drittanbietercookies, und der Analytics-Tracking-Server ist als ein Drittanbieter-Tracking-Server eingerichtet. </p> <p> <p>Hinweis: Das <span class="codeph">fid</span> ist eine Legacy-ID und wird nicht verwendet, wenn Sie den ID-Dienst auf Ihrer Website implementiert haben. In diesem Fall wird <span class="codeph">fid</span> nicht benötigt, da das Erstanbieter-<a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV-Cookie</a> es obsolet macht. Es wurde für die Unterstützung von altem Code und aus Verlaufsgründen beibehalten. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/technotes/visitor-identification.html" format="http" scope="external"> IP-Adresse, Benutzeragent, Gateway-IP-Adresse</a> </p> </td> 
   <td colname="col3"> <p>der Browser des Besuchers keine Cookies akzeptiert. </p> </td> 
  </tr> 
 </tbody> 
</table>

In vielen Szenarios können für einen Aufruf zwei oder drei verschiedene IDs vorliegen. Analytics verwendet jedoch die erste ID in der Liste als offizielle [!DNL Experience Cloud] ID. Wenn Sie beispielsweise eine benutzerspezifische Besucher-ID festlegen (die im vid-Abfrageparameter enthalten ist), wird diese ID bevorzugt vor anderen IDs verwendet, die möglicherweise für denselben Treffer vorliegen.

>[!MORELIKETHIS]
>
>* [Reihenfolge der Befehle für Analytics-IDs](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

