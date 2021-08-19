---
description: Eine optionale boolesche Kennzeichnung, die die ID-Synchronisierung deaktiviert.
keywords: ID-Dienst
title: disableIdSyncs
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '37'
ht-degree: 100%

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
