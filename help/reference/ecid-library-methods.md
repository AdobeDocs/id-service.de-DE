---
title: Methoden für die ECID-Bibliothek in einer Safari-ITP-Umgebung
seo-title: Methoden für die ECID-Bibliothek in einer Safari-ITP-Umgebung
description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
seo-description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 100%

---


# Methoden für die ECID-Bibliothek in einer Safari-ITP-Umgebung

Da Safari per ITP das domänenübergreifende Tracking einschränkt, setzt Adobe für Bibliotheken Best Practices ein, die einerseits Kunden unterstützen und andererseits auch den Datenschutz und die Wahlfreiheit der Konsumenten berücksichtigen.

Am 21. Februar 2019 gab Apple das aktuelle Update von ITP (Intelligent Tracking Prevention) bekannt. Im Gegensatz zu früheren Versionen, die sich auf Drittanbieter-Cookies konzentrierten, stehen in dieser Version neue Trackingmaßnahmen für Erstanbieter-Cookies im Vordergrund. Die Gültigkeit aller persistenten Cookies von Erstanbietern, die über die document.cookie-API gesetzt werden (auch „clientseitige Cookies“ genannt), ist auf sieben Tage begrenzt. Drittanbieter-Cookies werden. wie in früheren Versionen von ITP beschrieben, blockiert. Weitere Informationen zu ITP 2.1 seinen Auswirkungen auf Adobe-Lösungen finden Sie im Artikel [Safari ITP 2.1 Impact on Adobe Experience Cloud and Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Häufig gestellte Fragen zu Adobe ECID für Safari ITP

**Warum hat ITP 2.1 Einfluss auf das AMCV-Cookie, das von der Experience Cloud ID-Bibliothek (ECID) in der Erstanbieterdomäne eines Kunden gesetzt wird?**

Das AMCV-Cookie basiert derzeit auf der document.cookie-API und wird „clientseitig“ gesetzt. Safari bevorzugt Cookies, die vom Server eines Kunden gesetzt werden.

**Warum ist ein Cookie, das über einen CNAME-Trackingserver gesetzt wurde, zum Tracking in Safari besser?**

Die ITP-Regeln haben zum Ziel, den Entwicklern wieder mehr Kontrolle zu geben. Implementierungen über CNAME-Zertifikate können nicht allein über JavaScript erfolgen. Das CNAME-Zertifizierungsprogramm von Adobe (serverseitiges Tracking) ist im Einklang mit ITP und seit vielen Jahren Teil der Adobe-Strategie. Die ECID-Bibliothek bietet Methoden zum Wechsel von der Nutzung der ECID-Bibliothek zur CNAME-Implementierung.

**Warum konzentriert sich Adobe auf die ECID-Bibliothek, wenn heute mit CNAMEs andere Analytics-Methoden zum Besuchertracking verwendet werden?**

Anfangs wurden die ECID-Bibliothek, AMCV-Cookies und ECID (d. h. MID) als Methoden zur Integration aller Adobe-Lösungen in einer ID verwendet. Diese ID wird weiterhin die vorrangige Cookie-ID im Adobe-Produktportfolio sein. Sie ist auch die Standard-Cookie-ID für die Adobe Experience Platform.

**Helfen CNAMEs Kunden beim domänenübergreifenden Tracking?**

Es gelten dieselben Regeln und Einschränkungen bei CNAMEs wie zuvor. In manchen Fällen können CNAMEs bei einem Szenario mit mehreren Domänen hilfreich sein. Wenn eine Haupteinstiegs-Website vorhanden ist, über die Benutzer vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das Tracking mehrerer Domänen für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren. Doch obwohl CNAMEs in bestimmten Fällen in Umgebungen mit mehreren Domänen hilfreich sein können, liegt der Grund für den Umstieg von ECID auf CNAME-Implementierungen in der dauerhaften Besucheridentifizierung, und nicht im domänenübergreifenden Tracking. Weitere Informationen zu CNAME und dem domänenübergreifenden Tracking finden Sie unter [Datenerfassungs-CNAMEs und domänenübergreifendes Tracking](/help/reference/analytics-reference/cname.md).

Diese FAQs werden erweitert, sobald zusätzliche Änderungen bei ITP veröffentlicht werden. Weitere Informationen finden Sie unter [Adobe Experience League](https://experienceleague.adobe.com/?lang=de#recommended/solutions/analytics).

## Änderungen, Methoden und Konfigurationen in Verbindung mit ITP

Wenn zusätzliche Methoden zum Tracking in Safari entwickelt werden, werden sie auf dieser Seite hinzugefügt.

>[!NOTE]
>
>*Für die folgende Dokumentation gilt: ECID* = *MID* = *MCID*.

Unten finden Sie weitere Informationen zu ITP und zur Nutzung der ECID-Bibliothek.

## Verwendung der ECID-Bibliothek und des CNAME-Trackings, um die Gültigkeit der Besucher-ID zu verlängern

ITP 2.1 beeinträchtigt die Möglichkeit, clientseitige Cookies zu schreiben, wodurch Kunden keine präzisen Besucher-Trackinginformationen bereitgestellt werden können. Daher wurden die CNAME-Trackingserver von Adobe dahingehend angepasst, dass die Experience Cloud ID (ECID) eines Besuchers in einem Erstanbieter-Cookie gespeichert wird.

Diese Änderung ist nur für ECID-Kunden hilfreich, die einen Analytics-CNAME im Erstanbieterkontext verwenden. Wenn Sie Analytics-Kunde sind, der derzeit keinen CNAME verwendet, oder kein Analytics-Kunde sind, sind Sie dennoch zu einem CNAME-Datensatz berechtigt. Wenden Sie sich an die Kundenunterstützung oder Ihren Kundenbetreuer, um sich für einen [CNAME](https://docs.adobe.com/content/help/de-DE/core-services/interface/ec-cookies/cookies-first-party.html) zu registrieren.

Führen Sie ein Upgrade auf eine Version ab ECID-Bibliothek v. 4.3.0 durch, um diese Änderung nutzen zu können.

**Design**

Sobald eine ID-Anforderung an demdex.net gesendet und eine ECID abgerufen wird, wird eine ID-Anforderung an die Domäne des Kunden gesendet, sofern ein Trackingserver in Ihrer ECID-Bibliothek eingerichtet ist. Dieser Endpunkt liest den ecid-Parameter aus der Abfragezeichenfolge und setzt ein neues [Cookie](/help/introduction/cookies.md), das nur die ECID und ein Ablaufdatum umfasst, das zwei Jahre in der Zukunft liegt. Jedes Mal, wenn dieser Endpunkt auf diese Weise aufgerufen wird, wird das `s_ecid`-Cookie mit einem Ablaufdatum von zwei Jahren ab dem Zeitpunkt dieses Aufrufs umgeschrieben. Die ECID-Bibliothek muss auf Version 4.3.0 aktualisiert werden, damit der Wert dieses Cookies abgerufen werden kann.

Dieses neue `s_ecid`-Cookie hat denselben Opt-out-Status wie das AMCV-Cookie. Wenn die ECID im `s_ecid`-Cookie gelesen wird, wird demdex sofort aufgerufen, um den aktuellen Opt-out-Status für diese ID abzufragen, und im AMCV-Cookie gespeichert.

Wenn sich Ihr Kunde per Opt-out vom Analytics-Tracking anhand dieser [Methode](https://docs.adobe.com/content/help/de-DE/analytics/implementation/js/opt-out.html) abgemeldet hat, wird dieses `s_ecid`-Cookie gelöscht.

Der Name des Trackingservers sollte der VisitorJS-Bibliothek bereitgestellt werden, wenn die Bibliothek per trackingServer oder trackingServerSecure initialisiert wird. Dies sollte mit der trackingServer-Konfiguration in den Analytics-Konfigurationen übereinstimmen.

Wenn Sie sich gegen diese Methode entscheiden, fügen Sie Ihrer ECID-Bibliotheksimplementierung die folgende Konfiguration hinzu: discardtrackingServerECID. Wenn diese Konfiguration auf „true“ gesetzt ist, liest die Besucherbibliothek die vom Erstanbieter-Trackingserver festgelegte MID nicht.

![](assets/itp-proposal-v1.png)

## Verwendung der appendVisitorIDsTo-Methode für das domänenübergreifende Tracking (innerhalb der Domänen Ihres Unternehmens)

Mit dieser Funktion können Sie die ECID domänenübergreifend freigeben, wenn Browser Drittanbieter-Cookies blockieren. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst implementiert haben und Inhaber der Quell- und Zieldomäne sein. Verfügbar in VisitorAPI.js-Version 1.7.0 oder höher (jedoch nicht in Version 1.10.0).

**Design**

* Wenn ein Besucher zu Ihren anderen Domänen navigiert, gibt Visitor.appendVisitorIDsTo(url) eine URL zurück, bei der ECID als Abfrageparameter angehängt ist.

   Verwenden Sie diese URL zur Umleitung von der ursprünglichen Domäne zur Zieldomäne.

* Der ID-Dienstcode auf der Zieldomäne extrahiert die ECID aus der URL, statt bei Adobe eine neue Besucher-ID anzufordern.

   Diese Anforderung schließt die Drittanbieter-Cookie-ID ein, die in diesem Fall nicht verfügbar ist.

* Der ID-Dienstcode auf der Zielseite verwendet die übergebene ECID zum Tracken des Besuchers.

   >[!NOTE]
   >Wenn die Zielseite bereits über eine ECID aus vorherigen Besuchen verfügt, wird die Entscheidung, das vorhandene Cookie zu überschreiben, von der Konfiguration overwriteCrossDomainMCIDAndAID gesteuert. Weitere Informationen zu dieser Konfiguration finden Sie unter [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md).
   >
   >Weitere Informationen zu dieser Methode finden Sie auf der Seite [appendVisitorIDsTo (Cross Domain Tracking)](/help/library/get-set/appendvisitorid.md).
