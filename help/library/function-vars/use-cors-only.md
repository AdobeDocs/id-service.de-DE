---
description: Eine optionale boolesche Kennzeichnung, die steuert, wie der Browser Ressourcen vom Besucher-ID-Service anfordert.
keywords: Besucher-ID-Service
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
TQID: https://experienceleague.adobe.com/QMYUbL2y8X5gSUcLmYnKZnp5mfEu7-uiogOx3rx2dkY
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 46%

---

# useCORSOnly{#usecorsonly}

Eine optionale boolesche Kennzeichnung, die steuert, wie der Browser Ressourcen vom Besucher-ID-Service anfordert.

**Syntax:** `useCORSOnly: true|false` (Standard ist `false`.)

**Übersicht**

Wenn der Wert auf `false` festgelegt ist, führt der Browser Ressourcenprüfungen mit CORS und JSONP durch. Der Besucher-ID-Dienst versucht jedoch immer zuerst, Ressourcen mit CORS anzufordern. Bei älteren Browsern, die CORS nicht unterstützen, wird auf JSONP zurückgegriffen. Legen Sie `useCORSOnly:true` im Funktionsaufruf `Visitor.getInstance` fest, sofern Sie erzwingen müssen, dass der Browser nur CORS verwendet.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` Wenn Sie strenge Sicherheitsanforderungen haben. Sie sollten diesen Modus nur aktivieren, wenn Sie sicher sind, dass alle Ihre Besucher Browser verwenden, die CORS unterstützen. Die Benutzeroberfläche wird durch Browser, die CORS nicht unterstützen, nicht beeinflusst. Browser ohne CORS-Unterstützung können jedoch keine Ressourcen anfordern oder Daten mit Adobe CX Enterprise austauschen.

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

