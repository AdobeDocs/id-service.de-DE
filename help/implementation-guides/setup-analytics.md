---
description: Diese Anweisungen richten sich an Analytics-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
keywords: ID-Dienst
seo-description: Diese Anweisungen richten sich an Analytics-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
seo-title: Implementieren des Experience Cloud ID-Diensts für Analytics
title: Implementieren des Experience Cloud ID-Diensts für Analytics
uuid: 7 fbd 6 fa 0-1713-4232-8680-500 ed 62709 d 5
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Implementieren des Experience Cloud ID-Diensts für Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Diese Anweisungen richten sich an Analytics-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.

>[!IMPORTANT]
>
>* [Lesen Sie sich die Anforderungen durch,](../reference/requirements.md) bevor Sie beginnen.
>* Konfigurieren und testen Sie den Code in einer Entwicklungsumgebung, bevor er in das Produktivsystem übernommen wird.
>



Führen Sie folgende Schritte aus, um den ID-Dienst für Adobe Analytics zu implementieren:

1. [Herunterladen des ID-Dienst-Codes](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Fügen Sie die Funktion Visitor. getinstance dem ID-Dienst-Code hinzu.](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Fügen Sie Visitor. getinstance Ihre Experience Cloud-Organisations-ID hinzu.](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Hinzufügen Ihrer Tracking-Server zu Visitor. getinstance](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Datei appmeasurement. js oder s_ code. js aktualisieren](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [Hinzufügen des Besucher-API-Codes zur Seite](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Optional) Konfigurieren einer Übergangsphase](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Testen und Bereitstellen des ID-Dienst-Codes](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Step 1: Download the ID Service code {#section-ead9403a6b7e45b887f9ac959ef89f7f}

The [!DNL ID Service] requires the `VisitorAPI.js` code library. Zum Herunterladen dieser Code-Bibliothek tun Sie Folgendes:

1. Go to **[!UICONTROL Admin]** &gt; **[!UICONTROL Code Manager]**.
1. In [!DNL Code Manager], click either **[!UICONTROL JavaScript (New)]** or **[!UICONTROL JavaScript (Legacy)]**.

   Dies leitet das Herunterladen der komprimierten Code-Bibliotheken ein.

1. Entpacken Sie die Code-Datei und öffnen Sie die Datei `VisitorAPI.js`.

## Schritt 2: Add the Visitor.getInstance function to the ID Service Code {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* In älteren Versionen der ID-Dienst-API wurde diese Funktion an einem anderen Ort platziert, und es war eine andere Syntax erforderlich. Sollten Sie von einer Version migrieren, die älter ist als [Version 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), beachten Sie die hier beschriebene neue Platzierung und Syntax.
>* Code in Großbuchstaben ist ein Platzhalter für die tatsächlichen Werte. Ersetzen Sie diesen Text durch Ihre Organisations-ID, Ihre Tracking-Server-URL oder einen anderen benannten Wert.
>



**Teil 1: Kopieren Sie die unten stehende Funktion Visitor.getInstance**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
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

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your [!DNL Experience Cloud] organization ID. Sollten Sie Ihre Organisations-ID nicht kennen, finden Sie diese auf der Administrationsseite der [!DNL Experience Cloud]. Siehe auch [Administration – Kerndienste.](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html) Die bearbeitete Funktion sollte dem unten stehenden Beispiel ähnlich sehen.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Ändern Sie nicht* den Fall der Zeichen in Ihrer Organisations-ID. Bei der ID wird Groß- und Kleinschreibung beachtet und sie muss so eingegeben werden, wie sie von Adobe angegeben wird.

## Step 4: Add your tracking servers to Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

Tracking-Server werden für die Datenerfassung in [!DNL Analytics] verwendet.

**Teil 1: Ermitteln der Tracking-Server-URLs**

Check your `s_code.js` or `AppMeasurement.js` files to find the tracking server URLs. Die URLs werden von folgenden Variablen spezifiziert:

* `s.trackingServer`
* `s.trackingServerSecure`

**Teil 2: Festlegen der Tracking-Server-Variablen**

Zur Festlegung, welche Tracking-Server-Variablen verwendet werden sollen:

1. Beantworten Sie die Fragen in der unten stehenden Entscheidungsmatrix. Verwenden Sie die Variablen, die Ihren Antworten entsprechen.
1. Ersetzen Sie die Tracking-Server-Platzhalter durch Ihre eigenen Tracking-Server-URLs.
1. Entfernen Sie nicht verwendete Tracking-Server- und [!DNL Experience Cloud]-Servervariablen aus dem Code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>When used, match the [!DNL Experience Cloud] server URLs to their corresponding tracking server URLs like this: &gt;
>* [!DNL Experience Cloud] server URL = Tracking Server URL
>* [!DNL Experience Cloud] server sichere URL = Tracking server sichere URL
>



If you&#39;re not sure how to find your tracking server see the [FAQ](../faq-intro/faq.md) and [Correctly Populate the trackingServer and trackingServerSecure variables](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Step 5: Update your AppMeasurement.js or s_code.js file {#section-b53113aea1bd4de896e0e4e9a7edee19}

Add this function to your `AppMeasurement.js` or `s_code.js` file:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Place the code in the same section that contains configurations such as `linkInternalFilters`, `charSet`, `trackDownloads`, etc.

***(Optional, jedoch empfohlen)*Erstellung einer benutzerspezifischen Eigenschaft**

Set a custom prop in `AppMeasurement.js` or `s_code.js` to measure coverage. Add this custom prop to the `doPlugins` function of your `AppMeasurement.js` or `s_code.js` files:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Step 6: Add Visitor API code to the page {#section-d46d6aa324c842f2931d901e38d6db1d}

Place the `VisitorAPI.js` file within the `<head>` tags on each page. Wenn Sie die Datei `VisitorAPI.js` zu Ihrer Seite hinzufügen:

* Put it at the beginning of the `<head>` section to it appears before other solution tags.
* Sie muss vor AppMeasurement und dem Code für andere [!DNL Experience Cloud]-Lösungen ausgeführt werden.

Versetzen Sie diesen Code nach dem Testen und Überprüfen in die Produktionsumgebung.

## Step 7: (Optional) Configure a grace period {#section-7bbb2f72c26e4abeb8881e18366797a3}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). Übergangsphasen können bis zu 180 Tage dauern. Falls erforderlich, kann eine Übergangsphase auch erneuert werden.

**Partielle Implementierung**

Sie benötigen eine Übergangsphase, wenn Sie einige Seiten verwalten, die den ID-Dienst verwenden, und einige Seiten, die diesen nicht verwenden, die jedoch alle in der gleichen [!DNL Analytics] Report Suite aufgeführt sind. Dies ist oft bei Kunden der Fall, die über eine globale, domänenübergreifende Report Suite verfügen.

Nach Bereitstellung des ID-Diensts für alle Webseiten, die in der gleichen Suite aufgeführt sind, kann die Übergangsphase abgebrochen werden.

**Voraussetzungen für den s_vi-Cookie**

Sie müssen eine Übergangsphase einrichten, wenn für neue Besucher nach Migration zum ID-Dienst ein s_vi-Cookie erforderlich ist. Dies ist oft der Fall, wenn Ihre Implementierung den s_vi-Cookie liest und ihn in einer Variablen speichert.

Sobald Ihre Implementierung statt Lesen des s_vi-Cookies die MID erhält, kann die Übergangsphase abgebrochen werden.

Detaillierte Informationen zur Erfassung von Lebenszyklusmetriken in Ihrer mobilen Anwendung finden Sie unter [Cookies und der Experience Cloud ID-Dienst](../introduction/cookies.md).

Sie müssen eine Übergangsphase konfigurieren, wenn Sie Daten von einem Clickstream-Datenfeed an ein internes System senden und bei der Verarbeitung die Spalten `visid_high` und `visid_low` verwendet werden.

Discontinue the grace period after your data ingestion process can use the `post_visid_high` and `post_visid_low` columns.

Siehe [Clickstream-Datenspaltenbezug](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

**Clickstream-Datenverarbeitung**

## Step 8: Test and deploy ID Service code {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Sie können wie folgt testen und bereitstellen.

**Testen und überprüfen**

Prüfen Sie zum Testen Ihrer ID-Dienstimplementierung Folgendes:

* [AMCV-Cookie](../introduction/cookies.md) in der Domäne, in der Ihre Seite gehostet wird.
* MID-Wert in der [!DNL Analytics]-Bildanfrage mit dem [Adobe Debugger-Werkzeug](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html).

See, [Test and Verify the Experience Cloud ID Service](../implementation-guides/test-verify.md).

**Code bereitstellen**

Stellen Sie den Code nach bestandenen Tests bereit.

Sollten Sie in [Schritt 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3) einen Übergangszeitraum konfiguriert haben:

* Stellen Sie sicher, dass die [!DNL Analytics]-ID (AID) und die MID sich in der Bildabfrage befinden.
* Denken Sie daran, die Übergangsphase nach Erfüllung der Kriterien für eine Beendigung der Verwendung abzubrechen.
