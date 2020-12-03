---
description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bei der Verwendung von anderen Experience Cloud-Lösungen mit dem ID-Dienst.
keywords: ID Service
seo-description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bei der Verwendung von anderen Experience Cloud-Lösungen mit dem ID-Dienst.
seo-title: Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen
title: Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 63%

---


# Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen{#faqs-for-other-experience-cloud-solutions}

Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bei der Verwendung von anderen Experience Cloud-Lösungen mit dem ID-Dienst.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Kann ich das dynamische Tag-Management verwenden, um den Besucher-ID-Dienst bereitzustellen?**

Ja, dies ist die bevorzugte und empfohlene Bereitstellungsoption.

See [Standard Implementation with DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics und Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Wird der Besuchsverlauf eines Benutzers aus [!DNL Adobe Analytics] in den Export für [!DNL Audience Manager] aufgenommen, nachdem ich den Experience Cloud Identity-Dienst implementiert habe?**

Hierbei gibt es zwei Möglichkeiten:

* Wenn für den Besucher eine Besuchsaktivität nach der Implementierung des ID-Diensts festgestellt wird, dann werden der Besucher und der jeweilige Verlauf in den Datenexport für [!DNL Audience Manager] aufgenommen.
* Verfügt ein Benutzer nach der Implementierung des ID-Diensts über keine Aktivität zum Besuch, werden der Besucher und sein Verlauf nicht in den Datenexport nach Audience Manager einbezogen. Da keine neue Aktivität vorhanden ist, können wir die Analytics-ID nicht mit der Experience Cloud-ID verknüpfen.

