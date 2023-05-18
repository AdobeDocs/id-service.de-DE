---
description: Veröffentlichungen von Funktionen sowie Aktualisierungen oder Änderungen des Experience Cloud Identity Services im Jahr 2016.
keywords: ID-Dienst
title: Versionshinweise für 2016
feature-set: Experience Cloud Services
feature: TK421
exl-id: f96b9869-6282-4090-b392-797608e25a51
source-git-commit: d027f7fca8cf62d6b5d80ec3c37049ddd1afdd70
workflow-type: ht
source-wordcount: '1146'
ht-degree: 100%

---

# Versionshinweise für 2016 {#release-notes}

Veröffentlichungen von Funktionen sowie Aktualisierungen oder Änderungen des Experience Cloud Identity Services im Jahr 2016.

Diese Änderungen finden Sie auch in den [Experience Cloud-Versionshinweisen](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=de).

## Version 1.10 {#section-7d719b3213344a46858835042e0214ed}

November 2016

>[!IMPORTANT]
>
>* Für Version 1.10 wird [!UICONTROL AppMeasurement] 1.8.0 benötigt.
>* Ab Experience Cloud Identity Service-Bibliothek 2.0.0 beginnt die ID-Synchronisierung für Adobe Media Optimizer automatisch. Weitere Informationen finden Sie unter [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](/help/introduction/match-rates.md).


**Fehlerbehebungen und Verbesserungen**

* Es wurden Anweisungen hinsichtlich der Implementierung des ID-Diensts in einer serverseitigen Umgebung hinzugefügt.
* `Visitor.overwriteCrossDomainMCIDAndAID` wurde hinzugefügt, eine boolesche Funktion, mit der Sie die Experience Cloud- und Analytics-IDs auf anderen Domänen, deren Inhaber Sie sind, überschreiben können. Siehe [Besucher-ID überschreiben](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* `TS = UTC` Zeitstempel als Eigenschaft der Funktion `visitor.appendVisitorIDsTo` hinzugefügt. Der ID-Dienst legt mithilfe des Zeitstempels fest, ob die IDs in der Umleitungs-URL basierend auf einem 5-minütigen Alterungsintervall verwendet werden sollen. Siehe [Funktion zum Anhängen der Besucher-ID](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Es wurde `Visitor.getLocationHint,` eine neue Funktion hinzugefügt, die eine Region-ID zurückgibt. Siehe [Get Region IDs (Standorthinweis)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* `idSyncByURL` und `idSyncByDataSource` wurden hinzugefügt, 2 Funktionen, mit der Sie manuell eine ID-Synchronisation im Destination Publishing iFrame implementieren können. Siehe [ID-Synchronisierung über URL oder Datenquelle](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Ein Fehler wurde behoben, der bei `disableThirdPartyCalls:true` den AppMeasurement-Tracking-Anruf blockiert hat.
* Ein Fehler wurde behoben, bei dem der ID-Dienst daran gehindert wurde, die Experience Cloud ID (MID) über verschiedene Domänen hinweg zu übergeben.

## Version 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Oktober 2016

**Fehlerbehebungen und Verbesserungen**

* Es wurde ein Fehler behoben, der eindeutige Benutzer-IDs von Audience Manager (AAMUUIDs) als Experience Cloud IDs an den ID-Dienst weitergeleitet hatte.
* Wenn die Time-To-Live (TTL) für ein AMCV-Cookie abgelaufen ist, gibt der ID-Service die Information trotzdem an den Server weiter, sofern das Cookie eine Experience Cloud ID hat. Nach diesem Aufruf startet der ID-Dienst einen asynchronen Aufruf, um das Cookie zu aktualisieren. Damit wird die Leistung verbessert, da der ID-Dienst nicht mehr auf eine Antwort des Servers warten muss. So kann ein bestehender AMCV-Cookiewert verwendet und eine Aktualisierung angefordert werden.
* Der ID-Dienst synchronisiert Experience Cloud IDs (MIDs) automatisch mit Adobe Media Optimizer und anderen internen Adobe-Domänen direkt auf der Seite. Die automatische Synchronisierung ist für alle vorhandenen und neuen Konten aktiviert. Dies trägt zur Verbesserung der Übereinstimmungsraten für Media Optimizer bei. Für VisitorAPI.js Version 1.8 oder höher. Weitere Informationen finden Sie unter [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Neue und überarbeitete Dokumentation**

**Neu:** [Abrufen von Regionen- und Benutzer-IDs aus dem AMCV-Cookie](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Version 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

September 2016

**Fehlerbehebungen und Verbesserungen**

`disableThirdPartyCalls` wurde als optionale boolesche Kennzeichnung hinzugefügt, die Sie in der Funktion `Visitor.getInstance` festlegen können. Bei `disableThirdPartyCalls= true` gibt der ID-Dienst keine Aufrufe an andere Domänen aus. Die Standardeinstellung ist `disableThirdPartyCalls= false`. Siehe [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Version 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

August 2016

**Fehlerbehebungen und Verbesserungen**

* `idSyncAttachIframeOnWindowLoad` wurde als optionale boolesche Kennzeichnung hinzugefügt, die Sie in der Funktion `Visitor.getInstance` festlegen können. Wenn `idSyncAttachIframeOnWindowLoad= true`, dann lädt der ID-Dienst den iFrame zur ID-Synchronisierung beim Laden des Fensters. Standardmäßig lädt der ID-Dienst den iFrame so schnell wie möglich. Diese veraltete Kennzeichnung *ersetzt* `idSyncAttachIframeASAP`. Siehe [Visitor.getInstance-Funktionsvariablen](../library/function-vars/function-vars.md).

* Es wurde eine Funktion hinzugefügt, mit der [!DNL Experience Cloud] IDs über Domänen sowie native und hybride Anwendungen hinweg bis hin zu Webübergängen verfolgt werden können. Siehe [Hilfsfunktion zum Anhängen der Besucher-ID](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Dem Code von visitorAPI.js wurden Funktionen hinzugefügt, mit denen festgestellt werden kann, ob der ID-Dienst die [!DNL Experience Cloud] ID von Besuchern client- oder serverseitig generiert hat oder bei ID-Aufrufen eine Zeitüberschreitung aufgetreten ist. Siehe [Funktionen zur Verfolgung von Zeitüberschreitung](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) und [Verfolgen der clientseitigen Besucher-ID-Erstellung](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Neue und überarbeitete Dokumentation**

Überarbeitet: [Anforderungen an den Experience Cloud Identity Service](../reference/requirements.md)

**Bekannte Probleme**

Kunden, die [!DNL Audience Manager] DIL-Code und visitorAPI.js-Code auf derselben Seite verwenden, sollten die DIL-Variable `secureDataCollection= false`festlegen. Siehe [secureDataCollection](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=de).

## Version 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Juli 2016

>[!IMPORTANT]
>
>Für die Version 1.6.0 des [!DNL Experience Cloud] ID-Diensts ist AppMeasurement für JavaScript Version 1.6.2 *erforderlich*. Stellen Sie beim Upgrade auf ID-Dienstversion 1.6.0 sicher, dass Sie die richtige AppMeasurement-Codeversion verwenden.

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
   <td colname="col2"> <p>Mit CORS können Browser Ressourcen von einer anderen Domain als der aktuellen anfordern. Der Experience Cloud Identity Service bietet Unterstützung für CORS-Standards und ermöglicht somit clientseitige, ursprungsübergreifende Ressourcenanforderungen. Der ID-Dienst greift bei Browsern ohne CORS-Unterstützung auf JSONP-Anforderungen zurück. </p> <p>Siehe: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local">CORS-Unterstützung im Experience Cloud Identity Service</a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerbehebungen und Verbesserungen**

* Es wurde ein `d_fieldgroup`-Parameter zu ID-Synchronisierungsaufrufen über `dpm.demdex.net` hinzugefügt. Dieser neue Parameter wird zur internen Fehlerbehebung und zum Debuggen verwendet.

* Dem iFrame des ID-Diensts wurde ein Titelattribut hinzugefügt. Mithilfe eines iFrame-Titels können Bildschirmleser Benutzern Seiteninformationen bereitstellen, die Unterstützung bei der Interaktion mit Online-Inhalten benötigen. Das iFrame-Titelattribut ist auf `Adobe ID Syncing iFrame` eingestellt.
* `idSyncAttachIframeASAP: true` wurde als optionale Kennzeichnung hinzugefügt, die Sie in der Funktion `Visitor.getInstance` festlegen können. Wenn `true` ist, wird der ID-Synchronisierungs-iFrame so schnell wie möglich vom ID-Dienst geladen. Ziel ist eine Verbesserung der Übereinstimmungsraten bei der ID-Synchronisierung. Der iFrame wird vom ID-Dienst standardmäßig beim Laden des Fensters geladen. Siehe [Visitor.getInstance-Funktionsvariable](../library/function-vars/function-vars.md).

* Es wurde ein Fehler bei einer Rückruffunktion behoben, durch den AppMeasurement in eine Endlosschleife geriet.
* Das standardmäßige `loadTimeout`-Intervall wurde (von 500 Millisekunden) auf 30.000 Millisekunden festgelegt. Siehe [Visitor.getInstance-Funktionsvariable](../library/function-vars/function-vars.md).

**Neue und überarbeitete Dokumentation**

**Neu**

* [Implementieren des Experience Cloud Identity Services für Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Implementieren des Experience Cloud Identity Services für Analytics, Audience Manager und Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Überarbeitet**

* [Voraussetzungen für den Experience Cloud Identity-Service](../reference/requirements.md)
* [Testen und Überprüfen des Experience Cloud Identity-Service](../implementation-guides/test-verify.md)

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
   <td colname="col2"> <p>iFrame ist nun festgelegt wie folgt: <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin'; </span>. </p> <p>Die Beschränkung auf diese beiden zulässigen Token erhöht die Sicherheit und stattet den ID-Dienst mit den grundlegenden, für die ID-Synchronisierung benötigten Funktionen aus. </p> <p>Das sandbox-Attribut wird nicht in Internet Explorer Version 9 oder früher unterstützt. Weitere Informationen finden Sie im Abschnitt über Attribute in dieser <a href="https://developer.mozilla.org/de-DE/docs/Web/HTML/Element/iframe" format="https" scope="external">iFrame-Dokumentation</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Verschlüsseln der Experience Cloud ID (MID) </p> </td> 
   <td colname="col2"> <p>Der ID-Service verschlüsselt den MID-Wert, der vom Server zurückgegeben oder von der Funktion <span class="codeph">visitor.setMarketingCloudVisitorID()</span> festgelegt wird. Weitere Informationen zu MID finden Sie unter <a href="../introduction/cookies.md" format="dita" scope="local">Cookies und die Experience Cloud ID</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerbehebungen**

Die Besucher-API erzwingt keinen zusätzlichen Aufruf zur erneuten Synchronisierung mit Audience Manager mehr, wenn keine Legacy-Analytics-Besucher-ID vorhanden ist.

## Version 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Mai 2016

**Dokumentation – Aktualisierungen**

* [SDK-Anforderungen für Android und iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench und der Experience Cloud Identity-Service](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [Testen und Überprüfen des Experience Cloud Identity-Service](../implementation-guides/test-verify.md)

## Version 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

April 2016

**Dokumentation – Aktualisierungen**

[Implementieren des Experience Cloud Identity Services für Target](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

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
   <td colname="col2"> <p>Der <span class="keyword">Experience Cloud</span> ID-Dienst unterstützt Abmeldeanfragen von Besuchern. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Änderung des ID-Synchronisierungsintervalls </p> </td> 
   <td colname="col2"> <p>Der <span class="keyword">Experience Cloud ID</span>-Service führt ID-Synchronisierungsaufrufe nun bei jedem Aufruf der Datenerfassungsserver durch. Zuvor gab der ID-Dienst nur eine Anforderung beim ersten Aufruf auf, um eine <span class="keyword">Experience Cloud</span> ID zu erhalten. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Dokumentation – Aktualisierungen**

* [Implementierung des Experience Cloud Identity Services für](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd): Neue Vorgehensweise, die die Einrichtung des ID-Diensts mit Analytics [!DNL Analytics] beschreibt.

* [Entscheidungspunkte zur Experience Cloud Identity Servicemigration](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257): Überarbeiteter Text für mehr Klarheit. Wenn Sie mit nur einen Domain arbeiten, können Sie einen Datenerfassungs-CNAME eliminieren, wenn Sie ihn nicht mehr unterhalten möchten. Wenn Ihr CNAME funktioniert, ist dies jedoch nicht notwendig.

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
