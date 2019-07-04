---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud ID-Diensts.
keywords: ID-Dienst
seo-description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud ID-Diensts.
seo-title: Versionshinweise für 2019
title: Versionshinweise für 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Versionshinweise für 2019 {#release-notes}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud ID-Diensts.

## Versionshinweise für 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des [!DNL Experience Cloud] ID-Diensts.

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-in-Dienst**. Opt-in ist eine Erweiterung von [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/de_DE/mcvid/), mit der Sie steuern können, ob (und welche) Experience Cloud-Bibliotheken Cookies auf Webseiten für Besucher erstellen können. Mit [Launch](https://docs.adobelaunch.com/) können Sie die Zustimmung von Besuchern zu Experience Cloud-Lösungen einfacher einholen, indem Sie Analytics, Target, Audience Manager und anderen oder allen ausgewählten Experience Cloud-Lösungen die Nutzung Ihres Zustimmungsverwaltungssystems ermöglichen.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Element | Beschreibung |
|---|---|
| Die Kennzeichnung `disableIdSyncs` funktioniert nicht, nachdem eine Zeichenfolge übergeben wurde. | Behoben. Werte, die für den `disableidSyncs` Parameter in der `getInstance` Funktion festgelegt wurden, werden jetzt berücksichtigt. |
| Drittanbieter-iFrames erhalten die ECID nicht. | ECIDs, die in der mobilen Version von Safari und in verschiedenen iFrames nicht funktionierten, wurden korrigiert. |

