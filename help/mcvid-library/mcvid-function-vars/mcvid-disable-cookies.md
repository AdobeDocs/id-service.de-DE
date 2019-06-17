---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Cloud ID-Dienst das Drittanbieter-Cookie demdex.net zurückgibt.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Cloud ID-Dienst das Drittanbieter-Cookie demdex.net zurückgibt.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ed 5 aa 16-44 ca -4702-878 a -1 a 208 ca 95270
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Cloud ID-Dienst das Drittanbieter-Cookie demdex.net zurückgibt.

>[!NOTE]
>
>Diese Konfiguration wurde `idSyncDisable3rdPartySyncing``disableThirdPartyCookies` in der Version 3.0 vom 18. Januar 2018 in Version 3.0 umbenannt.

**Syntax:**`disableThirdPartyCookies: true|false` (Standard ist `false`.) Für `VisitorAPI.js` v 1.5.3 oder höher.

Wenn `disableThirdPartyCookies: true`der ID-Dienst das Drittanbieter-Cookie demdex. net nicht zurückgibt (siehe [Cookies und Experience Cloud ID-Dienst](../../mcvid-introduction/mcvid-cookies.md) ). Sollte der Cookie bereits im Browser des Besuchers gespeichert sein, wird dieser vom ID-Dienst nicht zur Erstellung einer neuen Experience Cloud ID (MID) oder Ausgabe einer bestehenden ID eingesetzt. Stattdessen wird vom ID-Dienst eine neue, zufällige MID im Erstanbieter-Cookie erstellt. Nach der Aktivierung können Sie mit dem ID-Dienst Daten erfassen und sie über verschiedene Experience Cloud-Lösungen hinweg freigeben.

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

