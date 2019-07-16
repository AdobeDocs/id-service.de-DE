---
description: Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Platform-Identitätsdienst, einschließlich Adobe Media Optimizer und des ID-Diensts.
keywords: ID-Dienst
seo-description: Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Platform-Identitätsdienst, einschließlich Adobe Media Optimizer und des ID-Diensts.
seo-title: Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten
title: Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten
uuid: 31bd655f-2b9e-4f8d-9a1f-e81a6110eda8
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten{#understanding-id-synchronization-and-match-rates}

Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Platform-Identitätsdienst, einschließlich Adobe Media Optimizer und des ID-Diensts.

## ID-Synchronisierung und Übereinstimmungsraten {#section-f652aae7234945e89d26dd833c5215fb}

Bei der ID-Synchronisierung werden durch den ID-Dienst zugewiesene IDs mit von unseren Kunden zu Sitebesuchern zugewiesenen IDs abgeglichen. Angenommen, der ID-Dienst hat eine Besucher-ID 1234 zugewiesen. Eine andere Plattform kennt diesen Besucher anhand der ID 4321. Der ID-Dienst ordnet diese IDs während des Synchronisierungsprozesses einander zu. Die Ergebnisse führen zu neuen Datenpunkten hinsichtlich dessen, was unsere Kunden über ihre Sitebesucher wissen. Wenn der ID-Dienst für eine ID keine Übereinstimmung finden kann, erstellt er zudem eine neue und verwendet diese ID für die künftige Synchronisierung.

Mithilfe von Übereinstimmungsraten wird die Effektivität des ID-Synchronisierungsprozesses gemessen und validiert. Hohe Übereinstimmungsraten deuten darauf hin, dass ein bestimmter Dienst effektiver ist und größere Onlinezielgruppen anspricht als ein Dienst mit niedrigen Übereinstimmungsraten. Das Vergleichen von Übereinstimmungsraten ist eine Möglichkeit, unterschiedliche integrierte Anzeigentechnologieplattformen quantifizierbar zu evaluieren.

![](assets/idsync2.png)

**Gewährleisten hoher Übereinstimmungsraten**

Zum Generieren hoher Übereinstimmungsraten ist es wichtig, den ID-Dienst ordnungsgemäß einzurichten (siehe [Standard-Implementierungshandbuch](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)). Eine ordnungsgemäße Implementierung hilft, hohe Übereinstimmungsraten sicherzustellen, da dadurch der ID-Dienst die gewünschten Cookies festlegen kann, um zu funktionieren bzw. IDs mit fähigen Datenpartnern zu synchronisieren. Faktoren wie eine langsame Internetverbindung, die Datenerfassung über Mobilgeräte oder Funknetzwerke können sich jedoch darauf auswirken, wie gut der ID-Dienst IDs erfasst, synchronisiert und abgleicht. Diese clientseitigen Variablen werden weder durch den ID-Dienst noch von [!DNL Adobe] gesteuert.

## Beschriebener ID-Synchronisierungsprozess {#section-a541a85cbbc74f5682824b1a2ee2a657}

Der ID-Dienst synchronisiert IDs in Echtzeit. Dieser Prozess arbeitet im Browser und nicht über eine Server-zu-Server-Datenübertragung. In der folgenden Tabelle werden die Schritte im ID-Synchronisierungsprozess beschrieben.

**Schritt 1: Seite laden**

Wenn ein Besucher auf Ihre Site kommt und eine Seite lädt, führt die Funktion `Visitor.getInstance` einen [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)- oder JSON-P-Aufruf an den ID-Dienst durch. Der ID-Dienst antwortet mit einem Cookie, der die [!DNL Experience Cloud] ID (MID) des Besuchers enthält. Bei der MID handelt es sich um eine jedem Sitebesucher zugewiesene eindeutige ID. Siehe auch [Cookies und der Experience Platform Identity Service](../introduction/cookies.md).

**Schritt 2: iFrame laden**

Während der Seitentext geladen wird, lädt der ID-Dienst einen iFrame namens *`Destination Publishing iFrame`*. Der [!DNL Destination Publishing iFrame] wird in einer Domäne geladen, die von der übergeordneten Seite getrennt ist. Dieses Design hilft beim Gewährleisten der Seitenleistung und verbessert die Sicherheit aufgrund des iFrames:

* Wird im Verhältnis zur übergeordneten Seite asynchron geladen. Die übergeordnete Seite kann demnach unabhängig vom [!DNL Destination Publishing iFrame] geladen werden. Das Laden des iFrames und von ID-Synchronisierungspixeln in iFrame wirkt sich weder auf die übergeordnete Seite noch auf die Benutzeroberfläche aus.
* Wird so schnell wie möglich geladen. Wenn dies zu schnell ist, können Sie den iFrame im Anschluss an das Fensterladeereignis laden (nicht empfohlen). Siehe [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) mit Einzelheiten.
* Verhindert, dass Code im iFrame Zugriff auf die übergeordnete Seite erlangt oder sie beeinflusst.

Siehe auch [Anforderungen des Experience Platform Identity Service Anforderungen und Sets IDs…](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)

**Schritt 3: ID-Synchronisierungen auslösen**

Die ID-Synchronisierung ist eine im Destination Publishing iFrame ausgelöste URL. Eine URL für die ID-Synchronisierung enthält, wie in diesem generischen Beispiel gezeigt, den ID-Synchronisierungsendpunkt eines Partners und eine Umleitungs-URL, die zu [!DNL Adobe] zurückleitet und die entsprechende ID enthält.

```
http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<
<varname>
  ADOBE_PARTNER_ID
</varname>>&dpuuid=<
<varname>
  PARTNER_UUID
</varname>>
```

Siehe auch [ID-Synchronisierung für eingehende Datenübertragungen](https://marketing.adobe.com/resources/help/en_US/aam/c_id_sync_in.html).

**Schritt 4: IDs speichern**

Synchronisierte IDs werden auf den [Edge- und Kerndatenservern](https://marketing.adobe.com/resources/help/en_US/aam/c_compedge.html) gespeichert.

## Synchronisierungsdienste verwalten die ID-Synchronisierung {#section-cd5784d7ad404a24aa28ad4816a0119a}

Der Begriff *`Sync Services`* bezieht sich auf interne [!DNL Experience Cloud]-Technologien, die für die ID-Synchronisation verantwortlich sind. Dieser Dienst ist standardmäßig aktiviert. Um ihn zu deaktivieren, müssen Sie eine [optionale Variable](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) zur ID-Dienstfunktion `Visitor.getInstance` hinzufügen. Die Synchronisierungsdienste gleichen unterschiedliche [!DNL Experience Cloud]-IDs ab, beispielsweise:

* [!DNL Experience Cloud]-Cookie-IDs von Drittanbietern mit [!DNL Experience Cloud]-IDs von Erstanbietern.

* [!DNL Experience Cloud]-Cookie-IDs von Erstanbietern mit [!DNL Adobe Media Optimizer]-IDs (AMO).

* [!DNL Experience Cloud]-Cookie-IDs von Drittanbietern mit Drittdatenanbieter- und Targeting Platform-IDs. Dies umfasst Dienste und Plattformen wie Datenanbieter, bedarfsgesteuerte bzw. anbieterseitige Plattformen, Werbenetzwerke, Austausche usw.
* [!DNL Experience Cloud]-Cookie-IDs von Erstanbietern mit geräteübergreifenden Partner-IDs.

## ID-Synchronisierung mit Adobe Media Optimizer {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Media Optimizer] bildet eine Ausnahme zum iFrame-basierten ID-Synchronisierungsprozess. Da es sich bei [!DNL Media Optimizer] um eine vertrauenswürdige Domäne handelt, erfolgt die ID-Synchronisierung von der übergeordneten Seite aus statt im [!DNL Destination Publishing iFrame]. Bei der Synchronisierung ruft der ID-Dienst [!DNL Media Optimizer] unter `cm.eversttech.net` dem älteren Domänennamen auf, der von [!DNL Media Optimizer] vor der Akquise durch Adobe verwendet wurde. Das Senden von Daten an [!DNL Media Optimizer] kann Übereinstimmungsraten verbessern und wird für Kunden mit Version 2.0 des ID-Diensts (oder höher) automatisch durchgeführt. Siehe auch [Cookies in Media Optimizer](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_media_optimizer.html).

>[!MORE_LIKE_THIS]
>
>* [Aufrufe an die Domäne „demdex.net“ ](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)

