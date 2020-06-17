---
title: Identifizieren von Unique Visitors
description: Dokumentation für Adobe ECID (ID-Dienst)
translation-type: ht
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: ht
source-wordcount: '234'
ht-degree: 100%

---


# Identifizieren von Unique Visitors

Die Methode zur Identifizierung von Unique Visitors in unterschiedlichen Kontexten beinhaltet eine priorisierte Sequenz, um eine exakte Bestimmung zu gewährleisten. Die folgende Tabelle zeigt diese priorisierte Sequenz:

| Verwendete Reihenfolge | Abfrageparameter (Erfassungsmethode) | Spaltenwert post_visid_type | Vorhanden, wenn |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/de-DE/analytics/components/metrics/unique-visitors.translate.html)  | 0  | `s.visitorID` festgelegt ist. |
|  2  | aid  [s_vi cookie](https://docs.adobe.com/content/help/de-DE/analytics/components/metrics/unique-visitors.translate.html)  | 3  | der Besucher über vorhandenes s_vi-Cookie verfügt, bevor Sie den Besucher-ID-Dienst bereitgestellt haben, oder wenn Sie eine [Schonfrist](https://docs.adobe.com/content/help/de-DE/id-service/using/reference/analytics-reference/grace-period.html) für die Besucher-ID konfiguriert haben.  |
|  3  | mid [Cookie AMCV_ von Identitätsdienst festgelegt](https://docs.adobe.com/content/help/de-DE/id-service/using/home.html)  |  5  |  der Browser des Besuchers Cookies (Erstanbieter) akzeptiert und der [!UICONTROL Identitätsdienst] bereitgestellt wird.  |
|  4  | fid [Fallbackcookie für H.25.3 oder höher oder AppMeasurement für JavaScript](https://docs.adobe.com/content/help/de-DE/analytics/components/metrics/unique-visitors.translate.html)  |  4  |  der Browser des Besuchers Cookies (von Erstanbietern) akzeptiert.  |
|  5  |  [HTTP-Kopfzeile für Mobilteilnehmer](https://docs.adobe.com/content/help/de-DE/analytics/components/metrics/unique-visitors.translate.html)  |  2  |  das Gerät als Mobilgerät erkannt wird.  |
|  6  |  [IP-Adresse, Benutzer-Agent, Gateway-IP-Adresse](https://docs.adobe.com/content/help/de-DE/analytics/components/metrics/unique-visitors.translate.html)  |  1  |  der Browser des Besuchers keine Cookies akzeptiert. |

Informationen zur Berichterstattung über Unique Visitors finden Sie unter [Unique Visitors in Analytics](https://docs.adobe.com/content/help/de-DE/analytics/components/metrics/unique-visitors.translate.html).
