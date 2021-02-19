---
description: Diese Eigenschaft überschreibt die Experience Cloud- und Analytics-IDs eines Besuchers, wenn dieser von einer Domäne zu einer zweiten Domäne navigiert. Um eine ID zu überschreiben, müssen Sie den ID-Dienst für jede Domäne besitzen und implementiert haben. Mit diesem Code können Sie IDs in Domänen, die Sie nicht steuern, nicht überschreiben.
keywords: ID-Dienst
seo-description: Diese Eigenschaft überschreibt die Experience Cloud- und Analytics-IDs eines Besuchers, wenn dieser von einer Domäne zu einer zweiten Domäne navigiert. Um eine ID zu überschreiben, müssen Sie den ID-Dienst für jede Domäne besitzen und implementiert haben. Mit diesem Code können Sie IDs in Domänen, die Sie nicht steuern, nicht überschreiben.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 23%

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Diese Eigenschaft überschreibt die Experience Cloud- und Analytics-IDs eines Besuchers, wenn dieser von einer Domäne zu einer zweiten Domäne navigiert. Um eine ID zu überschreiben, müssen Sie den ID-Dienst für jede Domäne besitzen und implementiert haben. Mit diesem Code können Sie IDs in Domänen, die Sie nicht steuern, nicht überschreiben.

**Syntax:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (Standard ist `false`)

**Codebeispiel**

Ihr JavaScript-Code könnte wie im folgenden Beispiel aussehen.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Nutzungsszenarios**

Zum Nachverfolgen von Sitebesuchern schreibt der ID-Dienst eine [!DNL Experience Cloud] ID (oder MID) in einen Browsercookie. In der folgenden Tabelle werden die gängigen Anwendungsfälle beschrieben, in denen Sie eine MID, die vom ID-Dienst in einer anderen Domäne festgelegt wurde, überschreiben möchten.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Anwendungsfall </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Identifizieren Sie Besucher auf unterschiedlichen Landingpages der Domäne.</b> </p> </td> 
   <td colname="col2"> <p>Angenommen, Ihnen gehören die Domänen A und B. In diesem Fall können Sie <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> festlegen, sofern: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">Jede Domäne hat eine eigene Landingpage. </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">Ein Besucher verfügt bereits über ein Cookie (und eine MID), das bei einem vorherigen Besuch von Domäne B gesetzt wurde. </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">Sie möchten einen Besucher konsistent identifizieren, wenn er von Domäne A zu Domäne B gelangt. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Besucher über Landingpages und Konversionsseiten hinweg identifizieren</b> </p> </td> 
   <td colname="col2"> <p>Angenommen, Ihnen gehören die Domänen A und B. In diesem Fall können Sie <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> festlegen, sofern: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">Domäne A ist eine Landingpage. </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">Domäne B eine separate Konversions-, Buchungs- oder andere Ende-des-Workflows-Seite ist, </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">Ein Besucher verfügt bereits über ein Cookie (und eine MID), das bei einem vorherigen Besuch von Domäne B gesetzt wurde, und Sie wissen, dass es sich hierbei nicht um serverseitige MIDs, sondern um weniger wünschenswerte clientseitige MIDs handelt. </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">Sie möchten einen Besucher konsistent identifizieren, wenn er von Domäne A zu Domäne B gelangt. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identifizieren Sie Besucher von mobilen Apps zu Webbrowsern.</b> </p> </td> 
   <td colname="col2"> <p>Dieser Anwendungsfall ist etwas anders. Es umfasst die Identifizierung von Benutzern, die von einer mobilen App zu Ihrer Website wechseln. In diesem Fall verfügt Ihr Besucher bereits über eine lokale MID, die von einer mobilen App festgelegt wird, und sie haben eine andere MID, die in einem Cookie auf Ihrer Website festgelegt ist. Sie können <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> festlegen, um die im Browsercookie festgelegte MID mit der durch die mobile Anwendung festgelegte MID zu überschreiben. </p> </td> 
  </tr> 
 </tbody> 
</table>

