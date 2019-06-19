---
cloud: platform-cloud
product: Identitätsdienst
audience: Endbenutzer
user-guide-title: Hilfe zu Experience Platform Identity Service
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 1af38efa5e85c09548a6dee6c9c550900f90a8ed

---


# Hilfe zum Identitätsdienst {#using}

+ [Hilfe zum Identitätsdienst](home.md)
+ Übersicht  {#intro}
   + [Übersicht  ](introduction/overview.md)
   + [Informationen zum Identitätsdienst](introduction/about-id-service.md)
   + [Cookies und der Identitätsdienst](introduction/cookies.md)
   + [Anfordern und Festlegen von IDs durch den Identitätsdienst](introduction/id-request.md)
   + [Synchronisierung und Übereinstimmungsraten](introduction/match-rates.md)
+ Implementierungshandbücher {#implementation-guides}
   + [Implementierungshandbücher](implementation-guides/implementation-guides.md)
   + [Implementierungsmethoden](implementation-guides/implementation-methods.md)
   + [Implementieren mit Launch](implementation-guides/ecid-implement-with-launch.md)
   + [Implementierung mit DTM](implementation-guides/standard.md)
   + [Für Analytics implementieren](implementation-guides/setup-analytics.md)
   + [Für Target implementieren](implementation-guides/setup-target.md)
   + [Implementierung für Analytics und Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [Implementierung für Analytics, Audience Manager und Target](implementation-guides/setup-aam-analytics-target.md)
   + [Verwenden des Identitätsdiensts mit A 4 T und einer serverseitigen Implementierung von Target](implementation-guides/ecid-a4t-target.md)
   + [Direkte Integration mit dem Identitätsdienst](implementation-guides/direct-integration.md)
   + [Nutzungsszenarios im Zusammenhang mit einer direkten Integration](implementation-guides/direct-integration-examples.md)
   + [Testen und Überprüfen des Identitätsdiensts](implementation-guides/test-verify.md)
   + Dokumentation-Dokumentation {#opt-in-service}
      + [Überblick über die Anmeldung](implementation-guides/opt-in-service/optin-overview.md)
      + [Einrichten des Opt-In-Dienstes](implementation-guides/opt-in-service/getting-started.md)
      + [Überprüfung der Anmeldung](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [Konfigurieren von Opt-in mit Launch](implementation-guides/opt-in-service/launch.md)
      + [Konfigurieren von Opt-in mit DTM](implementation-guides/opt-in-service/optin-dtm.md)
      + [Opt-in-Nutzungsszenarios](implementation-guides/opt-in-service/use-cases.md)
      + [Opt-in-Referenz](implementation-guides/opt-in-service/api.md)
      + [(Beta) Verwenden von Anmeldediensten mit IAB Framework](implementation-guides/opt-in-service/iab.md)
+ API für den Identitätsdienst {#id-service-api}
   + [Identitätsdienst-API-Übersicht](library/library.md)
   + Konfiguration {#configurations}
      + [Konfigurationen - Übersicht](library/function-vars/function-vars.md)
      + [audienceManagerServer und audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [isCoopSafe](library/function-vars/coopsafe.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
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
      + [Einstellen von Analytics und Identitys](reference/analytics-reference/analytics-ids.md)
      + [Reihenfolge der Befehle für Analytics-IDs](reference/analytics-reference/analytics-order-of-operations.md)
      + [Entscheidungspunkte für die Migration von Identitätsdiensten](reference/analytics-reference/migration-decisions.md)
      + [Migrationsszenarios für Identitätsdienst](reference/analytics-reference/migration-scenarios.md)
      + [Analytics- und Identitätsanforderungen](reference/analytics-reference/legacy-analytics.md)
      + [Datenerfassungs-CNAMEs und domänenübergreifendes Tracking](reference/analytics-reference/cname.md)
      + [Serverseitige Implementierung zusammen mit JavaScript](reference/analytics-reference/server-side.md)
      + [Die Übergangsphase für den Identitätsdienst](reference/analytics-reference/grace-period.md)
   + [Content Security Policies und der Identitätsdienst](reference/csp.md)
   + [COPPA-Unterstützung im Identitätsdienst](reference/coppa.md)
   + [CORS-Unterstützung im Identitätsdienst](reference/cors.md)
   + [Kunden-IDs und Authentifizierungsstatus](reference/authenticated-state.md)
   + [ECID-Bibliotheksmethoden in einer Safari ITP-Welt](reference/ecid-library-methods.md)
   + [Abrufen von Regions- und Benutzer-IDs aus dem AMCV-Cookie oder dem Identitätsdienst](reference/regions.md)
   + [Anforderungen für den Identitätsdienst](reference/requirements.md)
   + [Video Heartbeat und der Identitätsdienst](reference/heartbeat.md)
   + [Data Workbench und der Identitätsdienst](reference/dwb.md)
+ Häufig gestellte Fragen (FAQ){#faqs}
   + [Häufig gestellte Fragen - Übersicht](faq-intro/faq-intro.md)
   + [Häufig gestellte Fragen zum Identitätsdienst](faq-intro/faq.md)
   + [Häufig gestellte Fragen zu Analytics und Identitätsdienst](faq-intro/analytics-faq.md)
   + [Häufig gestellte Fragen zu anderen Experience Cloud-Lösungen](faq-intro/other-faq.md)
+ Versionshinweise für den Identitätsdienst {#release-notes}
   + [Versionshinweise für 2019](release-notes/release-notes.md)
   + [Versionshinweise für 2018](release-notes/notes-2018.md)
   + [Versionshinweise für 2017](release-notes/notes-2017.md)
   + [Versionshinweise für 2016](release-notes/notes-2016.md)
   + [Versionshinweise für 2015](release-notes/notes-2015.md)
