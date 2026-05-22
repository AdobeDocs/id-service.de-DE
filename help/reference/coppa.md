---
description: Der Children's Online Privacy Protection Act (COPPA) verbietet die Online-Erfassung personenbezogener Daten von Kindern unter 13 Jahren ohne nachweisliche Zustimmung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Experience Cloud Identity Servicecode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.
keywords: ID-Dienst
title: COPPA-Unterstützung im Experience Cloud Identity Service
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 357
ht-degree: 86%

---

# COPPA-Unterstützung im Experience Cloud Identity Service {#coppa-support-in-the-experience-cloud-id-service}

Der Children&#39;s Online Privacy Protection Act (COPPA) verbietet die Online-Erfassung personenbezogener Daten von Kindern unter 13 Jahren ohne nachweisliche Zustimmung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Experience Cloud Identity Servicecode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.

>[!NOTE]
>
>Nur bei Version 3.0.0 oder neuer.

**Cookies und Tracking**

Beim Laden einer Webseite wird vom [!DNL Experience Cloud] ID-Dienst ein [!DNL Adobe]-Datenerfassungsserver (DES) aufgerufen. Die DCS-Antwort beinhaltet ein Experience Cloud-Cookie und ein demdex.net-Cookie.

* Das Experience Cloud-Cookie wird in der Erstanbieter-Domain gesetzt. Sie kann nicht zur Verfolgung von Besuchern über Domains hinweg verwendet werden, es sei denn, diese Domains arbeiten zusammen, um Zugriff zu gewähren.
* Das demdex.net-Cookie wird in der Drittanbieter-Domain gesetzt. Er enthält eine eindeutige ID, mit der Besucher über unterschiedliche Domains hinweg verfolgt werden können.

**Cookies und COPPA-Compliance**

Drittanbieter-Cookies, die Domain-übergreifend Besucher auf Websites verfolgen, die sich (vorwiegend) an Minderjährige richten, lösen COPPA-Anforderungen für die elterliche Zustimmung aus. Damit die Forderungen von COPPA für interne Website-Analysen problemlos eingehalten werden können, kann – wie unten gezeigt – die Variable `disableThirdPartyCookies:true` der `Visitor.getInstance` Funktion hinzugefügt werden.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Ist die Variable auf `true` festgelegt, verhindert das `disableThirdPartyCookies` Objekt, dass der DES den Drittanbieter-Cookie demdex.net zurückgibt. Sollte der Cookie bereits im Browser des Besuchers gespeichert sein, wird dieser vom ID-Dienst nicht zur Erstellung einer neuen [!DNL Experience Cloud] ID oder Ausgabe einer bestehenden ID eingesetzt. Stattdessen wird vom [!DNL Experience Cloud] ID-Dienst eine neue, zufällige ID im Erstanbieter-Cookie erstellt. Nach der Aktivierung können mit dem ID-Dienst Daten gesammelt und über verschiedene [!DNL Experience Cloud]-Lösungen hinweg freigegeben werden, darunter auch andere, laut COPPA zulässige interne Operationen.

>[!MORELIKETHIS]
>
>* [Adobe-Datenschutzcenter](http://www.adobe.com/de/privacy.html)
>* [Was ist COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

