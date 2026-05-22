---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Cloud Identity Service das Drittanbieter-Cookie demdex.net zurückgibt.
keywords: ID-Dienst
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 97%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der Experience Cloud Identity Service das Drittanbieter-Cookie demdex.net zurückgibt.

>[!NOTE]
>
>Diese Konfiguration hieß `idSyncDisable3rdPartySyncing` und wurde in der am 18. Januar 2018 veröffentlichten Version 3.0 umbenannt in `disableThirdPartyCookies`.

**Syntax:** `disableThirdPartyCookies: true|false` (Standard ist `false`.) Für `VisitorAPI.js` Version 3.0.0 oder höher.

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

