---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Platform Identity Service das Drittanbieter-demdex. net-Cookie zurückgibt.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Platform Identity Service das Drittanbieter-demdex. net-Cookie zurückgibt.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Platform Identity Service das Drittanbieter-demdex. net-Cookie zurückgibt.

>[!NOTE]
>
>Diese Konfiguration hieß `idSyncDisable3rdPartySyncing` und wurde in der am 18. Januar 2018 veröffentlichten Version 3.0 umbenannt in `disableThirdPartyCookies`.

**Syntax:** `disableThirdPartyCookies: true|false` (Standard ist `false`.) Für `VisitorAPI.js` Version 1.5.3 oder höher.

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Platform Identity Service](../../introduction/cookies.md) ). Sollte der Cookie bereits im Browser des Besuchers gespeichert sein, wird dieser vom ID-Dienst nicht zur Erstellung einer neuen Experience Cloud ID (MID) oder Ausgabe einer bestehenden ID eingesetzt. Stattdessen wird vom ID-Dienst eine neue, zufällige MID im Erstanbieter-Cookie erstellt. Nach der Aktivierung können Sie mit dem ID-Dienst Daten erfassen und sie über verschiedene Experience Cloud-Lösungen hinweg freigeben.

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

