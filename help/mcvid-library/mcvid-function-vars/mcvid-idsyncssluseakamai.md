---
description: Legt fest, ob die Vorlage für die Zielveröffentlichung bei HTTPS-Verbindungen mit Akamai ausgeführt werden soll.
keywords: ID-Dienst
seo-description: Legt fest, ob die Vorlage für die Zielveröffentlichung bei HTTPS-Verbindungen mit Akamai ausgeführt werden soll.
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501 ccc 37-c 3 ab -4454-bfcf -3 e 3 c 3 e 8 b 5 ca 3
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

Legt fest, ob die Vorlage für die Zielveröffentlichung bei HTTPS-Verbindungen mit Akamai ausgeführt werden soll.

Die `idSyncSSLUseAkamai`-Konfiguration wird pro Partner aktiviert.

**Syntax: ** `idSyncSSLUseAkamai: true`

**Codebeispiel**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

