---
description: getMarketingCloudVisitorID gibt die Experience Cloud-Besucher-ID zurück.
keywords: ID-Dienst
seo-description: getMarketingCloudVisitorID gibt die Experience Cloud-Besucher-ID zurück.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93 e 16220-b 5 b 3-4 d 81-9189-30031 bc 15129
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID gibt die Experience Cloud-Besucher-ID zurück.

**Syntax:**` var *`Variablenname`* = visitor.getMarketingCloudVisitorID()`

Diese Methode wird üblicherweise für benutzerspezifische Lösungen verwendet, bei denen die Besucher-ID gelesen werden muss. Sie wird nicht für Standardimplementierungen verwendet. `getMarketingCloudVisitorID` kann auch bei Callback-Funktionen zum Lesen von [!DNL Analytics]-IDs und deren Übernahme in Ihr System oder Ihre Anwendung eingesetzt werden.

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingClouidID)
```

>[!TIP]
>
>Wenn Sie [!DNL Analytics] Kunde sind, suchen Sie nach der [!DNL Analytics] ID und senden Sie sie an Ihre Funktion. Beispielsweise ist es wünschenswert, bei der Weiterleitung einer Besucher-ID in versteckter Form an eine serverseitige Anwendung, die die Dateneingabe-API verwendet, beide Identifikatoren zur Verfügung zu haben. In diesem Fall sollten Sie die [!DNL Experience Cloud] Besucher- und [!DNL Analytics] Besucher-IDs erfassen und zurückgeben. Siehe [Abrufen von Analytics-Besucher-ID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md).
