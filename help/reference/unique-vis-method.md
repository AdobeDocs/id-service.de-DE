---
title: Identifizieren von Unique Visitors
description: Dokumentation für Adobe ECID (Besucher-ID-Service)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
TQID: https://experienceleague.adobe.com/1iZMkBA6-SnhhVmqp8qrFuk-Ev-tKOae5FAduivghXM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 249
ht-degree: 82%

---

# Identifizieren von Unique Visitors

Die Methode zur Identifizierung von Unique Visitors in unterschiedlichen Kontexten beinhaltet eine priorisierte Sequenz, um eine exakte Bestimmung zu gewährleisten. Die folgende Tabelle zeigt diese priorisierte Sequenz:

| Verwendete Reihenfolge | Abfrageparameter (Erfassungsmethode) | Spaltenwert post_visid_type | Vorhanden, wenn |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=de)  | 0  | `s.visitorID` festgelegt ist. |
|  2  | aid  [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=de#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | Der Besucher hatte ein vorhandenes s_vi-Cookie, bevor Sie den Besucher-ID-Dienst bereitgestellt haben, oder Sie haben eine Besucher-ID [Übergangsphase](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=de) konfiguriert.  |
|  3  | [AMCV_-Cookie, das vom Besucher-ID-Dienst gesetzt wird](../introduction/cookies.md)  |  5  |  Der Browser des Besuchers akzeptiert Cookies (Erstanbieter), und der Besucher-ID-Dienst wird bereitgestellt.  |
|  4  | fid [Fallbackcookie für H.25.3 oder höher oder AppMeasurement für JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=de#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  der Browser des Besuchers Cookies (von Erstanbietern) akzeptiert.  |
|  5  |  [HTTP-Kopfzeile für Mobilteilnehmer](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=de)  |  2  |  das Gerät als Mobilgerät erkannt wird.  |
|  6  |  [IP-Adresse, Benutzer-Agent, Gateway-IP-Adresse](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=de)  |  1  |  der Browser des Besuchers keine Cookies akzeptiert. |

{style="table-layout:auto"}

Informationen zur Berichterstattung über Unique Visitors finden Sie unter [Unique Visitors in Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=de).

