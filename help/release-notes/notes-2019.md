---
description: Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Besucher-ID-Service.
keywords: Besucher-ID-Service
title: Versionshinweise für 2019
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
TQID: https://experienceleague.adobe.com/KnO04dnP6z7gKrr8vkFiiToDSBfClpiOJkGq8949ahA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 426
ht-degree: 67%

---

# Versionshinweise für 2019 {#release-notes}

Funktionsveröffentlichungen, Aktualisierungen oder Änderungen des Besucher-ID-Service.

## Version 4.4.1

Checkbox für die Pre-Opt-in-Genehmigung für Media Analytics in der [!UICONTROL Experience Cloud ID Service] Tag-Erweiterung hinzufügen.

**Fehlerkorrekturen**

* Problem mit dem Parsen der Eingabezeichenfolge für [!UICONTROL Experience Cloud ID Service] Tag-Erweiterung „preOptInApprovals“.
* Performance-Abfall bei Verwendung von trackingServer.

## Version 4.4 {#version-4point4}

**Neue Funktion**

[SHA-256-Hash-Unterstützung für setCustomerIDs](/help/reference/hashing-support.md). Der Besucher-ID-Dienst (ECID) unterstützt den SHA-256-Hash-Algorithmus, mit dem Sie Kunden-IDs oder E-Mail-Adressen eingeben und Hash-IDs weitergeben können.

**Korrekturen und Verbesserungen**

* Die Konfiguration von `cookieDomain` wurde aktualisiert. Die ECID-Bibliothek filtert jetzt die leere Zeichenfolge `cookieDomain` in `initConfig` heraus und verwendet die Cookie-Domäne auf oberster Ebene, die durch die getDomain-Methode zurückgegeben wird.
* Ein Fehler wurde in Zusammenhang mit `getVisitorValues` in `localVisitor` behoben.
* Ein Fehler wurde behoben, durch den im Safari-Browser eine Abweichung beim MCOPTOUT-Wert aufgetreten ist, der von der `getVisitorValue`-Methode zurückgegeben wird.
* Die Opt-in-Bibliothek wurde aktualisiert, indem `optIn.off` zur Abmeldung von Ereignissen hinzugefügt wurde.
* Ein Fehler in Zusammenhang mit der setTimeout-Funktion wurde behoben, bei der `setTimeout` die Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) auf einigen Kunden-Sites verletzt hat.

## Version 4.3 {#version-4point3}

**Unterstützung für ITP 2.1**. Wenn ein Trackingserver mit einem Erstanbieter-CNAME eingerichtet ist, wird ein neues Cookie (s_ecid) zum ECID-Wert hinzugefügt. Die ECID-Bibliothek verweist auf den Wert, damit die ID über 7 Tage hinaus erhalten bleibt. Siehe [ECID-Bibliotheksmethoden in einer Safari-ITP-Umgebung](/help/reference/ecid-library-methods.md).

**Fehlerbehebung für secureCookie config.**

## Version 4.1

Aktualisierung von `publishDestinations` durch die Änderung in der neuen API. Mit dieser Aktualisierung können die Referrer-Informationen der Seite während der ID-Synchronisierung offengelegt werden, wenn gewünscht.

## Version 4.2

Unterstützung für das Audience Manager-Plug-in für IAB TCF, das über das Objekt „ECID Opt-in“ verfügbar ist.

**Fehlerkorrekturen**

* IAB + Opt-in kann keine MID für den erneuten Besuch von Kunden abrufen.
* Es wurde ein Fehler bei der doOptInApply-Opt-in-Konfiguration behoben.
* ECID-Opt-out deaktiviert ID-Synchronisationen.

## Version 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Opt-in-Dienst**. Opt-in ist eine Erweiterung der ECID, mit der Sie steuern können, ob (und welche) CX Enterprise-Bibliotheken Cookies auf Web-Seiten für Besucher erstellen können. Mit [Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) können Sie die Einholung von Einverständniserklärungen für Besucher zur CX Enterprise-Lösung vereinfachen, indem Sie Analytics, Target, Audience Manager und andere oder alle ausgewählten CX Enterprise-Lösungen für das Opt-in bei Ihrem Einverständnisverwaltungssystem aktivieren.

## Version 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Element | Beschreibung |
|---|---|
| Die Kennzeichnung `disableIdSyncs` funktioniert nicht, nachdem eine Zeichenfolge übergeben wurde. | Behoben. Werte, die für den `disableidSyncs` Parameter in der `getInstance` Funktion festgelegt wurden, werden jetzt berücksichtigt. |
| iFrames von Drittanbietern erhalten kein ECID | Nicht funktionierendes ECID auf Safari Mobile und nicht funktionierende ECIDs in verschiedenen iFrames wurden behoben. |

