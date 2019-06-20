---
description: Diese Anweisungen richten sich an Analytics-, Audience Manager- und Target-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
keywords: ID-Dienst
seo-description: Diese Anweisungen richten sich an Analytics-, Audience Manager- und Target-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
seo-title: Implementieren des Experience Cloud ID-Diensts für Analytics, Audience Manager und Target
title: Implementieren des Experience Cloud ID-Diensts für Analytics, Audience Manager und Target
uuid: 9 d 446 b 77-ca 62-4325-8 bb 0-ff 43 a 52313 c 0
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Implementieren des Experience Cloud ID-Diensts für Analytics, Audience Manager und Target {#implement-the-experience-cloud-id-service-for-analytics-audience-manager-and-target}

Diese Anweisungen richten sich an Analytics-, Audience Manager- und Target-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber Dynamisches Tag-Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.

>[!IMPORTANT]
>
>Read the ID service [requirements](../reference/requirements.md) before you begin and note the following requirements that are specific to this implementation: &gt;
>* Kunden, die s_code verwenden, können dieses Verfahren nicht durchführen. Zum Durchführen dieses Verfahrens müssen Sie ein Upgrade auf mbox-Code v61 vornehmen.
>* Konfigurieren und testen Sie diesen Code in einer Entwicklungsumgebung, *bevor* Sie ihn in der Produktionsumgebung implementieren.
>



## Step 1: Plan for server-side forwarding {#section-880797cc992d4755b29cada7b831f1fc}

Zusätzlich zu den hier beschriebenen Schritten sollten Kunden, die [!DNL Analytics] und [!DNL Audience Manager] verwenden, zur serverseitigen Weiterleitung migrieren. Mithilfe der serverseitigen Weiterleitung können Sie DIL (den Datenerfassungscode von Audience Manager) entfernen und ihn durch das [Zielgruppen-Management-Modul](https://marketing.adobe.com/resources/help/en_US/aam/c_profiles_audiences.html) ersetzen. Weitere Informationen finden Sie in der [Dokumentation zur serverseitigen Weiterleitung](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html).

Für die Migration zur serverseitigen Weiterleitung sind Planung und Koordinierung erforderlich. Dieser Prozess umfasst externe Änderungen an Ihrem Sitecode und interne Schritte, die Adobe zum Bereitstellen Ihres Kontos vornehmen muss. Viele dieser Migrationsverfahren müssen tatsächlich parallel erfolgen und werden zusammen freigegeben. Ihr Implementierungspfad sollte dieser Ereignisabfolge folgen:

1. Arbeiten Sie zum Planen der Migration Ihres ID-Diensts und der serverseitigen Weiterleitung mit Ihrem Ansprechpartner für [!DNL Analytics] und [!DNL Audience Manager] zusammen. Dabei sollte der Auswahl eines Tracking-Servers in diesem Plan eine wichtige Rolle zukommen.

1. [!DNL Profiles & Audiences]Erhalten Sie eine Freischaltung. Füllen Sie zunächst das Formular auf der [Integrations- und Bereitstellungssite](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) aus.

1. Implement the ID service and the [!DNL Audience Management Module] simultaneously. To work properly, the [!DNL Audience Management Module] (server-side forwarding) and the ID service must be released for the same set of pages and at the same time.

## Step 2: Download the ID Service code {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

Für den ID-Dienst ist die Code-Bibliothek `VisitorAPI.js` erforderlich. Zum Herunterladen dieser Code-Bibliothek tun Sie Folgendes:

1. Rufen Sie **[!UICONTROL Admin &gt; Code-Manager auf]**.
1. In Code Manager, click either **[!UICONTROL JavaScrpt (New)]** or **[!UICONTROL JavaScript (Legacy)]**. Dies leitet das Herunterladen der komprimierten Code-Bibliotheken ein.

1. Entpacken Sie die Code-Datei und öffnen Sie die Datei `VisitorAPI.js`.

## Step 3: Add the Visitor.getInstance function to the ID Service code {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* In älteren Versionen der ID-Dienst-API wurde diese Funktion an einem anderen Ort platziert, und es war eine andere Syntax erforderlich. Sollten Sie von einer Version migrieren, die älter ist als [Version 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), beachten Sie die hier beschriebene neue Platzierung und Syntax.
>* Code in Großbuchstaben ist ein Platzhalter für die tatsächlichen Werte. Ersetzen Sie diesen Text durch Ihre Organisations-ID, Ihre Tracking-Server-URL oder einen anderen benannten Wert.
>



**Teil 1: Kopieren Sie die unten stehende Funktion Visitor.getInstance**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**Teil 2: Hinzufügen von Funktionscode zur Datei VisitorAPI.js**

Platzieren Sie die Funktion `Visitor.getInstance` am Ende der Datei nach dem Code-Block. Die bearbeitete Datei sollte wie folgt aussehen:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Step 4: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-e2947313492546789b0c3b2fc3e897d8}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your Experience Cloud organization ID. Sollten Sie Ihre Organisations-ID nicht kennen, finden Sie diese auf der Administrationsseite der Experience Cloud. Die bearbeitete Funktion sollte dem unten stehenden Beispiel ähnlich sehen.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Ändern Sie nicht* den Fall der Zeichen in Ihrer Organisations-ID. Bei der ID wird Groß- und Kleinschreibung beachtet und sie muss so eingegeben werden, wie sie von Adobe angegeben wird.

## Step 5: Add your tracking servers to Visitor.getInstance {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics verwendet Tracking-Server für die Datenerfassung.

**Teil 1: Ermitteln der Tracking-Server-URLs**

Check your `s_code.js` or `AppMeasurement.js` files to find the tracking server URLs. Die URLs werden von folgenden Variablen spezifiziert:

* `s.trackingServer`
* `s.trackingServerSecure`

**Teil 2: Festlegen der Tracking-Server-Variablen**

Zur Festlegung, welche Tracking-Server-Variablen verwendet werden sollen:

1. Beantworten Sie die Fragen in der unten stehenden Entscheidungsmatrix. Verwenden Sie die Variablen, die Ihren Antworten entsprechen.
1. Ersetzen Sie die Tracking-Server-Platzhalter durch Ihre eigenen Tracking-Server-URLs.
1. Entfernen Sie nicht verwendete Tracking-Server- und Experience Cloud-Servervariablen aus dem Code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Passen Sie bei Verwendung den Experience Cloud-Server-urls den entsprechenden Tracking-Server-urls wie folgt an:

* Experience Cloud-Server-URL = Tracking-Server-URL
* Sichere Experience Cloud-Server-URL = sichere Tracking-Server-URL

Wenn Sie nicht genau wissen, wie Sie Ihren Tracking-Server finden, lesen Sie [Häufig gestellte Fragen](../faq-intro/faq.md) und [Korrektes Füllen der Variablen trackingServer und trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Step 6: Update your AppMeasurement.js file {#section-5517e94a09bc44dfb492ebca14b43048}

This step requires [!DNL AppMeasurement]. Sie können nicht fortfahren, wenn Sie weiterhin s_code verwenden.

Add the `Visitor.getInstance` function shown below to your `AppMeasurement.js` file. Place it in the section that contains configurations such as `linkInternalFilters`, `charSet`, `trackDownloads`, etc. :

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>At this point, you should remove the [!DNL Audience Manager] DIL code and replace it with the Audience Management Module. Anweisungen finden Sie im Thema über das [Implementieren der serverseitigen Weiterleitung](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html).

***(Optional, jedoch empfohlen)*Erstellung einer benutzerspezifischen Eigenschaft**

Festlegen einer benutzerdefinierten Eigenschaft zum Messen der Abdeckung in `AppMeasurement.js`. Fügen Sie der Funktion `doPlugins` der Datei `AppMeasurement.js` folgende benutzerspezifische Eigenschaft hinzu:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Step 7: Add Visitor API code to the page {#section-c2bd096a3e484872a72967b6468d3673}

Place the ` [!DNL VisitorAPI.js]` file within the `<head>` tags on each page. Wenn Sie die Datei `VisitorAPI.js` zu Ihrer Seite hinzufügen:

* Put it at the beginning of the `<head>` section to it appears before other solution tags.
* Sie muss vor AppMeasurement und dem Code für andere [!DNL Experience Cloud]-Lösungen ausgeführt werden.

## Step 8: (Optional) Configure a grace period {#section-aceacdb7d5794f25ac6ff46f82e148e1}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). Übergangsphasen können bis zu 180 Tage dauern. Falls erforderlich, kann eine Übergangsphase auch erneuert werden.

**Partielle Implementierung**

Sie benötigen eine Übergangsphase, wenn Sie einige Seiten verwalten, die den ID-Dienst verwenden, und einige Seiten, die diesen nicht verwenden, die jedoch alle in der gleichen Analytics Report Suite aufgeführt sind. Dies ist oft bei Kunden der Fall, die über eine globale, domänenübergreifende Report Suite verfügen.

Nach Bereitstellung des ID-Diensts für alle Webseiten, die in der gleichen Suite aufgeführt sind, kann die Übergangsphase abgebrochen werden.

**Voraussetzungen für den s_vi-Cookie**

Sie müssen eine Übergangsphase einrichten, wenn für neue Besucher nach Migration zum ID-Dienst ein s_vi-Cookie erforderlich ist. Dies ist oft der Fall, wenn Ihre Implementierung den s_vi-Cookie liest und ihn in einer Variablen speichert.

Sobald Ihre Implementierung statt Lesen des s_vi-Cookies die MID erhält, kann die Übergangsphase abgebrochen werden.

See also, [Cookies and the Experience Cloud ID Service](../introduction/cookies.md).

**Clickstream-Datenintegration**

Sie müssen eine Übergangsphase konfigurieren, wenn Sie Daten von einem Clickstream-Datenfeed an ein internes System senden und bei der Verarbeitung die Spalten `visid_high` und `visid_low` verwendet werden.

Discontinue the grace period after your data ingestion process can use the `post_visid_high` and `post_visid_low` columns.

Siehe auch [Clickstream-Datenspaltenbezug](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

## Step 9: Test and verify {#section-f857542bfc70496dbb9f318d6b3ae110}

Die [!DNL Experience Cloud]-Lösungen in dieser Implementierung geben IDs in der Form von Schlüssel-Wert-Paaren zurück. Jede Lösung verwendet unterschiedliche Schlüssel (z. B. die [!DNL Analytics]-SDID im Vergleich mit der mboxMCSDID von [!DNL Target]) für die Aufbewahrung derselben ID. Laden Sie zum Testen Ihrer Implementierung Ihre Seiten in einer Entwicklungsumgebung. Verwenden Sie Ihre Browserkonsole oder Software, die HTTP-Anforderungen und -antworten überwacht, um die unten aufgeführten IDs zu überprüfen. Der ID-Dienst wurde richtig implementiert, wenn die im Folgenden aufgeführten Schlüssel-Wert-Paare dieselben ID-Werte zurückgeben.

>[!TIP]
>
>You can use the [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=debugger.html) or the [Charles HTTP proxy](https://www.charlesproxy.com/) to check for these solution-specific IDs. Sie können jedoch auch ein beliebiges anderes Tool oder einen anderen Debugger verwenden, wenn sie sich am besten für Sie eignen.

**Alle Lösungen**

Suchen Sie nach Folgendem:

* [AMCV-Cookie](../introduction/cookies.md) in der Domäne, auf der Ihre Seite gehostet wird.
* [!DNL Experience Cloud] ID (MID) mit [!DNL Adobe] dem Debugger oder Ihrem bevorzugten Debugging-Tool.

For additional checks that help you determine if the ID service is working properly, see [Test and Verify the Experience Cloud ID Service](../implementation-guides/test-verify.md).

**Analytics**

Überprüfen Sie den SDID-Bezeichner in der JavaScript-Anforderung. Die Analytics-SDID sollte mit der mboxMCSDID von Target übereinstimmen.

Wenn in Ihren Tests eine AID zurückgegeben wird, bedeutet das entweder:

* Sie sind ein wiederkehrender Besucher im Prozess der Migration von alten [!DNL Analytics]-IDs.
* You have a [grace period](../reference/analytics-reference/grace-period.md) enabled.

Wenn Sie eine AID sehen, vergleichen Sie den zugehörigen Wert mit der mboxMCAVID von [!DNL Target]. Diese Werte sind identisch, wenn der ID-Dienst richtig implementiert wurde.

**Audience Manager**

Informationen zum Testen der serverseitigen Weiterleitung finden Sie in den Themen über das:

* [Ermitteln, ob Ihr Konto für das Empfangen von Weiterleitungsdaten bereit ist](https://marketing.adobe.com/resources/help/en_US/aam/ssf-success.html)
* [Ermitteln, ob Ihr Konto für das Empfangen von Weiterleitungsdaten nicht bereit ist](https://marketing.adobe.com/resources/help/en_US/aam/ssf-fail.html)

**Target**

Suchen Sie nach Folgendem:

* mboxMCGVID
* mboxMCSDID (die mboxMCSDID sollte mit der Analytics-SDID übereinstimmen)

Wenn in Ihren Tests eine mboxMCAVID zurückgegeben wird, bedeutet das entweder:

* Sie sind ein wiederkehrender Besucher im Prozess der Migration von alten [!DNL Analytics]-IDs.
* Sie haben eine Übergangsphase aktiviert.

Wenn Sie eine mboxMCAVID sehen, vergleichen Sie den zugehörigen Wert mit der [!DNL Analytics]-AID. Diese Werte sind identisch, wenn der ID-Dienst richtig implementiert wurde.

**Implementierung**

## Step 10: Deploy {#section-4188fa95e7dc455a986b48a6c517c1c9}

Stellen Sie den Code nach bestandenen Tests bereit.

Bei einer aktivierten Übergangsphase:

* Stellen Sie sicher, dass die Analytics-ID (AID) und die MID sich in der Bildabfrage befinden.
* Denken Sie daran, die Übergangsphase nach Erfüllung der [Kriterien für eine Beendigung](../implementation-guides/setup-aam-analytics-target.md#section-aceacdb7d5794f25ac6ff46f82e148e1) der Verwendung abzubrechen.

