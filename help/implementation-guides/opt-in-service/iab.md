---
description: Verbinden Sie seine Consent Management Platform (CMP) mit dem Audience Manager-Plug-in des Opt-ins für das IAB Transparency and Consent Framework (TCF).
title: Nutzung von Opt-in-Diensten mit IAB Framework
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 100%

---

# Nutzung von Opt-in-Diensten mit IAB Framework{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>Das folgende Dokument gilt nur für IAB 2.0, für dessen Verwendung Visitor.js-Version 5.0 erforderlich ist.

Verbinden Sie die Einverständnisverwaltungs-Plattform (CMP) mit dem Opt-in-IAB Transparency and Consent Framework (TCF)-Plug-in.

Adobe Audience Manager-Kunden, die [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) verwenden, können ihre Consent Management Platform (CMP) mit dem IAB-TCF-Plugin von Opt-in verbinden. Opt-in ist eine Funktion, die in die JavaScript-Bibliothek von ECID eingebettet ist und abhängig von den in einer CMP festgelegten Besuchervoreinstellungen einzelne Adobe-Lösungsbibliotheken deaktivieren kann. Wenn das IAB-TCF-Plugin von Opt-in mit der ECID-Bibliothek implementiert wird, werden die Besucherpräferenzen aus Ihrer IAB-TCF-unterstützten CMP automatisch dem Opt-in zugeordnet. Diese Einstellungen ermöglichen es, Audience Manager-basierte Bibliotheken (DIL und ECID) und zugehörige Anrufe nach Erhalt der Zustimmung zu aktivieren.

## Implementieren einer CMP mit IAB-Unterstützung {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Führen Sie folgende Schritte aus, um das Opt-in-Objekt in das IAB-TCF zu integrieren:

1. Implementieren Sie eine CMP, die IAB unterstützt und als IAB-Anbieter registriert ist, oder entwickeln Sie intern eine CMP, die den IAB-Spezifikationen entspricht, und registrieren Sie diese als eine CMP beim IAB TCF.
1. Definieren/Laden Sie `__tcfapi`, bevor Sie Adobe-JS laden.

Weitere Details finden Sie in den [Dokumenten des Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md).

## Aktivieren des IAB-TCF-Plug-ins des Opt-ins in Ihrer ECID-Javascript-Bibliothek {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in ist nur in ECID 4.0 oder höher verfügbar.

Verwenden Sie Adobe Experience Platform Launch, um das IAB-TCF-Plugin von Opt-in für Ihre Site zu implementieren. Wenn Sie IAB für das Opt-in manuell aktivieren, überprüfen Sie, ob die folgenden Einstellungen im Besucherobjekt auf „true“ gesetzt sind:

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

Sobald die Einstellungen korrekt konfiguriert sind, werden die ECID- und DIL-Bibliotheken je nach Genehmigungskriterien des CMP und des IAB-TCF aktiviert/deaktiviert.

>[!IMPORTANT]
>
>Audience Manager benötigt eine Zustimmung für die *Zwecke 1 und 10 und die Zustimmung des Anbieters*, um Cookies bereitzustellen und ID-Synchronisationen zu starten bzw. zu berücksichtigen. Weitere Informationen zum IAB-TCF-Plugin des Opt-ins finden Sie in der [Audience Manager-Dokumentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=de).

Weitere Informationen zum Validieren des IAB-TCF-Plug-ins von Opt-in finden Sie [hier in Nutzungsszenario 4 des Validierungsleitfadens](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Verwandte Dokumentation {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) – Hier finden Sie weitere Informationen zum IAB-Standard.
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) – Hier finden Sie weitere Informationen zu Opt-in, einer erforderlichen Komponente für die Zustimmungsverwaltung in Platform-Lösungen
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=de)
* [Ihre Auswahlmöglichkeiten bezüglich Datenschutz](https://www.adobe.com/de/privacy/opt-out.html#customeruse) – Ihre Benutzer haben auch die Möglichkeit, die Datenerfassung mit anderen globalen Opt-out-Tools abzulehnen. Globales Opt-out hat Vorrang vor der Opt-in- und IAB-TCF-Überprüfung.
