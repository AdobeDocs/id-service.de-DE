---
description: Bei manchen Implementierungen werden Besucher-IDs von JavaScript an einen Server übergeben, sodass vom Server weitere Analytics-Ereignisse (z. B. ein Kauf) gesendet werden können.
keywords: ID-Dienst
seo-description: Bei manchen Implementierungen werden Besucher-IDs von JavaScript an einen Server übergeben, sodass vom Server weitere Analytics-Ereignisse (z. B. ein Kauf) gesendet werden können.
seo-title: Serverseitige Implementierung zusammen mit JavaScript
title: Serverseitige Implementierung zusammen mit JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Serverseitige Implementierung zusammen mit JavaScript {#server-side-implementation-mixed-with-javascript}

Bei manchen Implementierungen werden Besucher-IDs von JavaScript an einen Server übergeben, sodass vom Server weitere Analytics-Ereignisse (z. B. ein Kauf) gesendet werden können.

Die ID-Dienst-API stellt die Methoden [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md) und [getAnalyticsVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md) für den Abruf der ID-Werte bereit, die dann an den Server übergeben werden können.

Stellen Sie sicher, dass sowohl die Experience Cloud-Besucher-ID als auch die Analytics-Besucher-ID vorliegt und beide IDs (sofern vorhanden) gesendet werden, damit alle gesendeten Daten dem bestehenden Analytics-Besucherprofil zugeordnet werden.

>[!IMPORTANT]
>
>AppMeasurement for Java unterstützt den Experience Cloud ID-Dienst derzeit nicht.

## Dateneinfüge-API {#section-955ce7664a4646d38b3005cb2df40baf}

Schließen Sie die Analytics-Besucher-ID (sofern festgelegt) in das Element `<visitorID>` ein.

Schließen Sie die Experience Cloud-Besucher-ID in das Element `<marketingCloudVisitorID>` ein.

Siehe [Supported XML Tags](https://marketing.adobe.com/developer/de_DE/documentation/data-insertion/r-supported-tags).

## AppMeasurement für Java {#section-d664b94934924d048300d9c2b6560085}

Der Experience Cloud ID-Dienst wird von AppMeasurement für Java derzeit nicht unterstützt.
