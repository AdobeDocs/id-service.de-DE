---
description: Diese Konfigurationen ermöglichen die Kommunikation zwischen verschiedenen Instanzen von ID-Dienstcode, die in einem iFrame implementiert sind, und solchen, die in die übergeordnete Seite implementiert sind. Sie sollen dabei helfen, Probleme in zwei konkreten Nutzungsszenarios zu lösen, in denen Sie die übergeordnete Seite/Domäne verwalten oder auch nicht und bei denen ID-Dienstcode im iFrame einer von Ihnen verwalteten Domäne geladen wird. Sie sind in VisitorAPI.js ab Codeversion 2.2 verfügbar.
keywords: ID-Dienst
seo-description: Diese Konfigurationen ermöglichen die Kommunikation zwischen verschiedenen Instanzen von ID-Dienstcode, die in einem iFrame implementiert sind, und solchen, die in die übergeordnete Seite implementiert sind. Sie sollen dabei helfen, Probleme in zwei konkreten Nutzungsszenarios zu lösen, in denen Sie die übergeordnete Seite/Domäne verwalten oder auch nicht und bei denen ID-Dienstcode im iFrame einer von Ihnen verwalteten Domäne geladen wird. Sie sind in VisitorAPI.js ab Codeversion 2.2 verfügbar.
seo-title: whitelistParentDomain und whitelistIframeDomains
title: whitelistParentDomain und whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# whitelistParentDomain und whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

Diese Konfigurationen ermöglichen die Kommunikation zwischen verschiedenen Instanzen von ID-Dienstcode, die in einem iFrame implementiert sind, und solchen, die in die übergeordnete Seite implementiert sind. Sie sollen dabei helfen, Probleme in zwei konkreten Nutzungsszenarios zu lösen, in denen Sie die übergeordnete Seite/Domäne verwalten oder auch nicht und bei denen ID-Dienstcode im iFrame einer von Ihnen verwalteten Domäne geladen wird. Sie sind in VisitorAPI.js ab Codeversion 2.2 verfügbar.

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

Der konfigurierte [!UICONTROL ID-Dienstcode] sollte in etwa wie im folgenden Beispiel aussehen.

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## Nutzungsszenarios {#section-fc2eeb93546b406fae3b102dbcd11de7}

Wenn Sie einen ID-Dienst-Cookie setzen und eine Besucher-ID zuweisen möchten, der Browser jedoch Drittanbieter-Cookies blockiert, können Sie das Problem mit diesen Konfigurationen lösen. Allerdings muss dazu eine der beiden folgenden Bedingungen erfüllt sein:

* Sie verwalten die übergeordnete Seite/Domäne oder auch nicht.
* Der ID-Dienstcode ist auf der übergeordneten Seite nicht installiert, jedoch in einem iFrame implementiert.

>[!TIP]
>
>Sie können diese Konfigurationen auch implementieren, wenn Sie Videos in einem iFrame mit [Video Heartbeat](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/) bereitstellen. Zur ordnungsgemäßen Funktionsweise benötigt Video Heartbeat eine vom ID-Dienst bereitgestellte ID (die MID).

**Nutzungsszenario 1: Der Browser blockiert Drittanbieter-Cookies und der ID-Dienst ist auf dem iFrame und der übergeordneten Seite implementiert**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Element des Nutzungsszenarios </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Bedingungen</b> </p> </td> 
   <td colname="col2"> <p>Dieses Nutzungsszenario beinhaltet die folgenden Bedingungen: </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">Unternehmen A implementiert den ID-Dienst auf seiner Homepage. </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">Unternehmen A implementiert den ID-Dienst in iFrame auf seiner Homepage. </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">Unternehmen A gehören die übergeordnete Seite und der iFrame. Das Unternehmen hat den ID-Dienst an beiden Stellen implementiert. </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">Ein Kunde lädt die übergeordnete Seite in einen Browser, der Drittanbieter-Cookies blockiert. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Ergebnisse</b> </p> </td> 
   <td colname="col2"> <p>Unter diesen Bedingungen verhält sich der ID-Dienst wie folgt: </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">Er funktioniert ordnungsgemäß auf der übergeordneten Seite. Er fordert AMCV-Cookies an und weist dem Site-Besucher eine eindeutige ID zu. </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">Er funktioniert nicht im iFrame. Der Grund ist, dass der Browser den iFrame als Drittanbieterdomäne betrachtet und den ID-Dienst daran hindert, den AMCV-Cookie zu setzen. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Lösung</b> </p> </td> 
   <td colname="col2"> <p>Ändern Sie die Funktion <span class="codeph">Visitor.getInstance</span> des ID-Diensts im iFrame mit diesen Whitelist-Konfigurationen. Geben Sie die übergeordneten und untergeordneten Domänen im Code an. Mit diesen Konfigurationen kann der ID-Dienstcode im iFrame eine Besucher-ID im ID-Dienstcode der übergeordneten Seite suchen. </p> <p>Wenn der ID-Dienstcode im iFrame keine Antwort von der übergeordneten Seite erhält, wird mit diesen Konfigurationen eine lokale Besucher-ID generiert. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Nutzungsszenario 2: Eine ID wird von einem iFrame angefordert, der in eine übergeordnete Seite eingebettet ist, über die Sie keine Kontrolle haben oder die den ID-Dienst nicht verwendet**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Element des Nutzungsszenarios </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Bedingungen</b> </p> </td> 
   <td colname="col2"> <p>Dieses Nutzungsszenario beinhaltet die folgenden Bedingungen: </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">Unternehmen A verwendet den ID-Dienst nicht. </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">Unternehmen A lädt einen iFrame auf der Seite. Dieser iFrame gehört Unternehmen B und wird in einer anderen Domäne als derjenigen von Unternehmen A geladen. </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">Der Browser blockiert Drittanbieter-Cookies. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Ergebnisse</b> </p> </td> 
   <td colname="col2"> <p>Unter diesen Bedingungen verhält sich der ID-Dienst wie folgt: </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">Er funktioniert nicht im iFrame. Der Grund ist, dass der Browser den iFrame als Drittanbieterdomäne betrachtet und den ID-Dienst daran hindert, den AMCV-Cookie zu setzen. </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">Es kann keine Besucher-ID von der übergeordneten Seite abgerufen werden, da Unternehmen A diesen Dienst nicht verwendet. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Lösung</b> </p> </td> 
   <td colname="col2"> <p>Ändern Sie die Funktion <span class="codeph">Visitor.getInstance</span> des ID-Diensts im iFrame mit diesen Whitelist-Konfigurationen. Geben Sie die übergeordneten und untergeordneten Domänen im Code an. Mit diesen Konfigurationen kann der ID-Dienstcode im iFrame eine Besucher-ID im ID-Dienstcode der übergeordneten Seite suchen. </p> <p>Wenn der ID-Dienstcode im iFrame keine Antwort von der übergeordneten Seite erhält, wird mit diesen Konfigurationen eine lokale Besucher-ID generiert. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Sicherheit der Konfiguration {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

Aus folgenden Gründen können Sie diese Konfigurationen sicher implementieren:

* Der in der übergeordneten Domäne implementierte ID-Dienst und die iFrame-Domäne müssen die gleiche Organisations-ID verwenden. Diese Whitelist-Konfigurationen funktionieren nicht, wenn sich die Organisations-IDs in der übergeordneten Domäne oder im iFrame unterscheiden.
* Diese Konfigurationen können nur mit der Domäne und den iFrames kommunizieren, die im Code angegeben sind.
* Die Kommunikation zwischen iFrame und übergeordneter Seite erfolgt in einem spezifischen Format. Wenn der ID-Dienst auf der übergeordneten Seite keine Anforderung im erwarteten Format erhält, schlägt dieser Kommunikationsvorgang fehl.

## Unterstützte Besucher-API-Methoden {#section-30c6a9f4dcdc4265a1149260b97cc057}

Der ID-Dienst unterstützt eine beschränkte Anzahl öffentlicher API-Methoden, wenn diese Whitelist-Konfigurationen implementiert werden. Die unterstützten Methoden sind je nach Nutzungsszenario (siehe Beschreibung oben) unterschiedlich.

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

