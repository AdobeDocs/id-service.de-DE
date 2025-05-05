---
title: Opt-in zur Steuerung von Experience Cloud-Aktivitäten auf Basis des Benutzereinverständnisses
description: Das Opt-in-Objekt von Adobe ist eine Erweiterung des Adobe Experience Platform Identity Service, mit dem Sie steuern können, ob und welche Experience Cloud-Lösungen basierend auf der Zustimmung des Endbenutzers auf Web-Seiten Cookies erstellen oder Beacons auslösen können.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 100%

---

# Steuern von Experience Cloud-Aktivitäten auf Basis des Anwendereinverständnisses

Das [!UICONTROL Opt-in]-Objekt von Adobe ist eine Erweiterung des [!UICONTROL Adobe Experience Platform Identity Service], mit dem Sie steuern können, ob und welche Experience Cloud-Lösungen basierend auf der Zustimmung des Endbenutzers auf Web-Seiten Cookies erstellen oder Beacons auslösen können.

## Die Grundlagen des [!UICONTROL Opt-in]

Ein wichtiger Aspekt der Datenschutzbestimmungen ist der Erwerb und die Übermittlung des Einverständnisses der Benutzer darüber, wie und von wem ihre personenbezogenen Daten verwendet werden dürfen. Die neueste Version des [!UICONTROL Identity Service] umfasst Funktionen, die bedingte Auslösung von Experience Cloud-Lösungs-Tags (z. B. vor und nach der Zustimmung) bereitstellen, je nachdem, ob die Zustimmung des Endbenutzers eingeholt wurde. Dies wird in der folgenden Abbildung verdeutlicht:

![Abbildung der Funktionsweise von [!UICONTROL Opt-in] ](assets/opt-in.png)

[!UICONTROL Opt-in] funktioniert wie folgt:

**Wenn [!UICONTROL Opt-in] im Identity Service aktiviert ist (über eine boolesche Variable), werden die Bibliotheken der Experience Cloud-Lösung daran gehindert, Tags auszulösen oder Cookies zu setzen, bis ein Einverständnis für diese Lösung erteilt wurde.**

Mit [!UICONTROL Opt-in] können Sie auch entscheiden, ob Tags vor dem Benutzereinverständnis ausgelöst werden. Diese Einwilligungsinformationen werden dann (zusammen mit der Einwilligung des Endbenutzers) gespeichert, damit sie bei nachfolgenden Hits verwendet werden können. Die Speicherung der Einwilligung ist in den [!UICONTROL Opt-in]-Optionen verfügbar. Sie können sie auch in eine CMP integrieren und eine Auswahl der Einwilligungen speichern lassen.

## Aktivieren und Konfigurieren von [!UICONTROL Opt-ins]

[!UICONTROL Opt-in] lässt sich am einfachsten mit Adobe Experience Platform-Tags (ehemals Launch) konfigurieren. Im folgenden kurzen Videos finden Sie eine Anleitung.

>[!VIDEO](https://video.tv.adobe.com/v/40334/?quality=12&captions=ger)

Wenn Sie keine Experience Platform-Tags verwenden, können Sie die Konfiguration des [!UICONTROL Opt-in] bei der Initialisierung des globalen Besucherobjekts festlegen, wie in der [Dokumentation](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=de) dargestellt.

## Implementierung des [!UICONTROL Opt-in] auf der Seite

All diese Setup- und Backend-Dinge sind nur zur Vorbereitung, um Website-Besuchern eine Schnittstelle mit Einverständnisoptionen zu präsentieren. Diese Benutzeroberfläche kann von Ihnen selbst erstellt werden. Sie können aber auch einen CMP-Partner (Consent Management Platform) beauftragen, um die Benutzeroberfläche zu erstellen.

Beim Einrichten einer Benutzeroberfläche für die Verwendung von [!UICONTROL Opt-in] zum Einholen des Einverständnisses sollte diese so konfiguriert werden, dass APIs aufgerufen werden, die mit dem [!UICONTROL Opt-in] verbunden sind und darüber informieren, dass einige oder alle Adobe Experience Cloud-Lösungen genehmigt werden. Ausführliche Informationen zu diesen APIs finden Sie in der [Opt-in-Referenzdokumentation](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=de). Weitere Informationen zum Opt-in finden Sie auch auf den umliegenden Dokumentationsseiten.

## Demo für [!UICONTROL Opt-in]

Im folgenden Video sehen Sie eine kurze Demo dazu, wie das [!UICONTROL Opt-in] auf einer Seite funktioniert und wie es beeinflusst, ob die Experience Cloud-Lösungen Cookies setzen können, Beacons starten können usw.

>[!VIDEO](https://video.tv.adobe.com/v/40339/?quality=12&captions=ger)

**HINWEIS:** Es ist wichtig zu beachten, dass zum Zeitpunkt der Erstellung dieses Artikels das [!UICONTROL Opt-in] nicht in den Bibliotheken aller Experience Cloud-Lösungen integriert war. Folgende Bibliotheken werden derzeit für [!UICONTROL Opt-in] unterstützt:

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
