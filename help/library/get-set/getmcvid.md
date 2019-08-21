---
description: getMarketingCloudVisitorID gibt die Experience Cloud-Besucher-ID zurück.
keywords: ID-Dienst
seo-description: getMarketingCloudVisitorID gibt die Experience Cloud-Besucher-ID zurück.
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID gibt die Experience Cloud-Besucher-ID zurück.

**Syntax:** ` var *`variable name`* = visitor.getMarketingCloudVisitorID()`

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
>Wenn Sie [!DNL Analytics]-Kunde sind, suchen Sie nach der [!DNL Analytics]-ID und senden Sie diese an Ihre Funktion. Beispielsweise ist es wünschenswert, bei der Weiterleitung einer Besucher-ID in versteckter Form an eine serverseitige Anwendung, die die Dateneingabe-API verwendet, beide Identifikatoren zur Verfügung zu haben. In diesem Fall sollten Sie die [!DNL Experience Cloud]- und [!DNL Analytics]-Besucher-IDs erfassen und zurückgeben. Siehe [Erhalten der Analytics-Besucher-ID](../../library/get-set/getanalyticsvisitorid.md).

