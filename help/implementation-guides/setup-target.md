---
description: Diese Anweisungen richten sich an Target-Kunden, die den Experience Cloud Identity-Dienst verwenden möchten, nicht aber Dynamic Tag Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
keywords: ID-Dienst
seo-description: Diese Anweisungen richten sich an Target-Kunden, die den Experience Cloud Identity-Dienst verwenden möchten, nicht aber Dynamic Tag Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
seo-title: Implementieren des Experience Cloud Identity-Diensts für Target
title: Implementieren des Experience Cloud Identity-Diensts für Target
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Implementieren des Experience Cloud Identity-Diensts für Target{#implement-the-experience-cloud-id-service-for-target}

Diese Anweisungen richten sich an Target-Kunden, die den Experience Cloud Identity-Dienst verwenden möchten, nicht aber Dynamic Tag Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.

>[!IMPORTANT]
>
>* [Lesen Sie sich die Anforderungen durch,](../reference/requirements.md) bevor Sie beginnen.
>* Konfigurieren und testen Sie den Code in einer Entwicklungsumgebung, bevor er in das Produktivsystem übernommen wird.
>



## Schritt 1: Herunterladen des ID-Dienst-Codes {#section-b32ba0548aa546a79dd38be59832a53e}.

Für den [!UICONTROL ID-Dienst] ist die Code-Bibliothek `VisitorAPI.js` erforderlich. Wenden Sie sich an die [Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html), um diesen Code zu erhalten.

## Schritt 2: Hinzufügen der Funktion „Visitor.getInstance“ zum ID-Dienst-Code {#section-287ef2958e9f43858fe9d630ae519e22}

**Teil 1: Kopieren Sie die unten stehende Funktion Visitor.getInstance**

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

Ersetzen Sie in der `Visitor.getInstance` Funktion den Ausdruck `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` durch Ihre [!DNL Experience Cloud]-Organisations-ID. Sollten Sie Ihre Organisations-ID nicht kennen, finden Sie diese auf der Administrationsseite der[!DNL Experience Cloud]. Siehe auch [Administration – Kerndienste.](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html) Die bearbeitete Funktion sollte dem unten stehenden Beispiel ähnlich sehen.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Wichtig:* Ändern Sie die Groß- oder Kleinschreibung Ihrer Organisations-ID nicht. Bei der ID wird Groß- und Kleinschreibung beachtet und sie muss so eingegeben werden, wie sie von Adobe angegeben wird.

## Schritt 4: Hinzufügen des Besucher-API-Codes zur Seite {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Stellen Sie die Datei `VisitorAPI.js` im Tag `<head>` Ihrer Seite bereit, bevor Sie den Bezug auf die Datei `mbox.js` einfügen. Der [!DNL Experience Cloud] ID-Dienst muss vor der Generierung des ersten [!DNL Target]-Netzwerkaufrufs ausgeführt werden. Versetzen Sie diesen Code nach dem Testen und Überprüfen in die Produktionsumgebung.

## Schritt 5: Testen und Bereitstellen des ID-Dienst-Codes {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Sie können dies wie folgt testen und bereitstellen.

**Testen und Verifizieren**

Zum Testen der ID-Dienstimplementierung:

* AMCV-Cookie in der Domäne suchen, in der Ihre Seite gehostet wird.
* Sicherstellen, dass `mboxMCGVID` in Ihrer [!DNL Target]-Anforderung erscheint und dass es die [!DNL Experience Cloud]-ID (MID) enthält.

Weitere Informationen zu AMCV-Cookie und MID siehe [Cookies und der Experience Cloud Identity-Dienst](../introduction/cookies.md)

**Bereitstellung**

Stellen Sie den Code nach bestandenen Tests bereit.
