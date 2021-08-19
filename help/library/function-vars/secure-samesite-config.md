---
description: Eine Konfiguration innerhalb der ECID, die zur Unterstützung von AMCV-Cookies auf Google AMP-Seiten verwendet werden kann.
keywords: ID-Dienst
title: Sichere und SameSite-Konfigurationen
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '154'
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
