---
description: Der Experience Cloud Identity-Dienst ersetzt die Legacy ID-Methoden für Analytics.
keywords: ID-Dienst
seo-description: Der Experience Platform Identity-Dienst ersetzt die Legacy ID-Methoden für Analytics.
seo-title: Einrichten von Analytics- und Experience Cloud IDs
title: Einrichten von Analytics- und Experience Cloud IDs
uuid: 421cf597-a3e0-4ca3-8ce8-d0c80cbb6aca
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# Einrichten von Analytics- und Experience Cloud IDs{#setting-analytics-and-experience-cloud-ids}

Der Experience Cloud Identity-Dienst ersetzt die Legacy ID-Methoden für Analytics.

Nach Implementierung des ID-Diensts wird dieser Code vor AppMeasurement ausgeführt. Mit dem ID-Dienst werden die IDs für Experience Cloud und Analytics abgerufen, damit diese Werte bereits vorliegen, wenn AppMeasurement geladen wird.

Beim Laden von AppMeasurement werden vom ID-Dienst die IDs für Experience Cloud und Analytics angefordert und mit jedem Server-Aufruf an die Datenerfassung gesendet. Da der ID-Dienst die Besucher-ID bestimmt und sie einfach an AppMeasurement übergibt, muss der ID-Dienst auf jeder Seite vor Ihrer AppMeasurement-JavaScript-Datei eingebunden und implementiert werden.

## Änderungen beim ID-Vorgang für Analytics {#section-79bb86ae63f546419bb1a7ef5e710462}

Die wesentliche Änderung bei der Migration auf den [!DNL Experience Cloud] ID-Dienst besteht darin, dass das ID-Cookie nun mit JavaScript gesetzt wird und nicht mehr im HTTP-Header, der vom Datenerfassungs-Webserver zurückgegeben wird. Um diese Änderung besser nachvollziehen zu können, werden in den folgenden Abschnitten die beiden Methoden zum Setzen von Cookies beschrieben.

**HTTP-Header**

Eine HTTP-Antwort eines Webservers setzt Cookies in einem Browser. So wird das `s_vi`-Cookie gesetzt. Mit dem `s_vi`-Cookie werden Analytics-Besucher identifiziert. Nachdem ein Cookie gesetzt wurde, wird es mit allen nachfolgenden HTTP-Anforderungen an den Server gesendet.

Wenn eine Anforderung an den Adobe-Datenerfassungsserver gesendet wird, wird geprüft, ob der Header einen `s_vi`-Cookie enthält. Wenn der Cookie in der Anforderung enthalten ist, wird er zur Identifizierung des Besuchers verwendet. Wenn der Cookie nicht in der Anforderung enthalten ist, generiert der Server eine eindeutige [!DNL Experience Cloud] ID, setzt sie als Cookie im HTTP-Antwort-Header und sendet diesen mit der Anforderung zurück. Der Cookie wird im Browser gespeichert und bei künftigen Besuchen der Seite an den Datenerfassungsserver zurückgesendet. Das ermöglicht die Identifikation des Besuchers über mehrere Besuche hinweg.

In einigen Browsern jedoch, wie beispielsweise Apple Safari, werden keine Cookies von Drittanbietern gespeichert. Dabei handelt es sich um im Browser gesetzte Cookies, die von anderen Domänen als der aktuell besuchten Website stammen. Zudem werden in Safari Cookies von Drittanbieterdomänen blockiert, wenn ein Besucher diese Domäne noch nie aufgerufen hat. Wenn Ihre Domäne z. B. `mysite.com` ist und sich Ihr Datenerfassungsserver unter der Domäne `mysite.omtrdc.net` befindet, wird der von `mysite.omtrdc.net` im HTTP-Header zurückgegebene Cookie möglicherweise vom Browser abgewiesen.

Damit dies umgangen werden kann, haben viele Kunden CNAME-Einträge für ihre Datenerfassungsserver implementiert. Dieser Vorgang kann effektiver Teil einer Strategie zur [Erstanbieter-Cookie-Implementierung](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/) sein. Wenn ein CNAME-Eintrag so konfiguriert wurde, dass ein Hostname unter der Domäne des Kunden einem Datenerfassungsserver zugeordnet wird (z. B. die Zuordnung von `metrics.mysite.com` zu `mysite.omtrdc.net`), wird das [!DNL Experience Cloud] ID-Cookie gespeichert, da die Datenerfassungsdomäne nun mit der Domäne der Website übereinstimmt. Somit erhöht sich die Wahrscheinlicheit, dass das Cookie des ID-Diensts gespeichert wird. Auf der anderen Seite verursacht diese Strategie Zusatzaufwand, da CNAME-Einträge erstellt und SSL-Zertifikate der Datenerfassungsserver gepflegt werden müssen.

**JavaScript**

Mit JavaScript können Cookies geschrieben werden, die in der Erstanbieterdomäne gesetzt werden (in der Domäne der aktuell aufgerufenen Website). Der [!DNL Experience Cloud] ID-Dienst verwendet diese Methode, um den Cookie `AMCV_###@AdobeOrg` zu setzen, der sämtliche Besucher-IDs enthält. Die Domäne des Tracking-Servers muss dabei nicht mehr mit der Domäne der Website übereinstimmen, damit der Besucher-ID-Cookie gespeichert wird. In der Mehrheit der Fälle wird dieses Verfahren für das Setzen des ID-Dienst-Cookies bevorzugt, da auf diese Weise der Aufwand für CNAME-Einträge und SSL-Zertifikate entfällt.

In bestimmten Situationen ist es zum Zweck des domänenübergreifenden Trackings jedoch vorteilhaft, im HTTP-Header Cookies zu setzen. Dies wird im Abschnitt [Datenerfassungs-CNAMEs und domänenübergreifendes Tracking](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d) näher erläutert.

## Benutzerdefinierte ID für Analytics {#section-b6a7bd19e9ff432390010062450808f6}

In Analytics können Besucher identifiziert werden, indem eine Kunden-ID mit `s.visitorID` festgelegt wird. Integrationen jedoch, bei denen Daten mithilfe des ID-Dienstes aus Analytics exportiert oder in die Anwendung importiert werden, funktionieren nicht, wenn ein Besucher mithilfe von `s.visitorID`.

Hierzu gehören unter anderem gemeinsam genutzte Zielgruppen, Analytics for Target (A4T) und Kundenattribute. Bei diesen Integrationen wird die Festlegung einer benutzerdefinierten Analytics ID nicht unterstützt.

## Reihenfolge für Analytics-Besucher-IDs {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

Nach der Bereitstellung des Besucher-ID-Diensts können Besucher in Analytics auf fünf verschiedene Arten identifiziert werden (in der Reihenfolge nach der Übersicht unten):

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Reihenfolge </th> 
   <th colname="col2" class="entry"> Abfrageparameter (Erfassungsmethode) </th> 
   <th colname="col3" class="entry"> Vorhanden, wenn </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>s.visitorID festgelegt ist. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (s_vi-Cookie)</a> </p> </td> 
   <td colname="col3"> <p>der Besucher bereits über ein s_vi-Cookie verfügte, bevor Sie den <span class="keyword">Experience Cloud</span> ID-Dienst einsetzten, oder Sie haben eine <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">Übergangsphase</a> konfiguriert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (AMCV_-Cookie, der vom Experience Cloud-Besucher-ID-Dienst gesetzt wird) </p> </td> 
   <td colname="col3"> <p>der Browser des Besuchers Erstanbieter-Cookies akzeptiert. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (Ausweichcookie für H.25.3 oder AppMeasurement für JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Ein Browser akzeptiert keine Drittanbietercookies, und der Analytics-Tracking-Server ist als ein Drittanbieter-Tracking-Server eingerichtet. </p> <p> <p>Hinweis: Das <span class="codeph">fid</span> ist eine Legacy-ID und wird nicht verwendet, wenn Sie den ID-Dienst auf Ihrer Website implementiert haben. In diesem Fall wird <span class="codeph">fid</span> nicht benötigt, da das Erstanbieter-<a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV-Cookie</a> es obsolet macht. Es wurde für die Unterstützung von altem Code und aus Verlaufsgründen beibehalten. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> IP-Adresse, Benutzeragent, Gateway-IP-Adresse</a> </p> </td> 
   <td colname="col3"> <p>der Browser des Besuchers keine Cookies akzeptiert. </p> </td> 
  </tr> 
 </tbody> 
</table>

In vielen Szenarios können für einen Aufruf zwei oder drei verschiedene IDs vorliegen. Analytics verwendet jedoch die erste ID in der Liste als offizielle [!DNL Experience Cloud] ID. Wenn Sie beispielsweise eine benutzerspezifische Besucher-ID festlegen (die im vid-Abfrageparameter enthalten ist), wird diese ID bevorzugt vor anderen IDs verwendet, die möglicherweise für denselben Treffer vorliegen.

>[!MORELIKETHIS]
>
>* [Reihenfolge der Befehle für Analytics-IDs](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

