---
audience: end-user
user-guide-title: Hilfe zum Adobe-Besucher-ID-Service
breadcrumb-title: Handbuch für den Besucher-ID-Service
user-guide-description: Der Besucher-ID-Dienst von Adobe bietet eine universelle, beständige ID zum Identifizieren Ihrer Besucher über alle Lösungen in CX Enterprise hinweg. Es hilft dabei, den alten Code zur ID-Generierung für CX Enterprise-Lösungen und -Services zu ersetzen.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: 7621dc8925235bd3cf159a404741bd02fc9b6a77
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 45%

---


# Hilfe zum Adobe-Besucher-ID-Service {#using}

+ [Hilfe zum Besucher-ID-Service](home.md)
+ Überblick {#intro}
   + [Überblick](introduction/overview.md)
   + [Über den Besucher-ID-Service](introduction/about-id-service.md)
   + [Cookies und der Besucher-ID-Dienst](introduction/cookies.md)
   + [Anfordern und Festlegen von IDs durch den Besucher-ID-Service](introduction/id-request.md)
   + [Grundlegendes zu Synchronisierung und Übereinstimmungsraten](introduction/match-rates.md)
+ Implementierung {#implementation}
   + [Methoden der Implementierung](implementation-guides/implementation-methods.md)
   + [Handbücher zur Implementierung](implementation-guides/implementation-guides.md)
   + [Mit Tags implementieren](implementation-guides/ecid-implement-with-launch.md)
   + [Für Analytics implementieren](https://experienceleague.adobe.com/de/docs/analytics/implementation/id/overview){target=_blank}
   + [Für Target implementieren](implementation-guides/setup-target.md)
   + [Für Analytics und Audience Manager implementieren](implementation-guides/setup-aam-analytics.md)
   + [Für Analytics, Audience Manager und Target implementieren](implementation-guides/setup-aam-analytics-target.md)
   + [Verwenden des Besucher-ID-Service mit A4T und einer serverseitigen Implementierung der Target-Komponente](implementation-guides/ecid-a4t-target.md)
   + [Direkte Integration mit dem Besucher-ID-Service](implementation-guides/direct-integration.md)
   + [Direkte Integration – Anwendungsfälle](implementation-guides/direct-integration-examples.md)
   + [Testen und Überprüfen des Besucher-ID-Service](implementation-guides/test-verify.md)
   + Opt-in-Service {#opt-in-service}
      + [Opt-in-Service – Übersicht](implementation-guides/opt-in-service/optin-overview.md)
      + [Einrichten des Opt-in-Service](implementation-guides/opt-in-service/getting-started.md)
      + [Validieren des Opt-in-Service](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Konfigurieren von Opt-in mit Tags](implementation-guides/opt-in-service/launch.md)
      + [Steuern von CX-Unternehmensaktivitäten auf Basis des Benutzereinverständnisses](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Opt-in-Nutzungsszenarios](implementation-guides/opt-in-service/use-cases.md)
      + [Opt-in-Referenz](implementation-guides/opt-in-service/api.md)
      + [Nutzen von Opt-in-Services mithilfe von IAB Framework nutzen](implementation-guides/opt-in-service/iab.md)
+ Visitor ID Service-API {#id-service-api}
   + [Übersicht über die Besucher-ID-Service-API](library/library.md)
   + Konfiguration {#configurations}
      + [Konfigurationsübersicht](library/function-vars/function-vars.md)
      + [audienceManagerServer und audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [Secure- und SameSite-Konfigurationen](library/function-vars/secure-samesite-config.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain und whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + Methoden {#methods}
      + [Methoden](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (domänenübergreifendes Tracking)](library/get-set/appendvisitorid.md)
      + [callTimeOut-Methoden](library/get-set/timeout-functions.md)
      + [ID-Synchronisation nach URL oder Datenquelle](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ Referenz {#reference}
   + [Referenzübersicht](reference/reference.md)
   + [Änderungen von Labels für Google Chrome SameSite](reference/chrome-samesite-labelling.md)
   + [Inhaltssicherheitsrichtlinien und der Besucher-ID-Service](reference/csp.md)
   + [COPPA-Unterstützung im Besucher-ID-Service](reference/coppa.md)
   + [CORS-Unterstützung im Besucher-ID-Service](reference/cors.md)
   + [Kunden-IDs und Authentifizierungsstatus](reference/authenticated-state.md)
   + [Methoden für die ECID-Bibliothek in einer Safari-ITP-Umgebung](reference/ecid-library-methods.md)
   + [Identifizieren von Unique Visitors](reference/unique-vis-method.md)
   + [Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem Besucher-ID-Service](reference/regions.md)
   + [Voraussetzungen für den Besucher-ID-Service](reference/requirements.md)
   + [Video Heartbeat und der Besucher-ID-Service](reference/heartbeat.md)
   + [SHA256 Hashing-Unterstützung für setCustomerIDs](reference/hashing-support.md)
+ Häufig gestellte Fragen (FAQ) {#faqs}
   + [FAQ-Übersicht](faq-intro/faq-intro.md)
   + [Häufig gestellte Fragen zum Besucher-ID-Service](faq-intro/faq.md)
   + [Häufig gestellte Fragen zu anderen CX Enterprise-Lösungen](faq-intro/other-faq.md)
+ Versionshinweise für den Besucher-ID-Service {#release-notes}
   + [Versionshinweise für 2022](release-notes/notes-2022.md)
   + [Versionshinweise für 2021](release-notes/notes-2021.md)
   + [Versionshinweise für 2020](release-notes/notes-2020.md)
   + [Versionshinweise für 2019](release-notes/notes-2019.md)
   + [Versionshinweise für 2018](release-notes/notes-2018.md)
   + [Versionshinweise für 2017](release-notes/notes-2017.md)
   + [Versionshinweise für 2016](release-notes/notes-2016.md)
   + [Versionshinweise für 2015](release-notes/notes-2015.md)
