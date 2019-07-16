---
description: Eine optionale boolesche Kennzeichnung, die steuert, wie der Experience Platform Identity Service den iframe für die ID-Synchronisierung lädt.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die steuert, wie der Experience Platform Identity Service den iframe für die ID-Synchronisierung lädt.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Eine optionale boolesche Kennzeichnung, die steuert, wie der Experience Platform Identity Service den iframe für die ID-Synchronisierung lädt.

**Syntax:** ` `idSyncAttachIframeOnWindowLoad= true|false`` (Standard ist `false`.)

Bei `idSyncAttachIframeOnWindowLoad: true` lädt der ID-Dienst den iFrame zur ID-Synchronisierung beim Laden des Fensters. Standardmäßig lädt der ID-Dienst den iFrame zur ID-Synchronisierung so schnell wie möglich anstelle des Ladens im Fenster.

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

