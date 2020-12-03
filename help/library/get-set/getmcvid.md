---
description: getMarketingCloudVisitorID gibt die Experience Cloud-Besucher-ID zurück.
keywords: ID Service
seo-description: getMarketingCloudVisitorID gibt die Experience Cloud-Besucher-ID zurück.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: tm+mt
source-git-commit: 4a5fbc971dc950c65e5c8f92dffdfe5dde528b54
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 89%

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID gibt die Experience Cloud-Besucher-ID zurück.

**Syntax:** ` var *`variable name`* = visitor.getMarketingCloudVisitorID()`

Diese Methode wird in der Regel bei benutzerdefinierten Lösungen verwendet, bei denen die Besucher-ID gelesen werden muss. Sie wird nicht von einer Standardimplementierung verwendet. `getMarketingCloudVisitorID` kann auch bei Callback-Funktionen zum Lesen von [!DNL Analytics]-IDs und deren Übernahme in Ihr System oder Ihre Anwendung eingesetzt werden.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>Wenn Sie [!DNL Analytics]-Kunde sind, suchen Sie nach der [!DNL Analytics]-ID und senden Sie diese an Ihre Funktion. Beispielsweise ist es wünschenswert, bei der Weiterleitung einer Besucher-ID in versteckter Form an eine serverseitige Anwendung, die die Dateneingabe-API verwendet, beide Identifikatoren zur Verfügung zu haben. In diesem Fall sollten Sie die [!DNL Experience Cloud]- und [!DNL Analytics]-Besucher-IDs erfassen und zurückgeben. Siehe [Erhalten der Analytics-Besucher-ID](../../library/get-set/getanalyticsvisitorid.md).

