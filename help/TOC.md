---
cloud: platform-cloud
audience: end-user
user-guide-title: Hilfe zum Experience Cloud Identity Service
breadcrumb-title: Identity Service-Handbuch
user-guide-description: Der Adobe Experience Cloud Identity Service bietet eine universelle, beständige ID zum Identifizieren Ihrer Besucher über alle Experience Cloud-Lösungen hinweg. Es hilft dabei, den alten Code zur ID-Generierung für Experience Cloud-Lösungen und -Services zu ersetzen.
user-guide-url: /content/help/en/id-service/using/home.html
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: ht
source-wordcount: '393'
ht-degree: 100%

---


# Hilfe zum Experience Cloud Identity Service {#using}

+ [Hilfe zum Identity Service](home.md)
+ Übersicht {#intro}
   + [Übersicht](introduction/overview.md)
   + [Über den ID-Dienst](introduction/about-id-service.md)
   + [Cookies und der ID-Service](introduction/cookies.md)
   + [Anfordern und Festlegen von IDs durch den ID-Service](introduction/id-request.md)
   + [Grundlegendes zu Synchronisierung und Übereinstimmungsraten](introduction/match-rates.md)
+ Implementierung {#implementation}
   + [Methoden der Implementierung](implementation-guides/implementation-methods.md)
   + [Handbücher zur Implementierung](implementation-guides/implementation-guides.md)
   + [Mit Experience Platform Tags implementieren](implementation-guides/ecid-implement-with-launch.md)
   + [Für Analytics implementieren](implementation-guides/setup-analytics.md)
   + [Für Target implementieren](implementation-guides/setup-target.md)
   + [Für Analytics und Audience Manager implementieren](implementation-guides/setup-aam-analytics.md)
   + [Für Analytics, Audience Manager und Target implementieren](implementation-guides/setup-aam-analytics-target.md)
   + [Nutzung des ID-Service mit A4T und Server-seitige Implementierung der Target-Komponente](implementation-guides/ecid-a4t-target.md)
   + [Direkte Integration mit dem ID-Service](implementation-guides/direct-integration.md)
   + [Direkte Integration – Anwendungsfälle](implementation-guides/direct-integration-examples.md)
   + [Testen und Überprüfen des ID-Service](implementation-guides/test-verify.md)
   + Opt-in-Service {#opt-in-service}
      + [Opt-in-Service – Übersicht](implementation-guides/opt-in-service/optin-overview.md)
      + [Einrichten des Opt-in-Service](implementation-guides/opt-in-service/getting-started.md)
      + [Validieren des Opt-in-Service](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Konfigurieren des Opt-in mithilfe von Experience Platform Launch](implementation-guides/opt-in-service/launch.md)
      + [Konfigurieren des Opt-in mithilfe von DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Steuern von Experience Cloud-Aktivitäten auf Basis des Anwendereinverständnisses](implementation-guides/opt-in-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.md)
      + [Opt-in-Nutzungsszenarios](implementation-guides/opt-in-service/use-cases.md)
      + [Opt-in-Referenz](implementation-guides/opt-in-service/api.md)
      + [Nutzen von Opt-in-Services mithilfe von IAB Framework nutzen](implementation-guides/opt-in-service/iab.md)
+ ID-Service-API {#id-service-api}
   + [ID-Service-API – Übersicht](library/library.md)
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
   + Analytics-Referenz {#analytics-reference}
      + [Analytics-Referenzübersicht](reference/analytics-reference/analytics-reference.md)
      + [CNAME-Implementierung – Übersicht](reference/analytics-reference/cname.md)
      + [Einrichten von Analytics- und Experience Cloud IDs](reference/analytics-reference/analytics-ids.md)
      + [Reihenfolge der Befehle für Analytics-IDs](reference/analytics-reference/analytics-order-of-operations.md)
      + [Entscheidungspunkte bei der Migration zum ID-Service](reference/analytics-reference/migration-decisions.md)
      + [Migrationsszenarios für den ID-Service](reference/analytics-reference/migration-scenarios.md)
      + [Analytics- und Identitätsanfragen](reference/analytics-reference/legacy-analytics.md)
      + [Serverseitige Implementierung zusammen mit JavaScript](reference/analytics-reference/server-side.md)
      + [Übergangsphase für den ID-Dienst](reference/analytics-reference/grace-period.md)
   + [Änderungen von Kennzeichnungen für Google Chrome SameSite](reference/chrome-samesite-labelling.md)
   + [Richtlinien zur Inhaltssicherheit und der ID-Service](reference/csp.md)
   + [COPPA-Unterstützung im ID-Service](reference/coppa.md)
   + [CORS-Unterstützung im ID-Service](reference/cors.md)
   + [Kunden-IDs und Authentifizierungsstatus](reference/authenticated-state.md)
   + [Methoden für die ECID-Bibliothek in einer Safari-ITP-Umgebung](reference/ecid-library-methods.md)
   + [Identifizieren von Unique Visitors](reference/unique-vis-method.md)
   + [Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem ID-Service](reference/regions.md)
   + [Voraussetzungen für den ID-Service](reference/requirements.md)
   + [Video Heartbeat und der ID-Service](reference/heartbeat.md)
   + [Data Workbench und der ID-Service](reference/dwb.md)
   + [SHA256 Hashing-Unterstützung für setCustomerIDs](reference/hashing-support.md)
+ Häufig gestellte Fragen (FAQ) {#faqs}
   + [FAQ-Übersicht](faq-intro/faq-intro.md)
   + [Häufig gestellte Fragen zum ID-Service](faq-intro/faq.md)
   + [Häufig gestellte Fragen zu Analytics und zum ID-Dienst](faq-intro/analytics-faq.md)
   + [Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen](faq-intro/other-faq.md)
+ Versionshinweise für ID-Service {#release-notes}
   + [Versionshinweise für 2020](release-notes/release-notes.md)
   + [Versionshinweise für 2019](release-notes/notes-2019.md)
   + [Versionshinweise für 2018](release-notes/notes-2018.md)
   + [Versionshinweise für 2017](release-notes/notes-2017.md)
   + [Versionshinweise für 2016](release-notes/notes-2016.md)
   + [Versionshinweise für 2015](release-notes/notes-2015.md)
+ [Analysetest im Inhaltsverzeichnis ausgeblendet](analytics-test-file-hidetoc.md)
