---
description: Versionshinweise und Aktualisierungen für das Jahr 2015
keywords: ID-Dienst
title: Versionshinweise für 2015
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 100%

---

# Versionshinweise für 2015 {#release-notes}

Versionshinweise und Aktualisierungen für das Jahr 2015

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

November 2015

Der Children&#39;s Online Privacy Protection Act (COPPA) verbietet die Online-Erfassung personenbezogener Daten von Kindern unter 13 Jahren ohne nachprüfbare elterliche Zustimmung. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem [!DNL Experience Cloud] ID-Dienstcode eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers verwendet werden. Siehe [COPPA-Unterstützung im Experience Cloud Identity Service](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Nur bei Version 1.5.3 oder neuer.

## Version 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

September 2015

* Es wurde ein Fehler im Safari-Browser behoben, durch den Synchronisierungsdienste nicht funktionierten, wenn Benutzer Drittanbieter-Cookies blockierten. (AAM-20764)
* Aufrufe des ID-Dienstes enthalten nun die Versions-ID im Parameter `d_visid_ver=`. Die zurückgegebene ID hilft internen Teams bei der Fehlerbehebung und Support-Problemen. (AAM-20824)

## Version 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

August 2015

* Ein Fehler wurde behoben, um zu verhindern, dass der ID-Dienst ein iframe anfordert, wenn keine zu synchronisierenden oder auszulösenden Daten vorhanden sind. (AAM-20164)
* Ein Fehler wurde behoben, durch den der ID-Dienst mehrteilige Top-Level-Domain-Cookies nicht ordnungsgemäß setzte. Wenn Sie beispielsweise eine Domain wie `my_company.co.uk` haben, würde der ID-Dienst unter bestimmten Umständen ein Cookie nur in `co.uk` setzen. (AN-104683)

  Dies betraf nur einige Clients, die *alle* der folgenden Kriterien erfüllten:

   * Verwenden des ID-Diensts.
   * Aktivierung einer [Schonfrist ](../reference/analytics-reference/grace-period.md)*oder* Verwendung von Cookies von Erstanbietern und Benutzer blockieren Cookies von Drittanbietern.

   * Besitz von Seiten mit mehrteiligen Top-Level-Domains.

Dokumentationsüberarbeitungen in dieser Version umfassen:

* [API-Methoden und Codebibliothek](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Reorganisierter Inhalt und Text. In den meisten Fällen erhält jede Methode eine eigene Seite.
* [Anforderungen für den Experience Cloud Identity Service](../reference/requirements.md): Überarbeiteter Inhalt und neu organisierter Text.

## Version 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Juli 2015

Der [!DNL Experience Cloud] ID-Dienst unterstützt mehrere IDs und Authentifizierungsstatus. Diese Änderung macht zudem die veraltete Unterstützung von [!DNL Audience Manager]-DPID-Zuordnungen zu Benutzern überflüssig, die von der `setCustomerIDs` Funktion verwendet wurden. Siehe [Kunden-IDs und Authentifizierungsstatus](../reference/authenticated-state.md).

## Version 1.4 {#section-f5c596f355b14da28f45c798df513572}

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

## Version 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

Februar 2015

Die Verarbeitung des Timeouts bei Anforderungen für AAM Blob und Location Hint wurde korrigiert. Bei einem Timeout bleiben diese Felder nun für die aktuelle Seite korrekt leer, und es werden alle Callbacks ausgeführt. Die Zeitüberschreitung wird als Fehlerbedingung behandelt, daher wird es auf der nächsten Seite erneut versucht. (AN-94473, AN-94474)

## Version 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Januar 2015

Überarbeitete `<head>/<body>` Tag-Suche für JSONP-Request `<script>` Tag-Container, sowie die Erstellung des `<script>`-Tags zur Berücksichtigung verschiedener DOM-Implementierungen (HTML vs. XHTML) mit möglicherweise unterschiedlichen Groß-/Kleinschreibungseinstellungen. (AN-9355)
