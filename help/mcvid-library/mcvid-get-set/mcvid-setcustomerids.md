---
description: setCustomerIDs legt einen oder mehr Schlüsselwertpaare fest, die Kunden-IDs und deren Authentifizierungsstatus identifizieren.
keywords: ID-Dienst
seo-description: setCustomerIDs legt einen oder mehr Schlüsselwertpaare fest, die Kunden-IDs und deren Authentifizierungsstatus identifizieren.
seo-title: „setCustomerIDs“
title: „setCustomerIDs“
uuid: 4 f 960 f 98-cec 2-4 db 6-84 ea -0259 e 2128 ea 2
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# „setCustomerIDs“{#setcustomerids}

setCustomerIDs legt einen oder mehr Schlüsselwertpaare fest, die Kunden-IDs und deren Authentifizierungsstatus identifizieren.

**Syntax:** `visitor.setCustomerIDs()`

Sie können, wie im Code-Beispiel unten dargestellt, einzelne oder mehrere IDs festlegen. Siehe [Kunden-IDs und Authentifizierungsstatus](../../mcvid-reference/mcvid-authenticated-state.md) für weitere Informationen und Beispiele.

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
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```
