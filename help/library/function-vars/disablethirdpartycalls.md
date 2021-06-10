---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.
keywords: domänenübergreifendes Tracking, ID-Dienst
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.

**Syntax:** ` `disableThirdPartyCalls: true false`` (Standard ist `false`.)

Bei `disableThirdPartyCalls: true` gibt der ID-Dienst keine Aufrufe an andere Domänen aus.

**Zielsetzung**

Diese Variable wurde für Kunden entwickelt, um:

* zu verhindern, dass der ID-Dienst auf ihren sicheren, authentifizierten Seiten Aufrufe durchführt.
* Site-Besucher mit einer Experience Cloud ID (MID) zu versehen.
* ihren anderen Experience Cloud-Lösungen eine einwandfreie Funktion zu ermöglichen.

**Implementierungsstrategie**

Da andere Experience Cloud-Lösungen die MID benötigen, ruft der ID-Dienst Adobe auf, diese ID zurückzugeben und festzulegen. Wenn Sie verhindern müssen, dass der ID-Dienst Aufrufe über authentifizierte Abschnitte Ihrer Website tätigt, sollten Sie diese erforderlichen Aufrufe über Seiten zulassen, für die zunächst keine Authentifizierung erforderlich ist. Wenn Ihr Sitebesucher über eine MID verfügt, können Sie `disableThirdPartyCalls= true` im ID-Dienstcode auf die authentifizierten Abschnitte Ihrer Site festlegen. Dabei wird davon ausgegangen, dass die meisten – wenn nicht sogar alle – Kunden zu einer Authentifizierungsseite navigieren, bevor sie Zugriff auf die sicheren Bereiche Ihrer Site erhalten.

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
