---
description: Nachdem Sie Opt-in auf Ihrer Website aktiviert haben, verwenden Sie die Validierungsmethoden, um mit den Entwicklertools in Ihrem Browser zu testen, ob der Service wie erwartet funktioniert.
title: Überprüfen des Opt-in-Dienstes
exl-id: f0bcb32a-ccad-40a4-b031-2584e4136ace
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 95%

---

# Überprüfen des Opt-in-Dienstes{#validating-opt-in-service}

Nachdem Sie Opt-in auf Ihrer Website aktiviert haben, verwenden Sie die Validierungsmethoden, um mit den Entwicklertools in Ihrem Browser zu testen, ob der Service wie erwartet funktioniert.

## Nutzungsszenario 1: Opt-in aktivieren {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

Löschen Sie vor dem Laden der Seite den Cache und die Cookies.

Klicken Sie in Chrome mit der rechten Maustaste auf die Webseite und wählen Sie „Inspect“. Wie im Screenshot oben beschrieben, wählen Sie die Registerkarte *Netzwerk*, um die vom Browser angeforderten Anfragen anzuzeigen.

Im obigen Beispiel haben wir die folgenden Adobe-JS-Tags auf der Seite installiert: ECID, AAM, Analytics und Target.

**Überprüfen der erwarteten Funktionsweise des Opt-in:**

Sie sollten keine Anfragen an Adobe-Server sehen:

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>Möglicherweise wird ein Aufruf von `http://dpm.demdex.net/optOutStatus` angezeigt. Auf diesem SCHREIBGESCHÜTZTEN Endpunkt wird der Opt-out-Status des Benutzers abgerufen. Dieser Endpunkt führt nicht zur Erstellung von Drittanbieter-Cookies und erfasst keine Informationen von der Seite.

Sie sollten keine Cookies sehen, die von den Adobe-Tags erstellt wurden: (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

Wechseln Sie in Chrome zur Registerkarte *Anwendung*, erweitern Sie den Abschnitt *Cookies* unter *Datenspeicherung* und wählen Sie den Domänennamen Ihrer Website aus:

![](assets/use_case_1_2.png)

## Nutzungsszenario 2: Opt-in aktivieren und speichern  {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

Der einzige Unterschied bei Nutzungsszenario 2 besteht darin, dass Sie *ein neues Cookie* sehen, das die Opt-in-Berechtigungen enthält, die von Ihrem Benutzer erteilt wurden: **adobeujs-optin**

## Nutzungsszenario 3: Opt-in aktivieren und Vorabgenehmigung für Adobe Analytics erteilen  {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Da Adobe Analytics bereits vor dem Opt-in genehmigt wurde, werden auf der Registerkarte „Netzwerk“ Anfragen an Ihren Tracking-Server angezeigt:

![](assets/use_case_3_1.png)

und Sie sehen Analytics-Cookies auf der Registerkarte „Anwendung“:

![](assets/use_case_3_2.png)

## Nutzungsszenario 4: Opt-in und IAB aktivieren  {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**Ansicht Ihrer aktuellen IAB-Zustimmung auf der Seite:**

Öffnen Sie die Entwickler-Tools und wählen Sie den Tab *Konsole*. Fügen Sie das folgende Code-Fragment ein und drücken Sie die Eingabetaste:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

Im Folgenden finden Sie eine Beispielausgabe, wenn die Ziele 1, 2 und 5 genehmigt werden und die Anbieter-ID von Audience Manager genehmigt wird:

* demdex.net/id: Das Vorhandensein dieses Aufrufs zeigt, dass ECID eine ID von demdex.net angefordert hat.
* demdex.net/event: Das Vorhandensein dieses Aufrufs zeigt, dass der DIL-Datenerfassungsaufruf erwartungsgemäß funktioniert.
* demdex.net/dest5.html: Das Vorhandensein dieses Aufrufs beweist, dass ID-Syncs ausgelöst werden.

![](assets/use_case_4_1.png)

Wenn einer der folgenden Werte ungültig ist, werden keine Anfragen an Adobe-Server und keine Adobe-Cookies angezeigt:

* Die Zwecke 1, 2 ODER 5 werden nicht genehmigt.
* Die Anbieter-ID von Audience Manager wurde nicht genehmigt.
