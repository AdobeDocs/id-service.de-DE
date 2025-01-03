---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Cloud Identity Service das Drittanbieter-Cookie demdex.net zurückgibt.
keywords: ID-Dienst
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 94%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Cloud Identity Service das Drittanbieter-Cookie demdex.net zurückgibt.

>[!NOTE]
>
>Diese Konfiguration hieß `idSyncDisable3rdPartySyncing` und wurde in der am 18. Januar 2018 veröffentlichten Version 3.0 umbenannt in `disableThirdPartyCookies`.

**Syntax:** `disableThirdPartyCookies: true|false` (Standard ist `false`.) für `VisitorAPI.js` Version 3.0.0 oder höher.

Wenn `disableThirdPartyCookies: true`, gibt der ID-Dienst das Drittanbieter-Cookie demdex.net nicht zurück (siehe [Cookies und der Experience Cloud Identity Service](../../introduction/cookies.md)). Sollte der Cookie bereits im Browser des Besuchers gespeichert sein, wird dieser vom ID-Dienst nicht zur Erstellung einer neuen Experience Cloud ID (MID) oder Ausgabe einer bestehenden ID eingesetzt. Stattdessen wird vom ID-Dienst eine neue, zufällige MID im Erstanbieter-Cookie erstellt. Nach der Aktivierung können Sie mit dem ID-Dienst Daten erfassen und sie über verschiedene Experience Cloud-Lösungen hinweg freigeben.

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```
