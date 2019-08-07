---
description: Ändern Sie den Standarddomänennamen, der von Aufrufen zum Experience Cloud-Identitätsdienst verwendet wird, in Ihren eigenen Namen für die Subdomäne mit diesen Konfigurationen.
keywords: ID-Dienst
seo-description: Ändern Sie den Standarddomänennamen, der von Aufrufen zum Experience Cloud-Identitätsdienst verwendet wird, in Ihren eigenen Namen für die Subdomäne mit diesen Konfigurationen.
seo-title: audienceManagerServer und audienceManagerServerSecure
title: audienceManagerServer und audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# audienceManagerServer und audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Ändern Sie den Standarddomänennamen, der von Aufrufen zum Experience Cloud-Identitätsdienst verwendet wird, in Ihren eigenen Namen für die Subdomäne mit diesen Konfigurationen.

**Syntax:**

* ` audienceManagerServer: " *`Name Ihrer untergeordneten Domäne`*.demdex.net"`
* ` audienceManagerServerSecure: " *`Name Ihrer untergeordneten Domäne`*.demdex.net"`

**Zielsetzung**

Normalerweise führt der [!DNL Experience Cloud] ID-Dienst Aufrufe an [!DNL Adobe] unter Verwendung von `dpm.demdex.net` durch. In bestimmten Fällen möchten Sie nicht, dass dieses Ziel aufgerufen wird, weil es zu allgemein oder zu sehr nach einem Drittanbieter aussieht. Damit der Aufruf des ID-Diensts mehr wie ein Erstanbieter-Aufruf aussieht, können Sie mit den folgenden Konfigurationen den Namen Ihrer untergeordneten [!DNL Audience Manager]-Domäne `demdex.net` hinzuzufügen (siehe unten). Weitere Informationen über den `dpm.demdex.net`-Aufruf finden Sie unter [Aufrufe an die Domäne „demdex.net“](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Anforderungen**

Für diese Konfigurationen müssen Sie Folgendes verwenden:

* Den Namen der untergeordneten [!DNL Audience Manager]-Domäne für den Datensatz Ihres Unternehmens. Überprüfen Sie den Namen oder fragen Sie Ihren Berater danach.
* Den Namen der untergeordneten Domäne, der Ihrer [!UICONTROL Organisations-ID] zugewiesen ist.
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

