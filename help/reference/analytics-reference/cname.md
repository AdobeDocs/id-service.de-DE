---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: Datenerfassungs-CNAMEs und domänenübergreifendes Tracking
title: Datenerfassungs-CNAMEs und domänenübergreifendes Tracking
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 8f4175b942ed4228ccd1f96791aa668be8aff95d

---


# Datenerfassungs-CNAMEs und domänenübergreifendes Tracking{#data-collection-cnames-and-cross-domain-tracking}

Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).

In Browsern, die Drittanbieter-Cookies akzeptieren, wird ein Cookie während der Anforderung einer Besucher-ID durch die Datenerfassungsserver gesetzt. Mit diesem Cookie kann der Besucher-ID-Dienst für alle Domänen, die mit derselben Experience Cloud-Organisations-ID konfiguriert sind, dieselbe Experience Cloud-Besucher-ID zurückgeben.

Für Browser, die keine Drittanbieter-Cookies akzeptieren, wird für jede Domäne eine neue Experience Cloud-Besucher-ID zugewiesen.

Das demdex.net-Cookie aktiviert den Besucher-ID-Dienst, um domänenübergreifendes Tracking auf derselben Ebene wie das s_vi-Cookie in Analytics zu ermöglichen, das von manchen Browsern akzeptiert und domänenübergreifend verwendet, von anderen Browsern dagegen abgelehnt wird.

## Datenerfassungs-CNAMEs {#section-48fd186d376a48079769d12c4bd9f317}

Wenn das Analytics-Cookie durch den Datenerfassungsserver gesetzt wurde, haben viele Kunden Datenerfassungsserver-CNAME-Einträge für die [Implementierung von Erstanbieter-Cookies](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/) konfiguriert, um Probleme mit Browsern zu verhindern, die Drittanbieter-Cookies zurückweisen. Mit diesem Verfahren wird die Domäne des Datenerfassungsservers so konfiguriert, dass sie mit der Websitedomäne übereinstimmt und das Besucher-ID-Cookie als Erstanbieter-Cookie gesetzt wird.

Da der Besucher-ID-Dienst das Besuchercookie mithilfe von JavaScript direkt in der Domäne der aktuellen Website setzt, ist diese Konfiguration zum Setzen von Erstanbieter-Cookies nicht mehr erforderlich.

Kunden mit nur einer Webeigenschaft (nur einer Domäne) können den Datenerfassungs-CNAME eliminieren und stattdessen den Namen des Datenerfassungshosts verwenden (`omtrdc.net` oder `2o7.net`).

Die Verwendung eines CNAME für die Datenerfassung bietet jedoch einen weiteren Vorteil: Sie können damit Besucher in Browsern, die keine Drittanbieter-Cookies akzeptieren, über eine Haupt-Landing-Domäne und weitere Domänen verfolgen. Für Kunden mit mehreren Webeigenschaften (mehreren Domänen) kann die Verwendung eines Datenerfassungs-CNAME von Vorteil sein. Im folgenden Abschnitt wird erklärt, wie domänenübergreifendes Besucher-Tracking funktioniert.

## So wird mit CNAMEs das domänenübergreifende Tracking aktiviert {#section-78925af798e24917b9abed79de290ad9}

Angesichts der Möglichkeiten zur Verwendung von Erstanbieter-Cookies in Drittanbieterkontexten in Apple Safari und einigen weiteren Browsern können Sie per CNAME Kunden über eine primäre Domäne und weitere Domänen, die denselben Trackingserver nutzen, verfolgen.

Sie haben z. B. eine primäre Website unter `mymainsite.com`. Sie haben den CNAME-Eintrag so konfiguriert, dass er auf Ihren sicheren Datenerfassungsserver zeigt: `smetrics.mymainsite.com`.

Wenn ein Besucher die Domäne `mymainsite.com` besucht, wird der ID-Dienst-Cookie vom Datenerfassungsserver gesetzt. Dies ist zulässig, da die Domäne des Datenerfassungsservers mit der Domäne der Website übereinstimmt. Dabei spricht man von der Verwendung eines Cookies in einem *Erstanbieterkontext* oder einfach von einem *Erstanbieter-Cookie*.

Wenn Sie dieselben Datenerfassungsserver auch für andere Websites verwenden (z. B. `myothersiteA.com` und `myothersiteB.com`), verhält es sich so, dass, wenn ein Besucher diese Websites später besucht, das beim Besuch auf `mymainsite.com` gesetzte Cookie in der HTTP-Anforderung an den Datenerfassungsserver gesendet wird (wie oben beschrieben senden Browser alle Cookies für eine Domäne in allen HTTP-Anforderungen an diese Domäne, selbst wenn die Domäne nicht mit der Domäne der aktuellen Website übereinstimmt). Dabei spricht man von der Verwendung eines Cookies in einem *Drittanbieterkontext* oder einfach von einem *Drittanbieter-Cookie*. Mit dieser Art der Verwendung kann dieselbe Besucher-ID auch auf den anderen Domänen verwendet werden. Beachten Sie, dass Browser Cookies in Kontexten von Drittanbietern anders behandeln als Erstanbieter-Cookies.

*Hinweis: Safari blockiert alle Cookies im Kontext von Drittanbietern, unabhängig davon, wie sie gesetzt sind.*

Daher sollte es sich bei Ihrer Erfassungsdomäne um eine Domäne handeln, die häufig besucht wird, damit Besucher über mehrere Domänen hinweg identifiziert werden können. Wenn es keine *häufig besuchte* Domäne gibt, die als Datenerfassungsdomäne verwendet werden kann, bringt das Verwalten eines CNAME-Eintrags für die Datenerfassungsdomäne keine domänenübergreifenden Vorteile mit sich. Besucher werden auf sekundärer Site und Hauptsite auf unterschiedliche Weise identifiziert, wenn nicht zuerst die Haupteinstiegssite besucht wird.

## Aktivierung der CNAME-Unterstützung mit dem Experience Cloud Identity-Dienst {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Die CNAME-Unterstützung des Datenerfassungs-Servers wird durch das Setzen der `visitor.marketingCloudServerSecure` Variablen aktiviert.
