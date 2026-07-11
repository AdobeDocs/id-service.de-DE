---
description: Mit diesen Konfigurationen können verschiedene Instanzen des Besucher-ID-Dienst-Codes, die in einem iFrame implementiert sind und sich auf der übergeordneten Seite befinden, miteinander kommunizieren. Sie sollen dabei helfen, Probleme in zwei bestimmten Anwendungsfällen zu lösen, in denen Sie die übergeordnete Seite/Domain steuern oder auch nicht und bei denen der Besucher-ID-Dienst-Code im iFrame einer Domain geladen wird, die Sie steuern. Sie sind in Version 2.2 (oder höher) des VisitorAPI.js-Codes verfügbar.
keywords: Besucher-ID-Service
title: whitelistParentDomain und whitelistIframeDomains
exl-id: 0ed1da79-7129-4f5f-b7ad-901348a13866
TQID: https://experienceleague.adobe.com/rlm1XMAy74wSMv4RS-WjyMVHd7DM703j0pP2vOyMAM0
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 904
ht-degree: 37%

---

# whitelistParentDomain und whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

Mit diesen Konfigurationen können verschiedene Instanzen des Besucher-ID-Dienst-Codes, die in einem iFrame implementiert sind und sich auf der übergeordneten Seite befinden, miteinander kommunizieren. Sie sollen dabei helfen, Probleme in zwei bestimmten Anwendungsfällen zu lösen, in denen Sie die übergeordnete Seite/Domain steuern oder auch nicht und bei denen der Besucher-ID-Dienst-Code im iFrame einer Domain geladen wird, die Sie steuern. Sie sind in `VisitorAPI.js` Code-Version 2.2 oder höher verfügbar.

Inhalt:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> Syntax </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> Codebeispiel </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> Nutzungsszenarios </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> Sicherheit der Konfiguration </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> Unterstützte Besucher-API-Methoden </a> </li> 
</ul>

## Syntax {#section-f645198bbaba4fba8961acb6e88d1470}

Beide Konfigurationselemente sind erforderlich, wenn Sie diesen Code verwenden.

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Konfigurationssyntax </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: " <span class="varname"> Domänenname der übergeordneten Seite </span>" </span> </p> </td> 
   <td colname="col2"> <p>Akzeptiert einen einzelnen Domänennamen, der als Zeichenfolge übergeben wird. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "iFrame Domain", "iFrame Domain", "iFrame Domain" </span>] </span> </p> </td> 
   <td colname="col2"> <p>Akzeptiert einen oder mehrere iFrame-Domänennamen, die als Array übergeben werden. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Codebeispiel {#section-09d0049fe88a473baa69d404c50bf8ae}

Der konfigurierte [!UICONTROL Visitor ID Service]-Code sollte in etwa wie im folgenden Beispiel aussehen.

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## Anwendungsfälle {#section-fc2eeb93546b406fae3b102dbcd11de7}

Mit diesen Konfigurationen können Sie das Problem lösen, ein Besucher-ID-Service-Cookie festzulegen und eine Besucher-ID zuzuweisen, wenn Browser Drittanbieter-Cookies blockieren und eine der folgenden Bedingungen zutrifft:

* Sie steuern die übergeordnete Seite/Domain oder steuern sie nicht.
* Der Besucher-ID-Dienst-Code ist nicht auf der übergeordneten Seite installiert, sondern in einem iFrame implementiert.

>[!TIP]
>
>Sie können diese Konfigurationen auch implementieren, wenn Sie Videos in einem iFrame mit [Video Heartbeat](https://docs.adobe.com/content/help/de-DE/experience-cloud/user-guides/home.translate.html) bereitstellen. Video Heartbeat benötigt eine Besucher-ID-Service-ID (die MID), um ordnungsgemäß zu funktionieren.

**Anwendungsfall 1: Der Browser blockiert Cookies von Drittanbietern, und der Besucher-ID-Service ist auf dem iFrame und der übergeordneten Seite implementiert**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nutzungsszenario </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Bedingungen</b> </p> </td> 
   <td colname="col2"> <p>Dieses Nutzungsszenario schließt die folgenden Bedingungen ein: </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">Unternehmen A implementiert den Besucher-ID-Service auf seiner Startseite. </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">Unternehmen A implementiert den Besucher-ID-Service in iFrame auf der Startseite. </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">Unternehmen A ist für die übergeordnete Seite und den iFrame verantwortlich und hat den Besucher-ID-Service an beiden Stellen implementiert. </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">Ein Kunde lädt die übergeordnete Seite in einen Browser, der Drittanbieter-Cookies blockiert. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Ergebnisse</b> </p> </td> 
   <td colname="col2"> <p>Unter diesen Bedingungen hat der Besucher-ID-Dienst folgende Möglichkeiten: </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">Er funktioniert ordnungsgemäß auf der übergeordneten Seite. Er fordert das AMCV-Cookie an, setzt es und weist dem Site-Besucher eine eindeutige ID zu. </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">Funktioniert nicht im iFrame. Dies liegt daran, dass der Browser den iFrame als Domain eines Drittanbieters betrachtet und den Besucher-ID-Service daran hindert, das AMCV-Cookie zu setzen. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Lösung</b> </p> </td> 
   <td colname="col2"> <p>Mit diesen Konfigurationen für die weiße Liste können Sie den Besucher-ID-Dienst <span class="codeph"> die Funktion Visitor.getInstance </span> im iFrame ändern. Geben Sie die übergeordneten und untergeordneten Domänen im Code an. Mit diesen Konfigurationen kann der Besucher-ID-Dienst-Code im iFrame den Besucher-ID-Dienst-Code auf der übergeordneten Seite auf eine Besucher-ID überprüfen. </p> <p>Wenn der Besucher-ID-Dienst-Code im iFrame keine übergeordnete Seite erhält, generieren diese Konfigurationen eine lokale Besucher-ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Anwendungsfall 2: Anfordern einer ID von einem iFrame, der in eine übergeordnete Seite eingebettet ist, die Sie nicht steuern oder die den Besucher-ID-Service nicht verwendet**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nutzungsszenario </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Bedingungen</b> </p> </td> 
   <td colname="col2"> <p>Dieses Nutzungsszenario schließt die folgenden Bedingungen ein: </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">Unternehmen A verwendet nicht den Besucher-ID-Service. </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">Firma A lädt einen iFrame auf die Seite. Dieser iFrame gehört Firma B und wird in einer anderen Domain als Firma A geladen. </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">Der Browser blockiert Drittanbieter-Cookies. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Ergebnisse</b> </p> </td> 
   <td colname="col2"> <p>Unter diesen Bedingungen hat der Besucher-ID-Dienst folgende Möglichkeiten: </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">Funktioniert nicht im iFrame. Dies liegt daran, dass der Browser den iFrame als Domain eines Drittanbieters betrachtet und den Besucher-ID-Service daran hindert, das AMCV-Cookie zu setzen. </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">Es kann keine Besucher-ID von der übergeordneten Seite abgerufen werden, da Firma A diesen Service nicht verwendet. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Lösung</b> </p> </td> 
   <td colname="col2"> <p>Mit diesen Konfigurationen für die weiße Liste können Sie den Besucher-ID-Dienst <span class="codeph"> die Funktion Visitor.getInstance </span> im iFrame ändern. Geben Sie die übergeordneten und untergeordneten Domänen im Code an. Mit diesen Konfigurationen kann der Besucher-ID-Dienst-Code im iFrame den Besucher-ID-Dienst-Code auf der übergeordneten Seite auf eine Besucher-ID überprüfen. </p> <p>Wenn der Besucher-ID-Dienst-Code im iFrame keine übergeordnete Seite erhält, generieren diese Konfigurationen eine lokale Besucher-ID. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Sicherheit der Konfiguration {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

Sie können diese Konfigurationen aus folgenden Gründen sicher implementieren:

* Der in der übergeordneten Domain implementierte Besucher-ID-Dienst und die iFrame-Domain müssen dieselbe IMS-Organisations-ID verwenden. Diese Konfigurationen der weißen Liste funktionieren nicht, wenn sich die IMS-Organisations-IDs für das übergeordnete Element oder den iFrame unterscheiden.
* Diese Konfigurationen kommunizieren nur mit der Domain und den iFrames, die im Code angegeben sind.
* Die Kommunikation zwischen dem iFrame und der übergeordneten Seite folgt einem bestimmten Format. Wenn der Besucher-ID-Dienst auf der übergeordneten Seite keine Anfrage im erwarteten Format erhält, schlägt dieser Freigabeprozess fehl.

## Unterstützte Besucher-API-Methoden {#section-30c6a9f4dcdc4265a1149260b97cc057}

Der Besucher-ID-Dienst unterstützt eine begrenzte Anzahl öffentlicher API-Methoden, wenn Sie diese Konfigurationen für die weiße Liste implementieren. Die unterstützten Methoden variieren je nach den oben beschriebenen Nutzungsszenarios.

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Anwendungsfall </th> 
   <th colname="col2" class="entry"> Unterstützte Methoden </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>1. Fall</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2. Fall</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

