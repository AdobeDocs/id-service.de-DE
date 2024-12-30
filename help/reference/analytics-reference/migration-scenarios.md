---
description: Enthält Beispiel-Serverkonfigurationen und führt die erforderlichen Migrationsschritte auf.
keywords: ID-Dienst
title: Migrationsszenarios für den Experience Cloud Identity Service
exl-id: 419532bf-399f-4646-a95f-31c35535d6fc
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 89%

---

# Migrationsszenarios für den Experience Cloud Identity Service {#experience-cloud-id-service-migration-scenarios}

Enthält Beispiel-Serverkonfigurationen und führt die erforderlichen Migrationsschritte auf.

## Nur eine Webeigenschaft {#section-6ccfea84628d46c99507cb124e7f5445}

* **Kunde**: Firma Beispiel GmbH
* **Experience Cloud aktiviert**: Nein
* **Web-Eigenschaften**: example.com
* **Datenerfassungs-Server**: metrics.example.com, smetrics.example.com
* **Analytics JavaScript-Datei**: Eine einzelne Datei für alle Seiten einer Site

Zunächst sollte dieser Kunde für die Experience Cloud aktiviert werden (siehe [Anforderungen](../../reference/requirements.md)). Da der Kunde über eine einzige JavaScript-Datei verfügt, braucht er keine Übergangsphase. Dieser Kunde richtet außerdem eine Besuchermigration ein und führt eine Migration weg von seinem Datenerfassungs-CNAME durch, der nicht mehr erforderlich ist.

## Mehrere JavaScript-Dateien, hartcodierte Bild-Tags {#section-a665f6ee202940449198e4e7a5dcac54}

* **Kunde**: Firma Noch ein Beispiel GmbH
* **Experience Cloud aktiviert**: Ja
* **Web-Eigenschaften**: anotherexample.com
* **Datenerfassungs-Server**: anotherexampleco.112.2o7.net
* **Analytics-JavaScript-Datei**: Mehrere JavaScript-Dateien. Eine Datei für seine Haupt-Site und eine weitere Datei für seinen Support-Bereich, die in einem separaten CMS verwaltet wird.
* **Andere Datenerfassungsmethoden**: Hartcodierte Bild-Tags in einem Site-Bereich

Zunächst sollte dieser Kunde seine Adobe Experience Cloud-Organisations-ID finden (siehe [Anforderungen](../../reference/requirements.md)). Anschließend sollte der Kunde eine Migrationsübergangsphase festlegen, da mehrere JavaScript-Dateien eingesetzt werden. Der Kunde richtet außerdem die Besuchermigration ein und migriert dann von `*.2o7.net` auf `*.sc.omtrdc.net`.

Wenn dieser Kunde bei der Vorbereitung der Einführung des [!DNL Experience Cloud] ID-Diensts auf den neuesten Analytics-JavaScript-Code aktualisiert, werden dabei auch alle hartcodierten Bild-Tags für die Verwendung von JavaScript aktualisiert.

## Mehrere Webeigenschaften, mehrere JavaScript-Dateien und Flash-basierter Videoplayer {#section-34647995ff3740b999fdee22d885e515}

* **Kunde**: Guter Kunde LLC
* **Experience Cloud aktiviert**: Ja
* **Web-Eigenschaften**: mymainsite.com, myothersiteA.com, myothersiteB.com
* **Datenerfassungs-Server**: metrics.mymainsite.com, smetrics.mymainsite.com
* **Analytics-JavaScript-Datei**: Mehrere JavaScript-Dateien. Eine Datei für jede Web-Eigenschaft.
* **Andere Datenerfassungsmethoden**: Ein Flash-basierter Video-Player

Zunächst sollte dieser Kunde seine Adobe Experience Cloud-Organisations-ID finden (siehe [Anforderungen](../../reference/requirements.md)). Anschließend sollte der Kunde eine Migrationsübergangsphase festlegen, da mehrere JavaScript-Dateien eingesetzt werden. Dieser Kunde verfolgt Besucher zwischen ihrer primären Domain und ihrer Sub-Domain und verwendet daher seine Datenerfassungs-CNAME mit dem Besucher-ID-Dienst weiterhin.

Wenn dieser Kunde bei der Vorbereitung der Einführung des [!DNL Experience Cloud] ID-Diensts auf den neuesten Analytics-JavaScript-Code aktualisiert, wird dabei auch der Flash-basierte Video-Player auf die neueste Version von AppMeasurement für Flash aktualisiert.
