---
description: Verbinden der Consent Management Platform (CMP) mit dem Audience Manager-Plugin der Opt-in-Funktion für das IAB Transparency and Consent Framework (TCF).
seo-description: Verbinden der Consent Management Platform (CMP) mit dem Audience Manager-Plugin für IAB Transparency and Consent Framework (TCF).
seo-title: Nutzung von Opt-in-Diensten mit IAB Framework
title: Nutzung von Opt-in-Diensten mit IAB Framework
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: 4c37c8dd3b76dbf17b955864f0562363350eaecd
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 71%

---


# Nutzung von Opt-in-Diensten mit IAB Framework {#using-opt-in-services-with-iab-framework}

>[!IMPORTANT] Das folgende Dokument gilt nur für IAB 2.0. Benutzer müssen Besucher.js Version 5.0 verwenden, um mit IAB 2.0 zu arbeiten.

Schließen Sie die Consent Management Platform (CMP) mit dem OPT-in-Plugin IAB Transparency and Consent Framework (TCF) an.

Adobe Audience Manager-Kunden, die [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) verwenden, können ihre Consent Management Platform (CMP) mit dem IAB-TCF-Plugin von Opt-in verbinden. Opt-in ist eine Funktion, die in die JavaScript-Bibliothek von ECID eingebettet ist und abhängig von den in einer CMP festgelegten Besuchervoreinstellungen einzelne Adobe-Lösungsbibliotheken deaktivieren kann. Wenn das IAB-TCF-Plugin von Opt-in mit der ECID-Bibliothek implementiert ist, werden die Voreinstellungen des Besuchers aus Ihrem CMP, der IAB TCF unterstützt, automatisch der Opt-in-Funktion zugeordnet. Diese Einstellungen ermöglichen es, Audience Manager-basierte Bibliotheken (DIL und ECID) und zugehörige Anrufe nach Erhalt der Zustimmung zu aktivieren.

## Implementieren einer CMP mit IAB-Unterstützung {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Führen Sie folgende Schritte aus, um das Opt-in-Objekt in das IAB-TCF zu integrieren:

1. Implementieren Sie eine CMP, die das IAB unterstützt und [als IAB-Anbieter registriert ist](https://vendorlist.consensu.org/vendorlist.json), oder entwickeln Sie intern eine CMP, die den IAB-Spezifikationen entspricht, und registrieren Sie diese bei IAB-TCF.
1. Definieren/Laden Sie `__tcfapi`, bevor Sie Adobe-JS laden.

Weitere Details finden Sie in den [Dokumenten des Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md).

## Enable Opt-in&#39;s IAB TCF plugin within your ECID Javascript Library {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>Opt-in ist nur in ECID 4.0 oder höher verfügbar.

Verwenden Sie Adobe Experience Platform Launch, um das IAB-TCF-Plugin für Ihre Site zu implementieren. Wenn Sie IAB für das Opt-in manuell aktivieren, überprüfen Sie, ob die folgenden Einstellungen im Besucherobjekt auf „true“ gesetzt sind:

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

Sobald die Einstellungen korrekt konfiguriert sind, werden die ECID- und DIL-Bibliotheken je nach Genehmigungskriterien des CMP und des IAB-TCF aktiviert/deaktiviert.

>[!IMPORTANT]
>
>Audience Manager benötigt eine Zustimmung für die *Zwecke 1 und 10 und die Zustimmung des Anbieters*, um Cookies bereitzustellen und ID-Synchronisationen zu starten bzw. zu berücksichtigen. Read more about the Opt-in&#39;s IAB TCF plugin in Audience Manager documentation [here](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).

For more information on how to validate Opt-in&#39;s IAB TCF plugin, check use case #4 in the validation guide [here](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Verwandte Dokumentation {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB Transparency and Consent Framework (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) – Hier finden Sie weitere Informationen zum IAB-Standard.
* [Adobe Opt-in](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) – Hier finden Sie weitere Informationen zu Opt-in, einer erforderlichen Komponente für die Zustimmungsverwaltung in Platform-Lösungen
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [Ihre Auswahlmöglichkeiten bezüglich Datenschutz](https://www.adobe.com/de/privacy/opt-out.html#customeruse) – Ihre Benutzer haben auch die Möglichkeit, die Datenerfassung mit anderen globalen Opt-out-Tools abzulehnen. Globales Opt-out hat Vorrang vor der Opt-in- und IAB-TCF-Überprüfung.