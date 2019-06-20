---
description: Gibt die Legacy-Analytics-ID (falls vorhanden) zurück, die vor der Implementierung des Experience Cloud ID-Diensts im s_ vi-Cookie gespeichert wurde. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.
keywords: ID-Dienst
seo-description: Gibt die Legacy-Analytics-ID (falls vorhanden) zurück, die vor der Implementierung des Experience Cloud ID-Diensts im s_ vi-Cookie gespeichert wurde. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Gibt die Legacy-Analytics-ID (falls vorhanden) zurück, die vor der Implementierung des Experience Cloud ID-Diensts im s_ vi-Cookie gespeichert wurde. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.

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
>If you&#39;re an [!DNL Analytics] customer, also check for and send the [!DNL Analytics] ID to your function. Beispielsweise ist es wünschenswert, bei der Weiterleitung einer Besucher-ID in versteckter Form an eine serverseitige Anwendung, die die Dateneingabe-API verwendet, beide Identifikatoren zur Verfügung zu haben. In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. See [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**Der Parameter „aid“ ist ein veralteter Wert**

Der Parameter `aid` taucht in einer Abfragezeichenfolge unter zweierlei verschiedenen Bedingungen auf.

**1. Fall**

Der Parameter `aid` taucht in einer Abfragezeichenfolge auf, wenn:

* The [!DNL Experience Cloud] ID service is deployed correctly.
* im [!DNL Analytics]s_vi-Cookie[ des eine Site besuchenden Benutzers bereits eine ](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html)-ID gespeichert ist.

**2. Fall**

You will see the `aid` parameter in a query string when your organization is using a [grace period](../../reference/analytics-reference/grace-period.md) before fully implementing the ID service. If the user visiting your site is new, and you&#39;re not using a grace period, the visitor will get the `mid` ( [!DNL Experience Cloud] ID) parameter.

>[!MORE_ LIKE_ THIS]
>
>* [Analytics-Cookies](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

