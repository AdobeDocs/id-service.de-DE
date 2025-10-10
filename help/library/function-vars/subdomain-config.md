---
description: Mit diesen Konfigurationen ändern Sie den Standard-Domänennamen, der bei Aufrufen an den Experience Cloud Identity Service verwendet wird, in den Namen Ihrer eigenen untergeordneten Domain.
keywords: ID-Dienst
title: audienceManagerServer und audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 100%

---

# audienceManagerServer und audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Mit diesen Konfigurationen ändern Sie den Standard-Domänennamen, der bei Aufrufen an den Experience Cloud Identity Service verwendet wird, in den Namen Ihrer eigenen untergeordneten Domain.

**Syntax:**

* `audienceManagerServer: " *`Name Ihrer untergeordneten Domain`*.demdex.net"`
* `audienceManagerServerSecure: " *`Name Ihrer untergeordneten Domain`*.demdex.net"`

**Zielsetzung**

Normalerweise führt der [!DNL Experience Cloud] ID-Dienst Aufrufe an [!DNL Adobe] unter Verwendung von `dpm.demdex.net` durch. In bestimmten Fällen möchten Sie nicht, dass dieses Ziel aufgerufen wird, weil es zu allgemein oder zu sehr nach einem Drittanbieter aussieht. Damit der Aufruf des ID-Diensts mehr wie ein Erstanbieter-Aufruf aussieht, können Sie mit den folgenden Konfigurationen den Namen Ihrer untergeordneten [!DNL Audience Manager]-Domain `demdex.net` hinzuzufügen (siehe unten). Weitere Informationen zum `dpm.demdex.net`-Aufruf finden Sie unter [Aufrufe an die Domain „demdex.net“](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de).

**Anforderungen**

Für diese Konfigurationen müssen Sie Folgendes verwenden:

* Den archivierbaren Namen der untergeordneten [!DNL Audience Manager]-Domain Ihres Unternehmens. Überprüfen Sie den Namen oder fragen Sie Ihren Berater danach.
* Den untergeordneten Domänenname, der Ihrer [!UICONTROL Organisations-ID] zugewiesen ist.
* *Beide* Konfigurationsparameter mit demselben Subdomänennamen.

**Codebeispiel**

In diesem Beispiel nehmen wir an, dass ein Unternehmen für Unterhaltungsmedien rechtliche Bedenken bei Aufrufen an `dpm.demdex.net` hat. In [!DNL Audience Manager] lautet der archivierbare untergeordnete Domänenname des Unternehmens „Music1“. Das folgende Codebeispiel zeigt, wie der Datenaufruf des ID-Diensts mit diesem kundenspezifischen untergeordneten Domänennamen versehen wird.

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
