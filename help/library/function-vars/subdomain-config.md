---
description: Ändern Sie den Standarddomänennamen, der von Aufrufen zum Experience Platform-Identitätsdienst verwendet wird, in Ihren eigenen Namen für die Subdomäne mit diesen Konfigurationen.
keywords: ID-Dienst
seo-description: Ändern Sie den Standarddomänennamen, der von Aufrufen zum Experience Platform-Identitätsdienst verwendet wird, in Ihren eigenen Namen für die Subdomäne mit diesen Konfigurationen.
seo-title: audienceManagerServer und audienceManagerServerSecure
title: audienceManagerServer und audienceManagerServerSecure
uuid: e 21 cacbf -5151-4 d 34-b 0 f 7-9 e 90275 f 4 c 7 c
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# audienceManagerServer und audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Ändern Sie den Standarddomänennamen, der von Aufrufen zum Experience Platform-Identitätsdienst verwendet wird, in Ihren eigenen Namen für die Subdomäne mit diesen Konfigurationen.

**Syntax:**

* ` audienceManagerServer: " *`Name Ihrer untergeordneten Domäne`*.demdex.net"`
* ` audienceManagerServerSecure: " *`Name Ihrer untergeordneten Domäne`*.demdex.net"`

**Zielsetzung**

Normally, the [!DNL Experience Cloud] ID service makes calls to [!DNL Adobe] at `dpm.demdex.net`. In bestimmten Fällen möchten Sie nicht, dass dieses Ziel aufgerufen wird, weil es zu allgemein oder zu sehr nach einem Drittanbieter aussieht. Damit der Aufruf des ID-Diensts mehr wie ein Erstanbieter-Aufruf aussieht, können Sie mit den folgenden Konfigurationen den Namen Ihrer untergeordneten [!DNL Audience Manager]-Domäne `demdex.net` hinzuzufügen (siehe unten). Weitere Informationen über den `dpm.demdex.net`-Aufruf finden Sie unter [Aufrufe an die Domäne „demdex.net“](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Voraussetzungen**

Für diese Konfigurationen müssen Sie Folgendes verwenden:

* Der [!DNL Audience Manager] Subdomänenname des Datensatzes für Ihr Unternehmen. Überprüfen Sie den Namen oder fragen Sie Ihren Berater danach.
* Der mit Ihr verknüpfte Subdomänenname [!DNL Organization ID].
* *Beide* Konfigurationsparameter mit dem gleichen untergeordneten Domänennamen.

**Codebeispiel**

In diesem Beispiel nehmen wir an, dass ein Unternehmen für Unterhaltungsmedien rechtliche Bedenken bei Aufrufen an `dpm.demdex.net` hat. In [!DNL Audience Manager] lautet der untergeordnete Domänenname des Unternehmens „Music1“. Das folgende Codebeispiel zeigt, wie der Datenaufruf des ID-Diensts mit diesem kundenspezifischen untergeordneten Domänennamen versehen wird.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

