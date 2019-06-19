---
description: Gibt die Legacy-Analytics-ID (falls vorhanden) zurück, die im s_ vi-Cookie gespeichert war, bevor der Experience Platform Identity Service implementiert wurde. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.
keywords: ID-Dienst
seo-description: Gibt die Legacy-Analytics-ID (falls vorhanden) zurück, die im s_ vi-Cookie gespeichert war, bevor der Experience Platform Identity Service implementiert wurde. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6 bb 8 ddfc -9 fc 1-4105-b 377-d 9 b 4 d 247 a 0 f 8
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

Gibt die Legacy-Analytics-ID (falls vorhanden) zurück, die im s_ vi-Cookie gespeichert war, bevor der Experience Platform Identity Service implementiert wurde. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.

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
>Wenn Sie [!DNL Analytics] Kunde sind, suchen Sie nach der [!DNL Analytics] ID und senden Sie sie an Ihre Funktion. Beispielsweise ist es wünschenswert, bei der Weiterleitung einer Besucher-ID in versteckter Form an eine serverseitige Anwendung, die die Dateneingabe-API verwendet, beide Identifikatoren zur Verfügung zu haben. In diesem Fall sollten Sie die [!DNL Experience Cloud] Besucher- und [!DNL Analytics] Besucher-IDs erfassen und zurückgeben. Siehe [getmarketingcloudvisitorid](../../library/get-set/getmcvid.md).

**Der Parameter „aid“ ist ein veralteter Wert**

Der Parameter `aid` taucht in einer Abfragezeichenfolge unter zweierlei verschiedenen Bedingungen auf.

**1. Fall**

Der Parameter `aid` taucht in einer Abfragezeichenfolge auf, wenn:

* Der [!DNL Experience Cloud] ID-Dienst wird ordnungsgemäß bereitgestellt.
* im [!DNL Analytics]s_vi-Cookie[ des eine Site besuchenden Benutzers bereits eine ](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html)-ID gespeichert ist.

**2. Fall**

Der `aid` Parameter in einer Abfragezeichenfolge wird angezeigt, wenn Ihr Unternehmen eine [Übergangsphase](../../reference/analytics-reference/grace-period.md) verwendet, bevor der ID-Dienst vollständig implementiert wird. Wenn der Benutzer, der Ihre Site besucht, neu ist und Sie keine Übergangsphase verwenden, ruft der Besucher den `mid` Parameter ( [!DNL Experience Cloud] ID) ab.

>[!MORE_ LIKE_ THIS]
>
>* [Analytics-Cookies](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

