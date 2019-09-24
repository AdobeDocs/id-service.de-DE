---
description: Enthält Beispiel-Serverkonfigurationen und führt die erforderlichen Migrationsschritte auf.
keywords: ID-Dienst
seo-description: Enthält Beispiel-Serverkonfigurationen und führt die erforderlichen Migrationsschritte auf.
seo-title: Migrationsszenarios für den Experience Cloud Identity-Dienst
title: Migrationsszenarios für den Experience Cloud Identity-Dienst
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Migrationsszenarios für den Experience Cloud Identity-Dienst {#experience-cloud-id-service-migration-scenarios}

Enthält Beispiel-Serverkonfigurationen und führt die erforderlichen Migrationsschritte auf.

## Nur eine Webeigenschaft {#section-6ccfea84628d46c99507cb124e7f5445}

* **Kunde**: Firma Beispiel GmbH
* **Für Experience Cloud freigeschaltet**: nein
* **Webeigenschaften**: beispiel.com
* **Datenerfassungsserver**: metrics.beispiel.com, smetrics.beispiel.com
* **Analytics-JavaScript-Datei**: nur eine Datei für alle Seiten der Site

Zuerst muss der Kunde für Experience Cloud freigeschaltet werden (siehe [Anforderungen](../../reference/requirements.md)). Außerdem ist der Kunde nicht auf eine Übergangsphase angewiesen, da er nur über eine einzige JavaScript-Datei verfügt. Der Kunde richtet außerdem die Besuchermigration ein und eliminiert dann den Datenerfassungs-CNAME, da er nicht mehr benötigt wird.

## Mehrere JavaScript-Dateien, hartcodierte Bild-Tags {#section-a665f6ee202940449198e4e7a5dcac54}

* **Kunde**: Firma Noch ein Beispiel GmbH
* **Für Experience Cloud freigeschaltet**: ja
* **Webeigenschaften**: nocheinbeispiel.com
* **Datenerfassungsserver**: nocheinbeispielgmbh.112.2o7.net
* **Analytics-JavaScript-Datei**: mehrere JavaScript-Dateien: eine Datei für die Hauptsite und eine weitere Datei für den Supportbereich, der über ein gesondertes CMS verwaltet wird
* **Weitere Datenerfassungsmethoden**: hartcodierte Bild-Tags in einem Sitebereich

Zuerst muss der Kunde seine Adobe Experience Cloud-Organisations-ID ermitteln (siehe [Anforderungen](../../reference/requirements.md)). Anschließend sollte der Kunde eine Migrationsübergangsphase festlegen, da mehrere JavaScript-Dateien eingesetzt werden. Der Kunde richtet außerdem die Besuchermigration ein und migriert dann von `*.2o7.net` auf `*.sc.omtrdc.net`.

Wenn dieser Kunde bei der Vorbereitung der Einführung des [!DNL Experience Cloud] ID-Diensts auf den neuesten Analytics-JavaScript-Code aktualisiert, werden dabei auch alle hartcodierten Bild-Tags für die Verwendung von JavaScript aktualisiert.

## Mehrere Webeigenschaften, mehrere JavaScript-Dateien und Flash-basierter Videoplayer {#section-34647995ff3740b999fdee22d885e515}

* **Kunde**: Guter Kunde LLC
* **Für Experience Cloud freigeschaltet**: ja
* **Webeigenschaften**: hauptsite.com, anderesiteA.com, anderesiteB.com
* **Datenerfassungsserver**: metrics.hauptsite.com, smetrics.hauptsite.com
* **Analytics-JavaScript-Datei**: mehrere JavaScript-Dateien: eine Datei für jede Webeigenschaft
* **Weitere Datenerfassungsmethoden**: Flash-basierter Videoplayer

Zuerst muss der Kunde seine Adobe Experience Cloud-Organisations-ID ermitteln (siehe [Anforderungen](../../reference/requirements.md)). Anschließend sollte der Kunde eine Migrationsübergangsphase festlegen, da mehrere JavaScript-Dateien eingesetzt werden. Der Kunde verfolgt Besucher domänenübergreifend über die primäre Domäne und die untergeordneten Domänen und wird daher zusammen mit dem Besucher-ID-Dienst auch weiterhin den Datenerfassungs-CNAME verwenden.

Wenn dieser Kunde bei der Vorbereitung der Einführung des [!DNL Experience Cloud] ID-Diensts auf den neuesten Analytics-JavaScript-Code aktualisiert, wird dabei auch der Flash-basierte Videoplayer auf die neueste Version von AppMeasurement für Flash aktualisiert.
