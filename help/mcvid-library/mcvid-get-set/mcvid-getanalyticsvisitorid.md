---
description: Gibt die Legacy-Analytics-ID (sofern vorhanden) zurück, die vor der Implementierung des Experience Cloud ID-Diensts im s_vi cookie-Cookie gespeichert war. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.
keywords: ID-Dienst
seo-description: Gibt die Legacy-Analytics-ID (sofern vorhanden) zurück, die vor der Implementierung des Experience Cloud ID-Diensts im s_vi cookie-Cookie gespeichert war. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8ddfc-9fc1-4105-b377-d9b4d247a0f8
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Gibt die Legacy-Analytics-ID (sofern vorhanden) zurück, die vor der Implementierung des Experience Cloud ID-Diensts im s_vi cookie-Cookie gespeichert war. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.

**Syntax** `var analyticsID = visitor.getAnalyticsVisitorID()`

Typischerweise wird diese Funktion bei benutzerdefinierten Lösungen eingesetzt, bei denen ein Lesen der Besucher-ID erforderlich ist. Sie wird nicht für Standardimplementierungen verwendet. `getAnalyticsVisitorID` kann auch bei Callback-Funktionen zum Lesen von [!DNL Analytics]-IDs und deren Übernahme in Ihr System oder Ihre Anwendung eingesetzt werden.

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
>Wenn Sie [!DNL Analytics]-Kunde sind, suchen Sie nach der [!DNL Analytics]-ID und senden Sie diese an Ihre Funktion. Beispielsweise ist es wünschenswert, bei der Weiterleitung einer Besucher-ID in versteckter Form an eine serverseitige Anwendung, die die Dateneingabe-API verwendet, beide Identifikatoren zur Verfügung zu haben. In diesem Fall sollten Sie die [!DNL Experience Cloud]- und [!DNL Analytics]-Besucher-IDs erfassen und zurückgeben. Siehe [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md).

**Der Parameter „aid“ ist ein veralteter Wert**

Der `aid` Parameter taucht in einer Abfragezeichenfolge unter zweierlei verschiedenen Bedingungen auf.

**1. Fall**

Der Parameter `aid` taucht in einer Abfragezeichenfolge auf, wenn:

* der [!DNL Experience Cloud] ID-Dienst ordnungsgemäß bereitgestellt wurde.
* Der Benutzer, der eine Site besucht, hat eine bereits vorhandene [!DNL Analytics]-ID, die in seinem [s_vi Cookie](https://marketing.adobe.com/resources/help/de_DE/whitepapers/cookies/?f=cookies_analytics.html) gespeichert ist.

**2. Fall**

Sie sehen den `aid` Parameter in einer Abfragezeichenfolge, wenn Ihr Unternehmen eine [Übergangsphase](../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) verwendet, bevor es den ID-Dienst vollständig implementiert. Hat der aktuelle Besucher Ihre Seite zuvor noch nie aufgerufen und sollten Sie keine Übergangsphase festgelegt haben, erhält der Besucher den Parameter `mid` ([!DNL Experience Cloud] ID).

>[!MORE_LIKE_THIS]
>
>* [Analytics Cookies](https://marketing.adobe.com/resources/help/de_DE/whitepapers/cookies/cookies_analytics.html)

