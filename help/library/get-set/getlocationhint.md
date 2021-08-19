---
description: Gibt die Regions-ID des Experience Cloud Identity-Diensts zurück. Eine Regions-ID (oder ein Standorthinweis) ist eine numerische ID für den geografischen Standort eines bestimmten ID-Dienst-Rechenzentrums. Sie benötigen die Regions-ID, um Server-seitige API-Aufrufe an Audience Manager durchführen zu können.
keywords: ID-Dienst
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '185'
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

Gibt die Regions-ID des Experience Cloud Identity-Diensts zurück. Eine Regions-ID (oder ein Standorthinweis) ist eine numerische ID für den geografischen Standort eines bestimmten ID-Dienst-Rechenzentrums. Sie benötigen die Regions-ID, um Server-seitige API-Aufrufe an Audience Manager durchführen zu können.

**Syntax:** ` var *`Name der Variablen`* = visitor.getLocationHint()`

Eine Liste der Regions-IDs und der entsprechenden Standorte finden Sie unter [DCS-Regions-IDs, Standorte und Hostnamen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=de).

**Codebeispiel**

Die Standorthinweisfunktion (location hint) liest die Regions-ID aus dem AMCV-Cookie. Wenn die Regions-ID bereits im AMCV-Cookie gesetzt ist, erfolgt der Callback sofort. Wenn die Regions-ID nicht gesetzt ist, wartet die Funktion auf eine Antwort vom Server, bevor die Regions-ID an den Callback übergeben wird. Ihr Code sollte dem folgenden Beispiel ähneln.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```
