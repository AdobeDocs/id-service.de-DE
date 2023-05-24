---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.
keywords: ID-Dienst
title: Versionshinweise für 2019
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
source-git-commit: 503683b66b6022b7c1fecbfb197fe17e05ae9c64
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 100%

---

# Versionshinweise zu Experience Cloud – 2019 {#release-notes}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Experience Cloud Identity Services.

## Version 4.4.1

Ein Kontrollkästchen für die Genehmigung vor dem Opt-in für Medienanalysen in der ECID Launch-Erweiterung wurde hinzugefügt.

**Fehlerbehebungen**

* Problem mit dem Parsen der Eingabe-Zeichenfolge für die ECID Launch-Erweiterung preOptInApprovals.
* Leistungsabfall bei Verwendung von trackingServer.

## Version 4.4 {#version-4point4}

**Neue Funktion**

[SHA-256-Hash-Unterstützung für setCustomerIDs](/help/reference/hashing-support.md). Experience Cloud ID Service (ECID) unterstützt den SHA-256-Hash-Algorithmus, mit dem Sie Kunden-IDs oder E-Mail-Adressen importieren und Hash-IDs exportieren können.

**Korrekturen und Verbesserungen**

* Die Konfiguration von `cookieDomain` wurde aktualisiert. Die ECID-Bibliothek filtert jetzt die leere Zeichenfolge `cookieDomain` in `initConfig` heraus und verwendet die Cookie-Domäne auf oberster Ebene, die durch die getDomain-Methode zurückgegeben wird.
* Ein Fehler wurde in Zusammenhang mit `getVisitorValues` in `localVisitor` behoben. 
* Ein Fehler wurde behoben, durch den im Safari-Browser eine Abweichung beim MCOPTOUT-Wert aufgetreten ist, der von der `getVisitorValue`-Methode zurückgegeben wird.
* Die Opt-in-Bibliothek wurde aktualisiert, indem `optIn.off` zur Abmeldung von Ereignissen hinzugefügt wurde.
* Ein Fehler in Zusammenhang mit der setTimeout-Funktion wurde behoben, bei der `setTimeout` die Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) auf einigen Kunden-Sites verletzt hat.

## Version 4.3 {#version-4point3}

**Unterstützung für ITP 2.1**. Wenn ein Trackingserver mit einem Erstanbieter-CNAME eingerichtet ist, wird ein neues Cookie (s_ecid) zum ECID-Wert hinzugefügt. Die ECID-Bibliothek referenziert den Wert, damit die ID über 7 Tage hinaus erhalten bleibt. Siehe [ECID-Bibliotheksmethoden in einer Safari-ITP-Umgebung](/help/reference/ecid-library-methods.md).

**Fehlerbehebung für secureCookie config.**

## Version 4.1

Aktualisierung von `publishDestinations` durch die Änderung in der neuen API. Mit dieser Aktualisierung können die Referrer-Informationen der Seite während der ID-Synchronisierung offengelegt werden, wenn gewünscht.

## Version 4.2

Unterstützung für das Audience Manager-Plug-in für IAB TCF, das über das Objekt „ECID Opt-in“ verfügbar ist.

**Fehlerbehebungen**

* IAB + Opt-in kann keine MID für den erneuten Besuch von Kunden abrufen.
* Ein Fehler bei der Konfiguration des Opt-ins doesOptInApply in wurde in DTM behoben.
* ECID-Opt-out deaktiviert ID-Synchronisationen.

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-in-Dienst**. Opt-in ist eine Erweiterung der Experience Cloud ID (ECID), mit der Sie steuern können, ob (und welche) Experience Cloud-Bibliotheken Cookies auf Webseiten für Besucher erstellen können. Mit [Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) können Sie die Zustimmung von Besuchern zu Experience Cloud-Lösungen einfacher einholen, indem Sie Analytics, Target, Audience Manager und anderen oder allen ausgewählten Experience Cloud-Lösungen die Nutzung Ihres Zustimmungsverwaltungssystems ermöglichen.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Element | Beschreibung |
|---|---|
| Die Kennzeichnung `disableIdSyncs` funktioniert nicht, nachdem eine Zeichenfolge übergeben wurde. | Behoben. Werte, die für den `disableidSyncs` Parameter in der `getInstance` Funktion festgelegt wurden, werden jetzt berücksichtigt. |
| iFrames von Drittanbietern erhalten kein ECID | Nicht funktionierendes ECID auf Safari Mobile und nicht funktionierende ECIDs in verschiedenen iFrames wurden behoben. |
