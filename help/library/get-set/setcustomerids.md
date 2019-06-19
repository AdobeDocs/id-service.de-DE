---
description: setCustomerIDs legt einen oder mehr Schlüsselwertpaare fest, die Kunden-IDs und deren Authentifizierungsstatus identifizieren.
keywords: ID-Dienst
seo-description: setCustomerIDs legt einen oder mehr Schlüsselwertpaare fest, die Kunden-IDs und deren Authentifizierungsstatus identifizieren.
seo-title: „setCustomerIDs“
title: „setCustomerIDs“
uuid: 4 f 960 f 98-cec 2-4 db 6-84 ea -0259 e 2128 ea 2
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# „setCustomerIDs“{#setcustomerids}

setCustomerIDs legt einen oder mehr Schlüsselwertpaare fest, die Kunden-IDs und deren Authentifizierungsstatus identifizieren.

**Syntax:** `visitor.setCustomerIDs()`

Sie können, wie im Code-Beispiel unten dargestellt, einzelne oder mehrere IDs festlegen. Siehe [Kunden-IDs und Authentifizierungsstatus](../../reference/authenticated-state.md) für weitere Informationen und Beispiele.

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

