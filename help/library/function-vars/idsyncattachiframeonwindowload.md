---
description: Eine optionale boolesche Kennzeichnung, die steuert, wie der Experience Platform Identity Service den iframe für die ID-Synchronisierung lädt.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die steuert, wie der Experience Platform Identity Service den iframe für die ID-Synchronisierung lädt.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa 2 c 2 fa 4-2 cab -4 e 08-8 d 35-729 a 6 c 3 e 459 a
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Eine optionale boolesche Kennzeichnung, die steuert, wie der Experience Platform Identity Service den iframe für die ID-Synchronisierung lädt.

**Syntax:**` `Idsyncattachiframeonwindowload = true | false «(Standard ist `false`.)

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

