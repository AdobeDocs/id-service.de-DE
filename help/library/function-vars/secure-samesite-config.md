---
description: Eine Konfiguration innerhalb der ECID, die zur Unterstützung von AMCV-Cookies auf Google AMP-Seiten verwendet werden kann.
keywords: ID-Dienst
title: Sichere und SameSite-Konfigurationen
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 156
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

