---
description: setCustomerIDs legt einen oder mehr Schlüsselwertpaare fest, die Kunden-IDs und deren Authentifizierungsstatus identifizieren.
keywords: ID-Dienst
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 100%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs legt einen oder mehr Schlüsselwertpaare fest, die Kunden-IDs und deren Authentifizierungsstatus identifizieren.

**Syntax:** `visitor.setCustomerIDs()`

Sie können, wie im Code-Beispiel unten dargestellt, einzelne oder mehrere IDs festlegen. Siehe [Kunden-IDs und Authentifizierungsstatus](../../reference/authenticated-state.md) mit weiteren Informationen und Beispielen.

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```
