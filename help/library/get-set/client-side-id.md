---
description: Rufen Sie diese ID-Dienst-Funktion auf, um zu ermitteln, ob der ID-Dienst eine Client-seitige Experience Cloud-Besucher-ID (MID) generiert hat. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
keywords: ID-Dienst
seo-description: Rufen Sie diese ID-Dienst-Funktion auf, um zu ermitteln, ob der ID-Dienst eine Client-seitige Experience Cloud-Besucher-ID (MID) generiert hat. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '148'
ht-degree: 100%

---

# isClientSideMarketingCloudVisitorID {#isclientsidemarketingcloudvisitorid}

Rufen Sie diese ID-Dienst-Funktion auf, um zu ermitteln, ob der ID-Dienst eine Client-seitige Experience Cloud-Besucher-ID (MID) generiert hat. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.

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
