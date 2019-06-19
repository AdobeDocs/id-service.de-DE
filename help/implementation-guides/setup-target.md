---
description: Diese Anweisungen richten sich an Target-Kunden, die den Experience Platform Identity Service verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
keywords: ID-Dienst
seo-description: Diese Anweisungen richten sich an Target-Kunden, die den Experience Platform Identity Service verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
seo-title: Implementieren des Experience Platform-Identitätsdiensts für Target
title: Implementieren des Experience Platform-Identitätsdiensts für Target
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Implementieren des Experience Platform-Identitätsdiensts für Target{#implement-the-experience-cloud-id-service-for-target}

Diese Anweisungen richten sich an Target-Kunden, die den Experience Platform Identity Service verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.

>[!IMPORTANT]
>
>* [Lesen Sie sich die Anforderungen durch,](../reference/requirements.md) bevor Sie beginnen.
>* Konfigurieren und testen Sie den Code in einer Entwicklungsumgebung, bevor er in das Produktivsystem übernommen wird.
>



## Schritt 1: ID-Dienst-Code abrufen {#section-b32ba0548aa546a79dd38be59832a53e}

Für den Code [!DNL ID Service] ist die `VisitorAPI.js` Codebibliothek erforderlich. Wenden Sie sich an die [Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html), um diesen Code zu erhalten.

## Schritt 2: Hinzufügen der Funktion Visitor. getinstance zum ID-Dienst-Code {#section-287ef2958e9f43858fe9d630ae519e22}

**Teil 1: Kopieren Sie die unten stehende Funktion Visitor.getInstance**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Teil 2: Fügen Sie der Datei VistorAPI.js Funktions-Code hinzu**

Platzieren Sie die Funktion `Visitor.getInstance` am Ende der Datei nach dem Code-Block. Die bearbeitete Datei sollte wie folgt aussehen:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Schritt 3: Fügen Sie Visitor. getinstance Ihre Experience Cloud-Organisations-ID hinzu. {#section-522b1877be9243c39b222859b821f0ce}

Ersetzen Sie in der `Visitor.getInstance` Funktion die `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` ID Ihres [!DNL Experience Cloud] Unternehmens. Sollten Sie Ihre Organisations-ID nicht kennen, finden Sie diese auf der Administrationsseite der [!DNL Experience Cloud]. Siehe auch [Administration – Kerndienste.](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html) Die bearbeitete Funktion sollte dem unten stehenden Beispiel ähnlich sehen.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Ändern Sie nicht* den Fall der Zeichen in Ihrer Organisations-ID. Bei der ID wird Groß- und Kleinschreibung beachtet und sie muss so eingegeben werden, wie sie von Adobe angegeben wird.

## Schritt 4: Hinzufügen des Besucher-API-Codes zur Seite {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Stellen Sie die `VisitorAPI.js` Datei auf Ihrer Site `<head>` vor dem Verweis auf die `mbox.js` Datei bereit. Der [!DNL Experience Cloud] ID-Dienst muss vor dem ersten [!DNL Target] Netzwerkaufruf ausgeführt werden. Versetzen Sie diesen Code nach dem Testen und Überprüfen in die Produktionsumgebung.

## Schritt 5: Testen und Bereitstellen des ID-Dienst-Codes {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Sie können wie folgt testen und bereitstellen.

**Testen und überprüfen**

Zum Testen der ID-Dienstimplementierung:

* AMCV-Cookie in der Domäne suchen, in der Ihre Seite gehostet wird.
* Die Verifizierung `mboxMCGVID` wird in Ihrer [!DNL Target] Anforderung angezeigt und enthält die [!DNL Experience Cloud] ID (MID).

Informationen zum AMCV-Cookie und zur MID finden Sie unter [Cookies und der Experience Platform Identity Service](../introduction/cookies.md) .

**Bereitstellung**

Stellen Sie den Code nach bestandenen Tests bereit.
