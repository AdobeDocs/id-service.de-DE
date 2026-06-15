---
description: Diese Anweisungen richten sich an Target-Kundinnen und Kunden, die den Identity Service von Experience Cloud verwenden möchten und keine Datenerfassungs-Tags verwenden. Es wird allerdings dringend empfohlen, Tags zum Implementieren des ID-Diensts zu verwenden. Tags vereinheitlichen den Implementierungs-Workflow und stellen automatisch sicher, dass der Code korrekt platziert und sequenziert wird.
keywords: ID-Dienst
title: Implementieren des Experience Cloud Identity Services für Target
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
TQID: https://experienceleague.adobe.com/1994Y39yotvpJkcYazVnG0w-GupHiZZipnLWSTbgle8
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 422
ht-degree: 100%

---

# Implementieren des Experience Cloud Identity Services für Target{#implement-the-experience-cloud-id-service-for-target}

Diese Anweisungen richten sich an Analytics-Kundinnen und Kunden, die den Identity Service von Experience Cloud verwenden möchten und keine [Datenerfassungs-Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) verwenden. Es wird allerdings dringend empfohlen, Tags zum Implementieren des ID-Diensts zu verwenden. Tags vereinheitlichen den Implementierungs-Workflow und stellen automatisch sicher, dass der Code korrekt platziert und sequenziert wird.

>[!IMPORTANT]
>
>* [Lesen Sie sich die Anforderungen durch,](../reference/requirements.md) bevor Sie beginnen.
>* Konfigurieren und testen Sie den Code in einer Entwicklungsumgebung, bevor er in das Produktivsystem übernommen wird.

## Schritt 1: Herunterladen des ID-Dienst-Codes {#section-b32ba0548aa546a79dd38be59832a53e}

Für den [!UICONTROL ID Service] ist die `VisitorAPI.js` Code-Bibliothek erforderlich. Wenden Sie sich an die [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html), um diesen Code zu erhalten.

## Schritt 2: Hinzufügen der Funktion „Visitor.getInstance“ zum ID-Dienst-Code {#section-287ef2958e9f43858fe9d630ae519e22}

**Teil 1: Kopieren Sie die Visitor.getInstance -Funktion unten**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Teil 2: Fügen Sie der Datei VisitorAPI.js Funktions-Code hinzu**

Platzieren Sie die `Visitor.getInstance` Funktion am Ende der Datei nach dem Code-Block. Die bearbeitete Datei sollte wie folgt aussehen:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Schritt 3: Hinzufügen der Experience Cloud-Organisations-ID zu Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

Ersetzen Sie in der `Visitor.getInstance` Funktion den Ausdruck `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` durch Ihre [!DNL Experience Cloud]-Organisations-ID. Sollten Sie Ihre Organisations-ID nicht kennen, finden Sie diese auf der Administrationsseite der [!DNL Experience Cloud]. Siehe auch [Administration – Core Services](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=de). Die bearbeitete Funktion sollte dem unten stehenden Beispiel ähnlich sehen.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Wichtig:* Ändern Sie die Groß- oder Kleinschreibung Ihrer Organisations-ID nicht. Bei der ID wird Groß- und Kleinschreibung beachtet und sie muss so eingegeben werden, wie sie von Adobe angegeben wird.

## Schritt 4: Hinzufügen des Besucher-API-Codes zur Seite {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Stellen Sie die Datei `VisitorAPI.js` im Tag `<head>` Ihrer Site bereit, bevor Sie den Bezug auf die Datei `mbox.js` einfügen. Der [!DNL Experience Cloud] ID-Dienst muss vor der Generierung des ersten [!DNL Target]-Netzwerkaufrufs ausgeführt werden. Versetzen Sie diesen Code nach dem Testen und Überprüfen in die Produktionsumgebung.

## Schritt 5: Testen und Bereitstellen des ID-Dienst-Codes {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Sie können dies wie folgt testen und bereitstellen.

**Testen und Verifizieren**

So testen Sie Ihre ID-Dienstimplementierung:

* Suchen Sie in der Domain, auf der Ihre Seite gehostet wird, nach dem AMCV-Cookie.
* Sicherstellen, dass `mboxMCGVID` in Ihrer [!DNL Target]-Anforderung erscheint und dass es die [!DNL Experience Cloud]-ID (MID) enthält.

Weitere Informationen zu AMCV-Cookie und MID siehe [Cookies und der Experience Cloud Identity Service](../introduction/cookies.md)

**Bereitstellen**

Stellen Sie Ihren Code nach Abschluss der Tests bereit.

