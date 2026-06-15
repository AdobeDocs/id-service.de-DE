---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.
keywords: domänenübergreifendes Tracking, ID-Dienst
title: disableThirdPartyCalls
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 200
ht-degree: 100%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der ID-Dienst andere Domänen aufruft.

**Syntax:** ` `disableThirdPartyCalls: true|false`` (Standard ist `false`.)

Bei `disableThirdPartyCalls: true` gibt der ID-Dienst keine Aufrufe an andere Domänen aus.

**Zweck**

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

