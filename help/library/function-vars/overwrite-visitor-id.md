---
description: Diese Eigenschaft überschreibt die Experience Cloud- und Analytics-ID eines Besuchers, wenn er von einer zu einer zweiten Domäne wechselt. Zum Überschreiben einer ID müssen Sie Inhaber des ID-Diensts auf jeder Domäne sein und die ID implementiert haben. Mit diesem Code können Sie keine IDs auf Domänen überschreiben, die Sie nicht steuern.
keywords: ID-Dienst
seo-description: Diese Eigenschaft überschreibt die Experience Cloud- und Analytics-ID eines Besuchers, wenn er von einer zu einer zweiten Domäne wechselt. Zum Überschreiben einer ID müssen Sie Inhaber des ID-Diensts auf jeder Domäne sein und die ID implementiert haben. Mit diesem Code können Sie keine IDs auf Domänen überschreiben, die Sie nicht steuern.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Diese Eigenschaft überschreibt die Experience Cloud- und Analytics-ID eines Besuchers, wenn er von einer zu einer zweiten Domäne wechselt. Zum Überschreiben einer ID müssen Sie Inhaber des ID-Diensts auf jeder Domäne sein und die ID implementiert haben. Mit diesem Code können Sie keine IDs auf Domänen überschreiben, die Sie nicht steuern.

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

Zum Nachverfolgen von Sitebesuchern schreibt der ID-Dienst eine [!DNL Experience Cloud] ID (oder MID) in einen Browsercookie. In der folgenden Tabelle sind die häufigsten Nutzungsszenarien aufgeführt und beschrieben, in denen Sie möglicherweise eine vorhandene MID überschreiben möchten, die durch den ID-Dienst in einer anderen Domäne festgelegt wurde.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Anwendungsfall </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Besucher auf unterschiedlichen Landingpages der Domäne identifizieren</b> </p> </td> 
   <td colname="col2"> <p>Angenommen, Ihnen gehören die Domänen A und B. In diesem Fall können Sie <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> festlegen, sofern: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">jede Domäne über eine eigene Landingpage verfügt, </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">ein Besucher bereits über ein Cookie (und eine MID) verfügt, das durch einen vorherigen Aufruf der Domäne B festgelegt wurde, </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">Sie einen Besucher einheitlich identifizieren möchten, wenn er von Domäne A zur Domäne B wechselt. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Besucher über Landingpages und Konversionsseiten hinweg identifizieren</b> </p> </td> 
   <td colname="col2"> <p>Angenommen, Ihnen gehören die Domänen A und B. In diesem Fall können Sie <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> festlegen, sofern: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">Domäne A eine Landingpage ist, </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">Domäne B eine separate Konversions-, Buchungs- oder andere Ende-des-Workflows-Seite ist, </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">Für einen Besucher bereits über den vorherigen Aufruf von Domäne B ein Cookie (und eine MID) festgelegt ist und Sie wissen, dass es sich hierbei im Vergleich zu serverseitigen MIDs um weniger wünschenswerte clientseitige MIDs handelt, </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">Sie einen Besucher einheitlich identifizieren möchten, wenn er von Domäne A zur Domäne B wechselt. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Besucher identifizieren, die von mobilen Anwendungen zu Webbrowsern wechseln</b> </p> </td> 
   <td colname="col2"> <p>Dieses Nutzungsszenario ist etwas anders. Es umfasst die Identifizierung von Benutzern, wenn sie von einer mobilen Anwendung zu Ihrer Website wechseln. In diesem Fall hat der Besucher bereits durch eine mobile Anwendung lokal eine MID festgelegt, und die in einem Cookie Ihrer Website festgelegte MID unterscheidet sich davon. Sie können <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> festlegen, um die im Browsercookie festgelegte MID mit der durch die mobile Anwendung festgelegte MID zu überschreiben. </p> </td> 
  </tr> 
 </tbody> 
</table>

