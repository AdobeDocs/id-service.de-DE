---
description: Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).
keywords: Reihenfolge der Vorgänge, ID-Dienst
title: CNAME-Implementierung – Übersicht
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 100%

---


# CNAME-Implementierung – Übersicht {#cname-implementation-overview}

Mit der CNAME-Implementierungen können Sie die von Adobe verwendete Sammel-Domain so anpassen, dass sie mit Ihrer eigenen Domain übereinstimmt. Dadurch kann Adobe First-Party-Cookies mithilfe von JavaScript Server-seitig anstatt Client-seitig setzen. In der Vergangenheit waren diese Server-seitigen First-Party-Cookies nicht den Einschränkungen unterworfen, die mit der ITP-Richtlinie (Intelligent Tracking Prevention) von Apple eingeführt wurden. Im November 2020 aktualisierte [!DNL Apple] jedoch diese Richtlinie, sodass diese Einschränkungen jetzt auch auf Cookies angewendet werden, die über CNAME gesetzt werden. Zurzeit sind sowohl Cookies, die auf der Server-Seite über CNAME gesetzt werden, als auch Cookies, die auf der Client-Seite über JavaScript gesetzt werden, gemäß der ITP-Richtlinie auf die Gültigkeitsdauer von sieben Tagen bzw. 24 Stunden beschränkt. Weitere Informationen zur ITP-Richtlinie finden Sie in diesem [!DNL Apple] Dokument [zur Tracking-Vermeidung](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Während eine CNAME-Implementierung keine Vorteile hinsichtlich der Cookie-Lebensdauer bietet, gibt es möglicherweise andere Vorteile wie bei Werbe-Blockern und weniger gängigen Browsern, die verhindern, dass Daten an Domains gesendet werden, die sie als Tracker klassifizieren. In diesen Fällen kann die Verwendung eines CNAME-Eintrags verhindern, dass Ihre Datenerfassung bei Benutzern unterbunden wird, die diese Tools verwenden.