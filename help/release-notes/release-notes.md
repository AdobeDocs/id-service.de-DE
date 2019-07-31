---
description: Funktionen, Aktualisierungen oder Änderungen an dem Experience Cloud-Identitätsdienst.
keywords: ID-Dienst
seo-description: Funktionen, Aktualisierungen oder Änderungen an dem Experience Cloud-Identitätsdienst.
seo-title: Versionshinweise für 2019
title: Versionshinweise für 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# Versionshinweise für 2019 {#release-notes}

Funktionen, Aktualisierungen oder Änderungen an dem Experience Cloud-Identitätsdienst.

## Versionshinweise für 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des [!DNL Experience Cloud] ID-Diensts.

## Version 4.4 {#version-4point4}

**Neue Funktion**

[SHA 256 Hashing-Unterstützung für setcustomerids](/help/reference/hashing-support.md). Der Experience Cloud ID-Dienst (ECID) unterstützt den SHA -256-Hashing-Algorithmus, der es Ihnen ermöglicht, Kunden-IDs oder E-Email-Adressen zu übermitteln und Hash-IDs auszugeben.

**Korrekturen, Verbesserungen, Verbesserungen**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. (CORE-29223)
* We fixed a bug related to `getVisitorValues` in `localVisitor`. (CORE-31287)
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. (CORE-29719)
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. (CORE-30623)

## Version 4.3 {#version-4point3}

**Unterstützung für ITP 2.1**. Wenn in einem Erstanbieter-CNAME ein Trackingserver festgelegt ist, wird ein neuer Cookie (s_ ecid) mit dem ECID-Wert platziert. Die ECID-Bibliothek verweist auf den Wert, um die ID über 7 Tage zu erhalten. See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**Fehlerbehebung für securecookie config.**

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-in-Dienst**. Die Teilnahme an der Teilnahme ist eine Erweiterung der Experience Cloud ID (ECID), mit der Sie steuern können, ob (und dann) Experience Cloud-Bibliotheken Cookies auf Webseiten für Besucher erstellen können. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Element | Beschreibung |
|---|---|
| Die Kennzeichnung `disableIdSyncs` funktioniert nicht, nachdem eine Zeichenfolge übergeben wurde. | Behoben. Werte, die für den `disableidSyncs` Parameter in der `getInstance` Funktion festgelegt wurden, werden jetzt berücksichtigt. |
| Drittanbieter-iFrames erhalten die ECID nicht. | ECIDs, die in der mobilen Version von Safari und in verschiedenen iFrames nicht funktionierten, wurden korrigiert. |

