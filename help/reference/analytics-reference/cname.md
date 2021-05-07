---
description: Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).
keywords: Reihenfolge der Vorgänge, ID-Dienst
seo-description: Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).
seo-title: Übersicht zur CNAME-Implementierung
title: Übersicht zur CNAME-Implementierung
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 28%

---


# Übersicht zur CNAME-Implementierung{#cname-implementation-overview}

Mit CNAME-Implementierungen können Sie die von der Adobe verwendete Erfassungsdomäne so anpassen, dass sie mit Ihrer eigenen Domäne übereinstimmt. Dadurch kann Adobe Erstanbieter-Cookies auf dem Server anstatt auf dem Client mithilfe von JavaScript einstellen. Bisher waren diese serverseitigen Erstanbieter-Cookies keinen Beschränkungen unterworfen, die gemäß der ITP-Richtlinie (Intelligent Tracking Prevention) von Apple vorgeschrieben wurden. Im November 2020 wurden ihre Richtlinien jedoch von [!DNL Apple] aktualisiert, sodass diese Einschränkungen auch auf Cookies angewendet wurden, die über CNAME eingestellt wurden. Zurzeit sind beide Cookies, die auf der Serverseite über CNAME gesetzt werden, und Cookies, die auf der Clientseite über JavaScript gesetzt werden, unter ITP auf einen Ablauf von sieben Tagen oder 24 Stunden beschränkt. Weitere Informationen zur ITP-Richtlinie finden Sie in diesem [!DNL Apple] Dokument [zur Verfolgungsverhütung](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Während eine CNAME-Implementierung keine Vorteile hinsichtlich der Cookie-Lebensdauer bietet, gibt es möglicherweise einige weitere Vorteile wie Anzeigenblocker und weniger häufige Browser, die verhindern, dass Daten an Domänen gesendet werden, die sie als Tracker klassifizieren. In diesen Fällen kann die Verwendung eines CNAME-Eintrags verhindern, dass die Datenerfassung für Benutzer, die diese Tools verwenden, unterbrochen wird.