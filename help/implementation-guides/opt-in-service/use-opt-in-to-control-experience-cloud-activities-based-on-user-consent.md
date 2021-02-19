---
title: Opt-in zur Steuerung von Experience Cloud-Aktivitäten auf Basis des Benutzereinverständnisses
description: Das Opt-in-Objekt von Adobe ist eine Erweiterung des Adobe Experience Platform Identity Service, mit dem Sie steuern können, ob und welche Experience Cloud-Lösungen basierend auf der Zustimmung des Endbenutzers auf Web-Seiten Cookies erstellen oder Beacons auslösen können.
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Experience Cloud-Aktivitäten auf Basis des Benutzereinverständnisses steuern

Das [!UICONTROL Opt-in]-Objekt von Adobe ist eine Erweiterung des [!UICONTROL Experience Platform Identity Service von Adobe], mit dem Sie steuern können, ob und welche Experience Cloud-Lösungen basierend auf der Zustimmung des Endbenutzers auf Web-Seiten Cookies erstellen oder Beacons auslösen können.

## Die Grundlagen des [!UICONTROL Opt-in]

Ein wichtiger Aspekt der Datenschutzbestimmungen ist der Erwerb und die Übermittlung des Einverständnisses der Benutzer darüber, wie und von wem ihre personenbezogenen Daten verwendet werden dürfen. Die neueste Version des [!UICONTROL Identity Service] umfasst Funktionen, die zwischen dem Benutzer (UI) und den Lösungen von Adobe angesiedelt sind. Dabei werden Adobe Experience Cloud-Lösungs-Tags abhängig davon ausgelöst, ob der Endbenutzer sein Einverständnis gegeben hat (z. B. vor und nach der Einverständniserteilung). Dies wird in der folgenden Abbildung verdeutlicht:

![Abbildung der Funktionsweise von [!UICONTROL Opt-in]](assets/opt-in.png)

[!UICONTROL Opt-in] ist im Grunde der Pförtner... oder der Schlüsselmeister Sie entscheiden.

Daraus ergibt sich Folgendes:

**Wenn [!UICONTROL Opt-in] im Identity Service aktiviert ist (über eine boolesche Variable), werden die Bibliotheken der Experience Cloud-Lösung daran gehindert, Tags auszulösen oder Cookies zu setzen, bis ein Einverständnis für diese Lösung erteilt wurde.**

[!UICONTROL Mit Opt-in] können Sie auch entscheiden, ob Tags *vor* dem Einverständnis eines Benutzers ausgelöst werden. Diese Einwilligungsinformationen werden dann (zusammen mit der Einwilligung des Endbenutzers) gespeichert, damit sie bei nachfolgenden Hits verwendet werden können. Die Speicherung der Einwilligung ist in den [!UICONTROL Opt-in]-Optionen verfügbar. Sie können sie auch in eine CMP integrieren und eine Auswahl der Einwilligungen speichern lassen.

## Aktivieren und Konfigurieren von [!UICONTROL Opt-ins]

[!UICONTROL Opt-in] lässt sich am einfachsten mit Adobe Experience Platform Launch konfigurieren. Im folgenden kurzen Videos finden Sie eine Anleitung.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Wenn Sie nicht Experience Platform Launch verwenden, können Sie die Konfiguration des [!UICONTROL Opt-in] bei der Initialisierung des globalen Besucher-Objekts festlegen, wie in der [Dokumentation](https://marketing.adobe.com/resources/help/de_DE/mcvid/getting-started.html)dargestellt.

## Implementierung des [!UICONTROL Opt-in] auf der Seite

All diese Setup- und Backend-Dinge sind nur zur Vorbereitung, um Website-Besuchern eine Schnittstelle mit Einverständnisoptionen zu präsentieren. Diese Benutzeroberfläche kann von Ihnen selbst erstellt werden. Sie können aber auch einen CMP-Partner (Consent Management Platform) beauftragen, um die Benutzeroberfläche zu erstellen.

Beim Einrichten einer Benutzeroberfläche für die Verwendung von [!UICONTROL Opt-in] zum Einholen des Einverständnisses sollte diese so konfiguriert werden, dass APIs aufgerufen werden, die mit dem [!UICONTROL Opt-in] verbunden sind und darüber informieren, dass einige oder alle Adobe Experience Cloud-Lösungen genehmigt werden. Ausführliche Informationen zu diesen APIs finden Sie in der [Opt-in-Referenzdokumentation](https://marketing.adobe.com/resources/help/de_DE/mcvid/api.html). Weitere Informationen zum Opt-in finden Sie auch auf den umliegenden Dokumentationsseiten.

## Demo für [!UICONTROL Opt-in]

Im folgenden Video sehen Sie eine kurze Demo dazu, wie das [!UICONTROL Opt-in] auf einer Seite funktioniert und wie es beeinflusst, ob die Experience Cloud-Lösungen Cookies setzen, Beacons starten usw.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**HINWEIS:** Es ist wichtig zu beachten, dass zum Zeitpunkt der Erstellung dieses Artikels [!UICONTROL Opt-in] nicht in den Bibliotheken aller Experience Cloud-Lösungen integriert war. Folgende Bibliotheken werden derzeit für [!UICONTROL Opt-in] unterstützt:

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
