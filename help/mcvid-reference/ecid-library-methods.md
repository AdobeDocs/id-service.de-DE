---
title: ECID-Bibliotheksmethoden in einer Safari ITP-Welt
seo-title: ECID-Bibliotheksmethoden in einer Safari ITP-Welt
description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
seo-description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
translation-type: tm+mt
source-git-commit: 1dd8b109f7e9567b5f72747ecc653d35d0942413

---


# ECID-Bibliotheksmethoden in einer Safari ITP-Welt

Da Safari die domänenübergreifende Verfolgung über ITP aufhebt, muss Adobe Best Practices für Bibliotheken aufrechterhalten, die Kunden unterstützen, sowie die Privatsphäre und Auswahl von Verbrauchern.

Am 21. Februar 2019 kündigte Apple das letzte Update an ITP an (intelligente Verfolgung der Verfolgung). Im Gegensatz zu früheren Versionen, die sich auf Drittanbieter-Cookies konzentrieren, werden in dieser Version neue Verfolgungsmaßnahmen für Erstanbieter-Cookies beschrieben. Alle beständigen Cookies von Erstanbietern, die über die document. cookie API, häufig als &quot;clientseitige Cookies&quot; bezeichnet, festgelegt werden, haben ihre Gültigkeit um 7 Tage begrenzt. Drittanbieter-Cookies werden wie in früheren Versionen von ITP beschrieben blockiert. Weitere Informationen zu ITP 2.1 und den Auswirkungen von Adobe-Lösungen finden Sie unter [Safari ITP 2.1 Auswirkungen auf Adobe Experience Cloud- und Experience Platform-Kunden](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Häufig gestellte Fragen zu Adobe ECID für Safari-ITP

**Warum hat das AMCV-Cookie, das von der Experience Cloud ID-Bibliothek (ECID) in der Domäne einer Kunden (ECID) gesetzt wird, von ITP 2.1 beeinflusst?**

Der AMCV-Cookie beruht derzeit auf der document. cookie API und wird über &quot;clientseitig&quot; festgelegt. Safari bevorzugt Cookies, die vom Server eines Kunden gesetzt werden.

**Warum wird ein Cookie, das über einen CNAME-Tracking-Server festgelegt wurde, eine bessere Option zur Verfolgung in Safari?**

Die Regeln des ITP konzentrieren sich auf die Kontrolle der Entwickler. Implementierungen über CNAME-Zertifikate können nicht allein über javascript ausgeführt werden. Das CNAME-Zertifizierungsprogramm von Adobe (serverseitige Verfolgung) ist mit ITP in Einklang und ist seit vielen Jahren Teil der Adobe-Strategie. Die ECID-Bibliothek gibt Methoden zum Verschieben der ECID-Bibliotheksfunktionalität in eine CNAME-Implementierung frei.

**Warum konzentriert sich Adobe auf die ECID-Bibliothek, wenn andere Analytics-Besucherverfolgungsmethoden heute mit cnames verwendet werden?**

Die ECID-Bibliothek, AMCV-Cookie und ECID (ebenfalls MID) wurden als Methode zur Integration aller Adobe-Lösungen in eine ID gestartet. Diese ID ist weiterhin die Cookie-Stufe-ID im Adobe-Produktplan und ist die Standard-Cookie-ID für die Adobe Experience Platform.

**Hilft cnames Kunden bei der Aktivierung der domänenübergreifenden Verfolgung?**

Die gleichen Regeln und Einschränkungen, die zuvor mit cnames vorhanden waren, sind weiterhin vorhanden. In einigen Fällen können cnames in einem Szenario mit mehreren Domänen hilfreich sein. Wenn Sie über eine Haupteinstiegssite verfügen, auf der Benutzer vor dem Besuch anderer Domänen identifiziert werden können, kann ein CNAME-Tracking in Browsern, die keine Drittanbieter-Cookies akzeptieren, aktiviert werden. Obwohl cnames in bestimmten Szenarien bei mehreren Domänen hilfreich sein können, liegt der Grund für die Umschalt der ECID in CNAME-Implementierungen bei der dauerhaften Besucheridentifizierung, nicht bei der Verfolgung mehrerer Domänen. For more on CNAME and multi-domain, see [Data Collection CNAMEs and Cross-Domain Tracking](/help/mcvid-reference/mcvid-analytics-reference/mcvid-cname.md).

Weitere faqs werden hier hinzugefügt, da zusätzliche ITP-Änderungen veröffentlicht werden. Weitere Fragen finden Sie in [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## ITP verwandte Änderungen, Methoden und Konfigurationen

Wenn zusätzliche Methoden zur Verfolgung innerhalb von Safari erstellt werden, werden sie als Referenz auf diese Seite hinzugefügt.

>[!NOTE]*ECID* = *MID* = *MCID* in der gesamten Dokumentation unten.

Unter Verwendung der ITP- und ECID-Bibliotheksnutzung finden Sie weitere Informationen.

## Verwenden Sie die ECID-Bibliothek und die CNAME-Verfolgung, um die Besucher-ID-Ablaufzeit zu erweitern.

ITP 2.1 gibt Ihnen die Möglichkeit, clientseitige Cookies zu schreiben, was die Möglichkeit bietet, präzise Besucherverfolgungsinformationen an Kunden zu liefern. Daher wird eine Änderung in den CNAME-Tracking-Servern von Adobe eingeführt, um die Experience Cloud ID (ECID) des Besuchers in einem Erstanbieter-Cookie zu speichern.

Diese Änderung ist nur für ECID-Kunden hilfreich, die einen Analytics-CNAME im Erstanbieterkontext verwenden. Wenn Sie Analytics-Kunde sind, der derzeit keinen CNAME oder einen Nicht Analytics-Kunden verwendet, können Sie weiterhin einen CNAME-Datensatz eingeben. Wenden Sie sich an den Kundendienst oder Ihren Kundenbetreuer, um die Registrierung für einen [CNAME zu starten](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

Aktualisieren Sie auf die ECID-Bibliothek v. 4.3.0 +, um diese Änderung nutzen zu können.

**Design**

Sobald eine ID-Anforderung an demdex. net gesendet und eine ECID abgerufen wird, wird eine ID-Anforderung an die Domäne des Kunden gesendet, wenn ein Trackingserver in Ihrer ECID-Bibliothek festgelegt wird. Dieser Endpunkt liest den ecid-Parameter aus der Abfragezeichenfolge und legt ein neues [Cookie](/help/mcvid-introduction/mcvid-cookies.md) fest, das nur die ECID und ein Ablaufdatum zwei Jahre in der Zukunft umfasst. Jedes Mal, wenn dieser Endpunkt aufgerufen wird, wird das `s_ecid` Cookie mit einem Ablaufdatum von zwei Jahren nach dem Aufruf dieses Aufrufs umgeschrieben. Die ECID-Bibliothek muss auf Version 4.3.0 aktualisiert werden, damit der Wert dieses Cookies abgerufen werden kann.

Dieses neue `s_ecid` Cookie folgt demselben Ausschluss-Status wie das AMCV-Cookie. Wenn die ECID aus dem `s_ecid` Cookie gelesen wird, wird demdex immer aufgerufen, um den neuesten Abmeldestatus für diese ID abzurufen und im AMCV-Cookie zu speichern.

Wenn Ihr Kunde die Analytics-Verfolgung über diese [Methode](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html)abmeldet, wird dieses `s_ecid` Cookie gelöscht.

Der Name des Tracking-Servers sollte der visitorjs-Bibliothek zur Verfügung gestellt werden, wenn die Bibliothek mit trackingserver oder trackingserversecure initialisiert wird. Dies sollte mit der trackingserver-Konfiguration in den Analytics-Konfigurationen übereinstimmen.

Wenn Sie sich gegen diese Methode entscheiden, fügen Sie Ihrer ECID-Bibliotheksimplementierung die folgende Konfiguration hinzu: Discardtrackingserverecid. Wenn diese Konfiguration auf &quot;true&quot; festgelegt ist, liest die Besucherbibliothek die vom Erstanbieter-Tracking-Server festgelegte MID nicht.

![](assets/itp-proposal-v1.png)

## Verwenden Sie die Methode appendvisitoridsto für die domänenübergreifende Verfolgung (in den mehreren Domänen Ihres Unternehmens).

Mit dieser Funktion können Sie die ECID eines Besuchers domänenübergreifend freigeben, wenn Browser Drittanbieter-Cookies blockieren. Um diese Funktion zu verwenden, müssen Sie den ID-Dienst implementiert haben und Inhaber der Quell- und Zieldomäne sein. Verfügbar in visitorapi. js Version 1.7.0 oder höher (jedoch nicht in Version 1.10.0).

**Design**

* Wenn ein Besucher zu Ihren anderen Domänen navigiert, gibt Visitor. appendvisitoridsto (url) eine URL zurück, die als Abfrageparameter angehängt ist.

   Verwenden Sie diese URL, um von der ursprünglichen Domäne in die Zieldomäne umzuleiten.

* Der ID-Dienst-Code in der Zieldomäne extrahiert die ECID aus der URL, anstatt an Adobe eine Anforderung für die ID dieses Besuchers zu senden.

   Diese Anforderung schließt die Drittanbieter-Cookie-ID ein, die in diesem Fall nicht verfügbar ist.

* Der ID-Dienst-Code auf der Zielseite verwendet die übergebene ECID zur Verfolgung des Besuchers.

   >[!NOTE]
   >Wenn die Zielseite bereits über eine ECID aus vorherigen Besuchen verfügt, wird die Entscheidung, das vorhandene Cookie zu überschreiben, von dieser Konfiguration überschrieben. Weitere Informationen zu dieser Konfiguration finden Sie unter [overwritecrossdomainmcidandaid](/help/mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md).
   >
   >Weitere Informationen zu dieser Methode finden Sie auf der [Referenzseite appendvisitoridsto (Domänenübergreifende](/help/mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md) Verfolgung).
