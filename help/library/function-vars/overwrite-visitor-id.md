---
description: Diese Eigenschaft überschreibt die ECID- und Analytics-IDs eines Besuchers beim Navigieren von einer Domain zu einer zweiten Domain. Um eine ID zu überschreiben, müssen Sie den Besucher-ID-Service für jede Domain besitzen und implementiert haben. Mit diesem Code können Sie keine IDs in Domains überschreiben, die Sie nicht steuern.
keywords: Besucher-ID-Service
title: overwriteCrossDomainMCIDAndAID
exl-id: 726261b1-c8d0-4b12-b0cb-52d7e21e7fac
TQID: https://experienceleague.adobe.com/dJUuTbc9zspC93WZrRaxBsp2BgpbE-z-iUuePQXGTeY
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 404
ht-degree: 71%

---

# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Diese Eigenschaft überschreibt die ECID- und Analytics-IDs eines Besuchers beim Navigieren von einer Domain zu einer zweiten Domain. Um eine ID zu überschreiben, müssen Sie den Besucher-ID-Service für jede Domain besitzen und implementiert haben. Mit diesem Code können Sie keine IDs in Domains überschreiben, die Sie nicht steuern.

**Syntax:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (Standard ist `false`)

**Codebeispiel**

Ihr JavaScript-Code sollte dem folgenden Beispiel ähneln.

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Nutzungsszenarios**

Zum Nachverfolgen von Website-Besuchern schreibt der Besucher-ID-Dienst eine ECID (oder MID) in ein Browser-Cookie. In der folgenden Tabelle werden gängige Anwendungsfälle aufgelistet und beschrieben, in denen Sie eine vorhandene MID überschreiben können, die vom Besucher-ID-Service in einer anderen Domain festgelegt wurde.

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
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">Domain B eine separate Konversions-, Buchungs- oder andere Ende-des-Workflows-Seite ist, </li> 
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

