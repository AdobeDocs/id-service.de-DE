---
description: Diese Anweisungen, Tools und Verfahren unterstützen Sie bei der Ermittlung, ob der ID-Dienst ordnungsgemäß funktioniert. Diese Tests gelten für den ID-Dienst im Allgemeinen und für andere ID-Dienst- und Experience Cloud-Lösungskombinationen.
keywords: ID-Dienst
seo-description: Diese Anweisungen, Tools und Verfahren unterstützen Sie bei der Ermittlung, ob der ID-Dienst ordnungsgemäß funktioniert. Diese Tests gelten für den ID-Dienst im Allgemeinen und für andere ID-Dienst- und Experience Cloud-Lösungskombinationen.
seo-title: Testen und Überprüfen des Experience Platform Identity Service
title: Testen und Überprüfen des Experience Platform Identity Service
uuid: 442 de 9 c 3-c 265-4412-89 bd-aeaa 286 ddad 6
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Testen und Überprüfen des Experience Platform Identity Service{#test-and-verify-the-experience-cloud-id-service}

Diese Anweisungen, Tools und Verfahren unterstützen Sie bei der Ermittlung, ob der ID-Dienst ordnungsgemäß funktioniert. Diese Tests gelten für den ID-Dienst im Allgemeinen und für andere ID-Dienst- und Experience Cloud-Lösungskombinationen.

## Voraussetzungen {#section-b1e76ad552ed4eb793b6e521a55127d4}

Wichtige Informationen, bevor Sie mit dem Testen und Überprüfen des ID-Diensts beginnen.

**Browserumgebungen**

Löschen Sie beim Testen in einer normalen Browsersitzung vor jedem Test Ihren Browsercache.

Alternativ können Sie den ID-Dienst in einer anonymen oder Inkognito-Browsersitzung testen. In einer anonymen Sitzung müssen Sie nicht vor jedem Test Ihre Browsercookies oder den Browsercache löschen.

**Werkzeuge**

Der [Adobe-Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html) und der [Charles-HTTP-Proxy](https://www.charlesproxy.com/) können Ihnen dabei helfen, zu bestimmen, ob der ID-Dienst für die richtige Funktionsweise mit Analytics konfiguriert wurde. Die Informationen in diesem Abschnitt basieren auf den durch den Adobe-Debugger und Charles zurückgegebenen Ergebnissen. Sie können jedoch auch ein beliebiges anderes Tool oder einen anderen Debugger verwenden, wenn sie sich am besten für Sie eignen.

## Testen mit dem Adobe-Debugger {#section-861365abc24b498e925b3837ea81d469}

Ihre Dienstintegration wird ordnungsgemäß konfiguriert, wenn Sie eine [!DNL Experience Cloud ID] (MID) in der [!DNL Adobe] Debugger-Antwort sehen. Weitere Informationen zur MID finden Sie unter [Cookies und der Experience Platform Identity Service](../introduction/cookies.md) .

So überprüfen Sie den Status des ID-Diensts mit dem [!DNL Adobe][-Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html):

1. Löschen Sie Ihre Browsercookies oder öffnen Sie eine anonyme Browsersitzung.
1. Laden Sie Ihre Testseite, die den ID-Dienstcode enthält.
1. Öffnen Sie den [!DNL Adobe] Debugger.
1. Suchen Sie in den Ergebnissen nach einer MID.

## Grundlegendes zu den Adobe Debugger-Ergebnissen {#section-bd2caa6643d54d41a476d747b41e7e25}

Die MID wird in einem Schlüssel-Wert-Paar gespeichert, das diese Syntax verwendet: `MID= *`Experience Cloud ID`*`. Der Debugger zeigt diese Informationen wie unten gezeigt an.

**Erfolg**

Der ID-Dienst wurde richtig implementiert, wenn eine Antwort wie die folgende angezeigt wird:

```
mid=20265673158980419722735089753036633573
```

Als [!DNL Analytics]-Kunde wird zusätzlich zur MID eine [!DNL Analytics] ID (AID) angezeigt. Dies geschieht:

* bei einigen Ihrer aktuellen/langfristigen Sitebesucher,
* wenn Sie eine Übergangsphase aktiviert haben.

**Fehler**

Wenden Sie sich an den [Kundendienst](https://helpx.adobe.com/marketing-cloud/contact-support.html), wenn der Debugger:

* keine MID zurückgibt,
* eine Fehlermeldung zurückgibt, die besagt, dass Ihre Partner-ID nicht bereitgestellt wurde.

## Testen mit dem Charles-HTTP-Proxy {#section-d9e91f24984146b2b527fe059d7c9355}

So überprüfen Sie den Status des ID-Diensts mit Charles:

1. Löschen Sie Ihre Browsercookies oder öffnen Sie eine anonyme Browsersitzung.
1. Starten Sie Charles.
1. Laden Sie Ihre Testseite, die den ID-Dienstcode enthält.
1. Suchen Sie nach den unten beschriebenen Anforderungs- und Antwortaufrufen und -daten.

## Verstehen der Charles-Ergebnisse {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Lesen Sie diesen Abschnitt, um Informationen dahingehend zu erhalten, wo und wonach Sie suchen müssen, wenn Sie Charles zum Überwachen von HTTP-Aufrufen verwenden.

**Erfolgreiche ID-Dienstanforderungen in Charles**

Ihr ID-Dienstcode funktioniert ordnungsgemäß, wenn die Funktion `Visitor.getInstance` einen JavaScript-Aufruf zu `dpm.demdex.net` startet. In einer erfolgreichen Anforderung ist Ihre [Organisations-ID](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) enthalten. Die Organisations-ID wird als Schlüssel-Wert-Paar weitergeleitet, die diese Syntax verwendet: `d_orgid= *`Organisations-ID`*`. Suchen Sie nach den `dpm.demdex.net` und den javascript-Aufrufen auf der [!DNL Structure] Registerkarte. Suchen Sie auf der [!DNL Request] Registerkarte nach Ihrer Organisations-ID.

![](assets/charles_request.png)

**Erfolgreiche ID-Dienstantworten in Charles**

Ihr Konto wurde ordnungsgemäß für den ID-Dienst bereitgestellt, wenn die Antwort von den [Datenerfassungsservern (Data Collection Servers, DCS)](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) eine MID zurückgibt. Die MID wird als Schlüssel-Wert-Paar zurückgegeben, die diese Syntax verwendet: `d_mid: *`Visitor Experience Cloud ID`*`. Suchen Sie wie unten gezeigt nach der MID auf der [!DNL Response] Registerkarte.

![](assets/charles_response_success.png)

**Fehlgeschlagene ID-Dienst-Antworten in Charles**

Ihr Konto wurde nicht richtig bereitgestellt, wenn die MID in der DCS-Antwort fehlt. Bei einer nicht erfolgreichen Antwort werden wie unten gezeigt einen Fehlercode und eine Meldung auf der [!DNL Response] Registerkarte zurückgegeben. Wenden Sie sich an den Kundendienst, wenn diese Fehlermeldung in der DCS-Antwort angezeigt wird.

![](assets/charles_response_unsuccessful.png)

Weitere Informationen über Fehlercodes finden Sie im Thema über die [DCS-Fehlercodes, -Meldungen und -Beispiele](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html).
