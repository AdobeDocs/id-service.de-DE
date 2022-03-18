---
description: Die Rolle des Experience Cloud Identity Services in Adobe Experience Cloud.
title: Experience Cloud ID-Dienst – Übersicht
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: ht
source-wordcount: '543'
ht-degree: 100%

---

# Experience Cloud ID-Dienst – Übersicht

Mit dem [!UICONTROL Experience Cloud Identity Service] wird die Nutzung des allgemeinen Identifizierungs-Frameworks für den Experience Cloud Core-Dienste (z. B. Kundenattribute und Zielgruppen) im Experience Platform Identity-Dienst ermöglicht.

>[!NOTE]
>
> Referenzen auf den ID-Dienst werden möglicherweise als Akronyme oder frühere Namen wie ECID, Experience Cloud ID-Dienst (MID) und Besucher-ID-Dienst angezeigt. Diese beziehen sich auf den [!UICONTROL Experience Cloud Identity Service]. Möglicherweise sehen Sie auch den Begriff [!UICONTROL Experience Platform Identity-Dienst]. Zur Klarstellung:

* [!UICONTROL Experience Platform Identity-Dienst]: Der Service, der Identitäten verknüpft. Es handelt sich dabei um den Service zum Verknüpfen von Geräten für das personenbasierte Erlebnis-Management.
* [!UICONTROL Experience Cloud ID-Dienst] (ECID): Die eindeutige, persistente ID, die einem Site-Besucher zugewiesen wird. Dies ist eine bestimmte Entität, die vom Platform Identity-Dienst verwendet werden kann.

Wenn Ihr Unternehmen den ID-Dienst implementiert, können Sie mit dieser ID denselben Site-Besucher und dessen Daten in unterschiedlichen Experience Cloud-Lösungen identifizieren.

![](assets/ecid-new.png)

Darüber hinaus kann der ID-Dienst die verschiedenen lösungsspezifischen IDs (beispielsweise Analytics-AID) ersetzen. Mit der Funktion [Kunden-IDs und Authentifizierungsstatus](/help/reference/authenticated-state.md) ermöglicht es Ihnen der ID-Dienst, eigene Kunden-IDs an Experience Cloud zu übergeben. Beachten Sie jedoch, dass der ID-Dienst nur mit den Lösungen funktioniert, die Sie bereits abonniert haben. Er bietet keinen Zugriff auf andere Produkte, wenn Sie nicht für sie angemeldet sind.

Künftig ist der ID-Dienst eine integrale Komponente von vielen aktuellen und künftigen Experience Cloud-Features, -Erweiterungen und -Services. Der ID-Dienst unterstützt derzeit [Analytics](http://www.adobe.com/de/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/de/marketing-cloud/data-management-platform.html) und [Target](http://www.adobe.com/de/marketing-cloud/testing-targeting.html). Zudem ist er erforderlich, wenn Sie sich an der Adobe Experience Cloud-Gerätekooperation beteiligen möchten. Wenn Sie den ID-Service nicht implementiert haben, ist es nun an der Zeit, eine Migrationsstrategie in Erwägung zu ziehen.

## Funktionszusammenfassung

Zusammenfassend leistet der ID-Service Folgendes:

* Er erstellt einen gemeinsamen Schlüssel oder eine gemeinsame ID, die zum Verknüpfen von Profilen und Identitäten verwendet werden kann.
* Er identifiziert ein Gerät eindeutig in mehreren Lösungen.
* Er legt ein Erstanbieter-Cookie in der Domain des Kunden fest, um sicherzustellen, dass die Verfolgung in derselben Domain erfolgt. Weitere Informationen finden Sie im Dokument zu [Cookies und Experience Cloud Identity Service](./cookies.md).
* Erhalten von Aliasen und ID-Zuordnungen von Experience Cloud-Kunden und -Partnern.
* Verwalten der ID-Synchronisierung innerhalb der Experience Cloud.
* Unterstützen der ID-Synchronisierung mit unterschiedlichen Drittanbietern im Anzeigentechnologiesystem.

## Anforderungen für den ID-Dienst

Ihre Lösung und andere Adobe-Codebibliotheken müssen diese [Anforderungen erfüllen](/help/reference/requirements.md), bevor Sie den ID-Dienst verwenden können.

* [Cookies und der Experience Cloud Identity Service](cookies.md): Der ID-Dienst verwendet Ihre Organisations-ID, das Experience Cloud-AMCV-Cookie und ein demdex-Cookie, um eindeutige und beständige IDs für die Besucher Ihrer Site zu erstellen und zu speichern. Mit diesen Cookies kann der ID-Dienst Besucher domänenübergreifend verfolgen und die Datenfreigabe zwischen unterschiedlichen Experience Cloud-Lösungen ermöglichen.
* [Anfordern und Festlegen von IDs durch den Experience Cloud Identity Service](id-request.md): Eine Übersicht über den ID-Anforderungs- und Antwortprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.
* [Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten](match-rates.md): Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Cloud Identity Service, einschließlich Adobe Media Optimizer und ID-Dienst.
