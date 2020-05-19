---
title: Identifizieren von Unique Visitors
description: Dokumentation für Adobe ECID (ID-Dienst).
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '223'
ht-degree: 100%

---


# Identifizieren von Unique Visitors

Die Methode zur Identifizierung von Unique Visitors in unterschiedlichen Kontexten beinhaltet eine priorisierte Sequenz, um eine exakte Bestimmung zu gewährleisten. Die folgende Tabelle zeigt diese priorisierte Sequenz:
 
| Verwendete Reihenfolge | Abfrageparameter (Erfassungsmethode) | Spaltenwert post_visid_type | Vorhanden, wenn |
|--- |--- |--- |--- |
| 1 | [vid (s.visitorID)](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html) | 0 |s.visitorID festgelegt ist.|
| 2 | [aid (s_vi cookie)](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html) | 3 |der Besucher über vorhandenes s_vi-Cookie verfügt, bevor Sie den Besucher-ID-Dienst bereitgestellt haben, oder wenn Sie eine [Schonfrist](https://docs.adobe.com/content/help/de-DE/id-service/using/reference/analytics-reference/grace-period.html) für die Besucher-ID konfiguriert haben. |
| 3 | [mid (vom Identitätsdienst gesetztes AMCV_-Cookie)](https://docs.adobe.com/content/help/de-DE/id-service/using/home.html) | 5 | Der Browser des Besuchers akzeptiert Cookies (Erstanbieter) und der Identitätsdienst wird bereitgestellt. |
| 4 | [fid (Fallback-Cookie auf H.25.3 oder höher oder AppMeasurement für JavaScript)](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html) | 4 | Der Browser des Besuchers akzeptiert Cookies (Erstanbieter). |
| 5 | [HTTP-Header für Mobilgerät](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html) | 2 | Gerät wird als Mobilgerät erkannt. |
| 6 | [IP-Adresse, User Agent, Gateway-IP-Adresse](https://docs.adobe.com/content/help/de-DE/analytics/technotes/visitor-identification.html) | 1 | Browser des Besuchers akzeptiert keine Cookies. |

Informationen zur Berichterstattung über Unique Visitors finden Sie unter [Unique Visitors in Analytics](https://docs.adobe.com/content/help/de-DE/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html).
