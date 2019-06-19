---
description: Gibt die Regions-ID für die Experience Platform Identity Service-ID zurück. Bei einer Regions-ID (oder einem Standorthinweis) handelt es sich um eine numerische ID für den geografischen Standort eines bestimmten ID-Dienst-Rechenzentrums. Sie benötigen die Regions-ID für serverseitige API-Aufrufe an Audience Manager.
keywords: ID-Dienst
seo-description: Gibt die Regions-ID für die Experience Platform Identity Service-ID zurück. Bei einer Regions-ID (oder einem Standorthinweis) handelt es sich um eine numerische ID für den geografischen Standort eines bestimmten ID-Dienst-Rechenzentrums. Sie benötigen die Regions-ID für serverseitige API-Aufrufe an Audience Manager.
seo-title: getLocationHint
title: getLocationHint
uuid: cdc 312 b 7-d 270-4 a 5 c-a 2 bb -0 fbb 37 f 1 e 2 f 4
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getLocationHint{#getlocationhint}

Gibt die Regions-ID für die Experience Platform Identity Service-ID zurück. Bei einer Regions-ID (oder einem Standorthinweis) handelt es sich um eine numerische ID für den geografischen Standort eines bestimmten ID-Dienst-Rechenzentrums. Sie benötigen die Regions-ID für serverseitige API-Aufrufe an Audience Manager.

**Syntax:**` var *`Variablenname`* = visitor.getLocationHint()`

Eine Liste der Regions-IDs und der entsprechenden Standorte finden Sie unter [DCS Region IDs, Locations, and Host Names](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html).

**Codebeispiel**

Die Standorthinweisfunktion liest die Regions-ID aus dem AMCV-Cookie. Wenn die Regions-ID bereits im AMCV-Cookie festgelegt wurde, erfolgt der Callback sofort. Wenn die Regions-ID nicht festgelegt ist, wartet die Funktion auf eine Antwort vom Server, bevor die Regions-ID an das Callback weitergegeben wird. Ihr Code sollte dem folgenden Beispiel ähneln.

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

