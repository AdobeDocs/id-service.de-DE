---
description: Diese Anweisungen richten sich an Target-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
keywords: ID-Dienst
seo-description: Diese Anweisungen richten sich an Target-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
seo-title: Implementieren des Experience Cloud ID-Diensts für Target
title: Implementieren des Experience Cloud ID-Diensts für Target
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Implementieren des Experience Cloud ID-Diensts für Target{#implement-the-experience-cloud-id-service-for-target}

Diese Anweisungen richten sich an Target-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.

>[!IMPORTANT]
>
>* [Lesen Sie sich die Anforderungen durch,](../reference/requirements.md) bevor Sie beginnen.
>* Konfigurieren und testen Sie den Code in einer Entwicklungsumgebung, bevor er in das Produktivsystem übernommen wird.
>



## Step 1: Get the ID Service code {#section-b32ba0548aa546a79dd38be59832a53e}

The [!DNL ID Service] requires the `VisitorAPI.js` code library. Wenden Sie sich an die [Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html), um diesen Code zu erhalten.

## Step 2: Add the Visitor.getInstance function to the ID Service code {#section-287ef2958e9f43858fe9d630ae519e22}

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

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your [!DNL Experience Cloud] organization ID. Sollten Sie Ihre Organisations-ID nicht kennen, finden Sie diese auf der Administrationsseite der [!DNL Experience Cloud]. Siehe auch [Administration – Kerndienste.](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html) Die bearbeitete Funktion sollte dem unten stehenden Beispiel ähnlich sehen.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Ändern Sie nicht* den Fall der Zeichen in Ihrer Organisations-ID. Bei der ID wird Groß- und Kleinschreibung beachtet und sie muss so eingegeben werden, wie sie von Adobe angegeben wird.

## Step 4: Add Visitor API code to the page {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Deploy the `VisitorAPI.js` file to your site in the `<head>` tags before the reference to the `mbox.js` file. The [!DNL Experience Cloud] ID service must execute before the first [!DNL Target] network call is generated. Versetzen Sie diesen Code nach dem Testen und Überprüfen in die Produktionsumgebung.

## Step 5: Test and deploy ID Service code {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Sie können wie folgt testen und bereitstellen.

**Testen und überprüfen**

Zum Testen der ID-Dienstimplementierung:

* AMCV-Cookie in der Domäne suchen, in der Ihre Seite gehostet wird.
* Verify `mboxMCGVID` appears in your [!DNL Target] request and that it contains the [!DNL Experience Cloud] ID (MID).

See [Cookies and the Experience Cloud ID Service](../introduction/cookies.md) for information about the AMCV cookie and the MID.

**Bereitstellung**

Stellen Sie den Code nach bestandenen Tests bereit.
