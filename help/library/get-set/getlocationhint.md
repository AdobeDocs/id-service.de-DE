---
description: Gibt die Regions-ID des Experience Cloud Identity-Diensts zurück. Eine Regions-ID (oder ein Standorthinweis) ist eine numerische ID für den geografischen Standort eines bestimmten ID-Dienst-Rechenzentrums. Sie benötigen die Regions-ID, um serverseitige API-Aufrufe an Audience Manager durchführen zu können.
keywords: ID Service
seo-description: Gibt die Regions-ID des Experience Cloud Identity-Diensts zurück. Eine Regions-ID (oder ein Standorthinweis) ist eine numerische ID für den geografischen Standort eines bestimmten ID-Dienst-Rechenzentrums. Sie benötigen die Regions-ID, um serverseitige API-Aufrufe an Audience Manager durchführen zu können.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getLocationHint{#getlocationhint}

Gibt die Regions-ID des Experience Cloud Identity-Diensts zurück. Eine Regions-ID (oder ein Standorthinweis) ist eine numerische ID für den geografischen Standort eines bestimmten ID-Dienst-Rechenzentrums. Sie benötigen die Regions-ID, um serverseitige API-Aufrufe an Audience Manager durchführen zu können.

**Syntax:** ` var *`Name der Variablen`* = visitor.getLocationHint()`

For a list of region IDs and corresponding locations, see [DCS Region IDs, Locations, and Host Names](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

**Codebeispiel**

Die Funktion &quot;location thint&quot;liest die Regions-ID aus dem AMCV-Cookie. Wenn die Regions-ID bereits im AMCV-Cookie festgelegt ist, erfolgt der Rückruf sofort. Wenn die Regions-ID nicht festgelegt ist, wartet die Funktion auf eine Antwort vom Server, bevor die Regions-ID an den Rückruf übergeben wird. Ihr Code sollte dem folgenden Beispiel ähneln.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

