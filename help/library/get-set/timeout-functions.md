---
description: Rufen Sie diese ID-Dienstfunktionen auf, um den Zeitüberschreitungsstatus für eine Experience Cloud Identity-Dienst-, Analytics- oder Audience Manager-ID-Anforderung zu ermitteln. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
keywords: ID-Dienst
title: callTimeOut-Methoden
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 100%

---

# callTimeOut-Methoden {#calltimeout-methods}

Rufen Sie diese ID-Dienstfunktionen auf, um den Zeitüberschreitungsstatus für eine Experience Cloud Identity-Dienst-, Analytics- oder Audience Manager-ID-Anforderung zu ermitteln. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.

## Zeitüberschreitungsfunktionen  {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Lösung oder Dienst </th> 
   <th colname="col2" class="entry"> Funktionssyntax </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Experience Cloud Identity-Dienst </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Funktionsantworten {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Antwort </th> 
   <th colname="col2" class="entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>Der ID-Dienst hat eine Anforderung gesendet, bei der eine Zeitüberschreitung aufgetreten ist. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>Der ID-Dienst hat eine Anforderung gesendet und vom Server eine erfolgreiche Antwort erhalten. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>Der ID-Dienst hat keine Anforderung gesendet. </p> </td> 
  </tr> 
 </tbody> 
</table>
