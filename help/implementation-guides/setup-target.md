---
description: Diese Anweisungen richten sich an Target-Kunden, die den Besucher-ID-Service verwenden möchten, nicht aber Tags. Es wird jedoch dringend empfohlen, Tags zu verwenden, um den Besucher-ID-Dienst zu implementieren. Tags vereinheitlichen den Implementierungs-Workflow und stellen automatisch sicher, dass der Code korrekt platziert und sequenziert wird.
keywords: Besucher-ID-Service
title: Implementieren des Adobe-Besucher-ID-Service für Target
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
TQID: https://experienceleague.adobe.com/1994Y39yotvpJkcYazVnG0w-GupHiZZipnLWSTbgle8
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 430
ht-degree: 47%

---

# Implementieren des Adobe-Besucher-ID-Service für Target{#implement-the-experience-cloud-id-service-for-target}

Diese Anweisungen richten sich an Target-Kunden, die den Besucher-ID-Service verwenden möchten, nicht aber [Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de). Es wird jedoch dringend empfohlen, Tags zu verwenden, um den Besucher-ID-Dienst zu implementieren. Tags vereinheitlichen den Implementierungs-Workflow und stellen automatisch sicher, dass der Code korrekt platziert und sequenziert wird.

>[!IMPORTANT]
>
>* [Lesen Sie sich die Anforderungen durch,](../reference/requirements.md) bevor Sie beginnen.
>* Konfigurieren und testen Sie den Code in einer Entwicklungsumgebung, bevor er in das Produktivsystem übernommen wird.

## Schritt 1: Abrufen des Besucher-ID-Service-Codes {#section-b32ba0548aa546a79dd38be59832a53e}

Für den Besucher-ID-Dienst ist die `VisitorAPI.js` Code-Bibliothek erforderlich. Wenden Sie sich an die [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html), um diesen Code zu erhalten.

## Schritt 2: Hinzufügen der Funktion Visitor.getInstance zum Besucher-ID-Dienst-Code {#section-287ef2958e9f43858fe9d630ae519e22}

**Teil 1: Kopieren Sie die Visitor.getInstance -Funktion unten**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 
```

**Teil 2: Funktionscode zur `VisitorAPI.js` hinzufügen**

Platzieren Sie die `Visitor.getInstance` Funktion am Ende der Datei nach dem Code-Block. Die bearbeitete Datei sollte wie folgt aussehen:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE");
```

## Schritt 3: Hinzufügen der IMS-Organisations-ID zu Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

Ersetzen Sie in der `Visitor.getInstance` Funktion `INSERT-IMS-ORG-ID-HERE` durch Ihre IMS-Organisations-ID. Wenn Sie Ihre IMS-Organisations-ID nicht kennen, finden Sie sie auf der Verwaltungsseite für CX Enterprise. Siehe auch [Administration – Core Services](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=de). Die bearbeitete Funktion sollte dem unten stehenden Beispiel ähnlich sehen.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Ändern Sie* Groß-/Kleinschreibung der Zeichen in Ihrer IMS-Organisations-ID. Bei der ID wird Groß- und Kleinschreibung beachtet und sie muss so eingegeben werden, wie sie von Adobe angegeben wird.

## Schritt 4: Hinzufügen des Besucher-API-Codes zur Seite {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Stellen Sie die Datei `VisitorAPI.js` im Tag `<head>` Ihrer Site bereit, bevor Sie den Bezug auf die Datei `mbox.js` einfügen. Der Besucher-ID-Dienst muss ausgeführt werden, bevor der erste Target-Netzwerkaufruf generiert wird. Versetzen Sie diesen Code nach dem Testen und Überprüfen in die Produktionsumgebung.

## Schritt 5: Testen und Bereitstellen des Besucher-ID-Dienst-Codes {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Sie können dies wie folgt testen und bereitstellen.

**Testen und Verifizieren**

So testen Sie die Implementierung des Besucher-ID-Service:

* Suchen Sie in der Domain, auf der Ihre Seite gehostet wird, nach dem AMCV-Cookie.
* Stellen Sie sicher, `mboxMCGVID` in Ihrer Target-Anfrage angezeigt wird und dass sie die ECID enthält.

Siehe [Cookies und der Besucher-ID-Dienst](../introduction/cookies.md) für Informationen über das AMCV-Cookie und die MID.

**Bereitstellen**

Stellen Sie Ihren Code nach Abschluss der Tests bereit.

