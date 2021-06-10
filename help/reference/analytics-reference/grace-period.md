---
description: Wir empfehlen, eine Übergangsphase zu konfigurieren, wenn mehrere JavaScript-Dateien vorhanden sind, die Daten an dieselbe Report Suite senden, oder wenn Sie für die Site weitere Technologien wie Flash-Videomessung verwenden.
keywords: ID-Dienst
title: Übergangsphase für den ID-Dienst
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 100%

---

# Übergangsphase für den ID-Dienst {#the-id-service-grace-period}

Wir empfehlen, eine Übergangsphase zu konfigurieren, wenn mehrere JavaScript-Dateien vorhanden sind, die Daten an dieselbe Report Suite senden, oder wenn Sie für die Site weitere Technologien wie Flash-Videomessung verwenden.

Nach der Bereitstellung des [!DNL Experience Cloud] ID-Diensts wird neuen Besuchern vom Datenerfassungsserver keine Analytics-Besucher-ID mehr zugewiesen. Wenn der [!DNL Experience Cloud] ID-Dienst für manche Bereiche der Site noch nicht implementiert wurde und Besucher diese Bereiche aufrufen, wird die Experience Cloud ID nicht erkannt und den Besuchern wird eine Legacy-Analytics-Besucher-ID zugewiesen. Dadurch können doppelte Besuchszahlen und eine falsche Attribution erzeugt werden.

Wenn beispielsweise der Supportbereich Ihrer Site in einem separaten CMS verwaltet wird, haben Sie möglicherweise eine andere Analytics-JavaScript-Datei für diesen Bereich. Wenn Sie die Besucher-ID auf Ihrer Haupt-Site bereitstellen, bevor Sie den ID-Dienst auf der Support-Site bereitstellen, erhalten neue Besucher beim Besuch des Support-Bereichs eine alte Analytics-ID. Besuche, die beide Site-Bereiche umfassen, werden als unterschiedliche Besuche gemeldet.

Wird der [!DNL Experience Cloud] ID-Dienst auf Sites bereitgestellt, die mehrere JavaScript-Dateien oder andere Technologien (z. B. Flash) verwenden, kann dies Koordinierungsprobleme verursachen, da der ID-Dienst für alle Sitebereiche gleichzeitig aktiviert werden muss. Mit der Konfiguration einer Übergangsphase wird neuen Besuchern vom [!DNL Experience Cloud] ID-Dienst weiterhin eine Analytics-Besucher-ID zugewiesen, damit sie richtig in Sitebereichen identifiziert werden, die noch nicht auf den ID-Dienst aktualisiert wurden.

>[!NOTE]
>
>Die Konfiguration einer Übergangsphase wird erst ab Version 1.3 des [!DNL Experience Cloud] ID-Diensts unterstützt.

## Wann sollte eine Übergangsphase konfiguriert werden? {#section-fd34c7ff697348a39f49258b7d39eb42}

Wenn Sie über eine einzige Analytics-JavaScript-Datei verfügen und keine anderen AppMeasurement-Bibliotheken verwenden, benötigen Sie keine Übergangsphase. Sie können einfach die JavaScript-Datei aktualisieren. Neue Besucher werden dann bei ihrem Besuch mit der Experience Cloud ID richtig identifiziert.

Wir empfehlen, eine Übergangsphase zu konfigurieren, wenn mehrere JavaScript-Dateien vorhanden sind, die Daten an *dieselbe Report Suite*, senden, oder wenn Sie für die Site weitere Technologien wie Flash-Videomessung verwenden.

## Wie wird eine Übergangsphase konfiguriert?  {#section-512d5cd8570e483cbdd8b04457a16ced}

[Kundenunterstützung kontaktieren](https://helpx.adobe.com/de/marketing-cloud/contact-support.html).
