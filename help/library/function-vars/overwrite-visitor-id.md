---
description: Diese Eigenschaft überschreibt die Experience Cloud- und Analytics-IDs eines Besuchers, wenn dieser von einer Domain zu einer zweiten Domain navigiert. Um eine ID zu überschreiben, müssen Sie den ID-Dienst für jede Domain besitzen und implementiert haben. Mit diesem Code können Sie keine IDs in Domains überschreiben, die Sie nicht steuern.
keywords: ID-Dienst
title: overwriteCrossDomainMCIDAndAID
exl-id: 726261b1-c8d0-4b12-b0cb-52d7e21e7fac
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 100%

---

# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Diese Eigenschaft überschreibt die Experience Cloud- und Analytics-IDs eines Besuchers, wenn dieser von einer Domain zu einer zweiten Domain navigiert. Um eine ID zu überschreiben, müssen Sie den ID-Dienst für jede Domain besitzen und implementiert haben. Mit diesem Code können Sie keine IDs in Domains überschreiben, die Sie nicht steuern.

**Syntax:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (Standard ist `false`)

**Codebeispiel**

Ihr JavaScript-Code sollte dem folgenden Beispiel ähneln.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Nutzungsszenarios**

Zum Nachverfolgen von Sitebesuchern schreibt der ID-Dienst eine [!DNL Experience Cloud] ID (oder MID) in einen Browsercookie. In der folgenden Tabelle werden die gängigen Anwendungsfälle beschrieben, in denen Sie eine MID, die vom ID-Dienst in einer anderen Domain festgelegt wurde, überschreiben möchten.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Anwendungsfall </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Identifizieren Sie Besucher auf unterschiedlichen Domain-Landingpages.</b> </p> </td> 
   <td colname="col2"> <p>Angenommen, Ihnen gehören die Domänen A und B. In diesem Fall können Sie <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> festlegen, sofern: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">Jede Domain besitzt eine eigene Landingpage. </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">Ein Besucher verfügt bereits über ein Cookie (und eine MID), das bei einem vorherigen Besuch von Domain B gesetzt wurde. </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">Sie möchten Besucher einheitlich identifizieren, wenn diese von Domain A zu Domain B wechseln. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Besucher über Landingpages und Konversionsseiten hinweg identifizieren</b> </p> </td> 
   <td colname="col2"> <p>Angenommen, Ihnen gehören die Domänen A und B. In diesem Fall können Sie <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> festlegen, sofern: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">Domain A ist eine Landingpage. </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">Domäne B eine separate Konversions-, Buchungs- oder andere Ende-des-Workflows-Seite ist, </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">Ein Besucher verfügt bereits über ein Cookie (und eine MID), das bei einem vorherigen Besuch von Domain B gesetzt wurde, und Sie wissen, dass es sich hierbei nicht um Server-seitige MIDs, sondern um weniger wünschenswerte Client-seitige MIDs handelt. </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">Sie möchten Besucher einheitlich identifizieren, wenn diese von Domain A zu Domain B wechseln. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identifizieren von Besuchern aus mobilen Apps gegenüber Webbrowsern</b> </p> </td> 
   <td colname="col2"> <p>Dieser Anwendungsfall ist etwas anders. Es umfasst die Identifizierung von Benutzern, die von einer mobilen App zu Ihrer Website wechseln. In diesem Fall verfügen Besucher bereits über eine MID, die von einer mobilen App lokal festgelegt wird, und sie haben eine andere MID, die in einem Cookie auf Ihrer Website festgelegt ist. Sie können <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> festlegen, um die im Browsercookie festgelegte MID mit der durch die mobile Anwendung festgelegte MID zu überschreiben. </p> </td> 
  </tr> 
 </tbody> 
</table>
