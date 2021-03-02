---
description: Eine Konfiguration innerhalb der ECID, die zur Unterstützung von AMCV-Cookies auf Google AMP-Seiten verwendet werden kann.
keywords: ID-Dienst
seo-description: Eine Konfiguration innerhalb der ECID, die zur Unterstützung von AMCV-Cookies auf Google AMP-Seiten verwendet werden kann.
seo-title: Sichere und gleicheSite-Konfigurationen
title: Sichere und gleicheSite-Konfigurationen
translation-type: tm+mt
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 2%

---


# Sichere und gleicheSite-Konfigurationen

Mit dieser Konfiguration können Sie die Einstellungen für Ihre Cookies ändern und [AMCV-Cookies](../../introduction/cookies.md) auf Google AMP-Seiten unterstützen.

Der Adobe-Besucher-ID-Dienst stellt ECID-Cookies mit der Browserstandardeinstellung `SameSite = Lax` ein, auf die nicht zugegriffen werden kann, wenn die Seite wie eine Google AMP-Seite in einen iframe geladen wird. Um auf ECID-Cookies zuzugreifen, verwenden Sie die folgenden Konfigurationen, um die Einstellung SameSite auf `SameSite = None` zu aktualisieren.

>[!NOTE]
>
>Beim Anwenden von `SameSite = None` müssen Cookies auf `Secure` gesetzt werden, damit Daten nur über HTTPS-Verbindungen übergeben werden können.

**Implementierung**:

Wenn Sie Adobe Experience Platform Launch verwenden, aktualisieren Sie Ihre Experience Cloud-ID-Erweiterung auf Version 5.1.0 und konfigurieren Sie `secureCookie: true` und `sameSiteCookie: none`.

Wenn Sie Experience Platform Launch nicht verwenden, aktualisieren Sie bei der Initialisierung der Besucher-Instanz auf die neueste Besucher 5.1.0-Bibliothek und befolgen Sie die folgenden Konfigurationen:

**Codebeispiel**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
