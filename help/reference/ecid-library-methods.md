---
title: Methoden für die ECID-Bibliothek in einer Safari-ITP-Umgebung
seo-title: Methoden für die ECID-Bibliothek in einer Safari-ITP-Umgebung
description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
seo-description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
translation-type: ht
source-git-commit: 012bf5db473b37b17e7af957c08da71b253c718f
workflow-type: ht
source-wordcount: '810'
ht-degree: 100%

---


# Methoden für die ECID-Bibliothek in einer Safari-ITP-Umgebung

>[!NOTE]
>
>Es wurden Aktualisierungen vorgenommen, um die neuesten Änderungen an ITP widerzuspiegeln, die am 12. November 2020 als Teil der Big Sur OS-Version veröffentlicht wurden.

Da Safari per ITP das domänenübergreifende Tracking einschränkt, setzt Adobe für Bibliotheken Best Practices ein, die einerseits Kunden unterstützen und andererseits auch den Datenschutz und die Wahlfreiheit der Konsumenten berücksichtigen.

Seit dem 10. November 2020 gilt für alle durch die API „document.cookie“ festgelegten persistenten Cookies von Erstanbietern, die häufig als „Client-seitige“ Cookies bezeichnet werden, sowie für Cookies, die durch CNAME-Implementierungen von Erstanbietern in Safari und mobilen iOS-Browsern gesetzt werden, eine Gültigkeit von sieben Tagen. Drittanbieter-Cookies werden, wie in früheren Versionen von ITP beschrieben, weiterhin blockiert. Weitere Informationen zu ITP 2.1 seinen Auswirkungen auf Adobe-Lösungen finden Sie im Artikel [Safari ITP 2.1 Impact on Adobe Experience Cloud and Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Änderungen, Methoden und Konfigurationen in Verbindung mit ITP

Wenn zusätzliche Methoden zum Tracking in Safari entwickelt werden, werden sie auf dieser Seite hinzugefügt.

>[!NOTE]
>
>Für die folgende Dokumentation gilt: *ECID* = *MID* = *MCID*.

Unten finden Sie weitere Informationen zu ITP und zur Nutzung der ECID-Bibliothek.

## Aktuelles Verhalten der ECID-Bibliothek mit ITP und dem WebKit von Apple

ITP 2.1 beeinträchtigt die Möglichkeit, clientseitige Cookies zu schreiben, wodurch Kunden keine präzisen Besucher-Trackinginformationen bereitgestellt werden können. Daher wurden die CNAME-Trackingserver von Adobe dahingehend angepasst, dass die Experience Cloud ID (ECID) eines Besuchers jetzt in einem Erstanbieter-Cookie gespeichert wird.

Diese Änderung ist nur für ECID-Kunden hilfreich, die einen Analytics-CNAME im Erstanbieterkontext verwenden. Wenn Sie Analytics-Kunde sind, der derzeit keinen CNAME verwendet, oder kein Analytics-Kunde sind, sind Sie dennoch zu einem CNAME-Datensatz berechtigt. Wenden Sie sich an die Kundenunterstützung oder Ihren Kundenbetreuer, um sich für einen [CNAME](https://docs.adobe.com/content/help/de-DE/core-services/interface/ec-cookies/cookies-first-party.html) zu registrieren.

Führen Sie ein Upgrade auf eine Version ab ECID-Bibliothek v. 4.3.0 durch, um diese Änderung nutzen zu können.

Im Folgenden werden das Verhalten der ECID-Bibliothek mit ITP 2.1 und die neuesten Änderungen erläutert, die Apple im Rahmen der Big Sur-Version vorgenommen hat.

**Design**

Sobald eine ID-Anforderung an demdex.net gesendet und eine ECID abgerufen wird, wird eine ID-Anforderung an die Domäne des Kunden gesendet, sofern ein Trackingserver in Ihrer ECID-Bibliothek eingerichtet ist. Dieser Endpunkt liest den ecid-Parameter aus der Abfragezeichenfolge und setzt ein neues [Cookie](/help/introduction/cookies.md), das nur die ECID und ein Ablaufdatum umfasst, das zwei Jahre in der Zukunft liegt. Jedes Mal, wenn dieser Endpunkt auf diese Weise aufgerufen wird, wird das `s_ecid`-Cookie mit einem Ablaufdatum von zwei Jahren ab dem Zeitpunkt dieses Aufrufs umgeschrieben. Die ECID-Bibliothek muss auf Version 4.3.0 aktualisiert werden, damit der Wert dieses Cookies abgerufen werden kann.

>[!IMPORTANT]
>
>Im Rahmen der Big Sur-Aktualisierungen wird ein über CNAME festgelegtes `s_ecid` Cookie auch sieben Tage bis zu seinem Ablauf gespeichert.

Dieses neue `s_ecid`-Cookie hat denselben Opt-out-Status wie das AMCV-Cookie. Wenn die ECID im `s_ecid`-Cookie gelesen wird, wird demdex sofort aufgerufen, um den aktuellen Opt-out-Status für diese ID abzufragen, und im AMCV-Cookie gespeichert.

Wenn sich Ihr Kunde per Opt-out vom Analytics-Tracking anhand dieser [Methode](https://docs.adobe.com/content/help/de-DE/analytics/implementation/js/opt-out.html) abgemeldet hat, wird dieses `s_ecid`-Cookie gelöscht.

Der Name des Trackingservers sollte der VisitorJS-Bibliothek unter Verwendung von `trackingServer` oder `trackingServerSecure` bereitgestellt werden, wenn die Bibliothek initialisiert wird. Dies sollte mit der `trackingServer`-Konfiguration in den Analytics-Konfigurationen übereinstimmen.

Wenn Sie sich gegen diese Methode entscheiden, fügen Sie Ihrer ECID-Bibliotheksimplementierung die folgende Konfiguration hinzu: `discardtrackingServerECID`. Wenn diese Konfiguration auf „true“ gesetzt ist, liest die Visitor-Bibliothek die vom Erstanbieter-Trackingserver festgelegte MID nicht.

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
