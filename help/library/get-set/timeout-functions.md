---
description: Rufen Sie diese ID-Dienstfunktionen auf, um den Timeout-Status für eine Experience Platform Identity Service-, Analytics- oder Audience Manager-ID-Anforderung festzulegen. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
keywords: ID-Dienst
seo-description: Rufen Sie diese ID-Dienstfunktionen auf, um den Timeout-Status für eine Experience Platform Identity Service-, Analytics- oder Audience Manager-ID-Anforderung festzulegen. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.
seo-title: callTimeOut-Methoden
title: callTimeOut-Methoden
uuid: e 5047498-11 db -4945-b 356-c 92 b 7 d 447573
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# callTimeOut-Methoden{#calltimeout-methods}

Rufen Sie diese ID-Dienstfunktionen auf, um den Timeout-Status für eine Experience Platform Identity Service-, Analytics- oder Audience Manager-ID-Anforderung festzulegen. In VisitorAPI.js Version 1.7.0 oder höher verfügbar.

## Zeitüberschreitungsfunktionen {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Lösung oder Dienst </th> 
   <th colname="col2" class="entry"> Funktionssyntax </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Experience Platform-Identitätsdienst </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. mcidcalltimedout ()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. analyticsidcalltimedout ()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variablename</span> = visitor. aamidcalltimedout ()</span> </p> </td> 
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
