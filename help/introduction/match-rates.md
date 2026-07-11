---
description: Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Besucher-ID-Dienst, einschließlich Adobe Media Optimizer und Besucher-ID-Dienst.
keywords: Besucher-ID-Service
title: Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten
exl-id: 9386824c-7d04-459b-9417-45b67f8a7b37
TQID: https://experienceleague.adobe.com/BNwk0vuY8bpEtqlaQjqkw22hZ-piNnnrHYjuy7Vam-Q
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 860
ht-degree: 46%

---

# Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten{#understanding-id-synchronization-and-match-rates}

Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Besucher-ID-Dienst, einschließlich Adobe Media Optimizer und Besucher-ID-Dienst.

## ID-Synchronisierung und Übereinstimmungsraten {#section-f652aae7234945e89d26dd833c5215fb}

Bei der ID-Synchronisierung werden IDs, die vom Besucher-ID-Service zugewiesen wurden, mit IDs abgeglichen, die Website-Besuchern von unseren Kunden zugewiesen wurden. Angenommen, der Besucher-ID-Dienst hat eine Besucher-ID „1234“ zugewiesen. Eine andere Plattform kennt diesen Besucher unter der ID „4321“. Der Besucher-ID-Dienst ordnet diese IDs während des Synchronisierungsprozesses zusammen zu. Die Ergebnisse erweitern das Wissen unseren Kunden über ihre Site-Besucher mit neuen Datenpunkten. Wenn der Besucher-ID-Service keine ID abgleichen kann, wird eine neue ID erstellt und diese ID für die zukünftige Synchronisierung verwendet.

Messen Sie Übereinstimmungsraten und überprüfen Sie die Effektivität des ID-Synchronisierungsprozesses. Hohe Übereinstimmungsraten deuten darauf hin, dass ein bestimmter Service effektiver ist und Zugang zu einer größeren Online-Zielgruppe bietet als ein Service mit niedrigen Übereinstimmungsraten. Der Vergleich von Übereinstimmungsraten ist eine quantifizierbare Methode zur Auswertung verschiedener integrierter Anzeigentechnologieplattformen.

![](assets/idsync2.png)

**Gewährleisten hoher Übereinstimmungsraten**

Eine ordnungsgemäße Implementierung trägt dazu bei, hohe Übereinstimmungsraten sicherzustellen, da der Besucher-ID-Service die Cookies setzen kann, die zum Funktionieren und Synchronisieren von IDs mit aktivierten Datenpartnern erforderlich sind. Faktoren wie langsame Internetverbindungen, die Datenerfassung von Mobilgeräten oder drahtlosen Netzwerken können sich jedoch darauf auswirken, wie gut der Besucher-ID-Dienst IDs erfasst, synchronisiert und abgleicht. Diese clientseitigen Variablen werden weder vom Besucher-ID-Service noch von Adobe gesteuert.

## Beschriebener ID-Synchronisierungsprozess {#section-a541a85cbbc74f5682824b1a2ee2a657}

Der Besucher-ID-Dienst synchronisiert IDs in Echtzeit. Dieser Prozess funktioniert im Browser und nicht über eine Server-zu-Server-Datenübertragung. In der folgenden Tabelle werden die Schritte im ID-Synchronisierungsprozess beschrieben.

**Schritt 1: Seite laden**

Wenn ein Besucher auf Ihre Site kommt und eine Seite lädt, führt die `Visitor.getInstance`-Funktion einen [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)- oder JSON-P-Aufruf an den Besucher-ID-Service durch. Der Besucher-ID-Dienst antwortet mit einem Cookie, der die ECID des Besuchers enthält. Bei der MID handelt es sich um eine jedem Sitebesucher zugewiesene eindeutige ID. Siehe auch [Cookies und der Besucher-ID-Dienst](../introduction/cookies.md).

**Schritt 2: iFrame laden**

Während der Seitentext geladen wird, lädt der Besucher-ID-Dienst einen iFrame namens *`Destination Publishing iFrame`*. Der [!UICONTROL Destination Publishing iFrame] wird in einer Domain geladen, die von der übergeordneten Seite getrennt ist. Dieses Design trägt zur Gewährleistung der Seiten-Performance bei und verbessert die Sicherheit, da der iFrame:

* asynchron in Bezug auf die übergeordnete Seite geladen wird. Die übergeordnete Seite kann demnach unabhängig vom [!UICONTROL Destination Publishing iFrame] geladen werden. Das Laden des iFrames und das Laden der ID-Synchronisierungspixel aus dem iFrame wirken sich nicht auf die übergeordnete Seite oder das Kundenerlebnis aus.
* so schnell wie möglich lädt. Wenn dies zu schnell ist, können Sie den iFrame nach dem Fensterladeereignis laden (nicht empfohlen). Weitere Informationen finden Sie unter [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4).
* verhindert, dass Code im iFrame Zugriff auf die übergeordnete Seite erhält oder diese beeinflusst.

Siehe auch [Anfordern und Festlegen von IDs durch den Besucher-ID-Service](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**Schritt 3: ID-Synchronisierungen auslösen**

Die ID-Synchronisierung ist eine URL, die im Destination Publishing iFrame ausgelöst wird. Wie in diesem generischen Beispiel gezeigt, enthält eine ID-Synchronisierungs-URL den ID-Synchronisierungsendpunkt eines Partners und eine Umleitungs-URL, bei der es sich um eine Umleitung zurück zu Adobe handelt, die ihre ID enthält.

`http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<ADOBE_PARTNER_ID>&dpuuid=<PARTNER_UUID>`

Siehe auch [ID-Synchronisierung für eingehende Datenübertragungen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/sending-audience-data/batch-data-transfer-process/id-sync-http.html?lang=de).

**Schritt 4: IDs speichern**

Synchronisierte IDs werden auf den [Edge- und Core-Daten-Servern gespeichert](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-edge.html?lang=de).

## Synchronisierungsdienste verwalten die ID-Synchronisierung {#section-cd5784d7ad404a24aa28ad4816a0119a}

Der Begriff *`Sync Services`* bezieht sich auf interne CX Enterprise-Technologien, die für die ID-Synchronisierung verantwortlich sind. Dieser Service ist standardmäßig aktiviert. Um ihn zu deaktivieren, fügen Sie [&#x200B; Funktion Besucher-ID](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414)Service eine „optionale Variable“ `Visitor.getInstance`. Die Synchronisierungs-Services gleichen unterschiedliche ECIDs ab, z. B.:

* CX-Enterprise-Cookie-IDs von Drittanbietern an Erstanbieter-ECIDs.

* First-Party-CX-Enterprise-Cookie-IDs zu Adobe Media Optimizer (AMO)-IDs.

* CX-Enterprise-Cookie-IDs von Drittanbietern an Datenanbieter- und Targeting-Plattform-IDs von Drittanbietern. Dies umfasst Services und Plattformen wie Datenanbieter, bedarfsgesteuerte bzw. anbieterseitige Plattformen, Werbenetzwerke, Austausche usw.
* First-Party-CX-Enterprise-Cookie-IDs zu geräteübergreifenden Partner-IDs.

## ID-Synchronisierung mit Adobe Advertising Cloud {#section-642c885ea65d45ffb761f78838735016}

Adobe Advertising Cloud (früher Adobe Media Optimizer genannt) bildet eine Ausnahme zum iFrame-basierten ID-Synchronisierungsprozess. Da es sich bei Advertising Cloud um eine vertrauenswürdige Domain handelt, erfolgt die ID-Synchronisierung von der übergeordneten Seite aus statt im [!UICONTROL Destination Publishing iFrame]. Bei der Synchronisierung ruft der Besucher-ID-Dienst Advertising Cloud unter `cm.eversttech.net` auf. Dies ist ein veralteter Domain-Name, der von Advertising Cloud vor der Akquise durch Adobe verwendet wurde. Das Senden von Daten an Advertising Cloud hilft, Übereinstimmungsraten zu verbessern, und wird für Kunden mit Version 2.0 des Besucher-ID-Service (oder höher) automatisch durchgeführt. Siehe auch [Advertising Cloud-Cookies](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-advertising-cloud.html?lang=de).

>[!MORELIKETHIS]
>
>* [Aufrufe an die Domain „demdex.net“](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de)

