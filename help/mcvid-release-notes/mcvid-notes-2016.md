---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud ID-Diensts im Jahr 2016.
keywords: ID-Dienst
seo-description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud ID-Diensts im Jahr 2016.
seo-title: 2016 – Versionshinweise
title: 2016 – Versionshinweise
uuid: 7 a 5 a 314 a -3 ff 8-4561-9 c 64-6 c 10 d 2223887
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 2016 – Versionshinweise {#release-notes}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud ID-Diensts im Jahr 2016.

Diese Änderungen sind auch in den [Experience Cloud-Versionshinweisen](https://marketing.adobe.com/resources/help/en_US/whatsnew/) enthalten. Ältere Ankündigungen finden Sie unter [Frühere Versionshinweise](https://marketing.adobe.com/resources/help/en_US/whatsnew/?f=c_legacy_releases.html).[!DNL Experience Cloud]

## Version 1.10 {#section-7d719b3213344a46858835042e0214ed}

November 2016

>[!IMPORTANT]
>
>* Für Version 1.10 [!DNL AppMeasurement] ist 1.8.0 erforderlich.
>* Ab Experience Cloud ID-Dienst-Bibliothek 2.0.0 beginnt die ID-Synchronisierung für Adobe Media Optimizer standardmäßig. Weitere Informationen finden Sie unter [Informationen zu ID-Synchronisation und Trefferquote](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-match-rates.html).
>



**Fehlerbehebungen und Verbesserungen**

* Es wurden Anweisungen hinsichtlich der Implementierung des ID-Diensts in einer serverseitigen Umgebung hinzugefügt.
* `Visitor.overwriteCrossDomainMCIDAndAID` wurde hinzugefügt, eine boolesche Funktion, mit der Sie die Experience Cloud- und Analytics-IDs auf anderen Domänen, deren Inhaber Sie sind, überschreiben können. Siehe [Besucher-ID überschreiben](../mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* `TS = UTC` Zeitstempel als Eigenschaft der `visitor.appendVisitorIDsTo`Funktion hinzugefügt. Der ID-Dienst ermittelt mit dem Zeitstempel, ob er die IDs in der Umleitungs-URL auf Basis eines 5-Minuten-Ablaufintervalls verwenden sollte. Siehe [Funktion zum Anhängen der Besucher-ID](../mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Es `Visitor.getLocationHint,` wurde eine neue Funktion hinzugefügt, die eine Regions-ID zurückgibt. Siehe [Abrufen von Regions-IDs (Standorthinweis)](../mcvid-library/mcvid-get-set/mcvid-getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

* `idSyncByURL` und `idSyncByDataSource` wurden hinzugefügt, 2 Funktionen, mit der Sie manuell eine ID-Synchronisation im Destination Publishing iFrame implementieren können. Siehe [ID-Synchronisierung nach URL oder Datenquelle](../mcvid-library/mcvid-get-set/mcvid-idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Ein Fehler wurde behoben, der bei `disableThirdPartyCalls:true` den AppMeasurement-Tracking-Anruf blockiert hat. 
* Ein Fehler wurde behoben, bei dem der ID-Dienst daran gehindert wurde, die Experience Cloud ID (MID) über verschiedene Domänen hinweg zu übergeben.

## Version 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Oktober 2016

**Fehlerbehebungen und Verbesserungen**

* Es wurde ein Fehler behoben, durch den Unique User-IDs für Audience Manager (AAMUUIDs) als Experience Cloud IDs an den ID-Dienst übergeben wurden.
* Wenn die Time-To-Live (TTL) für einen AMCV-Cookie abgelaufen ist, gibt der ID-Dienst die Information trotzdem an den Server zurück, sofern der Cookie eine Experience Cloud ID enthält. Nach diesem Aufruf startet der ID-Service einen asynchronen Aufruf, um das Cookie zu aktualisieren. Damit wird die Leistung verbessert, da der ID-Service nicht mehr auf eine Antwort des Servers warten muss. So kann ein bestehender AMCV-Cookiewert verwendet und eine Aktualisierung angefordert werden.
* Der ID-Dienst synchronisiert automatisch Experience Cloud IDs (MIDs) mit Adobe Media Optimizer und anderen internen Adobe-Domänen direkt auf der Seite. Die automatische Synchronisierung ist für alle vorhandenen und neuen Konten aktiviert. So wird die Trefferquote in Media Optimizer verbessert. Für VisitorAPI.js Version 1.8 oder höher. Weitere Informationen finden Sie unter [Informationen zu ID-Synchronisation und Trefferquote](../mcvid-introduction/mcvid-match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Neue und überarbeitete Dokumentation**

**Neu:**[Abrufen von Regions- und Benutzer-IDs aus dem AMCV-Cookie](../mcvid-reference/mcvid-regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Version 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

September 2016

**Fehlerbehebungen und Verbesserungen**

`disableThirdPartyCalls` wurde als optionale boolesche Kennzeichnung hinzugefügt, die Sie in der Funktion `Visitor.getInstance` festlegen können. Bei `disableThirdPartyCalls= true` gibt der ID-Dienst keine Aufrufe an andere Domänen aus. Die Standardeinstellung ist `disableThirdPartyCalls= false`. Siehe [disableThirdPartyCalls](../mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Version 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

August 2016

**Fehlerbehebungen und Verbesserungen**

* `idSyncAttachIframeOnWindowLoad` wurde als optionale boolesche Kennzeichnung hinzugefügt, die Sie in der Funktion `Visitor.getInstance` festlegen können. Wenn `idSyncAttachIframeOnWindowLoad= true` festgelegt ist, lädt der ID-Dienst den iFrame zur ID-Synchronisierung beim Laden des Fensters. Standardmäßig lädt der ID-Dienst den iFrame so schnell wie möglich. Diese Kennzeichnung *ersetzt* die veraltete Kennzeichnung `idSyncAttachIframeASAP`. Siehe [auch Visitor. getinstance-Funktionsvariablen](../mcvid-library/mcvid-function-vars/mcvid-function-vars.md).

* Es wurde eine Funktion hinzugefügt, mit der [!DNL Experience Cloud] IDs über Domänen sowie native und hybride Anwendungen hinweg bis hin zu Webübergängen verfolgt werden können. Siehe [Hilfsfunktion zum Anhängen der Besucher-ID](../mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Dem Code von visitorAPI.js wurden Funktionen hinzugefügt, mit denen festgestellt werden kann, ob der ID-Dienst die [!DNL Experience Cloud] ID von Besuchern Client- oder serverseitig generiert hat oder bei ID-Aufrufen eine Zeitüberschreitung aufgetreten ist. Siehe [Funktionen zur Verfolgung von Zeitüberschreitung](../mcvid-library/mcvid-get-set/mcvid-timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) und [Verfolgen der clientseitigen Besucher-ID-Erstellung](../mcvid-library/mcvid-get-set/mcvid-client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Neue und überarbeitete Dokumentation**

Überarbeitet: [Anforderungen für den Experience Cloud ID-Dienst](../mcvid-reference/mcvid-requirements.md)

**Bekannte Probleme**

Kunden, die [!DNL Audience Manager] DIL-Code und visitorAPI.js-Code auf derselben Seite verwenden, sollten die DIL-Variable `secureDataCollection= false`festlegen. Siehe [secureDataCollection](https://marketing.adobe.com/resources/help/en_US/aam/?f=dil-secure-data-collection.html).

## Version 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Juli 2016

>[!IMPORTANT]
>
>Für Version 1.6.0 des [!DNL Experience Cloud] ID-Diensts *ist* appmeasurement für javascript Version 1.6.2 erforderlich. Wenn Sie ein Upgrade auf den ID-Dienst Version 1.6.0 durchführen, stellen Sie sicher, dass Sie die richtige appmeasurement-Codeversion verwenden.

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
   <td colname="col2"> <p>Mithilfe von CORS können Browser Ressourcen von einer anderen als der aktuellen Domäne anfordern. Der Experience Cloud ID-Dienst bietet Unterstützung für CORS-Standards und ermöglicht somit clientseitige, ursprungsübergreifende Ressourcenanforderungen. Bei Browsern, die keine Unterstützung für CORS bieten, greift der ID-Dienst auf JSONP-Anforderungen zurück. </p> <p>Siehe: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../mcvid-reference/mcvid-cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> CORS-Unterstützung im Experience Cloud ID-Dienst </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerbehebungen und Verbesserungen**

* Es wurde ein `d_fieldgroup`-Parameter zu ID-Synchronisierungsaufrufen über `dpm.demdex.net` hinzugefügt. Dieser neue Parameter wird für die interne Fehlerbehebung und das Debuggen verwendet.

* Es wurde ein Titelattribut zum iFrame des ID-Dienstes hinzugefügt. Durch einen iFrame-Titel können Screenreader Seiteninformationen für Benutzer zur Verfügung stellen, die Hilfe bei der Interaktion mit Onlineinhalten benötigen. Das iFrame-Titelattribut ist auf `Adobe ID Syncing iFrame` eingestellt. 
* `idSyncAttachIframeASAP: true` wurde als optionale Kennzeichnung hinzugefügt, die Sie in der Funktion `Visitor.getInstance` festlegen können. Wenn `true` ist, wird der ID-Synchronisierungs-iFrame so schnell wie möglich vom ID-Dienst geladen. Ziel ist eine Verbesserung der Übereinstimmungsraten bei der ID-Synchronisierung. Der iFrame wird vom ID-Dienst standardmäßig beim Laden des Fensters geladen. Siehe [auch Visitor. getinstance-Funktionsvariablen](../mcvid-library/mcvid-function-vars/mcvid-function-vars.md).

* Es wurde ein Fehler bei einer Rückruffunktion behoben, durch den AppMeasurement in eine Endlosschleife geriet.
* Das standardmäßige `loadTimeout`-Intervall wurde (von 500 Millisekunden) auf 30.000 Millisekunden festgelegt. Siehe [auch Visitor. getinstance-Funktionsvariablen](../mcvid-library/mcvid-function-vars/mcvid-function-vars.md).

**Neue und überarbeitete Dokumentation**

**Neu**

* [Implementieren des Experience Cloud ID-Diensts für Analytics](../mcvid-implementation-guides/mcvid-setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Implementieren des Experience Cloud ID-Diensts für Analytics, Audience Manager und Target](../mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Überarbeitet**

* [Voraussetzungen für den Experience Cloud ID-Dienst](../mcvid-reference/mcvid-requirements.md)
* [Testen und Überprüfen des Experience Cloud ID-Diensts](../mcvid-implementation-guides/mcvid-test-verify.md)

## Version 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

Juni 2016

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
   <td colname="col2"> <p>iFrame ist nun festgelegt wie folgt: <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin'; </span>. </p> <p>Die Beschränkung auf diese beiden zulässigen Token erhöht die Sicherheit und stattet den ID-Dienst mit den grundlegenden, für die ID-Synchronisierung benötigten Funktionen aus. </p> <p>Das sandbox-Attribut wird nicht in Internet Explorer Version 9 oder früher unterstützt. Weitere Informationen finden Sie im Abschnitt über Attribute in dieser <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe" format="https" scope="external">iFrame-Dokumentation </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Verschlüsseln der Experience Cloud ID (MID) </p> </td> 
   <td colname="col2"> <p>Der ID-Dienst verschlüsselt den MID-Wert, der vom Server zurückgegeben oder von der Funktion <span class="codeph">visitor.setMarketingCloudVisitorID()</span> festgelegt wird. Weitere Informationen zur MID finden Sie unter <a href="../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local"> Cookies und die Experience Cloud ID </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Fehlerbehebungen**

Die Besucher-API erzwingt keinen zusätzlichen Aufruf zur erneuten Synchronisierung mit Audience Manager, wenn keine ältere Analytics-Besucher-ID vorhanden ist.

## Version 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Mai 2016

**Dokumentation – Aktualisierungen**

* [SDK-Anforderungen für Android und iOS](../mcvid-reference/mcvid-requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench und der Experience Cloud ID-Dienst](../mcvid-reference/mcvid-dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [Testen und Überprüfen des Experience Cloud ID-Diensts](../mcvid-implementation-guides/mcvid-test-verify.md)

## Version 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

April 2016

**Dokumentation – Aktualisierungen**

[Implementieren des Experience Cloud ID-Diensts für Target](../mcvid-implementation-guides/mcvid-setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## Version 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

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
   <td colname="col2"> <p>Der <span class="keyword">Experience Cloud ID</span>-Dienst führt ID-Synchronisierungsaufrufe nun bei jedem Aufruf der Datenerfassungsserver durch. Zuvor gab der ID-Dienst nur eine Anforderung beim ersten Aufruf auf, um eine <span class="keyword">Experience Cloud</span> ID zu erhalten. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Dokumentation – Aktualisierungen**

* [Implementierung des Experience Cloud ID-Diensts für ](../mcvid-implementation-guides/mcvid-setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd): Neue Vorgehensweise, die die Einrichtung des ID-Diensts mit Analytics[!DNL Analytics] beschreibt.

* [Entscheidungspunkte zur Experience Cloud ID-Dienstmigration](../mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257): Überarbeiteter Text für mehr Klarheit. Die Arbeit mit einer einzigen Domäne bedeutet, dass Sie von einem Datenerfassungs-CNAME weg migrieren können, wenn Sie diese Methode nicht länger einsetzen möchten. Eine Migration ist jedoch nicht erforderlich, wenn Ihr CNAME problemlos funktioniert.

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Januar 2016

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
   <td colname="col1"> <p> <a href="../mcvid-reference/mcvid-authenticated-state.md" format="dita" scope="local"> Kunden-IDs und Authentifizierungsstatus </a> </p> </td> 
   <td colname="col2"> <p>Überarbeiteter Text. Kunden-IDs dürfen nur als nicht codierte Werte weitergegeben werden. Ein Codieren der IDs führt zu doppelt codierten Identifikatoren. </p> </td> 
  </tr> 
 </tbody> 
</table>

