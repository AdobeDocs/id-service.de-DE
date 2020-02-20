---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts.
keywords: ID Service
seo-description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts.
seo-title: Versionshinweise für 2019
title: Versionshinweise für 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: ba84c4dac9023ab13f5176c5665adbbdaeb00d33

---


# Versionshinweise für 2019 {#release-notes}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity-Diensts.

## Versionshinweise für 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des [!DNL Experience Cloud] ID-Diensts.

## Version 4.4 {#version-4point4}

**Neue Funktion**

[SHA-256-Hash-Unterstützung für setCustomerIDs](/help/reference/hashing-support.md). Experience Cloud ID Service (ECID) unterstützt den SHA-256-Hash-Algorithmus, mit dem Sie Kunden-IDs oder E-Mail-Adressen importieren und Hash-IDs exportieren können.

**Korrekturen und Verbesserungen**

* Die Konfiguration von `cookieDomain` wurde aktualisiert. Die ECID-Bibliothek filtert jetzt die leere Zeichenfolge `cookieDomain` in `initConfig` heraus und verwendet die Cookie-Domäne auf oberster Ebene, die durch die getDomain-Methode zurückgegeben wird. (CORE-29223)
* Ein Fehler wurde in Zusammenhang mit `getVisitorValues` in `localVisitor` behoben. (CORE-31287)
* Ein Fehler wurde behoben, durch den im Safari-Browser eine Abweichung beim MCOPTOUT-Wert aufgetreten ist, der von der `getVisitorValue`-Methode zurückgegeben wird. (CORE-29719)
* Die Opt-in-Bibliothek wurde aktualisiert, indem `optIn.off` zur Abmeldung von Ereignissen hinzugefügt wurde.
* Ein Fehler in Zusammenhang mit der setTimeout-Funktion wurde behoben, bei der `setTimeout` die Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) auf einigen Kunden-Sites verletzt hat. (CORE-30623)

## Version 4.3 {#version-4point3}

**Unterstützung für ITP 2.1**. Wenn ein Trackingserver mit einem Erstanbieter-CNAME eingerichtet ist, wird ein neues Cookie (s_ecid) zum ECID-Wert hinzugefügt. Die ECID-Bibliothek referenziert den Wert, damit die ID über 7 Tage hinaus erhalten bleibt. Siehe [ECID-Bibliotheksmethoden in einer Safari-ITP-Umgebung](/help/reference/ecid-library-methods.md).

**Fehlerbehebung für secureCookie config.**

## Version 4.1

Aktualisierung `publishDestinations` pro API-Änderung. Mit dieser Aktualisierung können die Referrer-Informationen der Seite während der ID-Synchronisierung offengelegt werden, wenn gewünscht. (CORE-23693)

## Version 4.2

Unterstützung für das Audience Manager-Plugin für IAB TCF, verfügbar über das ECID-Opt-in-Objekt.

**Fehlerbehebungen**

* IAB + OptIn kann keine MID für den erneuten Besuch von Kunden erhalten (CORE-26022)
* Fehler bei der Konfiguration von opt-in doOptInApply in DTM (DTM-12958) behoben
* ECID-Ausschluss deaktiviert ID-Syncs (CORE-23814)

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-in-Dienst**. Opt-in ist eine Erweiterung der Experience Cloud-ID (ECID), mit der Sie steuern können, ob (und welche) Experience Cloud-Bibliotheken Cookies auf Webseiten für Besucher erstellen können. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Element | Beschreibung |
|---|---|
| Die Kennzeichnung`disableIdSyncs` funktioniert nicht, nachdem eine Zeichenfolge übergeben wurde. | Behoben. Werte, die für den `disableidSyncs` Parameter in der `getInstance` Funktion festgelegt wurden, werden jetzt berücksichtigt. |
| Drittanbieter-iFrames erhalten die ECID nicht. | ECIDs, die in der mobilen Version von Safari und in verschiedenen iFrames nicht funktionierten, wurden korrigiert. |

