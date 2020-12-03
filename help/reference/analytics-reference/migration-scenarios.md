---
description: Enthält Beispiel-Serverkonfigurationen und führt die erforderlichen Migrationsschritte auf.
keywords: ID Service
seo-description: Enthält Beispiel-Serverkonfigurationen und führt die erforderlichen Migrationsschritte auf.
seo-title: Migrationsszenarios für den Experience Cloud Identity-Dienst
title: Migrationsszenarios für den Experience Cloud Identity-Dienst
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 57%

---


# Migrationsszenarios für den Experience Cloud Identity-Dienst {#experience-cloud-id-service-migration-scenarios}

Enthält Beispiel-Serverkonfigurationen und führt die erforderlichen Migrationsschritte auf.

## Nur eine Webeigenschaft {#section-6ccfea84628d46c99507cb124e7f5445}

* **Kunde**: Firma Beispiel GmbH
* **Experience Cloud aktiviert**: Nein
* **Webeigenschaften**: example.com
* **Datenerfassungsserver**: metrics.example.com, smetrics.example.com
* **Analytics-JavaScript-Datei**: Eine einzelne Datei für alle Siteseiten

Zuerst muss der Kunde für Experience Cloud freigeschaltet werden (siehe [Anforderungen](../../reference/requirements.md)). Da der Kunde über eine einzige JavaScript-Datei verfügt, braucht er keine Übergangsphase. Der Kunde richtet außerdem eine Migration von Besuchern ein und eliminiert dann den Datenerfassungs-CNAME, was nicht erforderlich ist.

## Mehrere JavaScript-Dateien, hartcodierte Bild-Tags {#section-a665f6ee202940449198e4e7a5dcac54}

* **Kunde**: Firma Noch ein Beispiel GmbH
* **Experience Cloud aktiviert**: Ja
* **Webeigenschaften**: anotherexample.com
* **Datenerfassungsserver**: anotherexampleco.112.2o7.net
* **Analytics-JavaScript-Datei**: Mehrere JavaScript-Dateien. Eine Datei für ihre Haupt-Site, eine weitere Datei für ihren Supportbereich, die in einem separaten CMS verwaltet wird.
* **Andere Datenerfassungsmethoden**: Hartkodierte Bild-Tags in einem Sitebereich

Zuerst muss der Kunde seine Adobe Experience Cloud-Organisations-ID ermitteln (siehe [Anforderungen](../../reference/requirements.md)). Anschließend sollte der Kunde eine Migrationsübergangsphase festlegen, da mehrere JavaScript-Dateien eingesetzt werden. Der Kunde richtet außerdem die Besuchermigration ein und migriert dann von `*.2o7.net` auf `*.sc.omtrdc.net`.

Wenn dieser Kunde bei der Vorbereitung der Einführung des [!DNL Experience Cloud] ID-Diensts auf den neuesten Analytics-JavaScript-Code aktualisiert, werden dabei auch alle hartcodierten Bild-Tags für die Verwendung von JavaScript aktualisiert.

## Mehrere Webeigenschaften, mehrere JavaScript-Dateien und Flash-basierter Videoplayer {#section-34647995ff3740b999fdee22d885e515}

* **Kunde**: Guter Kunde LLC
* **Experience Cloud aktiviert**: Ja
* **Webeigenschaften**: mymainsite.com, myothersiteA.com, myothersiteB.com
* **Datenerfassungsserver**: metrics.mymainsite.com, smetrics.mymainsite.com
* **Analytics-JavaScript-Datei**: Mehrere JavaScript-Dateien. Eine Datei für jede Webeigenschaft.
* **Andere Datenerfassungsmethoden**: Ein Flash-basierter Videoplayer

Zuerst muss der Kunde seine Adobe Experience Cloud-Organisations-ID ermitteln (siehe [Anforderungen](../../reference/requirements.md)). Anschließend sollte der Kunde eine Migrationsübergangsphase festlegen, da mehrere JavaScript-Dateien eingesetzt werden. Der Kunde verfolgt Besucher zwischen seiner primären Domäne und seinen Subdomänen, sodass er seinen Datenerfassungs-CNAME mit dem Besucher-ID-Dienst weiter verwenden wird.

Wenn dieser Kunde bei der Vorbereitung der Einführung des [!DNL Experience Cloud] ID-Diensts auf den neuesten Analytics-JavaScript-Code aktualisiert, wird dabei auch der Flash-basierte Videoplayer auf die neueste Version von AppMeasurement für Flash aktualisiert.
