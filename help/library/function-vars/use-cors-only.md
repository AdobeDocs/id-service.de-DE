---
description: Eine optionale boolesche Kennzeichnung, die steuert, wie Browser Ressourcen vom Experience Cloud Identity Service anfordern.
keywords: ID-Dienst
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 87%

---

# useCORSOnly{#usecorsonly}

Eine optionale boolesche Kennzeichnung, die steuert, wie Browser Ressourcen vom Experience Cloud Identity Service anfordern.

**Syntax:** `useCORSOnly: true|false` (Standard ist `false`.)

**Übersicht**

Wenn der Wert auf `false` festgelegt ist, führt der Browser Ressourcenprüfungen mit CORS und JSONP durch. Der ID-Dienst versucht jedoch immer, zunächst Ressourcen mit CORS anzufordern. Bei älteren Browsern, die CORS nicht unterstützen, wird auf JSONP zurückgegriffen. Legen Sie `useCORSOnly:true` im Funktionsaufruf `Visitor.getInstance` fest, sofern Sie erzwingen müssen, dass der Browser nur CORS verwendet.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` Wenn Sie strenge Sicherheitsanforderungen haben. Sie sollten diesen Modus nur aktivieren, wenn Sie sicher sind, dass alle Ihre Besucher Browser verwenden, die CORS unterstützen. Die Benutzeroberfläche wird durch Browser, die CORS nicht unterstützen, nicht beeinflusst. Browser ohne CORS-Unterstützung können mit [!DNL Adobe Experience Cloud] jedoch weder Ressourcen anfordern noch Daten austauschen.

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

