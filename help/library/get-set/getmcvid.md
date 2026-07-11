---
description: getMarketingCloudVisitorID gibt die ECID zurück.
keywords: Besucher-ID-Service
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
TQID: https://experienceleague.adobe.com/Ltpdq4dlGbJ8h0vAZBD52Pq7gLaurxSDYqETkLqQfDw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 52%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID gibt die ECID zurück.

**Syntax:** `var *`Name der Variablen`* = visitor.getMarketingCloudVisitorID()`

Diese Methode wird in der Regel bei benutzerdefinierten Lösungen verwendet, bei denen die Besucher-ID gelesen werden muss. Sie wird nicht von einer Standardimplementierung verwendet. `getMarketingCloudVisitorID` funktioniert auch mit Callback-Funktionen, um Analytics-IDs zu lesen und sie in Ihr System oder Ihr Programm einzubringen.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get the ECID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Wenn Sie Analytics-Kunde sind, prüfen Sie auch, ob die Analytics-ID vorhanden ist, und senden Sie sie an Ihre Funktion. Beispielsweise ist es wünschenswert, bei der Weiterleitung einer Besucher-ID in versteckter Form an eine serverseitige Anwendung, die die Dateneingabe-API verwendet, beide Identifikatoren zur Verfügung zu haben. In diesem Fall sollten Sie die ECID- und Analytics-Besucher-IDs erfassen und zurückgeben. Siehe [Erhalten der Analytics-Besucher-ID](../../library/get-set/getanalyticsvisitorid.md).

