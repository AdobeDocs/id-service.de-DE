---
title: Identifizieren von Unique Visitors
description: Dokumentation für Adobe ECID (ID-Dienst).
translation-type: tm+mt
source-git-commit: dee27fb0150ce2c40f570f98b9af0b6904c16814

---


# Identifizieren von Unique Visitors

Die Methode zur Identifizierung von Unique Visitors in unterschiedlichen Kontexten beinhaltet eine priorisierte Sequenz, um eine exakte Bestimmung zu gewährleisten. Die folgende Tabelle zeigt diese priorisierte Sequenz:
 
| Verwendete Reihenfolge | Abfrageparameter (Erfassungsmethode) | Spaltenwert post_visid_type | Vorhanden, wenn |
|--- |--- |--- |--- |
| 1 | [vid (s.visitorID)](https://marketing.adobe.com/resources/help/de_DE/sc/implement/visid_custom.html) | 0 |s.visitorID festgelegt ist.|
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/de_DE/sc/implement/visid_analytics.html) | 3 |der Besucher über vorhandenes s_vi-Cookie verfügt, bevor Sie den Besucher-ID-Dienst bereitgestellt haben, oder wenn Sie eine [Schonfrist](https://marketing.adobe.com/resources/help/de_DE/mcvid/mcvid_grace_period.html) für die Besucher-ID konfiguriert haben. |
| 3 | [mid (vom Identitätsdienst gesetztes AMCV_-Cookie)](https://marketing.adobe.com/resources/help/de_DE/mcvid/) | 5 | Der Browser des Besuchers akzeptiert Cookies (Erstanbieter) und der Identitätsdienst wird bereitgestellt. |
| 4 | [fid (Fallback-Cookie auf H.25.3 oder höher oder AppMeasurement für JavaScript)](https://marketing.adobe.com/resources/help/de_DE/sc/implement/visid_fallback.html) | 4 | Der Browser des Besuchers akzeptiert Cookies (Erstanbieter). |
| 5 | [HTTP-Header für Mobilgerät](https://marketing.adobe.com/resources/help/de_DE/sc/implement/visid_mobile.html) | 2 | Gerät wird als Mobilgerät erkannt. |
| 6 | [IP-Adresse, User Agent, Gateway-IP-Adresse](https://marketing.adobe.com/resources/help/de_DE/sc/implement/visid_fallback.html) | 1 | Browser des Besuchers akzeptiert keine Cookies. |

Informationen zur Berichterstattung über Unique Visitors finden Sie unter [Unique Visitors in Analytics](https://docs.adobe.com/content/help/de-DE/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
