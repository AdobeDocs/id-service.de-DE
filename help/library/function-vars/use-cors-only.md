---
description: Eine optionale boolesche Kennzeichnung, die steuert, wie der Browser Ressourcen vom Experience Platform Identity Service anfordert.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die steuert, wie der Browser Ressourcen vom Experience Platform Identity Service anfordert.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607 dc 035-dffc -4 f 4 d-be 51-08 ef 6 c 0 a 8 mode
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# useCORSOnly{#usecorsonly}

Eine optionale boolesche Kennzeichnung, die steuert, wie der Browser Ressourcen vom Experience Platform Identity Service anfordert.

**Syntax:**`useCORSOnly: true|false` (Standard ist `false`.)

**Übersicht**

Wenn der Wert auf `false` festgelegt ist, führt der Browser Ressourcenprüfungen mit CORS und JSONP durch. Der ID-Dienst versucht jedoch immer zunächst, Ressourcen mit CORS anzufordern. Bei älteren Browsern, die CORS nicht unterstützen, wird auf JSONP zurückgegriffen. Legen Sie `useCORSOnly:true` im Funktionsaufruf `Visitor.getInstance` fest, sofern Sie erzwingen müssen, dass der Browser nur CORS verwendet.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` wenn Sie über strenge Sicherheitsanforderungen verfügen. Sie sollten diesen Modus nur dann aktivieren, wenn Sie davon überzeugt sind, dass alle Besucher Browser verwenden, die CORS unterstützen. Die Benutzeroberfläche wird durch Browser, die CORS nicht unterstützen, nicht beeinflusst. Browser ohne CORS-Unterstützung können mit [!DNL Adobe Experience Cloud] jedoch weder Ressourcen anfordern noch Daten austauschen.

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
