---
description: Der Children's Online Privacy Protection Act (COPPA) verbietet die Online-Erfassung personenbezogener Daten von Kindern unter 13 Jahren ohne nachweisliche Zustimmung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Experience Cloud Identity Servicecode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.
keywords: ID-Dienst
title: COPPA-Unterstützung im Experience Cloud Identity Service
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 85%

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

