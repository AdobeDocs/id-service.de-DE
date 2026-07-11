---
description: Die Rolle des Besucher-ID-Service in Adobe CX Enterprise.
title: Übersicht über den Adobe-Besucher-ID-Service
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 497
ht-degree: 18%

---

# Übersicht über den Adobe-Besucher-ID-Service

Der Adobe Visitor ID Service ermöglicht das allgemeine Identifizierungs-Framework für CX Enterprise Application Services. Sie können den Besucher-ID-Dienst verwenden, um die [ECID“ &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=de).

Die ECID ist ein gemeinsamer Identity-Namespace, der in Adobe Experience Platform- und CX Enterprise-Anwendungen verwendet wird, um das Besucherverhalten zu verfolgen und sicherzustellen, dass jedes Gerät über eine eindeutige Kennung verfügt, die sitzungsübergreifend bestehen kann.

>[!TIP]
>
>Der Besucher-ID-Dienst, der Experience Platform Identity Service und die ECID sind drei **verschiedene** Entitäten.

Der Besucher-ID-Service kann verschiedene anwendungsspezifische IDs ersetzen und die Funktion [Kunden-IDs und Authentifizierungsstatus](/help/reference/authenticated-state.md) nutzen, damit Sie Ihre eigenen Kunden-IDs an CX Enterprise übergeben können.

>[!NOTE]
>
>Der Besucher-ID-Dienst funktioniert nur mit den von Ihnen abonnierten CX Enterprise Application Services und bietet keinen Zugriff auf andere Anwendungs-Services, wenn Sie diese nicht abonniert haben.

Der Besucher-ID-Dienst unterstützt die folgenden Anwendungen:

* [Adobe Analytics](https://business.adobe.com/de/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/de/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/de/products/target/adobe-target.html)

Künftig ist der Besucher-ID-Service eine integrale Komponente vieler aktueller und künftiger CX Enterprise-Funktionen, -Erweiterungen und -Services. Der Besucher-ID-Service unterstützt derzeit [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Wenn Sie den Besucher-ID-Service nicht implementiert haben, ist es jetzt an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen.

## Funktionszusammenfassung

Zusammenfassend lässt sich sagen, dass der Besucher-ID-Service dabei hilft:

* Eindeutige Identifizierung eines Besuchers auf einem Gerät über mehrere Anwendungen hinweg.
* Setzt ein First-Party-Cookie in der Domain des Kunden, um das Tracking auf derselben Domain sicherzustellen. Weitere Informationen finden Sie im Dokument [Cookies und der Besucher](./cookies.md)ID-Dienst“.
* Erhält Aliase und ID-Zuordnungen von Kunden und Partnern von CX Enterprise.
* Verwaltet die ID-Synchronisierung innerhalb von CX Enterprise.
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.

## Anforderungen an den Besucher-ID-Service

Ihre Lösung und andere Adobe-Code-Bibliotheken müssen [bestimmte Anforderungen](/help/reference/requirements.md) erfüllen, bevor Sie den Besucher-ID-Dienst verwenden können.

* [Cookies und der Besucher-ID-Dienst](cookies.md): Der Besucher-ID-Dienst verwendet Ihre IMS-Organisations-ID, das CX Enterprise AMCV-Cookie und ein demdex-Cookie, um eindeutige und persistente Kennungen für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der Besucher-ID-Service Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen verschiedenen CX Enterprise-Lösungen ermöglichen.
* [Anfordern und Festlegen von IDs durch den Besucher-ID](id-request.md)Service: Eine Übersicht über den ID-Anforderungs- und Antwortprozess. Diese Beispiele decken die ID-Zuweisung auf einzelnen Sites, an verschiedenen Sites und für Sites ab, die von verschiedenen CX Enterprise-Kunden mit eigenen IMS-Organisations-IDs verwaltet werden.
* [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](match-rates.md): Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Besucher-ID-Dienst, einschließlich Adobe Media Optimizer und Besucher-ID-Dienst.

