---
description: Der Children’s Online Privacy Protection Act (COPPA; Gesetz zum Schutz der Privatsphäre von Kindern im Internet) verbietet die Onlineerfassung von persönlichen Daten von Kindern unter 13 ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Experience Cloud ID-Dienstcode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers verwendet werden.
keywords: ID-Dienst
seo-description: Der Children’s Online Privacy Protection Act (COPPA; Gesetz zum Schutz der Privatsphäre von Kindern im Internet) verbietet die Onlineerfassung von persönlichen Daten von Kindern unter 13 ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Experience Cloud ID-Dienstcode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers verwendet werden.
seo-title: COPPA-Unterstützung im Experience Cloud ID-Dienst
title: COPPA-Unterstützung im Experience Cloud ID-Dienst
uuid: 621 b 5 ebd -92 e 7-4635-be 85-8 d 7 e 36589 fcb
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# COPPA-Unterstützung im Experience Cloud ID-Dienst {#coppa-support-in-the-experience-cloud-id-service}

Der Children’s Online Privacy Protection Act (COPPA; Gesetz zum Schutz der Privatsphäre von Kindern im Internet) verbietet die Onlineerfassung von persönlichen Daten von Kindern unter 13 ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Experience Cloud ID-Dienstcode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers verwendet werden.

>[!NOTE]
>
>Nur bei Version 1.5.3 oder neuer.

**Cookies und Tracking**

Beim Laden einer Webseite wird vom [!DNL Experience Cloud] ID-Dienst ein [!DNL Adobe]-Datenerfassungsserver (DES) aufgerufen. Die DES-Antwort umfasst einen Experience Cloud-Cookie sowie einen demdex.net-Cookie.

* Der Experience Cloud-Cookie wird in der Erstanbieterdomäne gesetzt. Er kann nicht dazu verwendet werden, Besucher domänenübergreifend zu verfolgen, außer die Domänen sind so miteinander verknüpft, dass ein Zugriff möglich ist.
* Der demdex.net-Cookie wird in der Drittanbieterdomäne gesetzt. Er enthält einen eindeutigen Identifikator, der zur domänenübergreifenden Verfolgung von Benutzern verwendet werden kann.

**Cookies und Einhaltung von COPPA**

Drittanbieter-Cookies, die Besucher domänenübergreifend auf Websites verfolgen, die für Kinder (oder primär für Kinder) vorgesehen sind, lösen in Einklang mit COPPA eine Anforderung der elterlichen Zustimmung aus. Damit die Forderungen von COPPA für interne Website-Analysen problemlos eingehalten werden können, kann – wie unten gezeigt – die Variable `disableThirdPartyCookies:true` der Funktion `Visitor.getInstance` hinzugefügt werden.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Ist die Variable auf `true` festgelegt, verhindert das Objekt `disableThirdPartyCookies`, dass der DES den Drittanbieter-Cookie demdex.net zurückgibt. Sollte der Cookie bereits im Browser des Besuchers gespeichert sein, wird dieser vom ID-Dienst nicht zur Erstellung einer neuen [!DNL Experience Cloud] ID oder Ausgabe einer bestehenden ID eingesetzt. Stattdessen wird vom [!DNL Experience Cloud] ID-Dienst eine neue, zufällige ID im Erstanbieter-Cookie erstellt. Nach der Aktivierung können mit dem ID-Dienst Daten gesammelt und über verschiedene [!DNL Experience Cloud]-Lösungen hinweg freigegeben werden, darunter auch andere, laut COPPA zulässige interne Operationen.

>[!MORE_ LIKE_ THIS]
>
>* [Adobe Datenschutzcenter](http://www.adobe.com/privacy.html)
>* [Was ist COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

