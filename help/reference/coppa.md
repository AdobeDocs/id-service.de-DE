---
description: Der Children's Online Privacy Protection Act (COPPA) verbietet die Online-Erfassung personenbezogener Daten von Kindern unter 13 Jahren ohne nachweisliche Zustimmung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Besucher-ID-Dienst-Code eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.
keywords: Besucher-ID-Service
title: COPPA-Unterstützung im Besucher-ID-Service von Adobe
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 363
ht-degree: 36%

---

# COPPA-Unterstützung im Besucher-ID-Service von Adobe {#coppa-support-in-the-experience-cloud-id-service}

Der Children&#39;s Online Privacy Protection Act (COPPA) verbietet die Online-Erfassung personenbezogener Daten von Kindern unter 13 Jahren ohne nachweisliche Zustimmung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Besucher-ID-Dienst-Code eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.

>[!NOTE]
>
>Nur bei Version 3.0.0 oder neuer.

**Cookies und Tracking**

Beim Laden einer Web-Seite ruft der Besucher-ID-Dienst einen Adobe-Datenerfassungsserver (DCS) auf. Die DCS-Antwort enthält ein Cookie „CX Enterprise“ und ein Cookie &quot;demdex.net&quot;.

* Das CX-Enterprise-Cookie wird in der Erstanbieter-Domain gesetzt. Sie kann nicht zur Verfolgung von Besuchern über Domains hinweg verwendet werden, es sei denn, diese Domains arbeiten zusammen, um Zugriff zu gewähren.
* Das demdex.net-Cookie wird in der Drittanbieter-Domain gesetzt. Er enthält eine eindeutige ID, mit der Besucher über unterschiedliche Domains hinweg verfolgt werden können.

**Cookies und COPPA-Compliance**

Drittanbieter-Cookies, die Domain-übergreifend Besucher auf Websites verfolgen, die sich (vorwiegend) an Minderjährige richten, lösen COPPA-Anforderungen für die elterliche Zustimmung aus. Damit die Forderungen von COPPA für interne Website-Analysen problemlos eingehalten werden können, kann – wie unten gezeigt – die Variable `disableThirdPartyCookies:true` der `Visitor.getInstance` Funktion hinzugefügt werden.

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Ist die Variable auf `true` festgelegt, verhindert das `disableThirdPartyCookies` Objekt, dass der DES den Drittanbieter-Cookie demdex.net zurückgibt. Wenn ein Site-Besucher dieses Cookie bereits in seinem Browser hat, verwendet der Besucher-ID-Dienst es nicht, um eine neue ECID zu erstellen oder eine vorhandene ID zurückzugeben. Stattdessen erstellt der Besucher-ID-Dienst eine neue, zufällige ID im Erstanbieter-Cookie. Nach der Aktivierung können Sie Daten mit dem Besucher-ID-Service erfassen und über verschiedene CX Enterprise-Lösungen hinweg freigeben, einschließlich anderer interner Vorgänge, die nach COPPA zulässig sind.

>[!MORELIKETHIS]
>
>* [Adobe-Datenschutzcenter](http://www.adobe.com/de/privacy.html)
>* [Was ist COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

