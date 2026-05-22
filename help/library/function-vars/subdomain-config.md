---
description: Mit diesen Konfigurationen ändern Sie den Standard-Domänennamen, der bei Aufrufen an den Experience Cloud Identity Service verwendet wird, in den Namen Ihrer eigenen untergeordneten Domain.
keywords: ID-Dienst
title: audienceManagerServer und audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 222
ht-degree: 100%

---

# audienceManagerServer und audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Mit diesen Konfigurationen ändern Sie den Standard-Domänennamen, der bei Aufrufen an den Experience Cloud Identity Service verwendet wird, in den Namen Ihrer eigenen untergeordneten Domain.

**Syntax:**

* `audienceManagerServer: " *`Name Ihrer untergeordneten Domain`*.demdex.net"`
* `audienceManagerServerSecure: " *`Name Ihrer untergeordneten Domain`*.demdex.net"`

**Zweck**

Normalerweise führt der [!DNL Experience Cloud] ID-Dienst Aufrufe an [!DNL Adobe] unter Verwendung von `dpm.demdex.net` durch. In bestimmten Fällen möchten Sie nicht, dass dieses Ziel aufgerufen wird, weil es zu allgemein oder zu sehr nach einem Drittanbieter aussieht. Damit der Aufruf des ID-Diensts mehr wie ein Erstanbieter-Aufruf aussieht, können Sie mit den folgenden Konfigurationen den Namen Ihrer untergeordneten [!DNL Audience Manager]-Domain `demdex.net` hinzuzufügen (siehe unten). Weitere Informationen zum `dpm.demdex.net`-Aufruf finden Sie unter [Aufrufe an die Domain „demdex.net“](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de).

**Anforderungen**

Für diese Konfigurationen müssen Sie Folgendes verwenden:

* Den archivierbaren Namen der untergeordneten [!DNL Audience Manager]-Domain Ihres Unternehmens. Überprüfen Sie den Namen oder fragen Sie Ihren Berater danach.
* Den Namen der untergeordneten Domain, der Ihrer [!UICONTROL Organization ID] zugewiesen ist.
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

