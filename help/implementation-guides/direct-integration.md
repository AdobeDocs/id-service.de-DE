---
description: Mit dieser Implementierung können Kunden den ID-Dienst auf Geräten verwenden, die unseren JavaScript- oder SDK-Code nicht akzeptieren oder verwenden können. Dazu gehören Geräte wie Spielekonsolen, Smart-TVs oder andere internetfähige Geräte. Informationen zu Syntax, Codebeispielen und Definitionen finden Sie in diesem Abschnitt.
keywords: ID-Dienst
seo-description: Mit dieser Implementierung können Kunden den ID-Dienst auf Geräten verwenden, die unseren JavaScript- oder SDK-Code nicht akzeptieren oder verwenden können. Dazu gehören Geräte wie Spielekonsolen, Smart-TVs oder andere internetfähige Geräte. Informationen zu Syntax, Codebeispielen und Definitionen finden Sie in diesem Abschnitt.
seo-title: Direkte Integration mit dem Experience Cloud Identity-Dienst
title: Direkte Integration mit dem Experience Cloud Identity-Dienst
uuid: de502f7e-cffd-4130-b3ca-7d6b9a9caae9
exl-id: 29565b74-5fe7-41f7-b278-6a90559faab9
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '714'
ht-degree: 100%

---

# Direkte Integration mit dem Experience Cloud Identity-Dienst {#direct-integration-with-the-experience-cloud-id-service}

Mit dieser Implementierung können Kunden den ID-Dienst auf Geräten verwenden, die unseren JavaScript- oder SDK-Code nicht akzeptieren oder verwenden können. Dazu gehören Geräte wie Spielekonsolen, Smart-TVs oder andere internetfähige Geräte. Informationen zu Syntax, Codebeispielen und Definitionen finden Sie in diesem Abschnitt.

## Syntax {#section-a4754afec5ad40b6be00d6f1011d68bb}

Geräte, die weder die VisitorAPI.js- noch die SDK-Codebibliothek unterstützen, können Aufrufe direkt an die vom ID-Dienst verwendeten Datenerfassungsserver (DCS) richten. Dazu rufen Sie `dpm.demdex.net` auf und geben eine Anforderung im folgenden Format ein. Eine *kursive* Formatierung gibt einen Variablenplatzhalter an.

![](assets/directSyntax.png)

In diesem Syntaxbeispiel kennzeichnet das `d_` Präfix die Schlüssel-Wert-Paare im Aufruf als Variablen auf Systemebene. Sie können einige `d_`-Parameter an den ID-Dienst übergeben, konzentrieren Sie sich jedoch auf die Schlüssel-Wert-Paare, wie im Code oben gezeigt. Weitere Informationen zu anderen Variablen finden Sie unter [Unterstützte Attribute für DCS-API-Aufrufe](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-keys.html).

Der ID-Dienst unterstützt HTTP- und HTTPS-Aufrufe. Verwenden Sie HTTPS, um Daten von einer sicheren Seite weiterzugeben.

## Beispielanforderung {#section-26302b8851704888b6f8e6b2071bcdb0}

Ihre Anforderung könnte dem unten gezeigten Beispiel ähneln. Lange Variablen wurden gekürzt.

![](assets/directExample.png)

## Beispielantwort {#section-89bc103b3e9e4a8b98e74c32897b1200}

Der ID-Dienst gibt Daten in einem JSON-Objekt zurück, wie unten dargestellt. Ihre Antwort könnte anders aufgebaut sein.

```js
{
     "d_mid":"12345",
     "dcs_region":"6",
     "id_sync_ttl":"604800",
     "d_blob":"wxyz5432"
}
```

## Definierte Anforderungs- und Antwortparameter {#section-4a9912b545364dc4acad4f1ea5ec641d}

**Anfrageparameter**

<table id="table_C8FFA89AB74E4E31A6926CDE5CD54217"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Parameter </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dpm.demdex.net</span> </p> </td> 
   <td colname="col2"> <p>Eine ältere von <span class="keyword">Adobe</span> verwaltete Domäne. Siehe <a href="https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Aufrufe an die Domäne „demdex.net“</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_mid</span> </p> </td> 
   <td colname="col2"> <p>Die Experience Cloud-Besucher-ID. Siehe <a href="../introduction/cookies.md" format="dita" scope="local">Cookies und der Experience Cloud Identity-Dienst </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_orgid</span> </p> </td> 
   <td colname="col2"> <p>Ihre Experience Cloud-Organisations-ID. Informationen zum Auffinden dieser ID erhalten Sie unter  <a href="../reference/requirements.md" format="dita" scope="local">Voraussetzungen für den Experience Cloud Identity-Dienst</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cid</span> </p> </td> 
   <td colname="col2"> <p>Ein optionaler Parameter, der die Data Provider ID (DPID), die eindeutige Benutzer-ID (DPUUID) und eine <a href="../reference/authenticated-state.md" format="dita" scope="local"> authentifizierte Zustands-ID</a> an den ID-Dienst übergibt. Trennen Sie DPID und DPUUID durch das nicht druckbare Steuerzeichen <span class="codeph">%01</span>, wie im Codebeispiel gezeigt. </p> <p> <b>DPID und DPUUID</b> </p> <p>Weisen Sie im Parameter <span class="codeph">d_cid</span> alle zusammengehörigen Kombinationen aus DPID und DPUUID demselben <span class="codeph">d_cid</span>-Parameter zu. Dadurch können Sie mehrere IDs in einer einzigen Anforderung übergeben. Trennen Sie außerdem DPID, DPUUID und die optionale Authentifizierungskennzeichnung durch das nicht druckbare Steuerzeichen <span class="codeph">%01</span>. In den Beispielen weiter unten werden die Anbieter- und Benutzer-IDs durch <b>Fettdruck</b> hervorgehoben. </p> 
    <ul id="ul_2E19D837296B40E9ACD096495CF711C5"> 
     <li id="li_5B94B057654440B99B989BA60E4ED053">Syntax: <span class="codeph">...d_cid=DPID%01DPUUID%01authentication state...</span> </li> 
     <li id="li_B07833EF51D54F088574B7B7F9FB841A">Beispiel: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
    </ul> <p> <b>Authentifizierungsstatus</b> </p> <p>Dies ist eine optionale ID im Parameter <span class="codeph">d_cid</span>. Sie wird als Ganzzahl ausgedrückt und gibt den Authentifizierungsstatus von Benutzern an, wie unten gezeigt: </p> 
    <ul id="ul_E2B36922B11C4AA2A9016B6E2DC9EDAA"> 
     <li id="li_31C018E3F9514B938C73EF40C436715F"> <span class="codeph"> 0</span> (Unbekannt) </li> 
     <li id="li_1F125C3879324C2F8EF4613C0ECB5F02"> <span class="codeph"> 1</span> (Authentifiziert) </li> 
     <li id="li_EF6792D0115D407485079D5D7480D965"> <span class="codeph"> 2</span> (Abgemeldet) </li> 
    </ul> <p>Um einen Authentifizierungsstatus anzugeben, legen Sie diese Kennzeichnung im Anschluss an die Variable für die Benutzer-ID (UUID) fest. Trennen Sie UUID und Authentifizierungskennzeichnung durch das nicht druckbare Steuerzeichen <span class="codeph">%01</span>. In den Beispielen unten werden Authentifizierungs-IDs durch <b>Fettdruck</b> hervorgehoben. </p> <p>Syntax: <span class="codeph">...d_cid=DPID%01DPUUID%01authentication state</span> </p> <p>Beispiele: </p> 
    <ul id="ul_4C1054CE860A4D9C8DD85C2A8020C47F"> 
     <li id="li_AD4000BF3E0146C0BD37B1EC513EC314">Unbekannt: <span class="codeph">...d_cid=123%01456%010...</span> </li> 
     <li id="li_B037D424AADA4D41BF29381A9602AE61">Authentifiziert: <span class="codeph">...d_cid=123%01456%011...</span> </li> 
     <li id="li_0410FCB9E60D4DD08E7898D814E1C3C9">Abgemeldet: <span class="codeph">...d_cid=123%01456%012...</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dcs_region</span> </p> </td> 
   <td colname="col2"> <p>Der ID-Dienst ist ein geografisch verteiltes und lastausgeglichenes System. Die ID identifiziert die Region des Rechenzentrums, in dem der Aufruf verarbeitet wird. Siehe <a href="https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html" format="https" scope="external">DCS Region IDs, Locations, and Host Names</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cb</span> </p> </td> 
   <td colname="col2"> <p> <i>(Optional)</i> Ein Rückrufparameter, mit dem Sie eine JavaScript-Funktion im Anforderungstext ausführen können. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_blob</span> </p> </td> 
   <td colname="col2"> <p>Ein verschlüsselter Abschnitt der JavaScript-Metadaten. Durch Größenbeschränkungen wird der Blob auf höchstens 512 Byte begrenzt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_ver</span> </p> </td> 
   <td colname="col2"> <p>Erforderlich. Hiermit wird die API-Versionsnummer festgelegt. Behalten Sie <span class="codeph">d_ver=2</span> bei. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Antwortparameter**

Einige Antwortparameter sind Teil der Anforderung und wurden im obigen Abschnitt definiert.

<table id="table_58D0E8876DDC4A81B1F24F845E87EC18"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Parameter </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id_sync_ttl</span> </p> </td> 
   <td colname="col2"> <p>Das in Sekunden angegebene Neusynchronisierungsintervall. Der Standardwert beträgt 604.800 Sekunden (7 Tage). </p> </td> 
  </tr> 
 </tbody> 
</table>
