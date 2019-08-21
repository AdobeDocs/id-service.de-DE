---
description: Wir empfehlen, eine Übergangsphase zu konfigurieren, wenn mehrere JavaScript-Dateien vorhanden sind, die Daten an dieselbe Report Suite senden, oder wenn Sie für die Site weitere Technologien wie Flash-Videomessung verwenden.
keywords: ID-Dienst
seo-description: Wir empfehlen, eine Übergangsphase zu konfigurieren, wenn mehrere JavaScript-Dateien vorhanden sind, die Daten an dieselbe Report Suite senden, oder wenn Sie für die Site weitere Technologien wie Flash-Videomessung verwenden.
seo-title: Übergangsphase für den ID-Dienst
title: Übergangsphase für den ID-Dienst
uuid: 10a7db7d-de32-4379-914f-edaf929efa32
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Übergangsphase für den ID-Dienst{#the-id-service-grace-period}

Wir empfehlen, eine Übergangsphase zu konfigurieren, wenn mehrere JavaScript-Dateien vorhanden sind, die Daten an dieselbe Report Suite senden, oder wenn Sie für die Site weitere Technologien wie Flash-Videomessung verwenden.

Nach der Bereitstellung des [!DNL Experience Cloud] ID-Diensts wird neuen Besuchern vom Datenerfassungsserver keine Analytics-Besucher-ID mehr zugewiesen. Wenn der [!DNL Experience Cloud] ID-Dienst für manche Bereiche der Site noch nicht implementiert wurde und Besucher diese Bereiche aufrufen, wird die Experience Cloud ID nicht erkannt und den Besuchern wird eine Legacy-Analytics-Besucher-ID zugewiesen. Das kann zur doppelten Zählung von Besuchern und fehlerhaften Zuordnungen führen.

Wenn der Supportbereich der Site beispielsweise über ein gesondertes CMS verwaltet wird, verwenden Sie für diesen Bereich möglicherweise eine andere Analytics-JavaScript-Datei. Wenn Sie die Besucher-ID zuerst auf der Hauptsite und erst dann auf der Support-Site bereitstellen, wird Besuchern beim Besuch des Supportbereichs eine Legacy-Analytics-ID zugewiesen, und Besuche, bei denen beide Sitebereiche aufgerufen werden, werden als verschiedene Besuche erfasst.

Wird der [!DNL Experience Cloud] ID-Dienst auf Sites bereitgestellt, die mehrere JavaScript-Dateien oder andere Technologien (z. B. Flash) verwenden, kann dies Koordinierungsprobleme verursachen, da der ID-Dienst für alle Sitebereiche gleichzeitig aktiviert werden muss. Mit der Konfiguration einer Übergangsphase wird neuen Besuchern vom [!DNL Experience Cloud] ID-Dienst weiterhin eine Analytics-Besucher-ID zugewiesen, damit sie richtig in Sitebereichen identifiziert werden, die noch nicht auf den ID-Dienst aktualisiert wurden.

>[!NOTE]
>
>Die Konfiguration einer Übergangsphase wird erst ab Version 1.3 des [!DNL Experience Cloud] ID-Diensts unterstützt.

## Wann sollte eine Übergangsphase konfiguriert werden? {#section-fd34c7ff697348a39f49258b7d39eb42}

Wenn Sie nur eine Analytics-JavaScript-Datei verwenden und keine weiteren AppMeasurement-Bibliotheken, ist es nicht erforderlich, eine Übergangsphase zu konfigurieren. Sie können einfach die JavaScript-Datei aktualisieren. Neue Besucher werden dann bei ihrem Besuch mit der Experience Cloud ID richtig identifiziert.

Wir empfehlen, eine Übergangsphase zu konfigurieren, wenn mehrere JavaScript-Dateien vorhanden sind, die Daten an *dieselbe Report Suite* senden, oder wenn Sie auf der Site weitere Technologien wie Flash-Videomessung verwenden.

## Wie wird eine Übergangsphase konfiguriert? {#section-512d5cd8570e483cbdd8b04457a16ced}

Wenden Sie sich an [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html).
