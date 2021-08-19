---
description: Legt fest, ob die Vorlage für die Zielveröffentlichung bei HTTPS-Verbindungen mit Akamai ausgeführt werden soll.
keywords: ID-Dienst
title: idSyncSSLUseAkamai
exl-id: 74c24eb5-bf3d-4e6b-ac7d-1a37d940d77f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '39'
ht-degree: 100%

---

# idSyncSSLUseAkamai{#idsyncssluseakamai}

Legt fest, ob die Vorlage für die Zielveröffentlichung bei HTTPS-Verbindungen mit Akamai ausgeführt werden soll.

Die `idSyncSSLUseAkamai`-Konfiguration wird pro Partner aktiviert.

**Syntax:** `idSyncSSLUseAkamai: true`

**Codebeispiel**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```
