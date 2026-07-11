---
description: Der Besucher-ID-Service von Adobe ermöglicht das allgemeine Identifizierungs-Framework für CX Enterprise-Anwendungen und -Services. Zu diesem Zweck wird einem Site-Besucher eine eindeutige, persistente ID, die als ECID bezeichnet wird, zugewiesen.
keywords: Visitor ID Service; ECID
title: Adobe-Besucher-ID-Service
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 433
ht-degree: 30%

---

# Adobe-Besucher-ID-Service {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

Der Besucher-ID-**ist** [Experience Platform Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de). Der Besucher-ID-Dienst ist die `VisitorAPI.js` JavaScript-Bibliothek, die in diesem Handbuch beschrieben wird und die die ECID für Adobe Analytics, Audience Manager und Target festlegt. Wenn Sie nach dem Adobe Experience Platform-Service suchen, der Identitäten geräte- und systemübergreifend in ein einheitliches Kundenprofil auflöst, lesen Sie stattdessen die [Übersicht über den Experience Platform Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de).

>[!ENDSHADEBOX]

Der Besucher-ID-Service von Adobe ermöglicht das allgemeine Identifizierungs-Framework für CX Enterprise-Anwendungen und -Services. Zu diesem Zweck wird einem Site-Besucher eine eindeutige, persistente ID, die als ECID bezeichnet wird, zugewiesen.

## Die Hauptentitäten einer Identität

Um besser zu verstehen, wie Adobe die eindeutige Identifizierung von Besuchenden erleichtert und Identitätsinformationen auflöst, lesen Sie die folgende Aufschlüsselung:

* **Besucher-ID-**: Der Besucher-ID **Dienst ist für das Festlegen der ECID**. Weitere Informationen finden Sie im Abschnitt [Übersicht über den Besucher-ID-Service](./introduction/overview.md).
* **ECID**: Die ECID ist ein gemeinsamer Identity-Namespace, der in Adobe Experience Platform und Adobe CX Enterprise-Anwendungen zur Identifizierung von Personen und Geräten verwendet wird. Weitere Informationen zur ECID finden Sie in der [ECID-Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid).
* **Experience Platform Identity Service**: Der Experience Platform Identity Service bietet Ihnen einen umfassenden Überblick über Ihre Kunden und deren Verhalten, indem er Identitäten geräte- und systemübergreifend zusammenführt. Weitere Informationen finden Sie unter [Übersicht über den Experience Platform Identity Service](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=de).

## Erste Schritte

* [Übersicht über den Besucher-ID](introduction/overview.md)Service: Erfahren Sie, was der Besucher-ID-Service tut und wie er in CX Enterprise passt.
* [Voraussetzungen für den Besucher-ID-](reference/requirements.md): Vergewissern Sie sich, dass Ihre Lösungen und Code-Bibliotheken die Voraussetzungen erfüllen, bevor Sie den Besucher-ID-Dienst implementieren.
* [Implementierungsmethoden](implementation-guides/implementation-methods.md): Vergleichen Sie die Standardimplementierung mit [Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) mit nicht standardmäßigen, direkten Integrationsmethoden.

## Erkunden Sie die Dokumentation

**Implementierung**

* [Handbücher zur Implementierung](implementation-guides/implementation-guides.md)
* [Direkte Integration mit dem Besucher-ID-Service](implementation-guides/direct-integration.md)
* [Opt-in-Service - Übersicht](implementation-guides/opt-in-service/optin-overview.md)
* [Testen und Überprüfen des Besucher-ID-Service](implementation-guides/test-verify.md)

**API-Referenz**

* [Übersicht über die Besucher-ID-Service-API](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**Häufig gestellte Fragen (FAQ)**

* [Häufig gestellte Fragen zum Besucher-ID-Service](faq-intro/faq.md)
* [Häufig gestellte Fragen zu anderen CX Enterprise-Lösungen](faq-intro/other-faq.md)

## Zusätzliche Ressourcen

* [ECID JavaScript-Bibliotheksversionen](https://github.com/Adobe-Marketing-Cloud/id-service/releases) auf GitHub
* [Versionshinweise für den Besucher-ID-Service](release-notes/notes-2022.md)
* [Datenschutzzentrum von Adobe](http://www.adobe.com/de/privacy.html)
* [Dokumentation zu Adobe CX Enterprise](https://experienceleague.adobe.com/docs/home.html?lang=de)

