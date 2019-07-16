---
description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bei der Verwendung von anderen Experience Cloud-Lösungen mit dem ID-Dienst.
keywords: ID-Dienst
seo-description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bei der Verwendung von anderen Experience Cloud-Lösungen mit dem ID-Dienst.
seo-title: Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen
title: Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen{#faqs-for-other-experience-cloud-solutions}

Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bei der Verwendung von anderen Experience Cloud-Lösungen mit dem ID-Dienst.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Kann der Besucher-ID-Dienst mit Dynamic Tag Management bereitgestellt werden?**

Ja, dies ist die bevorzugte und empfohlene Implementierungsoption.

Siehe [Standardimplementierung mit DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics und Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Wird der Besuchverlauf eines Benutzers exportiert,[!DNL Adobe Analytics]nachdem[!DNL Audience Manager]ich den Experience Platform Identity Service implementiert habe?**

Hierbei gibt es zwei Möglichkeiten:

* Wenn für den Besucher eine Besuchsaktivität nach der Implementierung des ID-Diensts festgestellt wird, dann werden der Besucher und der jeweilige Verlauf in den Datenexport für [!DNL Audience Manager] aufgenommen.
* Wenn für den Besucher keine Besuchsaktivität nach der Implementierung des ID-Diensts festgestellt wird, dann werden der Besucher und der jeweilige Verlauf nicht in den Datenexport für Audience Manager aufgenommen. Ohne neue Aktivität gibt es keine Möglichkeit, die Analytics-ID der Experience Cloud ID zuzuordnen.

