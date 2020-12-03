---
description: Der Children’s Online Privacy Protection Act (COPPA; Gesetz zum Schutz der Privatsphäre von Kindern im Internet) verbietet die Onlineerfassung von persönlichen Daten von Kindern unter 13 Jahren ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Experience Cloud Identity-Dienstcode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.
keywords: ID Service
seo-description: Der Children’s Online Privacy Protection Act (COPPA; Gesetz zum Schutz der Privatsphäre von Kindern im Internet) verbietet die Onlineerfassung von persönlichen Daten von Kindern unter 13 Jahren ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Experience Cloud Identity-Dienstcode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.
seo-title: COPPA-Unterstützung im Experience Cloud Identity-Dienst
title: COPPA-Unterstützung im Experience Cloud Identity-Dienst
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 77%

---


# COPPA-Unterstützung im Experience Cloud Identity-Dienst {#coppa-support-in-the-experience-cloud-id-service}

Der Children’s Online Privacy Protection Act (COPPA; Gesetz zum Schutz der Privatsphäre von Kindern im Internet) verbietet die Onlineerfassung von persönlichen Daten von Kindern unter 13 Jahren ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Experience Cloud Identity-Dienstcode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.

>[!NOTE]
>
>Nur bei Version 3.0.0 oder neuer.

**Cookies und Tracking**

Beim Laden einer Webseite wird vom [!DNL Experience Cloud] ID-Dienst ein [!DNL Adobe]-Datenerfassungsserver (DES) aufgerufen. Die DCS-Antwort beinhaltet ein Experience Cloud-Cookie und ein demdex.net-Cookie.

* Das Experience Cloud-Cookie wird in der Erstanbieterdomäne gesetzt. Sie kann nicht zur domänenübergreifenden Verfolgung von Besuchern verwendet werden, es sei denn, diese Domänen arbeiten zusammen, um Zugriff zu gewähren.
* Das demdex.net-Cookie wird in der Drittanbieterdomäne gesetzt. Er enthält eine eindeutige ID, mit der Besucher domänenübergreifend verfolgt werden können.

**Cookies und COPPA-Compliance**

Drittanbieter-Cookies, die domänenübergreifend Besucher auf Websites verfolgen, die an Kinder gerichtet sind (oder primär für Kinder bestimmt sind), lösen Anforderungen an die elterliche Zustimmung von COPPA aus. Damit die Forderungen von COPPA für interne Website-Analysen problemlos eingehalten werden können, kann – wie unten gezeigt – die Variable `disableThirdPartyCookies:true` der `Visitor.getInstance` Funktion hinzugefügt werden.

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

