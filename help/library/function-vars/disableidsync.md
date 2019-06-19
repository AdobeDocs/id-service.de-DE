---
description: Eine optionale boolesche Kennzeichnung, die die ID-Synchronisierung deaktiviert.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die die ID-Synchronisierung deaktiviert.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8 bea 1 de 8-53 c 8-4 a 15-bcf 5-f 0869763 a 32 e
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# disableIdSyncs{#disableidsyncs}

Eine optionale boolesche Kennzeichnung, die die ID-Synchronisierung deaktiviert.

>[!NOTE]
>
>Diese Konfiguration wurde `idSyncDisableSyncs``disableIdSyncs` in der Version 3.0 vom 18. Januar 2018 in Version 3.0 umbenannt.

**Syntax:**`disableIdSyncs: true|false` (Standard ist `false`.)

**Codebeispiel**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

