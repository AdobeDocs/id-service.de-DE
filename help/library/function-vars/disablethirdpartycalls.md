---
description: Eine optionale boolesche Kennzeichnung, die verhindert, dass der Besucher-ID-Dienst Aufrufe an andere Domains sendet.
keywords: Domain-übergreifendes Tracking;Besucher-ID-Service
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
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 205
ht-degree: 24%

---

# disableThirdPartyCalls{#disablethirdpartycalls}

Eine optionale boolesche Kennzeichnung, die verhindert, dass der Besucher-ID-Dienst Aufrufe an andere Domains sendet.

**Syntax:** ` `disableThirdPartyCalls: true|false&grave;&grave; (Standard ist `false`.)

Bei der `disableThirdPartyCalls: true` führt der Besucher-ID-Dienst keine Aufrufe an andere Domains durch.

**Zweck**

Diese Variable wurde für Kunden entwickelt, um:

* , um zu verhindern, dass der Besucher-ID-Dienst Aufrufe von seinen sicheren, authentifizierten Seiten ausführt.
* Website-Besucherinnen und -Besucher, die eine ECID haben sollen.
* Die anderen CX Enterprise-Lösungen funktionieren ordnungsgemäß.

**Implementierungsstrategie**

Da andere CX Enterprise-Lösungen auf der MID basieren, ruft der Besucher-ID-Dienst Adobe auf, um diese ID zurückzugeben und festzulegen. Wenn Sie verhindern müssen, dass der Besucher-ID-Dienst Aufrufe aus authentifizierten Bereichen Ihrer Website ausführt, lassen Sie ihn diese erforderlichen Aufrufe von Seiten ausführen, für die keine Authentifizierung erforderlich ist. Nachdem der Site-Besucher über eine MID verfügt, können Sie `disableThirdPartyCalls= true` im Code des Besucher-ID-Service in den authentifizierten Bereichen Ihrer Site festlegen. Dabei wird davon ausgegangen, dass die meisten – wenn nicht sogar alle – Kunden zu einer Authentifizierungsseite navigieren, bevor sie Zugriff auf die sicheren Bereiche Ihrer Site erhalten.

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

