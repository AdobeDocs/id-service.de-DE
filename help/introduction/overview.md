---
description: Die Rolle des Experience Cloud Identity Services in Adobe Experience Cloud.
title: Übersicht über den Experience Cloud Identity Service
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 36%

---

# Übersicht über den Experience Cloud Identity Service

Der Experience Cloud Identity-Dienst ermöglicht das allgemeine Identifizierungs-Framework für Experience Cloud Application Services. Sie können den Experience Cloud Identity-Dienst verwenden, um die [Experience Cloud-ID (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).

Die ECID ist ein freigegebener Identitäts-Namespace, der in allen Adobe Experience Platform- und Experience Cloud-Anwendungen verwendet wird, um das Besucherverhalten zu verfolgen und sicherzustellen, dass jedes Gerät über eine eindeutige ID verfügt, die sitzungsübergreifend bestehen kann.

>[!TIP]
>
>Der Experience Cloud Identity-Dienst, der Experience Platform Identity-Dienst und die ECID sind drei **distinct** -Entitäten.

Der Experience Cloud Identity-Dienst kann verschiedene anwendungsspezifische IDs ersetzen und die [Kunden-IDs und Authentifizierungsstatus](/help/reference/authenticated-state.md) -Funktion verwenden, damit Sie Ihre eigenen Kunden-IDs an das Experience Cloud übergeben können.

>[!NOTE]
>
>Der Experience Cloud Identity-Dienst funktioniert nur mit Experience Cloud Application Services, die Sie abonniert haben, und bietet keinen Zugriff auf andere Anwendungsdienste, wenn Sie diese noch nicht abonniert haben.

Experience Cloud Identity Service unterstützt die folgenden Anwendungen:

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen Experience Cloud-Features, -Erweiterungen und -Services. Der ID-Dienst unterstützt derzeit [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Wenn Sie den ID-Service nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen.

## Funktionszusammenfassung

Zusammenfassend hilft der Experience Cloud Identity-Dienst bei Folgendem:

* Identifiziert einen Besucher auf einem Gerät in mehreren Anwendungen eindeutig.
* Setzt ein First-Party-Cookie in der Domain des Kunden, um das Tracking auf derselben Domain sicherzustellen. Weitere Informationen finden Sie im Dokument zu [Cookies und Experience Cloud Identity Service](./cookies.md).
* Erhalten von Aliasen und ID-Zuordnungen von Experience Cloud-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der Experience Cloud.
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.

## Experience Cloud Identity Service-Anforderungen

Ihre Lösungsbibliotheken und andere Adoben-Codebibliotheken müssen [bestimmte Anforderungen](/help/reference/requirements.md) bevor Sie Identity Service verwenden können.

* [Cookies und der Experience Cloud Identity-Dienst](cookies.md): Der Identity-Dienst für Experience Cloud Identity Service verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und beständige IDs für Ihre Site-Besucher zu erstellen und zu speichern. Mit diesen Cookies kann Identity Service Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen verschiedenen Experience Cloud-Lösungen ermöglichen.
* [Anfordern und Festlegen von IDs durch den Experience Cloud Identity Service](id-request.md): Eine Übersicht über den ID-Anforderungs- und Antwortprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.
* [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](match-rates.md): Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Cloud Identity-Dienst, einschließlich Adobe Media Optimizer und Identity Service.
