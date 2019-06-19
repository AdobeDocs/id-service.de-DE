---
description: Versionshinweise und Aktualisierungen für das Jahr 2015
keywords: ID-Dienst
seo-description: Versionshinweise und Aktualisierungen für das Jahr 2015
seo-title: Versionshinweise 2015
title: Versionshinweise 2015
uuid: 49423699-1 e 0 f -49 e 4-9135-2 ae 84 b 4 f 92 df
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Versionshinweise für 2015 {#release-notes}

Versionshinweise und Aktualisierungen für das Jahr 2015

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

November 2015

Der Children&#39;s Online Privacy Protection Act (COPPA) verbietet die Onlineerfassung persönlicher Informationen von Kindern unter 13 ohne nachweisliche Genehmigung der Eltern. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem [!DNL Experience Cloud] ID-Dienstcode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers verwendet werden. Siehe [COPPA-Unterstützung im Experience Platform Identity Service](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Nur bei Version 1.5.3 oder neuer.

## Version 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

September 2015

* Fehler im Safari-Browser behoben, der die Funktion der Synchronisierungsdienste verhinderte, wenn Benutzer Drittanbietercookies blockiert hatten. (AAM-20764)
* Aufrufe des ID-Diensts enthalten jetzt die Versions-ID im `d_visid_ver=` Parameter. Die zurückgegebene ID hilft internen Teams bei der Fehlerbehebung und Supportproblemen. (AAM-20824)

## Version 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

August 2015

* Ein Fehler wurde behoben, um zu verhindern, dass der ID-Dienst einen iframe anfordert, wenn keine zu synchronisierenden oder auszulösenden Daten vorhanden sind. (AAM-20164)
* Ein Fehler wurde behoben, durch den der ID-Dienst mehrteilige Top-Level-Domänen-Cookies nicht ordnungsgemäß setzte. Wenn Sie beispielsweise über eine Domäne verfügen, `my_company.co.uk`würde der ID-Dienst unter bestimmten Umständen ein Cookie festlegen `co.uk` . (AN-104683)

   Davon waren nur einige Kunden betroffen, die *alle* folgenden Kriterien erfüllten:

   * Verwendung des ID-Diensts.
   * Aktivierung einer [Schonfrist](../reference/analytics-reference/grace-period.md) *oder* Verwendung von Cookies von Erstanbietern und Benutzer blockieren Cookies von Drittanbietern.

   * Besitz von Seiten mit mehrteiligen Top-Level-Domains.

Dokumentationsüberarbeitungen in dieser Veröffentlichung umfassen:

* [API-Methoden und Code-Bibliothek](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Neu organisierter Inhalt und Text. In den meisten Fällen erhält jede Methode eine eigene Seite.
* [Anforderungen für den Experience Platform-Identitätsdienst](../reference/requirements.md): Überarbeiteter Inhalt und neu organisierter Text.

## Version 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Juli 2015

Der [!DNL Experience Cloud] ID-Dienst unterstützt mehrere IDs und Authentifizierungsstatus. Diese Änderung macht zudem die veraltete Unterstützung von [!DNL Audience Manager]-DPID-Zuordnungen zu Benutzern überflüssig, die von der Funktion `setCustomerIDs` verwendet wurden. Siehe [Kunden-IDs und Authentifizierungsstatus](../reference/authenticated-state.md)

## Version 1.4 {#section-f5c596f355b14da28f45c798df513572}

Mai 2015

Ab Version 1.4 ist die bevorzugte Methode zum Vornehmen von Einstellungen das Weiterleiten eines konfigurierten Objekts als zweiter Parameter für die Funktion `Visitor.getInstance`.

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

Weitere Informationen finden Sie unter [Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd).

## Version 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

Februar 2015

Fehlerbehebung der Zeitüberschreitung bei Anforderungen für AAM Blob und Location Hint. Bei einer Zeitüberschreitung bleiben diese Felder nun auf der aktuellen Seite im System leer und es werden alle Callbacks aufgerufen. Die Zeitüberschreitung wird als Fehler behandelt, sodass der Vorgang auf der nächsten Seite erneut versucht wird. (AN-94473, AN-94474)

## Version 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Januar 2015

`<head>/<body>` Die Tag-Suche für den JSONP-Anforderungs- `<script>` Container sowie die Erstellung des `<script>` Tags wurde überarbeitet, um verschiedene DOM-Implementierungen (HTML vs. XHTML) mit möglicherweise unterschiedlichen Einstellungen für die Groß-/Kleinschreibung zu berücksichtigen. (AN-9355)