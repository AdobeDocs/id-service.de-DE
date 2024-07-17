---
description: Diese Anweisungen richten sich an Analytics-Kundinnen und -Kunden, die den Identity Service von Experience Cloud verwenden möchten und keine Datenerfassungs-Tags verwenden. Es wird allerdings dringend empfohlen, Tags zum Implementieren des ID-Diensts zu verwenden. Tags vereinheitlichen den Implementierungs-Workflow und stellen automatisch sicher, dass der Code korrekt platziert und sequenziert wird.
keywords: ID-Dienst
title: Implementieren des Experience Cloud Identity Services für Analytics
exl-id: c0271e49-32e5-49ee-bb11-548751ccafad
source-git-commit: 792fb5d5192843f345577a99b6179fb6d95fedc0
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 100%

---

# Implementieren des Experience Cloud Identity Services für Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Diese Anweisungen richten sich an Analytics-Kundinnen und Kunden, die den Identity Service von Experience Cloud verwenden möchten und keine [Datenerfassungs-Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) verwenden. Es wird allerdings dringend empfohlen, Tags zum Implementieren des ID-Diensts zu verwenden. Tags vereinheitlichen den Implementierungs-Workflow und stellen automatisch sicher, dass der Code korrekt platziert und sequenziert wird.

>[!IMPORTANT]
>
>* [Lesen Sie sich die Anforderungen durch,](../reference/requirements.md) bevor Sie beginnen.
>* Konfigurieren und testen Sie den Code in einer Entwicklungsumgebung, bevor er in das Produktivsystem übernommen wird.

Führen Sie die folgenden Schritte aus, um den ID-Dienst für Adobe Analytics zu implementieren:

1. [Herunterladen des ID-Dienst-Codes](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Hinzufügen der Funktion „Visitor.getInstance“ zum ID-Dienst-Code](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Hinzufügen der Experience Cloud Organisations-ID zu Visitor.getInstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Hinzufügen Ihrer Tracking-Server zu Visitor.getInstance](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Aktualisieren der Datei AppMeasurement.js oder s_code.js](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19).
1. [Hinzufügen des Besucher-API-Codes zur Seite](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Optional) Konfigurieren einer Übergangsphase](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Testen und Bereitstellen des ID-Dienst-Codes](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Schritt 1: Herunterladen des ID-Dienst-Codes {#section-ead9403a6b7e45b887f9ac959ef89f7f}

Für den [!UICONTROL ID-Dienst] ist die Code-Bibliothek `VisitorAPI.js` erforderlich. Zum Herunterladen dieser Code-Bibliothek tun Sie Folgendes:

1. Rufen Sie **[!UICONTROL Admin]** > **[!UICONTROL Code-Manager]** auf.
1. Klicken Sie im [!UICONTROL Code-Manager] entweder auf **[!UICONTROL JavaScript (neu)]** oder auf **[!UICONTROL JavaScript (Legacy)]**.

   Dies leitet das Herunterladen der komprimierten Code-Bibliotheken ein.

1. Entpacken Sie die Code-Datei und öffnen Sie die `VisitorAPI.js` Datei.

## Schritt 2: Hinzufügen der Funktion „Visitor.getInstance“ zum ID-Service-Code {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* In früheren Versionen der ID-Dienst-API wurde diese Funktion an einer anderen Stelle und es war eine andere Syntax erforderlich. Wenn Sie von einer Version vor [Version 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572) migrieren, beachten Sie die hier beschriebene neue Platzierung und Syntax.
>* Code in GROSSBUCHSTABEN dient als Platzhalter für tatsächliche Werte. Ersetzen Sie diesen Text durch Ihre Organisations-ID, die Trackingserver-URL oder einen anderen benannten Wert.

**Teil 1: Kopieren Sie die Visitor.getInstance -Funktion unten**

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

**Teil 2: Fügen Sie der Datei VisitorAPI.js Funktions-Code hinzu**

Platzieren Sie die `Visitor.getInstance` Funktion am Ende der Datei nach dem Code-Block. Die bearbeitete Datei sollte wie folgt aussehen:

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

## Schritt 3: Hinzufügen der Experience Cloud-Organisations-ID zu Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

Ersetzen Sie in der `Visitor.getInstance` Funktion den Ausdruck `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` durch Ihre [!DNL Experience Cloud]-Organisations-ID. Sollten Sie Ihre Organisations-ID nicht kennen, finden Sie diese auf der Administrationsseite der [!DNL Experience Cloud]. Siehe auch [Administration – Core Services](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=de). Die bearbeitete Funktion sollte dem unten stehenden Beispiel ähnlich sehen.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Wichtig:* Ändern Sie die Groß- oder Kleinschreibung Ihrer Organisations-ID nicht. Bei der ID wird Groß- und Kleinschreibung beachtet und sie muss so eingegeben werden, wie sie von Adobe angegeben wird.

## Schritt 4: Hinzufügen Ihrer Tracking-Server zu Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

Tracking-Server werden für die [!DNL Analytics] Datenerfassung in verwendet.

**Teil 1: Ermitteln der Tracking-Server-URLs**

Überprüfen Sie die Datei `s_code.js` oder `AppMeasurement.js`, um die URLs der Tracking-Server zu ermitteln. Die URLs werden von folgenden Variablen spezifiziert:

* `s.trackingServer`
* `s.trackingServerSecure`

**Teil 2: Festlegen der Trackingserver-Variablen**

So legen Sie fest, welche Trackingserver-Variablen verwendet werden sollen:

1. Beantworten Sie die Fragen in der folgenden Entscheidungsmatrix. Verwenden Sie die Variablen, die Ihren Antworten entsprechen.
1. Ersetzen Sie die Trackingserver-Platzhalter durch Ihre Trackingserver-URLs.
1. Entfernen Sie nicht verwendete Tracking-Server- und [!DNL Experience Cloud]-Servervariablen aus dem Code.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Prüfen Sie bei Verwendung von [!DNL Experience Cloud]-Server-URLs deren Übereinstimmung mit den entsprechenden Tracking-Server-URLs wie folgt:
>
>* [!DNL Experience Cloud]-Server-URL = Tracking-Server-URL
>* Sichere [!DNL Experience Cloud]-Server-URL = sichere Tracking-Server-URL

Wenn Sie nicht genau wissen, wie Sie Ihren Trackingserver finden, lesen Sie die [FAQ](../faq-intro/faq.md) und [Korrektes Ausfüllen der Variablen „trackingServer“ und „trackingServerSecure“](https://helpx.adobe.com/de/analytics/kb/determining-data-center.html#).

## Schritt 5: Aktualisieren Sie Ihre AppMeasurement.js oder s_code.js-Datei {#section-b53113aea1bd4de896e0e4e9a7edee19}

Fügen Sie der Datei `AppMeasurement.js` oder `s_code.js` diese Funktion hinzu:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Platzieren Sie den Code im gleichen Abschnitt, in dem Konfigurationen wie `linkInternalFilters`, `charSet`, `trackDownloads` usw. enthalten sind.

***(Optional, jedoch empfohlen)* Erstellung einer benutzerspezifischen Eigenschaft.**

Festlegen einer benutzerspezifischen Eigenschaft zum Messen der Abdeckung in `AppMeasurement.js` oder `s_code.js` Fügen Sie der `doPlugins` Funktion, der Datei `AppMeasurement.js` oder `s_code.js` der Datei folgende benutzerspezifische Eigenschaft hinzu:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Schritt 6: Hinzufügen des Besucher-API-Codes zur Seite {#section-d46d6aa324c842f2931d901e38d6db1d}

Platzieren Sie die `VisitorAPI.js`-Datei innerhalb der `<head>`-Tags auf jeder Seite. Wenn Sie die `VisitorAPI.js` Datei zu Ihrer Seite hinzufügen:

* Platzieren Sie sie am Anfang des Abschnitts `<head>`, damit dies vor anderen Lösungstags angezeigt wird.
* Sie muss vor AppMeasurement und dem Code für andere [!DNL Experience Cloud]-Lösungen ausgeführt werden.

Versetzen Sie diesen Code nach dem Testen und Überprüfen in die Produktionsumgebung.

## Schritt 7: (Optional) Konfigurieren einer Übergangsphase {#section-7bbb2f72c26e4abeb8881e18366797a3}

Wenn eines dieser Nutzungsszenarios auf Ihre Situation zutrifft, bitten Sie die [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html), eine temporäre [Übergangsphase](../reference/analytics-reference/grace-period.md) einzurichten. Übergangsphasen können bis zu 180 Tage dauern. Bei Bedarf kann eine Übergangsphase verlängert werden.

**Partielle Implementierung**

Sie benötigen eine Übergangsphase, wenn Sie einige Seiten verwalten, die den ID-Dienst verwenden, und einige Seiten, die diesen nicht verwenden, die jedoch alle in der gleichen [!DNL Analytics] Report Suite aufgeführt sind. Dies ist häufig der Fall, wenn Sie eine globale Report Suite haben, die domänenübergreifend Berichte erstellt.

Beenden Sie die Übergangsphase, nachdem der ID-Dienst auf allen Webseiten bereitgestellt wurde, die in dieselbe Report Suite eingehen.

**s_vi-Cookie-Anforderungen**

Sie müssen eine Übergangsphase konfigurieren, wenn neue Besucher nach der Migration zum ID-Dienst über ein s_vi-Cookie verfügen müssen. Dies ist häufig der Fall, wenn Ihre Implementierung das s_vi-Cookie liest und es in einer Variablen speichert.

Beenden Sie die Übergangsphase, nachdem Ihre Implementierung die MID erfassen kann, anstatt das s_vi-Cookie zu lesen.

Siehe [Cookies und der Experience Cloud Identity Service](../introduction/cookies.md).

Sie müssen eine Übergangsphase konfigurieren, wenn Sie Daten von einem Clickstream-Datenfeed an ein internes System senden und bei der Verarbeitung die Spalten `visid_high` und `visid_low` verwendet werden.

Sobald Ihre Datenverarbeitungsprozesse die Spalten `post_visid_high` und `post_visid_low` einsetzen können, können Sie die Übergangsphase abbrechen.

Siehe [Clickstream-Datenspaltenreferenz](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html?lang=de).

**Clickstream-Datenverarbeitung**

## Schritt 8: Testen und Bereitstellen des ID-Dienst-Codes {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Sie können dies wie folgt testen und bereitstellen.

**Testen und Verifizieren**

Prüfen Sie zum Testen Ihrer ID-Dienstimplementierung Folgendes:

* [AMCV-Cookie](../introduction/cookies.md) in der Domain, auf der Ihre Seite gehostet wird.
* MID-Wert in der [!DNL Analytics]-Bildanforderung mit dem [Adobe-Debuggertool](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=de).

Siehe [Testen und Überprüfen des Experience Cloud Identity Services](../implementation-guides/test-verify.md).

**Bereitstellungscode**

Stellen Sie Ihren Code nach Abschluss der Tests bereit.

Wenn Sie in [Schritt 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3) eine Übergangsphase aktiviert haben:

* Stellen Sie sicher, dass die [!DNL Analytics]-ID (AID) und die MID sich in der Bildabfrage befinden.
* Denken Sie daran, die Übergangsphase nach Erfüllung der Kriterien für eine Beendigung der Verwendung abzubrechen.
