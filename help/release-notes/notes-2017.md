---
description: Funktionen, Aktualisierungen oder Änderungen am Experience Cloud-Identitätsdienst für 2017.
keywords: ID-Dienst
seo-description: Funktionen, Aktualisierungen oder Änderungen am Experience Cloud-Identitätsdienst für 2017.
seo-title: Versionshinweise für 2017
title: Versionshinweise für 2017
uuid: 79452df0-49db-42b8-96fe-01aa7629fbb5
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Versionshinweise für 2017 {#release-notes}

Funktionen, Aktualisierungen oder Änderungen am Experience Cloud-Identitätsdienst für 2017.

Diese Änderungen sind auch in den [Experience Cloud-Versionshinweisen](https://marketing.adobe.com/resources/help/en_US/whatsnew/) enthalten. Ältere ID-Dienst-Versionshinweise finden Sie unter [frühere Versionshinweise](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html) oder über die Links am unteren Rand dieser Seite.

>[!NOTE]
>
>Für die Monate März, April, Mai und Oktober 2017 gibt es keine kundenbezogenen Versionshinweise oder Code-Änderungen. Für diese Monate blieb der ID-Dienstcode unverändert auf dem Stand von Version 2.1.

## Version 2.5 {#section-27b441509124493f80984ed09bd9e88b}

September 2017

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
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
   <td colname="col2"> <p>Hierbei handelt es sich um eine asynchrone API, die standardmäßig IDs für Analytics, den ID-Dienst, die Abmeldung von der Datenerfassung, den geografischen Standort und Metadateninhalte („Blob“) zurückgibt. Sie können auch mit dem optionalen Enum-Wert <span class="codeph"> visitor.FIELDS</span> steuern, welche IDs zurückgegeben werden. Siehe <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerbehebungen und andere Änderungen**

* Es wurde ein Problem mit Chrome behoben, bei dem der ID-Dienst beim Klick auf die Zurück-Schaltfläche im Browser einen Fehler ausgelöst hat.
* Der ID-Dienst wiederholt die ID-Synchronisationen nun, wenn sich die Regions-ID in der Ereignisaufrufantwort ändert.
* Es wurde neue Dokumentation hinzugefügt: [Content Security-Richtlinien und der Experience Cloud-Identitätsdienst](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3), der erklärt, wie Whitelist-Aufrufe an die von dem ID-Dienst verwendeten Adobe-Domänen gesendet werden.

## Version 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

August 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>Eine optionale boolesche Konfiguration, die festlegt, ob der ID-Dienst Daten an die Adobe Experience Cloud-Gerätekooperation sendet oder nicht. <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local">isCoopSafe</a> anzeigen. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Überarbeitete Dokumentation**

Der Abschnitt [Häufig gestellte Fragen (FAQ)](/help/faq-intro/faq-intro.md) wurde aktualisiert und überarbeitet und enthält jetzt separate häufig gestellte Fragen für unterschiedliche [!DNL Experience Cloud]-Lösungen.

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

* Ein Fehler in VisitorAPI.js v2.2 wurde behoben, der dazu führte, dass der ID-Dienst nicht zusammen mit Target in Internet Explorer funktionierte.
* Code wurde überarbeitet, um zu verbessern, wie der ID-Dienst Daten an den Destination Publishing iFrame sendet. Dadurch wird die CPU entlastet.

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
   <td colname="col2"> <p>Diese Konfigurationen ermöglichen die Kommunikation zwischen verschiedenen Instanzen von ID-Dienstcode, die in einem iFrame implementiert sind, und solchen, die in die übergeordnete Seite implementiert sind. Sie sollen dabei helfen, Probleme in zwei konkreten Nutzungsszenarios zu lösen, in denen Sie die übergeordnete Seite/Domäne verwalten oder auch nicht und bei denen ID-Dienstcode im iFrame einer von Ihnen verwalteten Domäne geladen wird. </p> </td> 
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
   <td colname="col2"> <p>Der <span class="keyword">Audience Manager</span>-Dokumentation wurden Links zu Informationen hinzugefügt, die Aufrufe an die <span class="codeph">demdex.net</span>-Domäne beschreiben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten </a> </p> </td> 
   <td colname="col2"> <p>Der Abschnitt <span class="keyword">Media Optimizer</span> wurde überarbeitet, um den Aufruf an <span class="codeph">cm.eversttech.net</span> zu beschreiben. Dabei handelt es sich um eine automatische ID-Synchronisierung, die der ID-Dienst mit <span class="keyword">Media Optimizer</span> durchführt. Diese Funktion wurde im Januar 2017 veröffentlicht. Siehe <a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">Version 2.0</a> weiter unten. </p> </td> 
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
   <td colname="col1"> <p> ID-Dienst-API-Eigenschaft, <span class="codeph">idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>Durch diese Eigenschaft wird die Container-ID festgelegt, die von <span class="keyword">Audience Manager</span> für ID-Synchronisationen verwendet wird. Weitere Details unter <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external"> idSyncContainerID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>ID-Dienst-API-Methode, <span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>,<span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>Bei dieser öffentlichen Methode wird die Zusatzdaten-ID (<span class="wintitle">Supplemental Data ID</span>/SDID) als Abfragezeichenfolgenparameter an eine Umleitungs-URL angehängt. Siehe <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local">appendSupplementalDataIDTo</a>. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerbehebungen**

Es wurde ein Fehler behoben, durch den der ID-Dienst redundante Serveraufrufe für eine ID durchführte, statt die im AMCV-Cookie gespeicherte ID zu verwenden. (MCID-296)

**Neue Dokumentation**

[Verwendung der DNS-Vorab-Abfrage mit unterschiedlichen Experience Cloud-Lösungen und -Services `Learn how to use DNS prefetch to help reduce page load times.`](https://marketing.adobe.com/resources/help/en_US/mcloud/dns-prefetch.html)

## Version 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

Januar 2017

>[!IMPORTANT]
>
>Der ID-Dienst-Code v2.0 synchronisiert IDs standardmäßig automatisch mit Adobe Media Optimizer. Das bedeutet, dass die Seite `cm.eversttech.net`, eine ältere [!DNL Media Optimizer]-Domäne, die von [!DNL Adobe] verwaltet wird, aufruft. Weitere Informationen finden Sie unter [Informationen zu ID-Synchronisation und Trefferquote](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Fehlerbehebungen und Verbesserungen**

* Es wurde ein Fehler behoben, der AppMeasurement an der Durchführung von Tracking-Anrufen an Analytics hinderte. (MCID-254, MCID-256, MCID-286)
* Es wurde ein Fehler behoben, durch den beim ID-Dienst nicht direkt ein Fehler auftrat, wenn ein Besucher eine Anzeigensperre aktiviert hatte, die darauf konfiguriert war, die Domäne demdex.net auszuschließen. Dieser Fehler ist selten und ungewöhnlich, da die meisten Anzeigensperren die Domäne demdex.net nicht blockieren. (MCID-233)
* Es wurde ein Fehler behoben, der durch die Interaktion zwischen dem Code des ID-Diensts und einem benutzerdefinierten Skript auf der Website eines Kunden hervorgerufen wurde. Durch dieses Problem konnte der Internet Explorer 9 keine Webseiten laden. (MCID-206)

## Frühere Jahre {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Ältere ID-Dienst-Versionshinweise.
