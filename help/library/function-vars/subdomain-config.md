---
description: Mit diesen Konfigurationen ändern Sie den Standard-Domain-Namen, der von Aufrufen an den Besucher-ID-Dienst verwendet wird, in den Namen Ihrer eigenen Subdomain.
keywords: Besucher-ID-Service
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
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 234
ht-degree: 44%

---

# audienceManagerServer und audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Mit diesen Konfigurationen ändern Sie den Standard-Domain-Namen, der von Aufrufen an den Besucher-ID-Dienst verwendet wird, in den Namen Ihrer eigenen Subdomain.

**Syntax:**

* `audienceManagerServer: " *`Name Ihrer untergeordneten Domain`*.demdex.net"`
* `audienceManagerServerSecure: " *`Name Ihrer untergeordneten Domain`*.demdex.net"`

**Zweck**

Normalerweise ruft der Besucher-ID-Dienst Adobe unter `dpm.demdex.net` auf. In bestimmten Fällen möchten Sie nicht, dass dieses Ziel aufgerufen wird, weil es zu allgemein oder zu sehr nach einem Drittanbieter aussieht. Damit der Aufruf des Besucher-ID-Diensts mehr wie ein Erstanbieter-Aufruf aussieht, können Sie mit den folgenden Konfigurationen den Namen Ihrer Audience Manager-Subdomain `demdex.net` wie unten dargestellt hinzufügen. Weitere Informationen zum `dpm.demdex.net`-Aufruf finden Sie unter [Aufrufe an die Domain „demdex.net“](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=de).

**Anforderungen**

Für diese Konfigurationen müssen Sie Folgendes verwenden:

* Der Name der Audience Manager-Subdomain für den Datensatz Ihres Unternehmens. Überprüfen Sie den Namen oder fragen Sie Ihren Berater danach.
* Der mit Ihrer IMS-Organisations-ID verknüpfte Subdomain-Name.
* *Beide* Konfigurationsparameter mit demselben Subdomänennamen.

**Codebeispiel**

In diesem Beispiel nehmen wir an, dass ein Unternehmen für Unterhaltungsmedien rechtliche Bedenken bei Aufrufen an `dpm.demdex.net` hat. In Audience Manager lautet der Name der Unternehmens-Subdomain „Music1“. Das folgende Codebeispiel zeigt, wie Sie den Datenaufruf des Besucher-ID-Service mit diesem kundenspezifischen Subdomain-Namen versehen.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE",{ 
     ... 
     //Configure Visitor ID Service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

