---
title: Opt-in zur Steuerung von CX Enterprise-Aktivitäten auf Basis des Benutzereinverständnisses
description: Das Opt-in-Objekt von Adobe ist eine Erweiterung des Besucher-ID-Service von Adobe, mit dem Sie steuern können, ob und welche CX Enterprise-Lösungen basierend auf der Zustimmung des Endbenutzers auf Web-Seiten Cookies erstellen oder Beacons auslösen können.
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
TQID: https://experienceleague.adobe.com/YfYkXzK8wKw6JC3-EB2ljIOfXGXQV5r6Nw2-XYsGW6c
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 518
ht-degree: 28%

---

# Steuern von CX-Unternehmensaktivitäten auf Basis des Benutzereinverständnisses

Das Adobe [!UICONTROL Opt-in]-Objekt ist eine Erweiterung des Besucher-ID-Service von Adobe, mit dem Sie steuern können, ob und welche CX Enterprise-Lösungen basierend auf der Zustimmung des Endbenutzers auf Web-Seiten Cookies erstellen oder Beacons auslösen können.

## Die Grundlagen der [!UICONTROL Opt-In]

Ein wichtiger Aspekt der Datenschutzbestimmungen ist der Erwerb und die Übermittlung des Einverständnisses der Benutzer darüber, wie und von wem ihre personenbezogenen Daten verwendet werden dürfen. Die neueste Version des Besucher-ID-Service umfasst Funktionen, die bedingte Auslösung von CX Enterprise-Lösungs-Tags (z. B. vor und nach der Zustimmung) bereitstellen, je nachdem, ob die Zustimmung des Endbenutzers eingeholt wurde. Dies wird in der folgenden Abbildung verdeutlicht:

![Abbildung der Funktionsweise von [!UICONTROL Opt-in]](assets/opt-in.png)

[!UICONTROL Opt-in] funktioniert wie folgt:

**Wenn [!UICONTROL Opt-in] im Besucher-ID-Service aktiviert ist (über eine boolesche Variable), werden die CX Enterprise-Lösungsbibliotheken daran gehindert, Tags auszulösen oder Cookies zu setzen, bis ein Einverständnis für diese Lösung erteilt wurde.**

[!UICONTROL Opt-in] können Sie auch entscheiden, ob Tags vor dem Benutzereinverständnis ausgelöst werden. Diese Einverständnisinformationen werden dann (zusammen mit der Einwilligung des Endbenutzers) gespeichert, damit sie bei nachfolgenden Hits verwendet werden können. Die Speicherung des Einverständnisses ist in den [!UICONTROL Opt-in] Optionen verfügbar. Sie können aber auch eine CMP integrieren und das Einverständnis speichern lassen.

## Aktivieren und Konfigurieren von [!UICONTROL Opt-In]

[!UICONTROL Opt-in] lässt sich am einfachsten mit Tags konfigurieren. Im folgenden kurzen Videos finden Sie eine Anleitung.

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

Wenn Sie keine Tags verwenden, können Sie die Konfiguration von [!UICONTROL Opt-in] bei der Initialisierung des globalen Besucherobjekts festlegen, wie in der [Dokumentation) &#x200B;](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=de).

## Implementieren von [!UICONTROL Opt-In] auf der Seite

All diese Setup- und Backend-Dinge sind nur zur Vorbereitung, um Website-Besuchern eine Schnittstelle mit Einverständnisoptionen zu präsentieren. Diese Benutzeroberfläche kann von Ihnen selbst erstellt werden. Sie können aber auch einen CMP-Partner (Consent Management Platform) beauftragen, um die Benutzeroberfläche zu erstellen.

Wenn Sie eine Benutzeroberfläche einrichten, um [!UICONTROL Opt-in] zur Einholung von Einverständnissen zu verwenden, sollte diese so konfiguriert sein, dass sie APIs aufruft, die sich mit [!UICONTROL Opt-in] verbinden, und sie darüber informiert, dass sie einigen oder allen Adobe CX Enterprise-Lösungen zustimmt. Ausführliche Informationen zu diesen APIs finden Sie in der [Opt-in-Referenzdokumentation](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=de). Weitere Informationen zum Opt-in finden Sie auch auf den umliegenden Dokumentationsseiten.

## [!UICONTROL Opt-In] Demo

Im folgenden Video sehen Sie eine kurze Demo dazu, wie [!UICONTROL Opt-in] auf der Seite arbeiten und wie es beeinflusst, ob die CX Enterprise-Lösungen Cookies setzen können, Beacons starten können usw.

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**HINWEIS:** Es ist wichtig zu beachten, dass zum Zeitpunkt der Erstellung dieses Artikels [!UICONTROL Opt-in] nicht in den Bibliotheken aller CX Enterprise-Anwendungen integriert war. Die Bibliotheken, die derzeit für [!UICONTROL Opt-in] unterstützt werden, sind:

* Besucher-ID-Service
* Analytics
* Audience Manager
* Target

