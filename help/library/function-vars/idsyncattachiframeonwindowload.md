---
description: Eine optionale boolesche Kennzeichnung, die steuert, wie der Experience Cloud Identity Service den ID-Synchronisierungs-iFrame lädt.
keywords: ID-Dienst
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '77'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Eine optionale boolesche Kennzeichnung, die steuert, wie der Experience Cloud Identity Service den ID-Synchronisierungs-iFrame lädt.

**Syntax:** ` `idSyncAttachIframeOnWindowLoad= true|false`` (Standard ist `false`.)

Bei `idSyncAttachIframeOnWindowLoad: true` lädt der ID-Dienst den iFrame zur ID-Synchronisierung beim Laden des Fensters. Standardmäßig lädt der ID-Dienst den iFrame zur ID-Synchronisierung so schnell wie möglich statt erst beim Laden des Fensters.

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
