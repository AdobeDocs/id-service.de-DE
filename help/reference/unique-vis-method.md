---
title: Identifizieren von Unique Visitors
description: Dokumentation für Adobe ECID (ID-Dienst)
translation-type: tm+mt
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# Identifizieren von Unique Visitors

Die Methode zur Identifizierung individueller Besucher unter mehreren Kontexten umfasst eine priorisierte Sequenz, um die Genauigkeit bei dieser Bestimmung sicherzustellen. Die folgende Tabelle zeigt diese Reihenfolge mit Prioritäten:


 
| Verwendete Bestellung| Abfrageparameter (Erfassungsmethode)| Spaltenwert post_visid_type| Vorhanden, wenn ||—|—|—|— || 1 |[vid (s.visitorID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html)| 0 | s.visitorID eingestellt.| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html) configured. || 3 |[mid (AMCV_ cookie set by Identity Service)](https://marketing.adobe.com/resources/help/en_US/mcvid/)| 5 | Der Browser des Besuchers akzeptiert Cookies (Erstanbieter) und der Identitätsdienst wird bereitgestellt. || 4 |[fid (Ausweichcookie auf H.25.3 oder höher oder AppMeasurement für JavaScript)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 4 | Der Browser des Besuchers akzeptiert Cookies (Erstanbieter). || 5 |[HTTP Mobile Subscriber header](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html)| 2 | Gerät wird als Mobilgerät erkannt. || 6 |[IP Address, User Agent, Gateway IP Address](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 1 | Browser des Besuchers akzeptiert keine Cookies. |


Informationen zur Berichterstattung über individuelle Besucher finden Sie unter [Unique Visitors in Analytics](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
