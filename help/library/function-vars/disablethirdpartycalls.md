---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.
keywords: cross domain tracking;ID Service
seo-description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.
seo-title: disableThirdPartyCalls
title: disableThirdPartyCalls
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 58%

---


# disableThirdPartyCalls{#disablethirdpartycalls}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.

**Syntax:** ` `disableThirdPartyCalls: true|false`` (Standard ist `false`.)

Bei `disableThirdPartyCalls: true` gibt der ID-Dienst keine Aufrufe an andere Domänen aus.

**Zielsetzung**

Diese Variable wurde für Kunden entwickelt, die Folgendes benötigen:

* Damit verhindert wird, dass der ID-Dienst auf ihren sicheren, authentifizierten Seiten Aufrufe durchführt.
* Site-Besucher mit einer Experience Cloud-ID (MID).
* Die anderen Experience Cloud-Lösungen funktionieren einwandfrei.

**Implementierungsstrategie**

Da andere Experience Cloud-Lösungen auf der MID basieren, ruft der ID-Dienst die Adobe auf, diese ID zurückzugeben und festzulegen. Wenn Sie verhindern müssen, dass der ID-Dienst Aufrufe über authentifizierte Abschnitte Ihrer Website tätigt, sollten Sie diese erforderlichen Aufrufe über Seiten zulassen, für die zunächst keine Authentifizierung erforderlich ist. Wenn Ihr Sitebesucher über eine MID verfügt, können Sie `disableThirdPartyCalls= true` im ID-Dienstcode auf die authentifizierten Abschnitte Ihrer Site festlegen. Dabei wird davon ausgegangen, dass die meisten, wenn nicht sogar alle Kunden zu einer Authentifizierungsseite navigieren, bevor sie Zugriff auf die sicheren Teile Ihrer Site erhalten.

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

