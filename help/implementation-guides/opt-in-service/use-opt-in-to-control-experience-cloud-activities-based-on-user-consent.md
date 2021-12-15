---
title: Opt-in zur Steuerung von Experience Cloud-Aktivitäten auf Basis des Benutzereinverständnisses
description: Das Opt-in-Objekt für die Adobe ist eine Erweiterung des Adobe Experience Platform Identity-Diensts, mit dem Sie steuern können, ob und welche Experience Cloud-Lösungen basierend auf der Zustimmung des Endbenutzers Cookies auf Webseiten erstellen oder Beacons auslösen können.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 47%

---

# Experience Cloud-Aktivitäten auf Basis des Benutzereinverständnisses steuern

Die Adobe [!UICONTROL Opt-in] Object ist eine Erweiterung der Adobe [!UICONTROL Experience Platform Identity-Dienst], mit dem Sie steuern können, ob und welche Experience Cloud-Lösungen basierend auf der Zustimmung des Endbenutzers Cookies auf Webseiten erstellen oder Beacons auslösen können.

## Die Grundlagen des [!UICONTROL Opt-in]

Ein wichtiger Aspekt der Datenschutzbestimmungen ist der Erwerb und die Übermittlung des Einverständnisses der Benutzer darüber, wie und von wem ihre personenbezogenen Daten verwendet werden dürfen. Die neueste Version der [!UICONTROL Identity Service] umfasst Funktionen, die bedingte Auslösung von Experience Cloud-Lösungs-Tags (z. B. vor und nach der Zustimmung) bereitstellen, je nachdem, ob die Zustimmung des Endbenutzers eingeholt wurde. Dieser Prozess wird in der folgenden Abbildung gezeigt:

![ Abbildung der Funktionsweise von [!UICONTROL  Opt-in] ](assets/opt-in.png)

[!UICONTROL Opt-in] funktioniert wie folgt:

**Wenn [!UICONTROL Opt-in] im Identity Service aktiviert ist (über eine boolesche Variable), werden die Bibliotheken der Experience Cloud-Lösung daran gehindert, Tags auszulösen oder Cookies zu setzen, bis ein Einverständnis für diese Lösung erteilt wurde.**

[!UICONTROL Opt-in] Sie können auch entscheiden, ob Tags vor der Zustimmung des Benutzers ausgelöst werden. Anschließend werden diese Zustimmungsinformationen (zusammen mit der Einwilligung des Endbenutzers) gespeichert, damit sie bei nachfolgenden Treffern verwendet werden können. Die Speicherung der Einwilligung ist in den [!UICONTROL Opt-in]-Optionen verfügbar. Sie können sie auch in eine CMP integrieren und eine Auswahl der Einwilligungen speichern lassen.

## Aktivieren und Konfigurieren von [!UICONTROL Opt-ins]

[!UICONTROL Opt-in] ist am einfachsten mit Adobe Experience Platform-Tags (früher Launch) konfigurierbar. Im folgenden kurzen Videos finden Sie eine Anleitung.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Wenn Sie keine Experience Platform-Tags verwenden, können Sie [!UICONTROL Opt-in]-Konfiguration in der Initialisierung des globalen Besucherobjekts, wie in der [Dokumentation](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## Implementierung des [!UICONTROL Opt-in] auf der Seite

All diese Setup- und Backend-Dinge sind nur zur Vorbereitung, um Website-Besuchern eine Schnittstelle mit Einverständnisoptionen zu präsentieren. Diese Benutzeroberfläche kann von Ihnen selbst erstellt werden. Sie können aber auch einen CMP-Partner (Consent Management Platform) beauftragen, um die Benutzeroberfläche zu erstellen.

Beim Einrichten einer Benutzeroberfläche für die Verwendung von [!UICONTROL Opt-in] zum Einholen des Einverständnisses sollte diese so konfiguriert werden, dass APIs aufgerufen werden, die mit dem [!UICONTROL Opt-in] verbunden sind und darüber informieren, dass einige oder alle Adobe Experience Cloud-Lösungen genehmigt werden. Ausführliche Informationen zu diesen APIs finden Sie in der [Opt-in-Referenzdokumentation](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en). Weitere Informationen zum Opt-in finden Sie auch auf den umliegenden Dokumentationsseiten.

## Demo für [!UICONTROL Opt-in]

Im folgenden Video sehen Sie eine kurze Demo von [!UICONTROL Opt-in] Arbeiten auf der Seite und wie sie beeinflussen kann, ob die Experience Cloud-Lösungen Cookies setzen, Beacons starten usw.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**HINWEIS:** Es ist wichtig festzustellen, dass zum Zeitpunkt der Erstellung dieses Artikels [!UICONTROL Opt-in] wurde nicht für alle Experience Cloud-Anwendungen in die Bibliotheken integriert. Folgende Bibliotheken werden derzeit für [!UICONTROL Opt-in] unterstützt:

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
