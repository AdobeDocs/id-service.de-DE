---
description: Bei manchen Implementierungen werden Besucher-IDs von JavaScript an einen Server übergeben, sodass vom Server weitere Analytics-Ereignisse (z. B. ein Kauf) gesendet werden können.
keywords: ID Service
seo-description: Bei manchen Implementierungen werden Besucher-IDs von JavaScript an einen Server übergeben, sodass vom Server weitere Analytics-Ereignisse (z. B. ein Kauf) gesendet werden können.
seo-title: Serverseitige Implementierung zusammen mit JavaScript
title: Serverseitige Implementierung zusammen mit JavaScript
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 100%

---


# Serverseitige Implementierung zusammen mit JavaScript {#server-side-implementation-mixed-with-javascript}

Bei manchen Implementierungen werden Besucher-IDs von JavaScript an einen Server übergeben, sodass vom Server weitere Analytics-Ereignisse (z. B. ein Kauf) gesendet werden können.

Die ID-Dienst-API stellt die Methoden [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) und [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) bereit, um die ID-Werte abzurufen, die dann an den Server übergeben werden können.

Stellen Sie sicher, dass sowohl die Experience Cloud-Besucher-ID als auch die Analytics-Besucher-ID vorliegt und beide IDs (sofern vorhanden) gesendet werden, damit alle gesendeten Daten dem bestehenden Analytics-Besucherprofil zugeordnet werden.

>[!IMPORTANT]
>
>AppMeasurement for Java unterstützt den Experience Cloud Identity-Dienst derzeit nicht.

## Dateneinfüge-API {#section-955ce7664a4646d38b3005cb2df40baf}

Schließen Sie die Analytics-Besucher-ID (sofern festgelegt) in das Element `<visitorID>` ein.

Schließen Sie die Experience Cloud-Besucher-ID in das Element `<marketingCloudVisitorID>` ein.

Siehe [Unterstützte XML-Tags](https://www.adobe.io).

## AppMeasurement für Java {#section-d664b94934924d048300d9c2b6560085}

Der Experience Cloud Identity-Dienst wird von AppMeasurement für Java derzeit nicht unterstützt.
