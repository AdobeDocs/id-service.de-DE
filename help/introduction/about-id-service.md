---
description: Die Rolle des Experience Cloud Identity Service in Adobe Experience Cloud.
keywords: ID-Service
title: Übersicht
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: tm+mt
source-wordcount: '301'
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
* Er legt ein Erstanbieter-Cookie in der Domain des Kunden fest, um sicherzustellen, dass die Verfolgung in derselben Domain erfolgt. Weitere Informationen finden Sie unter [Experience Cloud](../introduction/cookies.md).
* Erhalten von Aliasen und ID-Zuordnungen von [!DNL Experience Cloud]-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der [!DNL Experience Cloud].
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.
