---
title: Opt-in zur Steuerung von Experience Cloud-Aktivitäten auf Basis der Benutzerzustimmung verwenden
description: Das Opt-in-Objekt für die Adobe ist eine Erweiterung des Adobe Experience Platform Identity Service, mit dem Sie steuern können, ob und welche Experience Cloud-Lösungen auf Webseiten Cookies erstellen oder Beacons auslösen können, basierend auf der Zustimmung des Endbenutzers.
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# Experience Cloud-Aktivitäten auf Basis der Benutzerzustimmung steuern

Das [!UICONTROL Opt-in] -Objekt für die Adobe ist eine Erweiterung des Identitätsdienstes [!UICONTROL für die Adobe von]Experience Platformen, mit dem Sie steuern können, ob und welche Experience Cloud-Lösungen auf Webseiten Cookies erstellen oder Beacons auslösen können, basierend auf der Zustimmung des Endbenutzers.

## Grundlagen der [!UICONTROL Teilnahme]

Ein wichtiger Aspekt der Datenschutzbestimmungen ist der Erwerb und die Weitergabe der Einwilligung der Nutzer darüber, wie und von wem ihre personenbezogenen Daten verwendet werden dürfen. Die neueste Version des [!UICONTROL Identitätsdienstes] umfasst Funktionen, die zwischen dem Benutzer (UI) und den Lösungen für die Adobe stehen und die bedingte Auslösung (z. B. Vor- und Nacheinwilligung) von Adobe Experience Cloud-Lösungstags abhängig davon bereitstellen, ob der Endbenutzer seine Einwilligung erteilt hat. Dies wird in der folgenden Abbildung gezeigt:

![Abbildung der Funktionsweise von [!UICONTROL Opt-in]](assets/opt-in.png)

[!UICONTROL Opt-in] ist im Grunde der Schütze... oder ist es der Keymaster? Du entscheidest.

Daraus ergibt sich Folgendes:

**Wenn die [!UICONTROL Option] im Identitätsdienst aktiviert ist (über eine boolesche Variable), werden die Bibliotheken der Experience Cloud-Projektmappe daran gehindert, Tags auszulösen oder Cookies zu setzen, bis die Zustimmung für diese Lösung erteilt wurde.**

[!UICONTROL Mit der Teilnahme] können Sie auch entscheiden, ob Tags *vor* der Benutzereinwilligung ausgelöst werden, und dann diese Einwilligungsinformationen (zusammen mit der Einwilligung des Endbenutzers) gespeichert werden, damit sie bei nachfolgenden Treffern verwendet werden können. Die Datenspeicherung der Einwilligung ist in den [!UICONTROL Optionen für die Einwilligung] verfügbar, oder Sie können sie in eine CMP integrieren und die Auswahl der Einwilligung speichern lassen.

## Aktivieren und Konfigurieren der [!UICONTROL Teilnahme]

[!UICONTROL Opt-in] ist auch mit Adobe Experience Platform Launch am einfachsten konfigurierbar. Ansicht des folgenden kurzen Videos, um zu sehen, wie.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Wenn Sie Experience Platform Launch nicht verwenden, können Sie die [!UICONTROL Opt-in]-Konfiguration bei der Initialisierung des globalen Besucher-Objekts festlegen, wie in der [Dokumentation](https://marketing.adobe.com/resources/help/en_US/mcvid/getting-started.html)dargestellt.

## Implementierung [!UICONTROL des] Teilnahme-Teilnehmers auf der Seite

All diese Setup- und Backend-Dinge sind nur in Vorbereitung, um eine Schnittstelle für die Site-Besucher mit Zustimmungsoptionen zu präsentieren. Diese Benutzeroberfläche kann von Ihnen erstellt werden oder Sie können einen CMP-Partner (Consent Management Platform) verwenden, um die Benutzeroberfläche zu erstellen.

Beim Einrichten einer Benutzeroberfläche für die Verwendung von [!UICONTROL Opt-in] zum Sammeln der Zustimmung sollte diese so konfiguriert werden, dass APIs aufgerufen werden, die mit dem [!UICONTROL Opt-in] verbunden werden, und es informiert werden, dass einige oder alle Adobe Experience Cloud-Lösungen genehmigt werden. Ausführliche Informationen zu diesen APIs finden Sie in der [Opt-in-Referenzdokumentation](https://marketing.adobe.com/resources/help/en_US/mcvid/api.html). Weitere Informationen zur Teilnahme finden Sie auch auf den umliegenden Dokumentationsseiten.

## [!UICONTROL Demo für Teilnahme]

Im folgenden Video sehen Sie eine kurze Demo zur [!UICONTROL Teilnahme] an der Seite und wie sie beeinflussen kann, ob die Experience Cloud-Lösungen Cookies setzen, Beacons starten usw. können.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**HINWEIS:** Es ist wichtig zu beachten, dass zum Zeitpunkt der Erstellung dieses Artikels [!UICONTROL Opt-in] nicht in die Bibliotheken für alle Experience Cloud-Lösungen integriert wurde. Folgende Bibliotheken werden derzeit für [!UICONTROL Opt-in] unterstützt:

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
