---
description: Das AMCV-Cookie enthält die Experience Cloud-ID (MID) und eine Regions-ID für Ihre Sitebesucher. Diese IDs werden als Schlüssel-Wert-Paare gespeichert. Die mid user-ID enthält die Experience Cloud ID des Besuchers. Die aamlh:region-ID enthält die Regions-ID für Ihre Sitebesucher. Sie können diese Informationen durch Analyse des AMCV-Cookies wiederherstellen.
keywords: ID Service
seo-description: Das AMCV-Cookie enthält die Experience Cloud-ID (MID) und eine Regions-ID für Ihre Sitebesucher. Diese IDs werden als Schlüssel-Wert-Paare gespeichert. Die mid user-ID enthält die Experience Cloud ID des Besuchers. Die aamlh:region-ID enthält die Regions-ID für Ihre Sitebesucher. Sie können diese Informationen durch Analyse des AMCV-Cookies wiederherstellen.
seo-title: Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem ID-Dienst
title: Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem ID-Dienst
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Abrufen von Regions- und Benutzer-IDs vom AMCV-Cookie oder dem ID-Dienst {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

Das AMCV-Cookie enthält die Experience Cloud-ID (MID) und eine Regions-ID für Ihre Sitebesucher. Diese IDs werden als Schlüssel-Wert-Paare gespeichert. Die mid:user-ID enthält die Experience Cloud ID des Besuchers. Die aamlh:region-ID enthält die Regions-ID für Ihre Site-Besucher. Sie können diese Informationen durch Analyse des AMCV-Cookies wiederherstellen.

For more information, see [Get User IDs and Regions Through the Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

Als [!DNL Audience Manager]-Kunde können Sie die Regions-ID aus der Antwort abrufen, die durch den Datenerfassungsserver (Data Collection Server, DCS) gesendet wurde. See [Get User IDs and Regions from a DCS Response](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

Sie können die Regions-ID auch mit einer durch den ID-Dienst bereitgestellten `GET`-Methode abrufen. Siehe [Abrufen von Regions-IDs (Standorthinweis)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
