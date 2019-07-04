---
description: Eine optionale boolesche Kennzeichnung, die die ID-Synchronisierung deaktiviert.
keywords: ID-Dienst
seo-description: Eine optionale boolesche Kennzeichnung, die die ID-Synchronisierung deaktiviert.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableIdSyncs{#disableidsyncs}

Eine optionale boolesche Kennzeichnung, die die ID-Synchronisierung deaktiviert.

>[!NOTE]
>
>Diese Konfiguration hieß `idSyncDisableSyncs` und wurde in der am 18. Januar 2018 veröffentlichten Version 3.0 umbenannt in `disableIdSyncs`.

**Syntax:** `disableIdSyncs: true|false` (Standard ist `false`.)

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

