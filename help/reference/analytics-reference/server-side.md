---
description: Bei manchen Implementierungen werden Besucher-IDs von JavaScript an einen Server übergeben, sodass vom Server weitere Analytics-Ereignisse (z. B. ein Kauf) gesendet werden können.
keywords: ID-Dienst
title: Serverseitige Implementierung zusammen mit JavaScript
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# Serverseitige Implementierung zusammen mit JavaScript {#server-side-implementation-mixed-with-javascript}

Bei manchen Implementierungen werden Besucher-IDs von JavaScript an einen Server übergeben, sodass vom Server weitere Analytics-Ereignisse (z. B. ein Kauf) gesendet werden können.

Die ID-Dienst-API stellt die Methoden [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) und [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) bereit, um die ID-Werte abzurufen, die dann an den Server übergeben werden können.

Stellen Sie sicher, dass sowohl die Experience Cloud-Besucher-ID als auch die Analytics-Besucher-ID vorliegt und beide IDs (sofern vorhanden) gesendet werden, damit alle gesendeten Daten dem bestehenden Analytics-Besucherprofil zugeordnet werden.

>[!IMPORTANT]
>
>AppMeasurement for Java unterstützt den Experience Cloud Identity Service derzeit nicht.

## Dateneinfüge-API {#section-955ce7664a4646d38b3005cb2df40baf}

Schließen Sie die Analytics-Besucher-ID (sofern festgelegt) in das Element `<visitorID>` ein.

Schließen Sie die Experience Cloud-Besucher-ID in das Element `<marketingCloudVisitorID>` ein.

Siehe [Unterstützte XML-Tags](https://developer.adobe.com/).

## AppMeasurement für Java {#section-d664b94934924d048300d9c2b6560085}

Der Experience Cloud Identity Service wird von AppMeasurement für Java derzeit nicht unterstützt.
