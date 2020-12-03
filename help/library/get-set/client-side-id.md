---
description: Rufen Sie diese ID-Dienstfunktion auf, um zu ermitteln, ob der ID-Dienst eine clientseitige Experience Cloud-Besucher-ID (MID) generiert hat. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
keywords: ID Service
seo-description: Rufen Sie diese ID-Dienstfunktion auf, um zu ermitteln, ob der ID-Dienst eine clientseitige Experience Cloud-Besucher-ID (MID) generiert hat. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 52%

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Rufen Sie diese ID-Dienstfunktion auf, um zu ermitteln, ob der ID-Dienst eine clientseitige Experience Cloud-Besucher-ID (MID) generiert hat. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.

**Syntax**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

In der folgenden Tabelle werden die von dieser Funktion zurückgegebenen Antworten Liste und beschrieben.

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
   <td colname="col2"> <p>Der ID-Dienst konnte oder hat keine MID vom <span class="keyword">Experience Cloud</span>-Server empfangen. Es wurde lokal eine MID erstellt, und zwar im Browser (clientseitig). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>Der ID-Dienst hat eine MID vom <span class="keyword">Experience Cloud</span>-Server empfangen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>Der ID-Dienst hat den <span class="keyword">Experience Cloud</span>-Server nicht aufgerufen. </p> </td> 
  </tr> 
 </tbody> 
</table>

