---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Besucher-ID-Dienst das Drittanbieter-Cookie demdex.net zurückgibt.
keywords: Besucher-ID-Service
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
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 16%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der Besucher-ID-Dienst das Drittanbieter-Cookie demdex.net zurückgibt.

>[!NOTE]
>
>Diese Konfiguration hieß `idSyncDisable3rdPartySyncing` und wurde in der am 18. Januar 2018 veröffentlichten Version 3.0 umbenannt in `disableThirdPartyCookies`.

**Syntax:** `disableThirdPartyCookies: true|false` (Standard ist `false`.) Für `VisitorAPI.js` Version 3.0.0 oder höher.

Wenn `disableThirdPartyCookies: true`, gibt der Besucher-ID-Dienst das Drittanbieter-Cookie demdex.net nicht zurück (siehe &quot;[&#x200B; und der Besucher-ID-Dienst](../../introduction/cookies.md) ). Wenn ein Site-Besucher dieses Cookie bereits in seinem Browser hat, verwendet der Besucher-ID-Dienst es nicht, um eine neue ECID zu erstellen oder eine vorhandene ID zurückzugeben. Stattdessen erstellt der Besucher-ID-Dienst im Erstanbieter-Cookie eine neue, zufällige MID. Nach der Aktivierung können Sie Daten mit dem Besucher-ID-Service erfassen und über verschiedene CX Enterprise-Lösungen hinweg freigeben.

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

