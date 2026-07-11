---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Besucher-ID-Service im Jahr 2016.
keywords: Besucher-ID-Service
title: Versionshinweise für 2016
feature-set: Experience Cloud Services
feature: TK421
exl-id: f96b9869-6282-4090-b392-797608e25a51
TQID: https://experienceleague.adobe.com/u91aLAt-ycKk1U1A1yhAVUAonGhV6fHWNRVTZB0QAXI
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11id: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 1114
ht-degree: 47%

---

# Versionshinweise für 2016 {#release-notes}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Besucher-ID-Service im Jahr 2016.

Diese Änderungen werden auch in den [CX Enterprise-Versionshinweisen](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=de) erfasst.

## Version 1.10 {#section-7d719b3213344a46858835042e0214ed}

November 2016

>[!IMPORTANT]
>
>* Version 1.10 erfordert [!UICONTROL AppMeasurement] 1.8.0.
>* Ab Version 2.0.0 des Besucher-ID-Service beginnt die ID-Synchronisierung für Adobe Media Optimizer standardmäßig. Weitere Informationen finden Sie unter [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](/help/introduction/match-rates.md).

**Fehlerbehebungen und Verbesserungen**

* Es wurden Anweisungen zur Implementierung des Besucher-ID-Service in einer Server-seitigen Umgebung hinzugefügt.
* `Visitor.overwriteCrossDomainMCIDAndAID` wurde eine boolesche Funktion hinzugefügt, mit der Sie die ECID- und Analytics-IDs in anderen Domains, deren Inhaber Sie sind, überschreiben können. Siehe [Besucher-ID überschreiben](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* `TS = UTC` Zeitstempel als Eigenschaft der Funktion `visitor.appendVisitorIDsTo` hinzugefügt. Der Besucher-ID-Dienst verwendet den Zeitstempel, um zu bestimmen, ob die IDs in der Umleitungs-URL basierend auf einem 5-minütigen Alterungsintervall verwendet werden sollen. Siehe [Funktion zum Anhängen der Besucher-ID](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Es wurde `Visitor.getLocationHint,` eine neue Funktion hinzugefügt, die eine Region-ID zurückgibt. Siehe [Get Region IDs (Standorthinweis)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* `idSyncByURL` und `idSyncByDataSource` wurden hinzugefügt, 2 Funktionen, mit der Sie manuell eine ID-Synchronisation im Destination Publishing iFrame implementieren können. Siehe [ID-Synchronisierung über URL oder Datenquelle](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Ein Fehler wurde behoben, der bei `disableThirdPartyCalls:true` den AppMeasurement-Tracking-Anruf blockiert hat.
* Es wurde ein Fehler behoben, der verhinderte, dass der Besucher-ID-Service die ECID über verschiedene Domains hinweg weitergab.

## Version 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Oktober 2016

**Fehlerbehebungen und Verbesserungen**

* Es wurde ein Fehler behoben, durch den Audience Manager Unique User IDs (AAMUUIDs) als ECIDs an den Besucher-ID-Service übergeben wurden.
* Wenn die Time-to-Live (TTL) für ein AMCV-Cookie abgelaufen ist, gibt der Besucher-ID-Service diese Informationen weiterhin an den Server zurück, solange das Cookie eine ECID enthält. Nach diesem Aufruf führt der Besucher-ID-Dienst einen asynchronen Aufruf durch, um das Cookie zu aktualisieren. Dies verbessert die Leistung, da der Besucher-ID-Dienst nicht auf eine Server-Antwort warten muss. So kann ein bestehender AMCV-Cookiewert verwendet und eine Aktualisierung angefordert werden.
* Der Besucher-ID-Dienst synchronisiert ECIDs (MIDs) automatisch mit Adobe Media Optimizer und anderen internen Adobe-Domains direkt auf der Seite. Die automatische Synchronisierung ist für alle vorhandenen und neuen Konten aktiviert. Dies trägt zur Verbesserung der Übereinstimmungsraten für Media Optimizer bei. Gilt für `VisitorAPI.js` Version 1.8 oder höher. Weitere Informationen finden Sie unter [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Neue und überarbeitete Dokumentation**

**Neu:** [Abrufen von Regionen- und Benutzer-IDs aus dem AMCV-Cookie](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Version 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

September 2016

**Fehlerbehebungen und Verbesserungen**

`disableThirdPartyCalls` wurde als optionale boolesche Kennzeichnung hinzugefügt, die Sie in der Funktion `Visitor.getInstance` festlegen können. Bei der `disableThirdPartyCalls= true` führt der Besucher-ID-Dienst keine Aufrufe an andere Domains durch. Die Standardeinstellung ist `disableThirdPartyCalls= false`. Siehe [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Version 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

August 2016

**Fehlerbehebungen und Verbesserungen**

* `idSyncAttachIframeOnWindowLoad` wurde als optionale boolesche Kennzeichnung hinzugefügt, die Sie in der Funktion `Visitor.getInstance` festlegen können. Wenn `idSyncAttachIframeOnWindowLoad= true`, lädt der Besucher-ID-Dienst den ID-Synchronisierungs-iFrame beim Laden des Fensters. Standardmäßig lädt der Besucher-ID-Service den iFrame so schnell wie möglich. Diese veraltete Kennzeichnung *ersetzt* `idSyncAttachIframeASAP`. Siehe [Visitor.getInstance-Funktionsvariablen](../library/function-vars/function-vars.md).

* Es wurde eine Funktion hinzugefügt, mit der das Tracking von ECIDs über Domains hinweg unterstützt wird, sowie native Apps und Hybrid-Apps zu Web-Übergängen. Siehe [Hilfsfunktion zum Anhängen der Besucher-ID](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Es wurden Funktionen zu `VisitorAPI.js` Code hinzugefügt, die bestimmen, ob der Besucher-ID-Service die Besucher-ECID Client- oder Server-seitig generiert hat oder ob bei ID-Aufrufen eine Zeitüberschreitung auftrat. Siehe [Funktionen zur Verfolgung von Zeitüberschreitung](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) und [Verfolgen der clientseitigen Besucher-ID-Erstellung](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Neue und überarbeitete Dokumentation**

Überarbeitet: [Anforderungen an den Besucher-ID-Service](../reference/requirements.md)

**Bekannte Probleme**

Kunden und Kundinnen, die Audience Manager DIL-Code und `VisitorAPI.js`-Code auf derselben Seite verwenden, sollten die DIL-`secureDataCollection= false` festlegen. Siehe [secureDataCollection](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=de).

## Version 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Juli 2016

>[!IMPORTANT]
>
>Version 1.6.0 des Besucher-ID-Service *erfordert* AppMeasurement für JavaScript Version 1.6.2. Wenn Sie auf Visitor ID Service Version 1.6.0 aktualisieren, stellen Sie sicher, dass Sie die richtige AppMeasurement-Code-Version verwenden.

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cross-Origin Resource Sharing (CORS) </p> </td> 
   <td colname="col2"> <p>Mit CORS können Browser Ressourcen von einer anderen Domain als der aktuellen anfordern. Der Besucher-ID-Service unterstützt CORS-Standards, um Client-seitige, ursprungsübergreifende Ressourcenanforderungen zu ermöglichen. Der Besucher-ID-Dienst wird auf JSONP-Anfragen in Browsern zurückgesetzt, die CORS nicht unterstützen. </p> <p>Siehe: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> der CORS-Unterstützung im Besucher-ID-Service </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerbehebungen und Verbesserungen**

* Es wurde ein `d_fieldgroup`-Parameter zu ID-Synchronisierungsaufrufen über `dpm.demdex.net` hinzugefügt. Dieser neue Parameter wird zur internen Fehlerbehebung und zum Debuggen verwendet.

* Dem iFrame des Besucher-ID-Service wurde ein Titelattribut hinzugefügt. Mithilfe eines iFrame-Titels können Bildschirmleser Benutzern Seiteninformationen bereitstellen, die Unterstützung bei der Interaktion mit Online-Inhalten benötigen. Das iFrame-Titelattribut ist auf `Adobe ID Syncing iFrame` eingestellt.
* `idSyncAttachIframeASAP: true` wurde als optionale Kennzeichnung hinzugefügt, die Sie in der Funktion `Visitor.getInstance` festlegen können. Bei der `true` lädt der Besucher-ID-Dienst den ID-Synchronisierungs-iFrame so schnell wie möglich. Ziel ist eine Verbesserung der Übereinstimmungsraten bei der ID-Synchronisierung. Standardmäßig lädt der Besucher-ID-Service den iFrame beim Laden des Fensters. Siehe [Visitor.getInstance-Funktionsvariable](../library/function-vars/function-vars.md).

* Es wurde ein Fehler bei einer Rückruffunktion behoben, durch den AppMeasurement in eine Endlosschleife geriet.
* Das standardmäßige `loadTimeout`-Intervall wurde (von 500 Millisekunden) auf 30.000 Millisekunden festgelegt. Siehe [Visitor.getInstance-Funktionsvariable](../library/function-vars/function-vars.md).

**Neue und überarbeitete Dokumentation**

**Neu**

* [Implementieren des Besucher-ID-Service für Analytics, Audience Manager und Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Überarbeitet**

* [Voraussetzungen für den Besucher-ID-Service](../reference/requirements.md)
* [Testen und Überprüfen des Besucher-ID-Service](../implementation-guides/test-verify.md)

## Version 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

Juni 2016

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Änderungen am <span class="codeph">iframe.sandbox</span>-Attribut </p> </td> 
   <td colname="col2"> <p>iFrame ist nun festgelegt wie folgt: <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin'; </span>. </p> <p>Wenn Sie nur diese beiden Token zulassen, wird die Sicherheit verbessert und der Besucher-ID-Dienst verfügt über die grundlegenden Funktionen, die für die ID-Synchronisierung erforderlich sind. </p> <p>Das sandbox-Attribut wird nicht in Internet Explorer Version 9 oder früher unterstützt. Weitere Informationen finden Sie im Abschnitt über Attribute in dieser <a href="https://developer.mozilla.org/de-DE/docs/Web/HTML/Element/iframe" format="https" scope="external">iFrame-Dokumentation</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Codieren der ECID </p> </td> 
   <td colname="col2"> <p>Der Besucher-ID-Dienst verschlüsselt den MID-Wert, der vom Server zurückgegeben oder von der </span> "<span class="codeph"> visitor.setMarketingCloudVisitorID()“ festgelegt wird. Weitere Informationen zur MID finden Sie unter <a href="../introduction/cookies.md" format="dita" scope="local"> von Cookies und ECID-</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerkorrekturen**

Die Besucher-API erzwingt keinen zusätzlichen Aufruf zur erneuten Synchronisierung mit Audience Manager mehr, wenn keine Legacy-Analytics-Besucher-ID vorhanden ist.

## Version 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Mai 2016

**Dokumentation – Aktualisierungen**

* [SDK-Anforderungen für Android und iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Testen und Überprüfen des Besucher-ID-Service](../implementation-guides/test-verify.md)

## Version 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

April 2016

**Dokumentation – Aktualisierungen**

[Implementieren des Besucher-ID-Service für Target](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## Version 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

März 2016

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Funktion </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Abmeldeunterstützung </p> </td> 
   <td colname="col2"> <p>Der Besucher-ID-Dienst unterstützt Opt-out-Anfragen von Besuchern. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Änderung des ID-Synchronisierungsintervalls </p> </td> 
   <td colname="col2"> <p>Der Besucher-ID-Dienst führt ID-Synchronisierungsaufrufe jetzt bei jedem Aufruf der Datenerfassungsserver durch. Zuvor stellte der Besucher-ID-Dienst beim ersten Aufruf nur eine Anfrage, um eine ECID abzurufen. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Januar 2016

**Dokumentation – Aktualisierungen**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Thema </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> Kunden-IDs und Authentifizierungsstatus </a> </p> </td> 
   <td colname="col2"> <p>Überarbeiteter Text. Kunden-IDs dürfen nur als nicht kodierte Werte übergeben werden. Durch das Kodieren von IDs werden doppelt-kodierte IDs erstellt. </p> </td> 
  </tr> 
 </tbody> 
</table>


