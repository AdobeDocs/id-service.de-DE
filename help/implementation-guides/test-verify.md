---
description: Diese Anweisungen, Tools und Verfahren unterstützen Sie bei der Ermittlung, ob der ID-Dienst ordnungsgemäß funktioniert. Diese Tests gelten für den ID-Dienst im Allgemeinen sowie für andere ID-Dienst- und Experience Cloud-Lösungskombinationen.
keywords: ID-Dienst
title: Testen und Überprüfen des Experience Cloud Identity Service
exl-id: afdf9778-e73d-46ca-9d2f-a65abaae2fe6
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 100%

---

# Testen und Überprüfen des Experience Cloud Identity Service{#test-and-verify-the-experience-cloud-id-service}

Diese Anweisungen, Tools und Verfahren unterstützen Sie bei der Ermittlung, ob der ID-Dienst ordnungsgemäß funktioniert. Diese Tests gelten für den ID-Dienst im Allgemeinen sowie für andere ID-Dienst- und Experience Cloud-Lösungskombinationen.

## Voraussetzungen {#section-b1e76ad552ed4eb793b6e521a55127d4}

Wichtige Informationen, die Sie vor Testen und Verifizieren des ID-Diensts kennen sollten.

**Browserumgebungen**

Löschen Sie beim Testen in einer normalen Browsersitzung vor jedem Test Ihren Browsercache.

Alternativ können Sie den ID-Dienst in einer anonymen oder Inkognito-Browsersitzung testen. In einer anonymen Sitzung müssen Sie Ihre Browser-Cookies oder den Cache nicht vor jedem Test löschen.

**Tools**

Der [Adobe-Debugger](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=de) und der [Charles-HTTP-Proxy](https://www.charlesproxy.com/) können Ihnen dabei helfen festzustellen, ob der ID-Dienst für Analytics richtig konfiguriert wurde. Die Informationen in diesem Abschnitt basieren auf den durch den Adobe-Debugger und Charles zurückgegebenen Ergebnissen. Sie können jedoch frei entscheiden, welches Tool oder welcher Debugger für Sie optimal ist.

## Testen mit dem Adobe-Debugger {#section-861365abc24b498e925b3837ea81d469}

Ihre Dienstintegration ist richtig konfiguriert, wenn in der [!DNL Adobe]-Debugger-Antwort eine [!DNL Experience Cloud ID] (MID) angezeigt wird. Siehe [Cookies und der Experience Cloud Identity Service](../introduction/cookies.md) mit weiteren Informationen zur MID.

So überprüfen Sie den Status des ID-Diensts mit dem [!DNL Adobe] [-Debugger](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=de):

1. Löschen Sie Ihre Browser-Cookies oder öffnen Sie eine anonyme Browser-Sitzung.
1. Laden Sie Ihre Testseite, die den ID-Dienst-Code enthält.
1. Öffnen Sie den [!DNL Adobe]-Debugger.
1. Suchen Sie in den Ergebnissen nach einer MID.

## Grundlegendes zu den Adobe-Debugger-Ergebnissen {#section-bd2caa6643d54d41a476d747b41e7e25}

Die MID wird in einem Schlüssel-Wert-Paar gespeichert, das die folgende Syntax verwendet: `MID= *`Experience Cloud ID`*`. Der Debugger zeigt diese Informationen wie unten gezeigt an.

**Erfolg**

Der ID-Dienst wurde ordnungsgemäß implementiert, wenn Sie eine Antwort sehen, die ungefähr so aussieht:

```
mid=20265673158980419722735089753036633573
```

Wenn Sie ein [!DNL Analytics]-Kunde sind, wird zusätzlich zur MID eine [!DNL Analytics] ID (AID) angezeigt. Dies geschieht:

* bei einigen Ihrer aktuellen/langjährigen Sitebesucher,
* Wenn Sie haben eine Übergangsphase aktiviert haben.

**Fehlgeschlagen**

Wenden Sie sich an die [Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html), wenn der Debugger:

* keine MID zurückgibt,
* eine Fehlermeldung zurückgibt, die angibt, dass Ihre Partner-ID nicht bereitgestellt wurde.

## Testen mit dem Charles-HTTP-Proxy {#section-d9e91f24984146b2b527fe059d7c9355}

So überprüfen Sie den Status des ID-Diensts mit Charles:

1. Löschen Sie Ihre Browser-Cookies oder öffnen Sie eine anonyme Browser-Sitzung.
1. Starten Sie Charles.
1. Laden Sie Ihre Testseite, die den ID-Dienst-Code enthält.
1. Suchen Sie nach den unten beschriebenen Anforderungs- und Antwortaufrufen und -daten.

## Grundlegendes zu den Charles-Ergebnissen {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Lesen Sie diesen Abschnitt, um Informationen dahingehend zu erhalten, wo und wonach Sie suchen müssen, wenn Sie Charles zum Überwachen von HTTP-Aufrufen verwenden.

**Erfolgreiche ID-Dienstanforderungen in Charles**

Ihr ID-Dienst-Code funktioniert ordnungsgemäß, wenn die Funktion `Visitor.getInstance` einen JavaScript-Aufruf zu `dpm.demdex.net` startet. Eine erfolgreiche Anforderung enthält Ihre [Organisations-ID](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). Die Organisations-ID wird als Schlüssel-Wert-Paar weitergegeben, das folgende Syntax verwendet: `d_orgid= *`d_orgid`*`. Die `dpm.demdex.net`- und JavaScript-Aufrufe finden Sie auf der Registerkarte [!UICONTROL Struktur]. Die Organisations-ID finden Sie auf der Registerkarte [!UICONTROL „Anforderung“].

![](assets/charles_request.png)

**Erfolgreiche ID-Dienstantworten in Charles**

Ihr Konto wurde ordnungsgemäß für den ID-Dienst bereitgestellt, wenn die Antwort von den [Datenerfassungsservern (Data Collection Servers, DCS)](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-data-collection.html?lang=de) eine MID zurückgibt. Die MID wird als ein Schlüssel-Wert-Paar zurückgegeben, das die folgende Syntax verwendet: `d_mid: *`visitor Experience Cloud ID`*`. Auf der Registerkarte [!UICONTROL „Antwort“] findet sich die MID, wie im Folgenden gezeigt.

![](assets/charles_response_success.png)

**Fehlerhafte ID-Dienstantworten in Charles**

Ihr Konto wurde nicht richtig bereitgestellt, wenn die MID in der DCS-Antwort fehlt. Bei einer fehlerhaften Antwort werden auf der Registerkarte [!UICONTROL Antwort] ein Fehler-Code und eine Fehlermeldung zurückgegeben, wie im Folgenden gezeigt. Wenden Sie sich an die Kundenunterstützung, wenn diese Fehlermeldung in der DCS-Antwort angezeigt wird.

![](assets/charles_response_unsuccessful.png)

Weitere Informationen zu Fehler-Codes finden Sie unter [DCS-Fehler-Codes, Meldungen und Beispiele](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html?lang=de).
