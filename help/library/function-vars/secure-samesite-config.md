---
description: Eine Konfiguration innerhalb der ECID, die zur Unterstützung von AMCV-Cookies auf Google AMP-Seiten verwendet werden kann.
keywords: ID-Dienst
seo-description: Eine Konfiguration innerhalb der ECID, die zur Unterstützung von AMCV-Cookies auf Google AMP-Seiten verwendet werden kann.
seo-title: Sichere und SameSite-Konfigurationen
title: Sichere und SameSite-Konfigurationen
translation-type: ht
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: ht
source-wordcount: '174'
ht-degree: 100%

---


# Sichere und SameSite-Konfigurationen

Mit dieser Konfiguration können Sie die Einstellungen für Ihre Cookies ändern und [AMCV-Cookies](../../introduction/cookies.md) auf Google AMP-Seiten unterstützen.

Der Adobe-Besucher-ID-Service stellt ECID-Cookies mit der Browser-Standardeinstellung `SameSite = Lax` ein, auf die nicht zugegriffen werden kann, wenn die Seite wie eine Google AMP-Seite in einen Iframe geladen wird. Um auf ECID-Cookies zuzugreifen, verwenden Sie die folgenden Konfigurationen, um die SameSite-Einstellung auf `SameSite = None` zu aktualisieren.

>[!NOTE]
>
>Darüber hinaus müssen bei der Anwendung von `SameSite = None` Cookies auf `Secure` festgelegt werden, damit Daten nur über HTTPS-Verbindungen weitergeleitet werden können.

**Implementierung**:

Wenn Sie Adobe Experience Platform Launch verwenden, aktualisieren Sie Ihre Experience Cloud ID-Erweiterung auf Version 5.1.0 und konfigurieren Sie `secureCookie: true` und `sameSiteCookie: none`.

Wenn Sie Experience Platform Launch nicht verwenden, aktualisieren Sie auf die neueste Besucher 5.1.0-Bibliothek und befolgen Sie bei der Initialisierung der Besucher-Instanz die folgenden Konfigurationen:

**Codebeispiel**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
