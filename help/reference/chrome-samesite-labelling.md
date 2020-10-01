---
title: Änderungen an der Google Chrome-Kennzeichnung auf derselben Site
seo-title: Änderungen an der Google Chrome-Kennzeichnung auf derselben Site
description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
seo-description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
translation-type: tm+mt
source-git-commit: f74a028532e95ab17f5d2e64697d69eb64e03391
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 4%

---


# Änderungen an der Google Chrome-Kennzeichnung auf derselben Site {#google-chrome-samesite-labelling-changes}

Das Attribut SameSite teilt Browsern mit, wann und wie Cookies in Erstanbieter- und Drittanbieterszenarien ausgelöst werden. Das Attribut &quot;SameSite&quot;kann einen von drei Werten haben: `strict`, `lax`oder `none`. Chrome, Firefox, Edge, Safari und Opera werden seit November 2017 unterstützt `strict` und `lax` wurden 2018 eingeführt `none` . Einige ältere Browser unterstützen diese Einstellung jedoch nicht.

Im Februar 2020 veröffentlichte Google Chrome 80 und änderte die Standardeinstellung von `none` in `lax` , wenn ein Cookie keinen festgelegten SameSite-Attributwert hat. Diese Einstellung verhindert, dass ein Cookie in einem Drittanbieterkontext verwendet wird, der auch als &quot;Site-übergreifend&quot;bezeichnet wird. Alle darauf folgenden Drittanbieter-Cookies müssen auf &quot;gesichert&quot;gesetzt `SameSite=none` und gekennzeichnet werden.

Cookies ohne einen angegebenen SameSite-Attributwert werden standardmäßig `lax`verwendet.

Weitere Informationen zu SameSite-Attributen finden Sie im [Cookie-Standard-Dokument](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) .

## Gleiche Site-Attributwerte

| GleicherSite-Attributwert | Beschreibungen |
| ------ | ------------ |
| `strict` | Cookies mit dieser Einstellung werden nur gesendet, wenn sowohl die verweisende Seite als auch die Landingpage zur gleichen Domäne wie das Cookie gehören. |
| `lax` | Cookies mit dieser Einstellung werden nur gesendet, wenn die in der URL des Browsers angezeigte Domäne mit der Domäne des Cookies übereinstimmt. Dies ist die neue Standardeinstellung für Cookies in Chrome. |
| `none` | Cookies mit dieser Einstellung stehen für den externen oder externen Zugriff zur Verfügung, z. B. &quot;site-übergreifend&quot;. Vor dieser Änderung `none` war die standardmäßige SameSite-Einstellung für Cookies, sodass sich bei Verwendung dieser Einstellung ein Cookie am ehesten der herkömmlichen Funktionsweise ähnelte. Google verlangt jedoch, dass alle Cookies mit dieser Einstellung jetzt das sichere Flag angeben. Das heißt, das Cookie wird nur erstellt und mit Anforderungen über HTTPS gesendet. Alle Site-übergreifenden Cookies ohne das sichere Flag werden von Google abgelehnt. |

## Was Sie als Adobe Experience Cloud-Kunde wissen müssen

**Keine JavaScript-Aktualisierungen erforderlich**

Adobe products hat bereits serverseitige Updates veröffentlicht, um Drittanbieter-Cookies mit den entsprechenden Attributen festzulegen. Unsere Kunden benötigen keine JavaScript-Bibliotheksaktualisierungen.

**Sicherstellen, dass Endpunkte von Drittanbietern HTTPS verwenden**

Alle Kunden sollten sich vergewissern, dass ihre JavaScript-Konfiguration HTTPS für ihre Adobe Services-Aufrufe verwendet. Zielgruppe, Audience Manager und der Experience Cloud Identity Service (ECID) leiten HTTP-Aufrufe von Drittanbietern an ihre jeweiligen HTTPS-Endpunkte weiter, was die Latenz erhöhen kann. Dies bedeutet, dass Sie Ihre Konfiguration nicht ändern müssen. Analytics-Kunden sollten ihre Implementierungen so aktualisieren, dass ausschließlich HTTPS verwendet wird, da für Analytics spezifische Weiterleitungen Datenverlust verursachen können.

**Richtig gekennzeichnete Cookies sollten Daten wie gewünscht erfassen**

Solange Cookies korrekt beschriftet sind, werden Browser keine Maßnahmen ergreifen, um sie zu blockieren. Die Verbraucher werden die Möglichkeit haben, bestimmte Cookie-Typen zu blockieren, aber derzeit scheint es sich hierbei lediglich um eine &quot;Opt-in&quot;-Einstellung zu handeln.

**Vorhandene Drittanbieter-Cookies ohne die aktualisierten Beschriftungen werden ignoriert**

Drittanbieter-Cookies, die erstellt wurden, bevor Chrome 80 mit der Erzwingung von SameSite=`none` begonnen hat, und sichere Flags-Einstellungen werden von Chrome 80 ignoriert, wenn diese Flags nicht vorhanden sind.

Viele der bestehenden Drittanbieter-Cookies der Adobe verfügen nicht über diese Flags und müssen vor einem Upgrade auf Chrome 80 von den Edge-Servern aktualisiert werden. Andernfalls gehen diese Cookies verloren. Die Aktualisierung der Edge-Server erfolgt automatisch, wenn Benutzer eine Website besuchen, auf der das Cookie verwendet wird.

Bei den meisten Adoben sind Cookies bereits die entsprechenden Flags zugewiesen. Eine Ausnahme bilden Analytics-Implementierungen, die die Datenerfassung von Drittanbietern verwenden und keine ECID verwenden. Die Anzahl neuer Besucher, die andernfalls Besucher zurückgegeben hätten, nimmt möglicherweise nur geringfügig, vorübergehend zu.

**Mögliche Verringerung der Cookie-Übereinstimmung für Ziel- und Marktpartner (nur Audience Manager)**

Während Adobe die Kontrolle über die Aktualisierung ihrer Cookies hat, kann Adobe keine Partner zwingen, die erforderlichen Änderungen vorzunehmen. Die Cookie-Übereinstimmung kann für Audience Manager, die Zielpartner oder Marketingpartner verwenden, die diese Aktualisierungen nicht durchgeführt haben, abnehmen.

**Analytics-freundliche Drittanbieter-Cookies (nur Analytics-`s_vi`Cookies)**

Einige Analytics-Implementierungen verwenden einen Analytics-CNAME-Alias, um die Erstellung des `s_vi` Cookies in der Domäne dieses CNAME zu aktivieren. Wenn sich der CNAME in derselben Domäne wie Ihre Website befindet, wird dies als Erstanbieter-Cookie bezeichnet. Wenn Sie jedoch über mehrere Domänen verfügen und denselben CNAME für die Datenerfassung in allen Ihren Domänen verwenden, wird dieser als Drittanbieter-Cookie für diese anderen Domänen bezeichnet.

Da `lax` der CNAME in Chrome zur neuen Standardeinstellung für SameSite wird, ist er nicht mehr auf anderen Domänen sichtbar.

Damit die Änderung berücksichtigt werden kann, setzt Analytics jetzt explizit den Wert &quot;SameSite&quot;des `s_vi` Cookies auf `lax`. Um dieses Cookie in einem benutzerfreundlichen Drittanbieterkontext zu verwenden, setzen Sie den Wert SameSite auf `none`. Dies bedeutet auch, dass Sie immer HTTPS verwenden müssen. Bitte wenden Sie sich an den Kundendienst, um den Wert von SameSite für Ihre sicheren CNAMEs zu ändern.

> [!IMPORTANT] Diese Aktion ist nicht erforderlich für Analytics-Kunden, die ECID verwenden, Kunden, die für jede ihrer Domänen einen separaten CNAME verwenden, oder Kunden, die nur Analytics-Datenerfassung von Drittanbietern verwenden.

## Cookies in Adobe Standard Besucher

In der folgenden Tabelle sind nur die gebräuchlichen Besucher-Standardcookies aufgeführt. Weitere Cookie-Konfigurationen finden Sie in der produktspezifischen Dokumentation oder wenden Sie sich an Ihren Kundenbetreuer.

### ECID

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Kundenseitige Erstanbieter | Kein Wert hinzugefügt *Chrome-Standardeinstellung `lax` | Konfigurierbar |
| AMCVS_###@AdobeOrg | Kundenseitige Erstanbieter | Kein Wert hinzugefügt *Chrome-Standardeinstellung `lax` | Konfigurierbar |
| s_ecid | Serverseitiger Erstanbieter | SameSite==`lax` | Nicht festgelegt |

### Audience Manager

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Drittanbieter | `none` | Als sicher festlegen |
| DEXP | Drittanbieter | `none` | Als sicher festlegen |

### Analytics

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Serverseitiger Erstanbieter bei Verwendung von `CNAME` </li> <li>Drittanbieter bei Verwendung von 2o7.net oder omtrdc.net</li></ul> | <ul><li>`lax` if-first-party</li> <li>`none` wenn Dritte</li></ul> *Kunden können Einstellungen über das Ticket für die Kundenunterstützung für Erstanbieterdomänen bearbeiten* | Bei Verwendung `none` und HTTPS-Anforderung festlegen |
| s_fid | Kundenseitige Erstanbieter | Kein zusätzlicher Wert *Chrome-Standardeinstellung `lax` | Nicht festgelegt |

### Target

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Erstanbieter | Kein Wert hinzugefügt *Chrome-Standardeinstellung `lax` | Nicht festgelegt |

### Ad Cloud

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Drittanbieter | `none` *Nur auf Google Chrome- und Chrome-basierten Browsern* | Bei Verwendung `none` und HTTPS-Anforderung festlegen |
| data_adcloud | Erstanbieter | Kein Wert hinzugefügt *Chrome-Standardeinstellung `lax` | Nicht festgelegt |
| ev_tm | Drittanbieter | `none` *Nur auf Google Chrome- und Chrome-basierten Browsern* | Bei Verwendung `none` und HTTPS-Anforderung festlegen |

### Bizible

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Drittanbieter | `none` | Secure |

### Marketo Munchkin

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Kundenseitige Erstanbieter | Kein Wert hinzugefügt *Chrome-Standardeinstellung `lax` | Für externe Seiten konfigurieren |

> !![IMPORTANT] Drittanbieter-Cookies von Adoben werden serverseitig eingestellt

Weitere Informationen finden Sie im Dokument zu den Google Chrome SameSite-Richtlinien der [Zielgruppe](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html).