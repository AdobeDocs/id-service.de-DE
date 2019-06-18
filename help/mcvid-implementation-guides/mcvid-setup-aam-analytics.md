---
description: Diese Anweisungen richten sich an Analytics- und Audience Manager-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber das Dynamic Tag Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
keywords: ID-Dienst
seo-description: Diese Anweisungen richten sich an Analytics- und Audience Manager-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber das Dynamic Tag Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.
seo-title: Implementieren des Experience Cloud ID-Diensts für Analytics und Audience Manager
title: Implementieren des Experience Cloud ID-Diensts für Analytics und Audience Manager
uuid: d 46050 ae -87 de -46 cc -911 b-d 3346 c 7 fd 511
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Implementieren des Experience Cloud ID-Diensts für Analytics und Audience Manager{#implement-the-experience-cloud-id-service-for-analytics-and-audience-manager}

Diese Anweisungen richten sich an Analytics- und Audience Manager-Kunden, die den Experience Cloud ID-Dienst verwenden möchten, nicht aber das Dynamic Tag Management (DTM). Es wird jedoch dringend empfohlen, DTM zum Implementieren des ID-Diensts zu verwenden. DTM optimiert die Implementierung des Workflows und gewährleistet automatisch die richtige Codeplatzierung und -abfolge.

>[!IMPORTANT]
>
>* [Lesen Sie sich die Anforderungen durch,](../mcvid-reference/mcvid-requirements.md) bevor Sie beginnen.
>* Für dieses Verfahren ist AppMeasurement erforderlich. Kunden, die s_code verwenden, können dieses Verfahren nicht durchführen.
>* Konfigurieren und testen Sie den Code in einer Entwicklungsumgebung, bevor er in das Produktivsystem übernommen wird.
>



## Schritt 1: Planen der serverseitigen Weiterleitung {#section-880797cc992d4755b29cada7b831f1fc}

Zusätzlich zu den hier beschriebenen Schritten sollten Kunden, die [!DNL Analytics] und [!DNL Audience Manager] verwenden, zur serverseitigen Weiterleitung migrieren. Mithilfe der serverseitigen Weiterleitung können Sie DIL (den Datenerfassungscode von Audience Manager) entfernen und ihn durch das [Zielgruppen-Management-Modul](https://marketing.adobe.com/resources/help/en_US/aam/c_profiles_audiences.html) ersetzen. Weitere Informationen finden Sie in der [Dokumentation zur serverseitigen Weiterleitung](https://marketing.adobe.com/resources/help/en_US/analytics/audiences/ssf.html).

Für die Migration zur serverseitigen Weiterleitung sind Planung und Koordinierung erforderlich. Dieser Prozess umfasst externe Änderungen an Ihrem Sitecode und interne Schritte, die Adobe zum Bereitstellen Ihres Kontos vornehmen muss. Viele dieser Migrationsverfahren müssen tatsächlich parallel erfolgen und werden zusammen freigegeben. Ihr Implementierungspfad sollte dieser Ereignisabfolge folgen:

1. Arbeiten Sie zum Planen der Migration Ihres ID-Diensts und der serverseitigen Weiterleitung mit Ihrem Ansprechpartner für [!DNL Analytics] und [!DNL Audience Manager] zusammen. Dabei sollte der Auswahl eines Tracking-Servers in diesem Plan eine wichtige Rolle zukommen.

1. [!DNL Profiles & Audiences]Erhalten Sie eine Freischaltung. Füllen Sie zunächst das Formular auf der [Integrations- und Bereitstellungssite](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) aus.

1. Implementieren Sie den ID-Dienst und gleichzeitig [!DNL Audience Management Module] . Um ordnungsgemäß zu funktionieren, müssen die [!DNL Audience Management Module] (serverseitige Weiterleitung) und der ID-Dienst für denselben Seitensatz und gleichzeitig freigegeben werden.

## Schritt 2: Herunterladen des ID-Dienst-Codes {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

Für den ID-Dienst ist die Code-Bibliothek `VisitorAPI.js` erforderlich. Zum Herunterladen dieser Code-Bibliothek tun Sie Folgendes:

1. Wechseln Sie zu **[!UICONTROL Admin]** &gt; **[!UICONTROL Code-Manager]**.

1. Klicken Sie im Code-Manager entweder **[!UICONTROL auf javascript (Neu)]** oder **[!UICONTROL auf javascript (Legacy)]**. Dies leitet das Herunterladen der komprimierten Code-Bibliotheken ein.

1. Entpacken Sie die Code-Datei und öffnen Sie die Datei `VisitorAPI.js`.

## Schritt 3: Hinzufügen der Funktion Visitor. getinstance zum ID-Dienst-Code {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* In älteren Versionen der ID-Dienst-API wurde diese Funktion an einem anderen Ort platziert, und es war eine andere Syntax erforderlich. Sollten Sie von einer Version migrieren, die älter ist als [Version 1.4](../mcvid-release-notes/mcvid-notes-2015.md#section-f5c596f355b14da28f45c798df513572), beachten Sie die hier beschriebene neue Platzierung und Syntax.
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

## Schritt 4: Fügen Sie Visitor. getinstance Ihre Experience Cloud-Organisations-ID hinzu. {#section-e2947313492546789b0c3b2fc3e897d8}

Ersetzen Sie in der `Visitor.getInstance` Funktion die `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` Experience Cloud-Organisations-ID. Sollten Sie Ihre Organisations-ID nicht kennen, finden Sie diese auf der Administrationsseite der Experience Cloud. Die bearbeitete Funktion sollte dem unten stehenden Beispiel ähnlich sehen.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Ändern Sie nicht* den Fall der Zeichen in Ihrer Organisations-ID. Bei der ID wird Groß- und Kleinschreibung beachtet und sie muss so eingegeben werden, wie sie von Adobe angegeben wird.

## Schritt 5: Hinzufügen Ihrer Tracking-Server zu Visitor. getinstance {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics verwendet Tracking-Server für die Datenerfassung.

**Teil 1: Ermitteln der Tracking-Server-URLs**

Überprüfen Sie Ihre `s_code.js` Dateien `AppMeasurement.js` , um die Tracking-Server-urls zu finden. Die URLs werden von folgenden Variablen spezifiziert:

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

Wenn Sie nicht genau wissen, wie Sie Ihren Tracking-Server finden, lesen Sie [Häufig gestellte Fragen](../mcvid-faq-intro/ecid-faq.md) und [Korrektes Füllen der Variablen trackingServer und trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Schritt 6: Datei appmeasurement. js aktualisieren {#section-5517e94a09bc44dfb492ebca14b43048}

Dieser Schritt [!DNL AppMeasurement]ist erforderlich. Sie können nicht fortfahren, wenn Sie weiterhin s_code verwenden.

Fügen Sie `Visitor.getInstance` der `AppMeasurement.js` Datei die unten stehende Funktion hinzu. Platzieren Sie es im Abschnitt mit Konfigurationen wie `linkInternalFilters``charSet``trackDownloads`, usw.:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>Zu diesem Zeitpunkt sollten Sie den [!DNL Audience Manager] DIL-Code entfernen und durch das Zielgruppen-Management-Modul ersetzen. Anweisungen finden Sie im Thema über das [Implementieren der serverseitigen Weiterleitung](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html).

***(Optional, jedoch empfohlen)*Erstellung einer benutzerspezifischen Eigenschaft**

Festlegen einer benutzerdefinierten Eigenschaft zum Messen der Abdeckung in `AppMeasurement.js`. Fügen Sie der Funktion `doPlugins` der Datei `AppMeasurement.js` folgende benutzerspezifische Eigenschaft hinzu:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Schritt 7: Hinzufügen des Besucher-API-Codes zur Seite {#section-c2bd096a3e484872a72967b6468d3673}

Platzieren Sie die ` [!DNL VisitorAPI.js]` Datei in den `<head>` Tags auf jeder Seite. Wenn Sie die Datei `VisitorAPI.js` zu Ihrer Seite hinzufügen:

* Platzieren Sie es am Anfang des `<head>` Abschnitts, damit er vor anderen Lösungstags angezeigt wird.
* Sie muss vor AppMeasurement und dem Code für andere [!DNL Experience Cloud]-Lösungen ausgeführt werden.

## Schritt 8: (Optional) Konfigurieren einer Übergangsphase {#section-aceacdb7d5794f25ac6ff46f82e148e1}

Wenden Sie sich bei einem dieser Anwendungsfälle an die [Kundenunterstützung](https://helpx.adobe.com/marketing-cloud/contact-support.html) , um eine vorübergehende [Übergangsphase](../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)einzurichten. Übergangsphasen können bis zu 180 Tage dauern. Falls erforderlich, kann eine Übergangsphase auch erneuert werden.

**Partielle Implementierung**

Sie benötigen eine Übergangsphase, wenn Sie einige Seiten verwalten, die den ID-Dienst verwenden, und einige Seiten, die diesen nicht verwenden, die jedoch alle in der gleichen Analytics Report Suite aufgeführt sind. Dies ist oft bei Kunden der Fall, die über eine globale, domänenübergreifende Report Suite verfügen.

Nach Bereitstellung des ID-Diensts für alle Webseiten, die in der gleichen Suite aufgeführt sind, kann die Übergangsphase abgebrochen werden.

**Voraussetzungen für den s_vi-Cookie**

Sie müssen eine Übergangsphase einrichten, wenn für neue Besucher nach Migration zum ID-Dienst ein s_vi-Cookie erforderlich ist. Dies ist oft der Fall, wenn Ihre Implementierung den s_vi-Cookie liest und ihn in einer Variablen speichert.

Sobald Ihre Implementierung statt Lesen des s_vi-Cookies die MID erhält, kann die Übergangsphase abgebrochen werden.

Siehe auch [Cookies und Experience Cloud ID-Dienst](../mcvid-introduction/mcvid-cookies.md).

**Clickstream-Datenintegration**

Sie müssen eine Übergangsphase konfigurieren, wenn Sie Daten von einem Clickstream-Datenfeed an ein internes System senden und bei der Verarbeitung die Spalten `visid_high` und `visid_low` verwendet werden.

Sobald der Datenerfassungsprozess die Spalten `post_visid_high` und `post_visid_low` Spalten verwenden kann, können Sie die Übergangsphase abbrechen.

Siehe auch [Clickstream-Datenspaltenbezug](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

## Schritt 9: Testen und Bereitstellen des ID-Dienst-Codes {#section-f857542bfc70496dbb9f318d6b3ae110}

Sie können wie folgt testen und bereitstellen.

**Testen und überprüfen**

Prüfen Sie zum Testen Ihrer ID-Dienstimplementierung Folgendes:

* [AMCV-Cookie](../mcvid-introduction/mcvid-cookies.md) in der Domäne, auf der Ihre Seiten gehostet werden.
* MID-Wert in der Analytics-Bildanforderung mit dem [Adobe-Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html).
* Siehe auch [Testen und Überprüfen des Experience Cloud ID-Diensts](../mcvid-implementation-guides/mcvid-test-verify.md).

Lesen Sie [So überprüfen Sie Ihre Implementierung der serverseitigen Weiterleitung](https://marketing.adobe.com/resources/help/en_US/reference/ssf-verify.html), um die serverseitige Weiterleitung zu überprüfen.

**Bereitstellung**

Stellen Sie den Code nach bestandenen Tests bereit.

Bei einer aktivierten Übergangsphase:

* Stellen Sie sicher, dass die Analytics-ID (AID) und die MID sich in der Bildabfrage befinden.
* Denken Sie daran, die Übergangsphase nach Erfüllung der Kriterien für eine Beendigung der Verwendung abzubrechen.

