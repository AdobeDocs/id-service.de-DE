---
description: Gibt die Legacy-Analytics-ID (sofern vorhanden) zurück, die vor der Implementierung des Experience Cloud Identity-Diensts im s_vi-Cookie gespeichert war. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.
keywords: ID-Dienst
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 100%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Gibt die Legacy-Analytics-ID (sofern vorhanden) zurück, die vor der Implementierung des Experience Cloud Identity-Diensts im s_vi-Cookie gespeichert war. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.

**Syntax** `var analyticsID = visitor.getAnalyticsVisitorID()`

Diese Funktion wird in der Regel bei benutzerdefinierten Lösungen verwendet, bei denen die Besucher-ID gelesen werden muss. Sie wird nicht von einer Standardimplementierung verwendet. `getAnalyticsVisitorID` kann auch bei Callback-Funktionen zum Lesen von [!DNL Analytics]-IDs und deren Übernahme in Ihr System oder Ihre Anwendung eingesetzt werden.

**Beispielcode**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>Wenn Sie [!DNL Analytics]-Kunde sind, suchen Sie nach der [!DNL Analytics]-ID und senden Sie diese an Ihre Funktion. Beispielsweise ist es wünschenswert, bei der Weiterleitung einer Besucher-ID in versteckter Form an eine serverseitige Anwendung, die die Dateneingabe-API verwendet, beide Identifikatoren zur Verfügung zu haben. In diesem Fall sollten Sie die [!DNL Experience Cloud]- und [!DNL Analytics]-Besucher-IDs erfassen und zurückgeben. Siehe [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**Der Parameter „aid“ ist ein veralteter Wert**

Der `aid` Parameter taucht in einer Abfragezeichenfolge unter zweierlei verschiedenen Bedingungen auf.

**1. Fall**

Der Parameter `aid` taucht in einer Abfragezeichenfolge auf, wenn:

* der [!DNL Experience Cloud] ID-Dienst ordnungsgemäß bereitgestellt wurde.
* Im [s_vi-Cookie](https://docs.adobe.com/content/help/de-DE/core-services/interface/ec-cookies/cookies-analytics.html#section-5d50a078de444d12b7d927d68ff3b679) des eine Site besuchenden Benutzers bereits eine [!DNL Analytics]-ID gespeichert ist.

**2. Fall**

Sie sehen den `aid` Parameter in einer Abfragezeichenfolge, wenn Ihr Unternehmen eine [Übergangsphase](../../reference/analytics-reference/grace-period.md) verwendet, bevor es den ID-Dienst vollständig implementiert. Hat der aktuelle Besucher Ihre Seite zuvor noch nie aufgerufen und sollten Sie keine Übergangsphase festgelegt haben, erhält der Besucher den Parameter `mid` ([!DNL Experience Cloud] ID).

>[!MORELIKETHIS]
>
>* [Cookies in Analytics](https://docs.adobe.com/content/help/de-DE/core-services/interface/ec-cookies/cookies-privacy.html)

