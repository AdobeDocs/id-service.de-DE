---
title: Identifizieren von Unique Visitors
description: Dokumentation für Adobe ECID (ID-Dienst).
translation-type: tm+mt
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 66%

---


# Identifizieren von Unique Visitors

Die Methode zur Identifizierung von Unique Visitors in unterschiedlichen Kontexten beinhaltet eine priorisierte Sequenz, um eine exakte Bestimmung zu gewährleisten. Die folgende Tabelle zeigt diese priorisierte Sequenz:

| Verwendete Reihenfolge | Abfrage-Parameter (Erfassungsmethode) | Spaltenwert post_visid_type | Vorhanden, wenn |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` festgelegt ist. |
|  2  | aid  [s_vi cookie](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html)  | 3  | der Besucher über vorhandenes s_vi-Cookie verfügt, bevor Sie den Besucher-ID-Dienst bereitgestellt haben, oder wenn Sie eine [Schonfrist](https://docs.adobe.com/content/help/de-DE/id-service/using/reference/analytics-reference/grace-period.html) für die Besucher-ID konfiguriert haben.  |
|  3  | mid-[AMCV_-Cookie vom Identitätsdienst eingestellt](https://docs.adobe.com/content/help/de-DE/id-service/using/home.html)  |  5  |  Der Browser des Besuchers akzeptiert Cookies (Erstanbieter) und der[!UICONTROL Identitätsdienst]wird bereitgestellt.  |
|  4  | fid [fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html)  |  4  |  Besuchers Browser akzeptiert Cookies (Erstanbieter).  |
|  5  |  [HTTP-Kopfzeile für Mobilteilnehmer](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html)  |  2  |  Das Gerät wird als Mobilgerät erkannt.  |
|  6  |  [IP Address, User Agent, Gateway IP Address](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html)  |  1  |  Besuchers Browser akzeptiert keine Cookies. |

Informationen zur Berichterstattung über Unique Visitors finden Sie unter [Unique Visitors in Analytics](https://docs.adobe.com/content/help/de-DE/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
