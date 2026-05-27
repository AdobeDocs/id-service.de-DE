---
description: Die Rolle des Experience Cloud Identity Service in Adobe Experience Cloud.
keywords: ID-Service
title: Überblick
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
TQID: https://experienceleague.adobe.com/YUy7gs28-5lGzLmfE-MJ4nRtQc7I05Q4nRCBO4gOdMI
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 321
ht-degree: 100%

---

# Über den ID-Dienst{#aboutidservice}

Die Rolle des Experience Cloud Identity Services in Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Der Experience Cloud Identity Service: Ein Grundelement der Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Mit dem Experience Cloud Identity Service werden das allgemeine Identifizierungs-Framework für die Experience Cloud Core Services, Lösungen sowie benutzerdefinierte Attribute und Zielgruppen ermöglicht. Der ID-Service funktioniert durch die Zuweisung einer eindeutigen, dauerhaften ID zu einem Site-Besucher. Wenn Ihr Unternehmen den ID-Service implementiert, können Sie mit dieser ID denselben Site-Besucher und dessen Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid-new.png)

Darüber hinaus kann der ID-Service die verschiedenen lösungsspezifischen IDs (beispielsweise Analytics-AID) ersetzen. Mit der Funktion [Kunden-IDs und Authentifizierungsstatus](../reference/authenticated-state.md) ermöglicht es Ihnen der ID-Service, eigene Kunden-IDs an [!DNL Experience Cloud] zu übergeben. Beachten Sie jedoch, dass der ID-Service nur mit den Lösungen funktioniert, die Sie bereits abonniert haben. Er bietet keinen Zugriff auf andere Produkte, wenn Sie nicht für sie angemeldet sind.

Künftig ist der ID-Service eine integrale Komponente von vielen aktuellen und künftigen [!DNL Experience Cloud]-Features, -Erweiterungen und -Services. Der ID-Service unterstützt derzeit [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der [!DNL Adobe Experience Cloud]-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Service nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen.

## Funktionszusammenfassung {#section-96555473455c4bf8924c2d56ff4f3255}

Zusammenfassend leistet der ID-Service Folgendes:

* Er erstellt einen gemeinsamen Schlüssel oder eine gemeinsame ID, die zum Verknüpfen von Profilen und Identitäten verwendet werden kann.
* Er identifiziert ein Gerät eindeutig in mehreren Lösungen.
* Setzt ein First-Party-Cookie in der Domain des Kunden, um das Tracking auf derselben Domain sicherzustellen. Weitere Informationen finden Sie unter [Experience Cloud](../introduction/cookies.md).
* Erhalten von Aliasen und ID-Zuordnungen von [!DNL Experience Cloud]-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der [!DNL Experience Cloud].
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.

