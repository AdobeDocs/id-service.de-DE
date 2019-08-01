---
description: Der Children’s Online Privacy Protection Act (COPPA; Gesetz zum Schutz der Privatsphäre von Kindern im Internet) verbietet die Onlineerfassung von persönlichen Daten von Kindern unter 13 ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken nach COPPA haben, können ihrem Experience Cloud Identity Service-Code eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.
keywords: ID-Dienst
seo-description: Der Children’s Online Privacy Protection Act (COPPA; Gesetz zum Schutz der Privatsphäre von Kindern im Internet) verbietet die Onlineerfassung von persönlichen Daten von Kindern unter 13 ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken nach COPPA haben, können ihrem Experience Cloud Identity Service-Code eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.
seo-title: COPPA-Unterstützung im Experience Cloud-Identitätsdienst
title: COPPA-Unterstützung im Experience Cloud-Identitätsdienst
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2

---


# COPPA Support in the Experience Cloud Identity Service {#coppa-support-in-the-experience-cloud-id-service}

Der Children’s Online Privacy Protection Act (COPPA; Gesetz zum Schutz der Privatsphäre von Kindern im Internet) verbietet die Onlineerfassung von persönlichen Daten von Kindern unter 13 ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken nach COPPA haben, können ihrem Experience Cloud Identity Service-Code eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden.

>[!NOTE]
>
>Nur bei Version 3.0.0 oder neuer.

**Cookies und Tracking**

Beim Laden einer Webseite wird vom [!DNL Experience Cloud] ID-Dienst ein [!DNL Adobe]-Datenerfassungsserver (DES) aufgerufen. Die DES-Antwort umfasst einen Experience Cloud-Cookie sowie einen demdex.net-Cookie.

* Der Experience Cloud-Cookie wird in der Erstanbieterdomäne gesetzt. Er kann nicht dazu verwendet werden, Besucher domänenübergreifend zu verfolgen, außer die Domänen sind so miteinander verknüpft, dass ein Zugriff möglich ist.
* Der demdex.net-Cookie wird in der Drittanbieterdomäne gesetzt. Er enthält einen eindeutigen Identifikator, der zur domänenübergreifenden Verfolgung von Benutzern verwendet werden kann.

**Cookies und Einhaltung von COPPA**

Drittanbieter-Cookies, die Besucher domänenübergreifend auf Websites verfolgen, die für Kinder (oder primär für Kinder) vorgesehen sind, lösen in Einklang mit COPPA eine Anforderung der elterlichen Zustimmung aus. Damit die Forderungen von COPPA für interne Website-Analysen problemlos eingehalten werden können, kann – wie unten gezeigt – die Variable `disableThirdPartyCookies:true` der `Visitor.getInstance` Funktion hinzugefügt werden.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Ist die Variable auf `true` festgelegt, verhindert das `disableThirdPartyCookies` Objekt, dass der DES den Drittanbieter-Cookie demdex.net zurückgibt. Sollte der Cookie bereits im Browser des Besuchers gespeichert sein, wird dieser vom ID-Dienst nicht zur Erstellung einer neuen [!DNL Experience Cloud] ID oder Ausgabe einer bestehenden ID eingesetzt. Stattdessen wird vom [!DNL Experience Cloud] ID-Dienst eine neue, zufällige ID im Erstanbieter-Cookie erstellt. Nach der Aktivierung können mit dem ID-Dienst Daten gesammelt und über verschiedene [!DNL Experience Cloud]-Lösungen hinweg freigegeben werden, darunter auch andere, laut COPPA zulässige interne Operationen.

>[!MORE_LIKE_THIS]
>
>* [Adobe Datenschutzcenter](http://www.adobe.com/privacy.html)
>* [Was ist COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

