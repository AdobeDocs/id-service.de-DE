---
title: Kennzeichnungs-Änderungen für Google Chrome SameSite
seo-title: Kennzeichnungs-Änderungen für Google Chrome SameSite
description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
seo-description: Dokumentation für die Adobe ECID-Bibliothek (ID-Dienst).
translation-type: tm+mt
source-git-commit: 592ca6ca6a72e57b728e286d0b730c5bd93c0c7b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Kennzeichnungs-Änderungen für Google Chrome SameSite {#google-chrome-samesite-labelling-changes}

Das SameSite-Attribut teilt Browsern mit, wann und wie Cookies in Erstanbieter- und Drittanbieterszenarien ausgelöst werden. Das SameSite-Attribut kann einen von drei Werten haben: `strict`, `lax` oder `none`. Chrome, Firefox, Edge, Safari und Opera unterstützen `strict` und `lax` seit November 2017, während `none` 2018 eingeführt wurde. Einige ältere Browser unterstützen diese Einstellung jedoch nicht.

Im Februar 2020 veröffentlichte Google Chrome 80 und änderte die Standardeinstellung von `none` in `lax`, wenn ein Cookie keinen festgelegten SameSite-Attributwert hat. Diese Einstellung verhindert, dass ein Cookie in einem Drittanbieterkontext verwendet wird, der auch als „Site-übergreifend“ bezeichnet wird. Alle darauf folgenden Drittanbieter-Cookies müssen auf `SameSite=none` gesetzt und als sicher gekennzeichnet werden.

Für Cookies ohne angegebenen SameSite-Attributwert wird standardmäßig `lax` festgelegt.

Weitere Informationen zu SameSite-Attributen finden Sie im [Dokument zu Cookie-Standards](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1).

## SameSite-Attributwerte

| SameSite-Attributwert | Beschreibungen |
| ------ | ------------ |
| `strict` | Cookies mit dieser Einstellung werden nur gesendet, wenn sowohl die verweisende Seite als auch die Landingpage zur gleichen Domäne wie das Cookie gehören. |
| `lax` | Cookies mit dieser Einstellung werden nur gesendet, wenn die in der URL des Browsers angezeigte Domäne mit der Domäne des Cookies übereinstimmt. Dies ist die neue Standardeinstellung für Cookies in Chrome. |
| `none` | Cookies mit dieser Einstellung stehen für den externen Zugriff oder den Zugriff durch Drittanbieter zur Verfügung, z. B. „site-übergreifend“. Vor dieser Änderung war `none` die standardmäßige SameSite-Einstellung für Cookies, so dass die Verhaltensweise eines Cookies bei Verwendung dieser Einstellung am ehesten der herkömmlichen Funktionsweise ähnelt. Google verlangt jedoch, dass alle Cookies mit dieser Einstellung jetzt das Flag „Sicher“ angeben. Das heißt, das Cookie wird nur erstellt und mit Anforderungen über HTTPS gesendet. Alle site-übergreifenden Cookies ohne das Flag „Sicher“ werden von Google abgelehnt. |

## Was Sie als Adobe Experience Cloud-Kunde wissen müssen

**Keine JavaScript-Aktualisierungen erforderlich**

Für Adobe-Produkte wurden bereits serverseitige Updates veröffentlicht, um Cookies von Drittanbietern mit den entsprechenden Attributen festzulegen. Unsere Kunden benötigen keine Aktualisierungen für JavaScript-Bibliotheken.

**Sicherstellen, dass Endpunkte von Drittanbietern HTTPS verwenden**

Alle Kunden sollten sicherstellen, dass ihre JavaScript-Konfiguration HTTPS für ihre Aufrufe an Adobe-Dienste verwendet. Target, Audience Manager und der Experience Cloud Identity Service (ECID) leiten HTTP-Aufrufe von Drittanbietern an ihre jeweiligen HTTPS-Endpunkte weiter, was die Latenz erhöhen kann. Dies bedeutet, dass Sie Ihre Konfiguration nicht ändern müssen. Analytics-Kunden sollten ihre Implementierungen so aktualisieren, dass ausschließlich HTTPS verwendet wird, da für Analytics spezifische Weiterleitungen zu Datenverlusten führen können.

**Richtig gekennzeichnete Cookies sollten Daten wie gewünscht erfassen**

Solange Cookies korrekt gekennzeichnet sind, ergreifen Browser keine Maßnahmen, um sie zu blockieren. Die Verbraucher haben die Möglichkeit, bestimmte Cookie-Typen zu blockieren, aber derzeit scheint es sich hierbei lediglich um eine „Opt-in“-Einstellung zu handeln.

**Vorhandene Drittanbieter-Cookies ohne aktualisierte Kennzeichnungen werden ignoriert**

Drittanbieter-Cookies, die erstellt wurden, bevor Chrome 80 mit der Erzwingung von SameSite=`none` und Einstellungen mit dem Flag „Sicher“ begonnen hat, werden von Chrome 80 ignoriert, wenn diese Flags nicht vorhanden sind.

Viele der bestehenden Drittanbieter-Cookies von Adobe verfügen nicht über diese Flags und müssen vor einem Upgrade auf Chrome 80 von den Edge-Servern aktualisiert werden. Andernfalls gehen diese Cookies verloren. Die Aktualisierung der Edge-Server erfolgt automatisch, wenn Benutzer eine Website besuchen, auf der das Cookie verwendet wird.

Bei den meisten Adobe-Produkten sind Cookies bereits die entsprechenden Flags zugewiesen. Eine Ausnahme bilden Analytics-Implementierungen, die die Datenerfassung von Drittanbietern verwenden und keine ECID verwenden. Bei Kunden kann es zu einem geringfügigen vorübergehenden Anstieg neuer Besucher kommen, die sonst wiederkehrende Besucher wären.

**Mögliche Verringerung der Cookie-Übereinstimmung für Ziel- und Marketplace-Partner (nur Audience Manager)**

Adobe hat zwar die Kontrolle über die Aktualisierung von Cookies, kann Partner jedoch nicht zwingen, die erforderlichen Änderungen vorzunehmen. Die Cookie-Übereinstimmung verringert sich möglicherweise für Audience Manager-Kunden mit Ziel- oder Marketplace-Partnern, die diese Aktualisierungen noch nicht durchgeführt haben.

**Analytics-freundliche Drittanbieter-Cookies (nur Analytics `s_vi`-Cookies)**

Einige Analytics-Implementierungen verwenden einen Analytics-CNAME-Alias, um die Erstellung des `s_vi`-Cookies in der Domäne dieses CNAME zu ermöglichen. Wenn sich der CNAME in derselben Domäne wie Ihre Website befindet, wird dieses Cookie als Erstanbieter-Cookie bezeichnet. Wenn Sie jedoch über mehrere Domänen verfügen und denselben CNAME für die Datenerfassung in all Ihren Domänen verwenden, wird er in diesen anderen Domänen als Drittanbieter-Cookie designiert.

Mit `lax` als neuer standardmäßiger SameSite-Einstellung in Chrome ist der CNAME nicht mehr auf anderen Domänen sichtbar.

Damit die Änderung berücksichtigt werden kann, legt Analytics für den SameSite-Wert des `s_vi`-Cookies nun explizit `lax` fest. Um dieses Cookie in einem benutzerfreundlichen Drittanbieterkontext zu verwenden, setzen Sie den SameSite-Wert auf `none`. Dies bedeutet auch, dass Sie immer HTTPS verwenden müssen. Wenden Sie sich an die Kundenunterstützung, um den SameSite-Wert für Ihre sicheren CNAMEs zu ändern.

>[!IMPORTANT]
>
>Es gibt bestimmte Kundengruppen, für die diese Aktion nicht erforderlich ist. Dazu zählen Analytics-Kunden, die ECID verwenden, Kunden, die für jede ihrer Domains einen separaten CNAME verwenden, sowie Kunden, die nur die Analytics-Datenerfassung von Drittanbietern verwenden.

## Standardmäßige Besucher-Cookies von Adobe

In der folgenden Tabelle sind nur die gebräuchlichen standardmäßigen Besucher-Cookies aufgeführt. Weitere Cookie-Konfigurationen finden Sie in der produktspezifischen Dokumentation. Alternativ können Sie sich an Ihren Kundenbetreuer wenden.

### ECID

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Kundenseitiger Erstanbieter | Kein Wert hinzugefügt; *Chrome übernimmt standardmäßig die Einstellung `lax` | Konfigurierbar |
| AMCVS_###@AdobeOrg | Kundenseitiger Erstanbieter | Kein Wert hinzugefügt; *Chrome übernimmt standardmäßig die Einstellung `lax` | Konfigurierbar |
| s_ecid | Serverseitiger Erstanbieter | SameSite==`lax` | Nicht festgelegt |

### Audience Manager

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Drittanbieter | `none` | Als sicher festlegen |
| Dextp | Drittanbieter | `none` | Als sicher festlegen |

### Analytics

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Serverseitiger Erstanbieter bei Verwendung von `CNAME` </li> <li>Drittanbieter bei Verwendung von 2o7.net oder omtrdc.net</li></ul> | <ul><li>`lax`, wenn Erstanbieter</li> <li>`none`, wenn Drittanbieter</li></ul> *Kunden können Einstellungen über das Einreichen eines Tickets für Erstanbieterdomänen bei der Kundenunterstützung bearbeiten* | Festlegen, wenn `none` und HTTPS-Anforderung verwendet werden |
| s_fid | Kundenseitiger Erstanbieter | Kein Wert hinzugefügt; *Chrome übernimmt standardmäßig die Einstellung `lax` | Nicht festgelegt |

### Target

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Erstanbieter | Kein Wert hinzugefügt; *Chrome übernimmt standardmäßig die Einstellung `lax` | Nicht festgelegt |

### Ad Cloud

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Drittanbieter | `none` *Nur auf Google Chrome- und Chrome-basierten Browsern* | Festlegen, wenn `none` und HTTPS-Anforderung verwendet werden |
| data_adcloud | Erstanbieter | Kein Wert hinzugefügt; *Chrome übernimmt standardmäßig die Einstellung `lax` | Nicht festgelegt |
| ev_tm | Drittanbieter | `none` *Nur auf Google Chrome- und Chrome-basierten Browsern* | Festlegen, wenn `none` und HTTPS-Anforderung verwendet werden |

### Bizible

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Drittanbieter | `none` | Secure |

### Marketo Munchkin

| Cookie | Typ | SameSite-Attribut | Secure-Attribut |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Kundenseitiger Erstanbieter | Kein Wert hinzugefügt; *Chrome übernimmt standardmäßig die Einstellung `lax` | Für externe Seiten konfigurierbar |

> !![IMPORTANT] Drittanbieter-Cookies von Adobe werden serverseitig eingestellt

Weitere Informationen finden Sie im Dokument zu den [Target-Google Chrome SameSite-Richtlinien](https://docs.adobe.com/content/help/de-DE/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.translate.html).