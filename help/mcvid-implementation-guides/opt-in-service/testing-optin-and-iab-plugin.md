---
description: Nachdem Sie die Teilnahme an der Website aktiviert haben, testen Sie mithilfe der Validierungsmethoden, ob der Dienst mit den Developer Tools in Ihrem Browser erwartungsgemäß funktioniert.
seo-description: Nachdem Sie die Teilnahme an der Website aktiviert haben, testen Sie mithilfe der Validierungsmethoden, ob der Dienst mit den Developer Tools in Ihrem Browser erwartungsgemäß funktioniert.
seo-title: Überprüfung der Anmeldung
title: Überprüfung der Anmeldung
uuid: 1743360 a-d 557-4 e 50-8697-0 fa 92 b 302 cbc
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Überprüfung der Anmeldung{#validating-opt-in-service}

Nachdem Sie die Teilnahme an der Website aktiviert haben, testen Sie mithilfe der Validierungsmethoden, ob der Dienst mit den Developer Tools in Ihrem Browser erwartungsgemäß funktioniert.

## Anwendungsfall 1: Teilnahme aktivieren {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

Löschen Sie vor dem Laden der Seite Ihren Cache und die Cookies.

Klicken Sie mit der rechten Maustaste in Chrome auf die Webseite und wählen Sie „Untersuchen“. Wie im Screenshot oben gezeigt, wählen Sie die Registerkarte *Network*, um die vom Browser gestellten Anfragen zu sehen.

Im Beispiel oben wurden die folgenden Adobe JS-Tags auf der Seite installiert: ECID, AAM, Analytics und Target.

**So können Sie nachweisen, dass die Teilnahme wie erwartet funktioniert:**

Sie sollten keine Anfragen an diese Adobe-Server sehen:

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>Möglicherweise wird ein Aufruf an `http://dpm.demdex.net/optOutStatus`einen Schreibgeschützten Endpunkt angezeigt, der zum Abrufen des Abmeldestatus des Besuchers verwendet wird. Dieser Endpunkt führt nicht dazu, dass Drittanbieter-Cookies erstellt werden. Es werden auch keine Informationen auf der Seite erfasst.

Sie sollten keine von folgenden Adobe-Tags erstellten Cookies sehen: (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

Wechseln Sie in Chrome zur Registerkarte *Application*, erweitern Sie unter *Storage* den Abschnitt *Cookies* und wählen Sie den Domänennamen Ihrer Website aus:

![](assets/use_case_1_2.png)

## Nutzungsszenario 2: Opt-in aktivieren und speichern {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

Der einzige Unterschied bei Nutzungsszenario 2 besteht darin, dass Sie *ein neues Cookie* sehen, das die Opt-in-Berechtigungen enthält, die von Ihrem Benutzer erteilt wurden: **adobeujs-optin**

## Nutzungsszenario 3: Opt-in aktivieren und Vorabgenehmigung für Adobe Analytics erteilen {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Da Adobe Analytics über eine Vorabgenehmigung vor dem Opt-in verfügt, sehen Sie die Anfragen an Ihren Tracking-Server auf der Registerkarte „Network“:

![](assets/use_case_3_1.png)

Außerdem sehen Sie Analytics-Cookies auf der Registerkarte „Application“:

![](assets/use_case_3_2.png)

## Nutzungsszenario 4: Opt-in und IAB aktivieren {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**Anzeigen Ihrer aktuellen IAB-Zustimmung auf der Seite:**

Öffnen Sie die Entwicklertools und wählen Sie die Registerkarte *Console*. Fügen Sie das folgende Code-Snippet ein und drücken Sie die Eingabetaste:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

Hier sehen Sie eine Beispielausgabe, wenn eine Genehmigung für die Zwecke 1, 2 und 5 und die Audience Manager-Anbieter-ID erteilt wurde:

* demdex.net/id: Das Vorhandensein dieses Aufrufs zeigt, dass ECID eine ID von demdex.net angefordert hat.
* demdex.net/event: Das Vorhandensein dieses Aufrufs zeigt, dass der DIL-Datenerfassungsaufruf wie erwartet funktioniert.
* demdex.net/dest5.html: Das Vorhandensein dieses Aufrufs zeigt, dass ID-Synchronisationen ausgelöst werden.

![](assets/use_case_4_1.png)

Wenn einer der folgenden Punkte nicht zutrifft, sehen Sie keine Anfragen an Adobe-Server und keine Adobe-Cookies:

* Zweck 1, 2 ODER 5 wurde nicht genehmigt.
* Die Audience Manager-Anbieter-ID wurde nicht genehmigt.