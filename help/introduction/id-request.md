---
description: Eine Übersicht über den ID-Anforderungs- und -Ausgabeprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.
keywords: ID-Dienst
seo-description: Eine Übersicht über den ID-Anforderungs- und -Ausgabeprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.
seo-title: Anfordern und Festlegen von IDs durch den Experience Cloud Identity-Dienst
title: Anfordern und Festlegen von IDs durch den Experience Cloud Identity-Dienst
uuid: ff7f5b7e-e959-4391-b75c-b7a36286e0ea
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Anfordern und Festlegen von IDs durch den Experience Cloud Identity-Dienst{#how-the-experience-cloud-id-service-requests-and-sets-ids}

Eine Übersicht über den ID-Anforderungs- und -Ausgabeprozess. Diese Beispiele decken die ID-Zuweisung auf individuellen Sites, Site-übergreifend und für durch verschiedene Experience Cloud-Kunden verwaltete Sites mit eigenen Kunden-IDs ab.

>[!NOTE]
>
>Wenn Sie nicht genau wissen, wie der Experience Cloud Identity-Dienst die Besucher-ID erstellt, lesen Sie in [Experience Cloud](../introduction/cookies.md) nach.

**Tipp:** Siehe auch unser [ID-Dienst-Video zum domänenübergreifenden Tracking](https://helpx.adobe.com/de/marketing-cloud-core/kb/MCID/CrossDomain.html).

## Anfordern einer Experience Cloud ID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

In den folgenden Beispielen wird dargestellt, wie der ID-Dienst die Experience Cloud-Besucher-ID anfordert und erhält. Es wird anhand zweier fiktiver Unternehmen, „Food Company“ und „Sports Company“, erklärt, wie die Datenflüsse für ID-Anforderungen und -Antworten funktionieren. Jedes Unternehmen verfügt über eine eindeutige Experience Cloud-Organisations-ID und hat den ID-Dienstcode auf jeder Site implementiert. In diesen Anwendungsfällen werden die Datenströme für eine allgemeine ID-Dienstimplementierung ohne Analytics, Legacy-IDs oder Drittanbieter-Cookies blockierende Browser dargestellt.

![](assets/sample_sites.png)

**Erste Anfrage**

In diesem Beispiel besucht ein Neukunde die Pizza-Site, die von der Food Company verwaltet wird. Die Food Company hat auf der Pizza-Site ID-Dienst-Code implementiert. Beim Laden der Site wird vom ID-Dienst-Code der AMCV-Cookie in der Pizzadomäne gesucht.

* Ist der AMCV-Cookie gesetzt, verfügt der Site-Besucher über eine Experience Cloud ID. In diesem Fall verfolgt das Cookie den Besucher und teilt Daten mit anderen Experience Cloud-Lösungen.
* Wenn das AMCV-Cookie nicht gesetzt ist, ruft der ID-Dienst-Code einen regionalen [Datenerfassungsserver](https://marketing.adobe.com/resources/help/en_US/aam/?f=c_compcollect.html) (DCS) auf unter `dpm.demdex.net/id` (siehe auch [Aufrufe an die Domäne „demdex.net“](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)). Im Aufruf enthalten ist auch die Organisations-ID der Food Company. Die Organisations-ID wird in der Funktion `Visitor.getInstance` des ID-Dienst-Codes festgelegt.

![](assets/request1.png)

**Erste Antwort**

In der Antwort gibt der DES die [!DNL Experience Cloud] ID (MID) und den demdex-Cookie zurück. Der ID-Dienst-Code schreibt den MID-Wert in das AMCV-Cookie. Wenn der DES beispielswiese einen MID-Wert von 1234 zurückgibt, würde dieser als `mid|1234` im AMCV-Cookie gespeichert und in der Erstanbieter-Pizzadomäne gesetzt werden. Der demdex-Cookie enthält zudem eine eindeutige ID (nennen wir diese einmal 5678). Dieser Cookie wird in der Drittanbieter-demdex.net-Domäne gesetzt, die von der Pizzadomäne unabhängig ist.

![](assets/response1.png)

Im nächsten Beispiel werden Sie sehen, wie demdex- und Organisations-ID es dem ID-Dienst ermöglichen, die korrekte MID zu erstellen und zurückzugeben, wenn der Besucher zu einer anderen von der Food Company verwalteten Site wechselt.

## Site-übergreifende Anforderung und Antwort {#section-15ea880453af467abd2874b8b4ed6ee9}

In diesem Beispiel navigiert der Food-Company-Besucher von der Pizza-Site zur Taco-Site. Die Food Company hat auf der Taco-Site ID-Dienst-Code implementiert. Der Besucher hat die Taco-Site vorher noch nie aufgerufen.

Unter diesen Umständen ist für die Taco-Site kein AMCV-Cookie vorhanden. Außerdem kann der ID-Dienst nicht den AMCV-Cookie verwenden, der auf der Pizza-Site gesetzt wurde, da dieser sich ausschließlich auf die Pizzadomäne bezieht. Somit muss der ID-Dienst den DES aufrufen, um eine Besucher-ID zu suchen und anzufordern. In diesem Fall enthält der DES die Organisations-ID der Food Company *sowie* die demdex-ID. Beachten Sie, dass die demdex-ID von der Pizza-Site abgerufen und als Drittanbieter-Cookie unter der Domäne demdex.net gespeichert wurde.

![](assets/request2.png)

Nachdem der DES Organisations-ID und demdex-ID erhalten hat, wird die korrekte MID für unseren Site-Besucher erstellt und zurückgegeben. Da die mathematisch anhand der Organisations-ID und der demdex-ID ermittelt wird, enthält der AMCV-Cookie den MID-Wert `mid = 1234`mid = .

![](assets/response2.png)

## ID-Anforderungen von anderen Sites {#section-ba9a929e50d64b0aba080630fd83b6f1}

In diesem Beispiel verlässt der Besucher die Food-Company-Sites und navigiert zur Fußballseite, die von der Sports Company verwaltet wird. Beim Aufruf der Fußballseite läuft der gleiche ID-Prüfungs- und -Anfrageprozess ab, der in den vorangegangenen Beispielen beschrieben wurde. Da die Sports Company jedoch über eine eigene Organisations-ID verfügt, gibt der ID-Dienst eine andere MID zurück. Die neue MID ist für die von der Sports Company verwalteten Domänen eindeutig und ermöglicht es dem Unternehmen, Besucherdaten zu verfolgen und lösungsübergreifend in der [!DNL Experience Cloud] freizugeben. Die demdex-ID bleibt für den Besucher gleich, da sie in einem Drittanbieter-Cookie enthalten ist und domänenübergreifend fortbesteht.

![](assets/req_resp.png)

