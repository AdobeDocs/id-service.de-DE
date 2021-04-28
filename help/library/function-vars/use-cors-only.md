---
description: Eine optionale boolesche Kennzeichnung, die steuert, wie Browser Ressourcen vom Experience Cloud Identity-Dienst anfordern.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die steuert, wie Browser Ressourcen vom Experience Cloud Identity-Dienst anfordern.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '163'
ht-degree: 100%

---

# useCORSOnly {#usecorsonly}

Eine optionale boolesche Kennzeichnung, die steuert, wie Browser Ressourcen vom Experience Cloud Identity-Dienst anfordern.

**Syntax:** `useCORSOnly: true|false` (Standard ist `false`.)

**Übersicht**

Wenn der Wert auf `false` festgelegt ist, führt der Browser Ressourcenprüfungen mit CORS und JSONP durch. Der ID-Dienst versucht jedoch immer, zunächst Ressourcen mit CORS anzufordern. Bei älteren Browsern, die CORS nicht unterstützen, wird auf JSONP zurückgegriffen. Legen Sie `useCORSOnly:true` im Funktionsaufruf `Visitor.getInstance` fest, sofern Sie erzwingen müssen, dass der Browser nur CORS verwendet.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` Wenn Sie strenge Sicherheitsanforderungen haben. Sie sollten diesen Modus nur dann aktivieren, wenn Sie davon überzeugt sind, dass alle Besucher Browser verwenden, die CORS unterstützen. Die Benutzeroberfläche wird durch Browser, die CORS nicht unterstützen, nicht beeinflusst. Browser ohne CORS-Unterstützung können mit [!DNL Adobe Experience Cloud] jedoch weder Ressourcen anfordern noch Daten austauschen.

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
