---
description: Gibt die Legacy-Analytics-ID (falls vorhanden) zurück, die vor der Implementierung des Besucher-ID-Service im s_vi-Cookie gespeichert war. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.
keywords: Besucher-ID-Service
title: getAnalyticsVisitorID
exl-id: 82973de4-4257-4aab-9268-4ab124a01ee2
TQID: https://experienceleague.adobe.com/xJRR3qXoJpCnyFqKuEZqvEs0MpPCCA0brWOT6WbngX4
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 313
ht-degree: 46%

---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Gibt die Legacy-Analytics-ID (falls vorhanden) zurück, die vor der Implementierung des Besucher-ID-Service im s_vi-Cookie gespeichert war. Wurde einem Besucher niemals eine Analytics-ID zugewiesen, wird eine leere Zeichenfolge zurückgegeben.

**Syntax** `var analyticsID = visitor.getAnalyticsVisitorID()`

Diese Funktion wird in der Regel bei benutzerdefinierten Lösungen verwendet, bei denen die Besucher-ID gelesen werden muss. Sie wird nicht von einer Standardimplementierung verwendet. `getAnalyticsVisitorID` funktioniert auch mit Callback-Funktionen, um Analytics-IDs zu lesen und sie in Ihr System oder Ihr Programm einzubringen.

**Beispielcode**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>Wenn Sie Analytics-Kunde sind, prüfen Sie auch, ob die Analytics-ID vorhanden ist, und senden Sie sie an Ihre Funktion. Beispielsweise ist es wünschenswert, bei der Weiterleitung einer Besucher-ID in versteckter Form an eine serverseitige Anwendung, die die Dateneingabe-API verwendet, beide Identifikatoren zur Verfügung zu haben. In diesem Fall sollten Sie die ECID- und Analytics-Besucher-IDs erfassen und zurückgeben. Siehe [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md).

**Der Parameter „aid“ ist ein veralteter Wert**

Der `aid` Parameter taucht in einer Abfragezeichenfolge unter zweierlei verschiedenen Bedingungen auf.

**1. Fall**

Der Parameter `aid` taucht in einer Abfragezeichenfolge auf, wenn:

* Der Besucher-ID-Dienst wird ordnungsgemäß bereitgestellt.
* Der Benutzer, der eine Site besucht, verfügt über eine bereits vorhandene Analytics ID, die in seinem [s_vi-Cookie gespeichert ](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=de#section-5d50a078de444d12b7d927d68ff3b679).

**2. Fall**

Der `aid`-Parameter wird in einer Abfragezeichenfolge angezeigt, wenn Ihr Unternehmen eine [ Übergangsphase verwendet, ](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/migration) den Besucher-ID-Service vollständig zu implementieren. Wenn der Besucher Ihrer Site neu ist und Sie keine Übergangsphase verwenden, erhält der Besucher den `mid` (ECID)-Parameter.

>[!MORELIKETHIS]
>
>* [Cookies in Analytics](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-privacy.html?lang=de)

