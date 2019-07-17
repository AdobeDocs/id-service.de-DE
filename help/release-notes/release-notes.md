---
description: Funktionen, Aktualisierungen oder Änderungen an dem Experience Cloud-Identitätsdienst.
keywords: ID-Dienst
seo-description: Funktionen, Aktualisierungen oder Änderungen an dem Experience Cloud-Identitätsdienst.
seo-title: Versionshinweise für 2019
title: Versionshinweise für 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Versionshinweise für 2019 {#release-notes}

Funktionen, Aktualisierungen oder Änderungen an dem Experience Cloud-Identitätsdienst.

## Versionshinweise für 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des [!DNL Experience Cloud] ID-Diensts.

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-in-Dienst**. Die Teilnahme an der Teilnahme ist eine Erweiterung der Experience Cloud ID (ECID), mit der Sie steuern können, ob (und dann) Experience Cloud-Bibliotheken Cookies auf Webseiten für Besucher erstellen können. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Element | Beschreibung |
|---|---|
| Die Kennzeichnung `disableIdSyncs` funktioniert nicht, nachdem eine Zeichenfolge übergeben wurde. | Behoben. Werte, die für den `disableidSyncs` Parameter in der `getInstance` Funktion festgelegt wurden, werden jetzt berücksichtigt. |
| Drittanbieter-iFrames erhalten die ECID nicht. | ECIDs, die in der mobilen Version von Safari und in verschiedenen iFrames nicht funktionierten, wurden korrigiert. |

