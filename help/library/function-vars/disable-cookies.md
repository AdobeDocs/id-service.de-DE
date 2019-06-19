---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Platform Identity Service das Drittanbieter-demdex. net-Cookie zurückgibt.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Platform Identity Service das Drittanbieter-demdex. net-Cookie zurückgibt.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ed 5 aa 16-44 ca -4702-878 a -1 a 208 ca 95270
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Platform Identity Service das Drittanbieter-demdex. net-Cookie zurückgibt.

>[!NOTE]
>
>Diese Konfiguration wurde `idSyncDisable3rdPartySyncing``disableThirdPartyCookies` in der Version 3.0 vom 18. Januar 2018 in Version 3.0 umbenannt.

**Syntax:**`disableThirdPartyCookies: true|false` (Standard ist `false`.) Für `VisitorAPI.js` v 1.5.3 oder höher.

Wenn `disableThirdPartyCookies: true`der ID-Dienst das Drittanbieter-Cookie demdex. net nicht zurückgibt (siehe [Cookies und Experience Platform Identity Service](../../introduction/cookies.md) ). Sollte der Cookie bereits im Browser des Besuchers gespeichert sein, wird dieser vom ID-Dienst nicht zur Erstellung einer neuen Experience Cloud ID (MID) oder Ausgabe einer bestehenden ID eingesetzt. Stattdessen wird vom ID-Dienst eine neue, zufällige MID im Erstanbieter-Cookie erstellt. Nach der Aktivierung können Sie mit dem ID-Dienst Daten erfassen und sie über verschiedene Experience Cloud-Lösungen hinweg freigeben.

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

