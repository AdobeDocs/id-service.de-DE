---
description: Rufen Sie diese Funktion des Besucher-ID-Dienstes auf, um zu ermitteln, ob der Besucher-ID-Dienst eine Client-seitige ECID (MID) generiert hat. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
keywords: Besucher-ID-Service
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 128
ht-degree: 32%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Rufen Sie diese Funktion des Besucher-ID-Dienstes auf, um zu ermitteln, ob der Besucher-ID-Dienst eine Client-seitige ECID (MID) generiert hat. Verfügbar in `VisitorAPI.js` Version 1.7.0 oder höher.

**Syntax**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

In der folgenden Tabelle werden die von dieser Funktion zurückgegebenen Antworten aufgelistet und beschrieben.

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Antwort </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> wahr</span> </p> </td> 
   <td colname="col2"> <p>Der Besucher-ID-Dienst konnte keine MID vom CX Enterprise-Server empfangen oder hat sie nicht erhalten. Es wurde lokal eine MID erstellt, und zwar im Browser (clientseitig). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>Der Besucher-ID-Dienst hat vom CX Enterprise-Server eine MID erhalten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>Der Besucher-ID-Dienst hat den CX Enterprise-Server nicht aufgerufen. </p> </td> 
  </tr> 
 </tbody> 
</table>

