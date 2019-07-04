---
description: Mit diesen Konfigurationen ändern Sie den Standard-Domänennamen, der von Aufrufen an den Experience Cloud ID-Dienst verwendet wird, in den Namen Ihrer eigenen untergeordneten Domäne.
keywords: ID-Dienst
seo-description: Mit diesen Konfigurationen ändern Sie den Standard-Domänennamen, der von Aufrufen an den Experience Cloud ID-Dienst verwendet wird, in den Namen Ihrer eigenen untergeordneten Domäne.
seo-title: audienceManagerServer und audienceManagerServerSecure
title: audienceManagerServer und audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# audienceManagerServer und audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Mit diesen Konfigurationen ändern Sie den Standard-Domänennamen, der von Aufrufen an den Experience Cloud ID-Dienst verwendet wird, in den Namen Ihrer eigenen untergeordneten Domäne.

**Syntax:**

* ` audienceManagerServer: " *`Name Ihrer untergeordneten Domäne`*.demdex.net"`
* ` audienceManagerServerSecure: " *`Name Ihrer untergeordneten Domäne`*.demdex.net"`

**Zielsetzung**

Normalerweise führt der [!DNL Experience Cloud] ID-Dienst Aufrufe an [!DNL Adobe] unter Verwendung von `dpm.demdex.net` durch. In bestimmten Fällen möchten Sie nicht, dass dieses Ziel aufgerufen wird, weil es zu allgemein oder zu sehr nach einem Drittanbieter aussieht. Damit der Aufruf des ID-Diensts mehr wie ein Erstanbieter-Aufruf aussieht, können Sie mit den folgenden Konfigurationen den Namen Ihrer untergeordneten [!DNL Audience Manager]-Domäne `demdex.net` hinzuzufügen (siehe unten). Weitere Informationen zum Aufruf `dpm.demdex.net` finden Sie unter [Aufrufe an die Domäne „demdex.net“](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Voraussetzungen**

Für diese Konfigurationen müssen Sie Folgendes verwenden:

* Den Namen der untergeordneten [!DNL Audience Manager]-Domäne für den Datensatz Ihres Unternehmens. Überprüfen Sie den Namen oder fragen Sie Ihren Berater danach.
* Den Namen der untergeordneten Domäne, der Ihrer [!DNL Organization ID] zugewiesen ist.
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

