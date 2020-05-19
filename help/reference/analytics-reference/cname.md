---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: Datenerfassungs-CNAMEs und domänenübergreifendes Tracking
title: Datenerfassungs-CNAMEs und domänenübergreifendes Tracking
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: ht
source-git-commit: 9fe63cf3983a2ed6642837b02a3c3441ef745d70
workflow-type: ht
source-wordcount: '602'
ht-degree: 100%

---


# Datenerfassungs-CNAMEs und domänenübergreifendes Tracking {#data-collection-cnames-and-cross-domain-tracking}

Wenn eine Haupteinstiegssite vorhanden ist, über die Kunden vor dem Besuch weiterer Domänen identifiziert werden können, besteht die Möglichkeit, per CNAME das domänenübergreifende Tracking für Browser zu aktivieren, die keine Drittanbieter-Cookies akzeptieren (z. B. Safari).

In Browsern, die Drittanbieter-Cookies akzeptieren, wird von den Datenerfassungs-Servern bei der Anforderung einer Besucher-ID ein Cookie gesetzt. Mit diesem Cookie kann der Besucher-ID-Dienst für alle Domänen, die mit derselben Experience Cloud-Organisations-ID konfiguriert sind, dieselbe Experience Cloud-Besucher-ID zurückgeben.

Für Browser, die keine Drittanbieter-Cookies akzeptieren, wird für jede Domäne eine neue Experience Cloud-Besucher-ID zugewiesen.

Das demdex.net-Cookie aktiviert den Besucher-ID-Dienst, um domänenübergreifendes Tracking auf derselben Ebene wie das s_vi-Cookie in Analytics zu ermöglichen, das von manchen Browsern akzeptiert und domänenübergreifend verwendet, von anderen Browsern dagegen abgelehnt wird.

## Datenerfassungs-CNAMEs {#section-48fd186d376a48079769d12c4bd9f317}

Wenn das Analytics-Cookie durch den Datenerfassungs-Server gesetzt wurde, konfigurieren viele Kunden Datenerfassungs-Server-CNAME-Einträge für die [Implementierung von Erstanbieter-Cookies](https://docs.adobe.com/content/help/de-DE/core-services/interface/ec-cookies/cookies-first-party.html), um Probleme mit Browsern zu verhindern, die Drittanbieter-Cookies zurückweisen. Durch diesen Prozess wird die Domäne des Datenerfassungs-Servers so konfiguriert, dass sie mit Ihrer Website-Domäne übereinstimmt, sodass das Besucher-ID-Cookie als Erstanbieter-Cookie gesetzt wird.

Da der Besucher-ID-Dienst das Besucher-Cookie mithilfe von JavaScript direkt in der Domäne der aktuellen Website setzt, wird diese Konfiguration nicht mehr zum Setzen von Erstanbieter-Cookies benötigt.

Kunden mit nur einer Webeigenschaft (nur einer Domäne) können den Datenerfassungs-CNAME eliminieren und stattdessen den Namen des Datenerfassungshosts verwenden (`omtrdc.net` oder `2o7.net`).

Die Verwendung eines CNAME für die Datenerfassung bietet jedoch einen zusätzlichen Vorteil, da Sie Besucher zwischen einer Haupt-Landing-Domäne und anderen Domänen in Browsern, die keine Drittanbieter-Cookies akzeptieren, verfolgen können. Kunden mit mehreren Web-Eigenschaften (mehreren Domänen) können vom Unterhalt eines Datenerfassungs-CNAME profitieren. Im folgenden Abschnitt wird erläutert, wie domänenübergreifendes Besucher-Tracking funktioniert.

## Domänenübergreifendes Tracking {#section-78925af798e24917b9abed79de290ad9}

Der Besucher-ID-Dienst verwendet „demdex.net“ als Domäne zum domänenübergreifenden Tracking von Besuchern (jedoch innerhalb derselben Eigentümerfirma), sofern die Datenschutzeinstellungen und Browser-Einstellungen des Benutzers dies zulassen.

Ein CNAME bietet keine weiteren domänenübergreifenden Vorteile. Sie haben z. B. eine primäre Website unter `mymainsite.com`. Sie haben den CNAME-Eintrag so konfiguriert, dass er auf Ihren sicheren Datenerfassungsserver zeigt: `smetrics.mymainsite.com`.

Wenn ein Besucher die Domäne `mymainsite.com` besucht, wird der ID-Dienst-Cookie vom Datenerfassungsserver gesetzt. Dies ist zulässig, da die Domäne des Datenerfassungsservers mit der Domäne der Website übereinstimmt. Dabei spricht man von der Verwendung eines Cookies in einem *Erstanbieterkontext* oder einfach von einem *Erstanbieter-Cookie*.

Wenn Sie dieselben Datenerfassungsserver auch für andere Websites verwenden (z. B. `myothersiteA.com` und `myothersiteB.com`), verhält es sich so, dass, wenn ein Besucher diese Websites später besucht, das beim Besuch auf `mymainsite.com` gesetzte Cookie in der HTTP-Anforderung an den Datenerfassungsserver gesendet wird (wie oben beschrieben senden Browser alle Cookies für eine Domäne in allen HTTP-Anforderungen an diese Domäne, selbst wenn die Domäne nicht mit der Domäne der aktuellen Website übereinstimmt). Dies wird als Verwendung eines Cookies in einem *Drittanbieterkontext* oder nur eines *Drittanbieter-Cookies* bezeichnet, auch wenn Sie einen CNAME verwenden. Adobe empfiehlt für jede eindeutige Domäne einen CNAME.

*Hinweis: Safari blockiert alle Cookies im Kontext von Drittanbietern, unabhängig davon, wie sie gesetzt sind.*

## Aktivierung der CNAME-Unterstützung mit dem Experience Cloud Identity-Dienst {#section-25d4feb686d944e3a877d7aad8dbdf9a}

Die CNAME-Unterstützung des Datenerfassungs-Servers wird durch das Setzen der `visitor.marketingCloudServerSecure` Variablen aktiviert.
