---
description: Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bei der Verwendung von anderen Experience Cloud-Lösungen mit dem ID-Dienst.
keywords: ID-Dienst
title: Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---

# Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen {#faqs-for-other-experience-cloud-solutions}

Häufig gestellte Fragen zu den Funktionen, der Funktionalität und den Problemen bei der Verwendung von anderen Experience Cloud-Lösungen mit dem ID-Dienst.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**Kann ich das Dynamic Tag Management verwenden, um den Besucher-ID-Dienst bereitzustellen?**

Ja, dies ist die bevorzugte und empfohlene Implementierungsoption.

Siehe [Standardimplementierung mit DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics und Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**Wird der Besuchsverlauf eines Benutzers aus [!DNL Adobe Analytics] in den Export für [!DNL Audience Manager] aufgenommen, nachdem ich den Experience Cloud Identity-Dienst implementiert habe?**

Hierbei gibt es zwei Möglichkeiten:

* Wenn für den Besucher eine Besuchsaktivität nach der Implementierung des ID-Diensts festgestellt wird, dann werden der Besucher und der jeweilige Verlauf in den Datenexport für [!DNL Audience Manager] aufgenommen.
* Weist ein Benutzer nach der Implementierung des ID-Diensts keine Besucheraktivität auf, werden der Besucher und sein Verlauf nicht in den Datenexport nach Audience Manager einbezogen. Da keine neue Aktivität vorhanden ist, kann die Analytics-ID nicht mit der Experience Cloud ID verknüpft werden.
