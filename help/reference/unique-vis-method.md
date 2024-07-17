---
title: Identifizieren von Unique Visitors
description: Dokumentation für Adobe ECID (ID-Dienst)
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
source-git-commit: c65816530ae2269b216f60b9b0450077e5aaac2f
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 100%

---

# Identifizieren von Unique Visitors

Die Methode zur Identifizierung von Unique Visitors in unterschiedlichen Kontexten beinhaltet eine priorisierte Sequenz, um eine exakte Bestimmung zu gewährleisten. Die folgende Tabelle zeigt diese priorisierte Sequenz:

| Verwendete Reihenfolge | Abfrageparameter (Erfassungsmethode) | Spaltenwert post_visid_type | Vorhanden, wenn |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=de)  | 0  | `s.visitorID` festgelegt ist. |
|  2  | aid  [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=de#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | der Besucher über vorhandenes s_vi-Cookie verfügt, bevor Sie den Besucher-ID-Dienst bereitgestellt haben, oder wenn Sie eine [Schonfrist](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=de) für die Besucher-ID konfiguriert haben.  |
|  3  | mid [Cookie AMCV_ von Identitätsdienst festgelegt](../introduction/cookies.md)  |  5  |  Der Browser des Besuchers akzeptiert Cookies (Erstanbieter), und der [!DNL Identity Service] wird bereitgestellt.  |
|  4  | fid [Fallbackcookie für H.25.3 oder höher oder AppMeasurement für JavaScript](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=de#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  der Browser des Besuchers Cookies (von Erstanbietern) akzeptiert.  |
|  5  |  [HTTP-Kopfzeile für Mobilteilnehmer](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=de)  |  2  |  das Gerät als Mobilgerät erkannt wird.  |
|  6  |  [IP-Adresse, Benutzer-Agent, Gateway-IP-Adresse](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=de)  |  1  |  der Browser des Besuchers keine Cookies akzeptiert. |

{style="table-layout:auto"}

Informationen zur Berichterstattung über Unique Visitors finden Sie unter [Unique Visitors in Analytics](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=de).
