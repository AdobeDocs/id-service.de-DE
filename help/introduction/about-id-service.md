---
description: Die Rolle des Besucher-ID-Service in Adobe CX Enterprise.
keywords: Besucher-ID-Service
title: Überblick
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
TQID: https://experienceleague.adobe.com/YUy7gs28-5lGzLmfE-MJ4nRtQc7I05Q4nRCBO4gOdMI
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 29%

---

# Über den Besucher-ID-Service{#aboutidservice}

Die Rolle des Besucher-ID-Service in Adobe CX Enterprise.

<!--
mcvid-functionality.xml
-->

## Der Besucher-ID-Service: Ein Grundelement der Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Der Besucher-ID-Dienst ermöglicht das allgemeine Identifizierungs-Framework für die Core Services von CX Enterprise, Lösungen sowie Kundenattribute und Zielgruppen. Der ID-Service funktioniert durch die Zuweisung einer eindeutigen, dauerhaften ID zu einem Site-Besucher. Wenn Ihr Unternehmen den Besucher-ID-Service implementiert, können Sie mit dieser ID denselben Site-Besucher und dessen Daten in verschiedenen CX Enterprise-Lösungen identifizieren.

![](assets/ecid-new.png)

Außerdem kann der Besucher-ID-Service die verschiedenen lösungsspezifischen IDs (z. B. Analytics-AID) ersetzen. Mit der Funktion [Kunden-IDs und Authentifizierungsstatus](../reference/authenticated-state.md) ermöglicht es Ihnen der Besucher-ID-Service, eigene Kunden-IDs an CX Enterprise zu übergeben. Beachten Sie jedoch, dass der Besucher-ID-Dienst nur mit den Lösungen funktioniert, die Sie bereits abonniert haben. Er bietet keinen Zugriff auf andere Produkte, wenn Sie nicht für sie angemeldet sind.

Künftig ist der Besucher-ID-Service eine integrale Komponente vieler aktueller und künftiger CX Enterprise-Funktionen, -Erweiterungen und -Services. Der Besucher-ID-Service unterstützt derzeit [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Außerdem ist er erforderlich, wenn Sie sich an der Adobe Device Co-op beteiligen möchten. Wenn Sie den Besucher-ID-Service nicht implementiert haben, ist es jetzt an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen.

## Funktionszusammenfassung {#section-96555473455c4bf8924c2d56ff4f3255}

Zusammenfassend lässt sich sagen, dass der Besucher-ID-Dienst:

* Er erstellt einen gemeinsamen Schlüssel oder eine gemeinsame ID, die zum Verknüpfen von Profilen und Identitäten verwendet werden kann.
* Er identifiziert ein Gerät eindeutig in mehreren Lösungen.
* Setzt ein First-Party-Cookie in der Domain des Kunden, um das Tracking auf derselben Domain sicherzustellen. Siehe [Cookies und der Besucher-ID-Dienst](../introduction/cookies.md).
* Erhält Aliase und ID-Zuordnungen von Kunden und Partnern von CX Enterprise.
* Verwaltet die ID-Synchronisierung innerhalb von CX Enterprise.
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.

