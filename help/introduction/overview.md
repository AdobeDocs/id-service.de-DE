---
description: Die Rolle des Experience Cloud Identity Services in Adobe Experience Cloud.
title: Übersicht über den Experience Cloud Identity Service
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: ht
source-wordcount: '489'
ht-degree: 100%

---

# Übersicht über den Experience Cloud Identity Service

Das allgemeine Identifizierungs-Framework für Experience Cloud Application Services beruht auf dem Experience Cloud Identity Service. Sie können den Experience Cloud Identity Service verwenden, um die [Experience Cloud-ID (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=de) festzulegen.

Die ECID ist ein gemeinsamer Identitäts-Namespace, der in allen Adobe Experience Platform- und Experience Cloud-Anwendungen verwendet wird, um das Besucherverhalten zu verfolgen und sicherzustellen, dass jedes Gerät über eine eindeutige ID verfügt, die sitzungsübergreifend bestehen kann.

>[!TIP]
>
>Der Experience Cloud Identity Service, der Experience Platform Identity Service und die ECID sind drei **verschiedene** Entitäten.

Der Experience Cloud Identity Service kann verschiedene anwendungsspezifische IDs ersetzen und die Funktion [Kunden-IDs und Authentifizierungsstatus](/help/reference/authenticated-state.md) nutzen, damit Sie Ihre eigenen Kunden-IDs an Experience Cloud übergeben können.

>[!NOTE]
>
>Der Experience Cloud Identity Service funktioniert nur mit Experience Cloud Application Services, die Sie abonniert haben, und bietet keinen Zugriff auf andere Anwendungs-Services, die Sie nicht abonniert haben.

Der Experience Cloud Identity Service unterstützt die folgenden Anwendungen:

* [Adobe Analytics](https://business.adobe.com/de/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/de/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/de/products/target/adobe-target.html)

Künftig ist der ID-Service eine integrale Komponente von vielen aktuellen und künftigen Experience Cloud-Features, -Erweiterungen und -Services. Der ID-Dienst unterstützt derzeit [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Wenn Sie den ID-Service nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen.

## Funktionszusammenfassung

Zusammenfassend lässt sich sagen, dass der Experience Cloud Identity Service bei Folgendem hilft:

* Eindeutige Identifizierung eines Besuchers auf einem Gerät über mehrere Anwendungen hinweg.
* Setzt ein First-Party-Cookie in der Domain des Kunden, um das Tracking auf derselben Domain sicherzustellen. Weitere Informationen finden Sie im Dokument zu [Cookies und Experience Cloud Identity Service](./cookies.md).
* Erhalten von Aliasen und ID-Zuordnungen von Experience Cloud-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der Experience Cloud.
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.

## Voraussetzungen für den Experience Cloud Identity Service

Ihre Lösung und andere Adobe-Code-Bibliotheken müssen [bestimmte Anforderungen](/help/reference/requirements.md) erfüllen, bevor Sie den Identity Service verwenden können.

* [Cookies und der Experience Cloud Identity Service](cookies.md): Der Experience Cloud Identity Service verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und persistente Kennungen für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der Identity Service Besucher domain-übergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
* [Anfordern und Festlegen von IDs durch den Experience Cloud Identity Service](id-request.md): Eine Übersicht über den ID-Anforderungs- und Antwortprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.
* [ID-Synchronisierung und Übereinstimmungsraten](match-rates.md): Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Cloud Identity Service einschließlich Adobe Media Optimizer und Identity Service.
