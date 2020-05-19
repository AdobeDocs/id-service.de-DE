---
description: Das AMCV-Cookie enthält die Experience Cloud-ID (MID) und eine Regions-ID für Ihre Sitebesucher. Diese IDs werden als Schlüssel-Wert-Paare gespeichert. Die mid user-ID enthält die Experience Cloud ID des Besuchers. Die aamlh:region-ID enthält die Regions-ID für Ihre Sitebesucher. Sie können diese Informationen durch Analyse des AMCV-Cookies wiederherstellen.
keywords: ID Service
seo-description: Das AMCV-Cookie enthält die Experience Cloud-ID (MID) und eine Regions-ID für Ihre Sitebesucher. Diese IDs werden als Schlüssel-Wert-Paare gespeichert. Die mid user-ID enthält die Experience Cloud ID des Besuchers. Die aamlh:region-ID enthält die Regions-ID für Ihre Sitebesucher. Sie können diese Informationen durch Analyse des AMCV-Cookies wiederherstellen.
seo-title: Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem ID-Dienst
title: Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem ID-Dienst
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '295'
ht-degree: 100%

---


# Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem ID-Dienst {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Das AMCV-Cookie enthält die Experience Cloud-ID (MID) und eine Regions-ID für Ihre Sitebesucher. Diese IDs werden als Schlüssel-Wert-Paare gespeichert. Die mid:user-ID enthält die Experience Cloud ID des Besuchers. Die aamlh:region-ID enthält die Regions-ID Ihrer Sitebesucher. Sie können diese Informationen durch Analyse des AMCV-Cookies wiederherstellen.

Weitere Informationen finden Sie unter [Abrufen von Benutzer-IDs und Regionen über den Experience Cloud Identity-Dienst](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

Als [!DNL Audience Manager]-Kunde können Sie die Regions-ID aus der Antwort abrufen, die durch den Datenerfassungsserver (Data Collection Server, DCS) gesendet wurde. Siehe [Abrufen von Benutzer-IDs und Regionen aus einer DCS-Antwort](https://docs.adobe.com/content/help/de-DE/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

Sie können die Regions-ID auch mit einer durch den ID-Dienst bereitgestellten `GET`-Methode abrufen. Siehe [Abrufen von Regions-IDs (Standorthinweis)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
