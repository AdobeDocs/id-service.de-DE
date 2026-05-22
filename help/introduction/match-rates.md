---
description: Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Cloud Identity Service, einschließlich Adobe Media Optimizer und ID-Service.
keywords: ID-Service
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
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 819
ht-degree: 96%

---

# Grundlegendes zu ID-Synchronisierung und Übereinstimmungsraten{#understanding-id-synchronization-and-match-rates}

Eine Übersicht über die ID-Synchronisierungsprozesse und Übereinstimmungsraten im Experience Cloud Identity Service, einschließlich Adobe Media Optimizer und ID-Dienst.

## ID-Synchronisierung und Übereinstimmungsraten {#section-f652aae7234945e89d26dd833c5215fb}

Bei der ID-Synchronisierung werden durch den ID-Service zugewiesene IDs mit von unseren Kunden zu Site-Besuchern zugewiesenen IDs abgeglichen. Angenommen, der ID-Service hat eine Besucher-ID „1234“ zugewiesen. Eine andere Plattform kennt diesen Besucher unter der ID „4321“. Der ID-Service ordnet diese IDs während des Synchronisierungsprozesses zusammen zu. Die Ergebnisse erweitern das Wissen unseren Kunden über ihre Site-Besucher mit neuen Datenpunkten. Wenn der ID-Serviceeine ID nicht zuordnen kann, wird eine neue ID erstellt und diese ID für die künftige Synchronisierung verwendet.

Messen Sie Übereinstimmungsraten und überprüfen Sie die Effektivität des ID-Synchronisierungsprozesses. Hohe Übereinstimmungsraten deuten darauf hin, dass ein bestimmter Service effektiver ist und Zugang zu einer größeren Online-Zielgruppe bietet als ein Service mit niedrigen Übereinstimmungsraten. Der Vergleich von Übereinstimmungsraten ist eine quantifizierbare Methode zur Auswertung verschiedener integrierter Anzeigentechnologieplattformen.

![](assets/idsync2.png)

**Gewährleisten hoher Übereinstimmungsraten**

Eine ordnungsgemäße Implementierung trägt dazu bei, hohe Übereinstimmungsraten sicherzustellen, da der ID-Service die Cookies setzen kann, die zum Arbeiten mit und Synchronisieren von IDs mit aktivierten Datenpartnern erforderlich sind. Faktoren wie langsame Internetverbindungen, die Datenerfassung von Mobilgeräten oder drahtlosen Netzwerken können sich jedoch auf die Qualität der Erfassung, Synchronisierung und des Abgleichs von IDs durch den ID-Service auswirken. Diese clientseitigen Variablen werden weder durch den ID-Service noch von [!DNL Adobe] gesteuert.

## Beschriebener ID-Synchronisierungsprozess {#section-a541a85cbbc74f5682824b1a2ee2a657}

Der ID-Service synchronisiert IDs in Echtzeit. Dieser Prozess funktioniert im Browser und nicht über eine Server-zu-Server-Datenübertragung. In der folgenden Tabelle werden die Schritte im ID-Synchronisierungsprozess beschrieben.

**Schritt 1: Seite laden**

Wenn ein Besucher auf Ihre Site kommt und eine Seite lädt, führt die Funktion `Visitor.getInstance` einen [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)- oder JSON-P-Aufruf an den ID-Service durch. Der ID-Service antwortet mit einem Cookie, der die [!DNL Experience Cloud] ID (MID) des Besuchers enthält. Bei der MID handelt es sich um eine jedem Sitebesucher zugewiesene eindeutige ID. Siehe auch [Cookies und der Experience Cloud Identity Service](../introduction/cookies.md).

**Schritt 2: iFrame laden**

Während der Seitentext geladen wird, lädt der ID-Service einen iFrame namens *`Destination Publishing iFrame`*. Der [!UICONTROL Destination Publishing iFrame] wird in einer Domain geladen, die von der übergeordneten Seite getrennt ist. Dieses Design trägt zur Gewährleistung der Seiten-Performance bei und verbessert die Sicherheit, da der iFrame:

* asynchron in Bezug auf die übergeordnete Seite geladen wird. Die übergeordnete Seite kann demnach unabhängig vom [!UICONTROL Destination Publishing iFrame] geladen werden. Das Laden des iFrames und das Laden der ID-Synchronisierungspixel aus dem iFrame wirken sich nicht auf die übergeordnete Seite oder das Kundenerlebnis aus.
* so schnell wie möglich lädt. Wenn dies zu schnell ist, können Sie den iFrame nach dem Fensterladeereignis laden (nicht empfohlen). Weitere Informationen finden Sie unter [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4).
* verhindert, dass Code im iFrame Zugriff auf die übergeordnete Seite erhält oder diese beeinflusst.

Siehe auch [Anfordern und Festlegen von IDs durch den Experience Cloud Identity Service](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**Schritt 3: ID-Synchronisierungen auslösen**

Die ID-Synchronisierung ist eine URL, die im Destination Publishing iFrame ausgelöst wird. Eine URL für die ID-Synchronisierung enthält, wie in diesem generischen Beispiel gezeigt, den ID-Synchronisierungsendpunkt eines Partners und eine Umleitungs-URL, die zu [!DNL Adobe] zurückleitet und die entsprechende ID enthält.

`http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<ADOBE_PARTNER_ID>&dpuuid=<PARTNER_UUID>`

Siehe auch [ID-Synchronisierung für eingehende Datenübertragungen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/sending-audience-data/batch-data-transfer-process/id-sync-http.html?lang=de).

**Schritt 4: IDs speichern**

Synchronisierte IDs werden auf den [Edge- und Core-Daten-Servern gespeichert](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/system-components/components-edge.html?lang=de).

## Synchronisierungsdienste verwalten die ID-Synchronisierung {#section-cd5784d7ad404a24aa28ad4816a0119a}

Der Begriff *`Sync Services`* bezieht sich auf interne [!DNL Experience Cloud]-Technologien, die für die ID-Synchronisation verantwortlich sind. Dieser Service ist standardmäßig aktiviert. Um sie zu deaktivieren, fügen Sie [&#x200B; ID-Service-`Visitor.getInstance` eine &#x200B;](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414)optionale Variable“ hinzu. Die Synchronisierungs-Services gleichen unterschiedliche [!DNL Experience Cloud]-IDs ab, beispielsweise:

* [!DNL Experience Cloud]-Cookie-IDs von Drittanbietern mit [!DNL Experience Cloud]-IDs von Erstanbietern.

* [!DNL Experience Cloud]-Cookie-IDs von Erstanbietern mit [!DNL Adobe Media Optimizer]-IDs (AMO).

* [!DNL Experience Cloud]-Cookie-IDs von Drittanbietern mit Drittdatenanbieter- und Targeting Platform-IDs. Dies umfasst Services und Plattformen wie Datenanbieter, bedarfsgesteuerte bzw. anbieterseitige Plattformen, Werbenetzwerke, Austausche usw.
* [!DNL Experience Cloud]-Cookie-IDs von Erstanbietern mit geräteübergreifenden Partner-IDs.

## ID-Synchronisierung mit Adobe Advertising Cloud {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Advertising Cloud] (früher [!DNL Adobe Media Optimizer] genannt) bildet eine Ausnahme zum iFrame-basierten ID-Synchronisierungsprozess. Da es sich bei [!DNL Advertising Cloud] um eine vertrauenswürdige Domain handelt, erfolgt die ID-Synchronisierung von der übergeordneten Seite aus statt im [!UICONTROL Destination Publishing iFrame]. Bei der Synchronisierung ruft der ID-Dienst [!DNL Advertising Cloud] unter `cm.eversttech.net` den älteren Domänennamen auf, der von [!DNL Advertising Cloud] vor der Akquise durch Adobe verwendet wurde. Das Senden von Daten an [!DNL Advertising Cloud] kann Übereinstimmungsraten verbessern und wird für Kunden mit Version 2.0 des ID-Service (oder höher) automatisch durchgeführt. Siehe auch [Advertising Cloud-Cookies](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-advertising-cloud.html?lang=de).

>[!MORELIKETHIS]
>
>* [Aufrufe an die Domain „demdex.net“](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de)

