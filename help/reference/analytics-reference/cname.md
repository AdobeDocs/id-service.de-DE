---
description: Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).
keywords: Reihenfolge der Vorgänge, ID-Dienst
title: CNAME-Implementierung – Übersicht
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: d2586fc722be25df1b82caaf2cc6de6a2a6c31bf
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 100%

---

# CNAME-Implementierung – Übersicht {#cname-implementation-overview}

Mit der CNAME-Implementierungen können Sie die von Adobe verwendete Sammel-Domain so anpassen, dass sie mit Ihrer eigenen Domain übereinstimmt. Diese Domains werden auch als Erstanbieter-Erfassungs-Domains bezeichnet. Diese Implementierungen ermöglichen es Adobe, Erstanbieter-Cookies Server-seitig und nicht Client-seitig mit JavaScript zu setzen. In der Vergangenheit waren diese Server-seitigen First-Party-Cookies nicht den Einschränkungen unterworfen, die mit der ITP-Richtlinie (Intelligent Tracking Prevention) von Apple eingeführt wurden. Im November 2020 aktualisierte [!DNL Apple] jedoch diese Richtlinie, sodass diese Einschränkungen jetzt auch auf Cookies angewendet werden, die über CNAME gesetzt werden. Zurzeit sind sowohl Cookies, die auf der Server-Seite über CNAME gesetzt werden, als auch Cookies, die auf der Client-Seite über JavaScript gesetzt werden, gemäß der ITP-Richtlinie auf die Gültigkeitsdauer von sieben Tagen bzw. 24 Stunden beschränkt. Weitere Informationen zur ITP-Richtlinie finden Sie in diesem [!DNL Apple] Dokument [zur Tracking-Vermeidung](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Auch wenn eine CNAME-Implementierung keine Vorteile hinsichtlich der Cookie-Lebensdauer bietet, kann sie andere Vorteile haben. Zu den Vorteilen gehört die Umgehung der Funktionen von Ad-Blockern und selten verwendeten Browser, die keine Daten an Domains senden, die sie als Tracker klassifizieren. In diesen Fällen kann die Verwendung eines CNAME-Eintrags verhindern, dass Ihre Datenerfassung bei Benutzern unterbunden wird, die diese Tools verwenden.

Darüber hinaus können Sie bei CNAME-Implementierungen einen [benutzerdefinierten RDC-Typ auswählen](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=de), der steuert, wohin die Treffer der Benutzer zunächst weitergeleitet werden. Die meisten Kunden verwenden keine benutzerdefinierten RDC-Typen.
