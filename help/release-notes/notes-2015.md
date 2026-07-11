---
description: Versionshinweise und Aktualisierungen für das Jahr 2015
keywords: Besucher-ID-Service
title: Versionshinweise für 2015
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
TQID: https://experienceleague.adobe.com/WmeSY7aRbvnZJN0a-lNR-yYzWzF4dfJLPZqA--6lpYQ
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 454
ht-degree: 61%

---

# Versionshinweise für 2015 {#release-notes}

Versionshinweise und Aktualisierungen für das Jahr 2015

## Version 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

November 2015

Der Children&#39;s Online Privacy Protection Act (COPPA) verbietet die Online-Erfassung personenbezogener Daten von Kindern unter 13 Jahren ohne nachprüfbare elterliche Zustimmung. Kunden, die Bedenken im Hinblick auf COPPA haben, können ihrem Besucher-ID-Dienst-Code eine optionale Variable hinzufügen, die verhindert, dass Cookies in der Drittanbieterdomäne eines Browsers gesetzt werden. Siehe [COPPA-Unterstützung im Besucher-ID-Service](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413). Nur bei Version 1.5.3 oder neuer.

## Version 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

September 2015

* Es wurde ein Fehler im Safari-Browser behoben, durch den Synchronisierungsdienste nicht funktionierten, wenn Benutzer Drittanbieter-Cookies blockierten. (AAM-20764)
* Aufrufe des Besucher-ID-Service enthalten jetzt die Versions-ID im `d_visid_ver=`. Die zurückgegebene ID hilft internen Teams bei der Fehlerbehebung und Support-Problemen. (AAM-20824)

## Version 1.5.1 {#section-f4309d7917964a748fee4bdb45bffa44}

August 2015

* Es wurde ein Fehler behoben, der verhinderte, dass der Besucher-ID-Dienst einen iframe anforderte, wenn keine zu synchronisierenden oder auszulösenden Daten vorhanden waren. (AAM-20164)
* Es wurde ein Fehler behoben, durch den der Besucher-ID-Dienst ein mehrteiliges Domain-Cookie der obersten Ebene nicht ordnungsgemäß setzen konnte. Wenn Sie beispielsweise eine Domain wie `my_company.co.uk` haben, würde der Besucher-ID-Dienst unter bestimmten Umständen ein Cookie nur in `co.uk` setzen. (AN-104683)

  Dies betraf nur einige Clients, die *alle* der folgenden Kriterien erfüllten:

   * Verwenden des Besucher-ID-Service.
   * Eine [Übergangsphase](https://experienceleague.adobe.com/en/docs/analytics/implementation/id/migration) *oder* wurde aktiviert, da Erstanbieter-Cookies verwendet und Benutzer Drittanbieter-Cookies blockieren.
   * Besitz von Seiten mit mehrteiligen Top-Level-Domains.

Dokumentationsüberarbeitungen in dieser Version umfassen:

* [API-Methoden und Codebibliothek](../library/library.md#concept-ff27497375644a898d47984aefb21c97): Reorganisierter Inhalt und Text. In den meisten Fällen erhält jede Methode eine eigene Seite.
* [Anforderungen für den Besucher-ID-](../reference/requirements.md): Überarbeiteter Inhalt und neu organisierter Text.

## Version 1.5 {#section-db5edfa11ae143ada07a96e0ab06dc57}

Juli 2015

Der Besucher-ID-Dienst unterstützt mehrere IDs und Authentifizierungsstatus. Durch diese Änderung wird auch die veraltete Unterstützung für Audience Manager DPID-Zuordnungen zu Benutzer-IDs entfernt, die von der `setCustomerIDs` verwendet werden. Siehe [Kunden-IDs und Authentifizierungsstatus](../reference/authenticated-state.md).

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

## Version 1.3.5 {#section-eed4567f058f446d9a819e4682621aed}

Februar 2015

Die Verarbeitung des Timeouts bei Anforderungen für AAM Blob und Location Hint wurde korrigiert. Bei einem Timeout bleiben diese Felder nun für die aktuelle Seite korrekt leer, und es werden alle Callbacks ausgeführt. Die Zeitüberschreitung wird als Fehlerbedingung behandelt, daher wird es auf der nächsten Seite erneut versucht. (AN-94473, AN-94474)

## Version 1.3.4 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

Januar 2015

Überarbeitete `<head>/<body>` Tag-Suche für JSONP-Request `<script>` Tag-Container, sowie die Erstellung des `<script>`-Tags zur Berücksichtigung verschiedener DOM-Implementierungen (HTML vs. XHTML) mit möglicherweise unterschiedlichen Groß-/Kleinschreibungseinstellungen. (AN-9355)

