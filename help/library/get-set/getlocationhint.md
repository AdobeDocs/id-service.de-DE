---
description: Gibt die Regions-ID des Besucher-ID-Service zurück. Eine Regions-ID (oder Standorthinweis) ist eine numerische Kennung für den geografischen Standort eines bestimmten Besucher-ID-Service-Rechenzentrums. Sie benötigen die Regions-ID, um Server-seitige API-Aufrufe an Audience Manager durchführen zu können.
keywords: Besucher-ID-Service
title: getLocationHint
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
TQID: https://experienceleague.adobe.com/Q58a-bmHINs-3mhlUarH8Ipo85tNhjTjMDSlZLFcHsw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 196
ht-degree: 70%

---

# getLocationHint{#getlocationhint}

Gibt die Regions-ID des Besucher-ID-Service zurück. Eine Regions-ID (oder Standorthinweis) ist eine numerische Kennung für den geografischen Standort eines bestimmten Besucher-ID-Service-Rechenzentrums. Sie benötigen die Regions-ID, um Server-seitige API-Aufrufe an Audience Manager durchführen zu können.

**Syntax:** `var *`Name der Variablen`* = visitor.getLocationHint()`

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

