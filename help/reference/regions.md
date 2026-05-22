---
description: Das AMCV-Cookie enthält die Experience Cloud ID (MID) und eine Regions-ID für Ihre Sitebesucher. Diese IDs werden als Schlüssel-Wert-Paare gespeichert. Die mid user-ID enthält die Experience Cloud ID des Besuchers. Die aamlh:region-ID enthält die Regions-ID für Ihre Sitebesucher. Sie können diese Informationen durch Analyse des AMCV-Cookies wiederherstellen.
keywords: ID-Dienst
title: Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem ID-Dienst
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 240
ht-degree: 91%

---

# Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem ID-Dienst {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Das AMCV-Cookie enthält die Experience Cloud ID (MID) und eine Regions-ID für Ihre Sitebesucher. Diese IDs werden als Schlüssel-Wert-Paare gespeichert. Die Mid:user-ID enthält die Experience Cloud-ID des Besuchers. Die aamlh:region ID enthält die Regions-ID für die Besucher Ihrer Site. Sie können diese Informationen durch Analyse des AMCV-Cookies wiederherstellen.

Weitere Informationen finden Sie unter [Abrufen von Benutzer-IDs und Regionen über den Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=de).

Als [!DNL Audience Manager]-Kunde können Sie die Regions-ID aus der Antwort abrufen, die durch den Datenerfassungsserver (Data Collection Server, DCS) gesendet wurde. Siehe [Abrufen von Benutzer-IDs und Regionen aus einer DCS-Antwort](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=de).

Sie können die Regions-ID auch mit einer durch den ID-Dienst bereitgestellten `GET`-Methode abrufen. Siehe [Abrufen von Regions-IDs (Standorthinweis)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).

