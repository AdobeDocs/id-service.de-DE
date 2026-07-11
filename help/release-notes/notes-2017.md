---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Besucher-ID-Service im Jahr 2017.
keywords: Besucher-ID-Service
title: Versionshinweise für 2017
exl-id: 0b51d3b1-e405-4473-9e1a-f89a55250e5e
TQID: https://experienceleague.adobe.com/lt0zISb6FrqIuziYTt8pA6VZyU4XQkVsIha19v-LU7w
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 751
ht-degree: 47%

---

# Versionshinweise für 2017 {#release-notes}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Besucher-ID-Service im Jahr 2017.

Diese Änderungen werden auch in den [CX Enterprise-Versionshinweisen](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=de) erfasst.

>[!NOTE]
>
>Für die Monate März, April, Mai und Oktober 2017 gibt es keine kundenbezogenen Versionshinweise oder Code-Änderungen. In diesen Monaten blieb der Visitor ID Service-Code mit Version 2.1 unverändert.

## Version 2.5 {#section-27b441509124493f80984ed09bd9e88b}

September 2017

<!--
<p>
<note type="important">
Visitor ID Service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>Hierbei handelt es sich um eine asynchrone API, die standardmäßig Kennungen für Analytics, den Besucher-ID-Service, das Opt-out von der Datenerfassung, den geografischen Standort und „Blob“-Inhalte von Metadaten zurückgibt. Sie können auch mit dem optionalen Aufzählungswert <span class="codeph"> visitor.FIELDS</span> steuern, welche IDs zurückgegeben werden. Siehe <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerbehebungen und andere Änderungen**

* Es wurde ein Fehler im Zusammenhang mit Chrome behoben, der dazu führte, dass der Besucher-ID-Dienst beim Klicken auf die Schaltfläche „Zurück“ in diesem Browser einen Fehler ausgab.
* Der Besucher-ID-Dienst löst jetzt ID-Synchronisierungen erneut aus, wenn sich die Regions-ID in der Antwort des Ereignisaufrufs ändert.
* Es wurde die neue Dokumentation [Inhaltssicherheitsrichtlinien und der Besucher-ID-Dienst](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3) hinzugefügt, in der erläutert wird, wie Sie Aufrufe an Adobe-Domains, die vom Besucher-ID-Dienst verwendet werden, auf die Whitelist setzen können.

<!--
## Version 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

August, 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>An optional, Boolean configuration that determines if the Visitor ID Service sends (or does not send) data to the Adobe Device Co-op. See <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Revised Documentation**

Updated and revised the [FAQs](/help/faq-intro/faq-intro.md) to include separate FAQs for different CX Enterprise solutions. 
-->

## Version 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

Juli 2017

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>Wenn diese Konfiguration der Funktion <span class="codeph">Visitor.getInstance</span> hinzugefügt wird, können Sie das standardmäßige Ablaufintervall für die SDID (Supplemental Data ID) bei der Übergabe der ID an eine andere Seite überschreiben. Die Funktion <span class="codeph">sdidParamExpiry</span> wird zusammen mit der Hilfsfunktion <span class="codeph">appendSupplimentalDataTo</span> verwendet. Siehe <a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>Diese Funktion wurde hauptsächlich für A4T-Kunden entwickelt, um sie bei der Lösung von Problemen bei der Arbeit mit IDs auf Single-Page-Sites/-Bildschirmen oder -Apps zu unterstützen. Siehe <a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local">resetState</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerbehebungen und andere Änderungen**

* Es wurde ein Fehler in `VisitorAPI.js` v2.2 behoben, der verhinderte, dass der Besucher-ID-Dienst und Target in Internet Explorer zusammenarbeiteten.
* Überarbeiteter Code, um zu verbessern, wie der Besucher-ID-Service Daten an den Destination Publishing iFrame sendet. Dadurch wird die CPU-Auslastung reduziert.

## Version 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

Veröffentlichung: Juni 2017

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain und whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>Mit diesen Konfigurationen können verschiedene Instanzen des Besucher-ID-Dienst-Codes, die in einem iFrame implementiert sind und sich auf der übergeordneten Seite befinden, miteinander kommunizieren. Sie sollen dabei helfen, Probleme in zwei bestimmten Anwendungsfällen zu lösen, in denen Sie die übergeordnete Seite/Domain steuern oder auch nicht und bei denen der Besucher-ID-Dienst-Code im iFrame einer Domain geladen wird, die Sie steuern. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Aktualisierungen der Dokumentation für Mai {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Thema </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../faq-intro/faq.md" format="dita" scope="local"> FAQs </a> </p> </td> 
   <td colname="col2"> <p>Der <span class="keyword">Analytics</span>-Abschnitt wurde mit Angaben zum Auffinden von Tracking-Serverinformationen aktualisiert. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Aktualisierungen der Dokumentation für April {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Thema </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer und audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>Der <span class="keyword">Audience Manager</span>-Dokumentation wurden Links zu Informationen hinzugefügt, die Aufrufe an die <span class="codeph">demdex.net</span>-Domain beschreiben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten </a> </p> </td> 
   <td colname="col2"> <p>Der Abschnitt <span class="keyword">Media Optimizer</span> wurde überarbeitet, um den Aufruf an <span class="codeph">cm.eversttech.net</span> zu beschreiben. Dies ist die automatische ID-Synchronisierung, die der Besucher-ID-Service mit <span class="keyword"> Media Optimizer durchführt</span>. Diese Funktion wurde im Januar 2017 veröffentlicht. Siehe <a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">Version 2.0</a> weiter unten. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

Veröffentlichungsdatum: Februar 2017

**Funktionen**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> Besucher-ID-Dienst-API-Eigenschaft, <span class="codeph"> idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>Durch diese Eigenschaft wird die Container-ID festgelegt, die von <span class="keyword">Audience Manager</span> für ID-Synchronisationen verwendet wird. Weitere Details unter <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external"> idSyncContainerID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Visitor ID Service API-Methode, <span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>,<span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>Bei dieser öffentlichen Methode wird die Zusatzdaten-ID (<span class="wintitle">Supplemental Data ID</span>/SDID) als Abfragezeichenfolgenparameter an eine Umleitungs-URL angehängt. Siehe <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local">appendSupplementalDataIDTo</a>. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerkorrekturen**

Es wurde ein Fehler behoben, der dazu führte, dass der Besucher-ID-Dienst redundante Server-Aufrufe für eine ID durchführte, anstatt die im AMCV-Cookie gespeicherte ID zu verwenden. (MCID-296)

**Neue Dokumentation**

[Verwenden des DNS-Vorabrufs mit verschiedenen CX Enterprise-Lösungen und -Services](https://experienceleague.adobe.com/docs/core-services/interface/more-resources/dns-prefetch.html?lang=de)

## Version 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

Januar 2017

>[!IMPORTANT]
>
>Der Besucher-ID-Dienst-Code v2.0 synchronisiert IDs standardmäßig automatisch mit Adobe Media Optimizer. Dies bedeutet, dass die Seite `cm.eversttech.net` aufruft, eine ältere Media Optimizer-Domain, die von Adobe verwaltet wird. Weitere Informationen finden Sie unter [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Fehlerbehebungen und Verbesserungen**

* Es wurde ein Fehler behoben, durch den AppMeasurement keine Tracking-Aufrufe an Analytics senden konnte. (MCID-254, MCID-256, MCID-286)
* Es wurde ein Fehler behoben, der verhinderte, dass der Besucher-ID-Dienst sofort fehlschlug, wenn ein Besucher eine Anzeigensperre aktiviert hatte, die so konfiguriert war, dass sie die Domain demdex.net ausschließt. Dieser Fehler ist selten und ungewöhnlich, da die meisten Werbeblocker die Domain „demdex.net“ nicht blockieren. (MCID-233)
* Es wurde ein Fehler behoben, der durch Interaktionen zwischen dem Code des Besucher-ID-Service und einem benutzerdefinierten Skript auf der Website eines Kunden verursacht wurde. Dieses Problem verhinderte das Laden von Webseiten in Internet Explorer 9. (MCID-206)

## Frühere Jahre {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Ältere Versionshinweise zum Besucher-ID-Service.

