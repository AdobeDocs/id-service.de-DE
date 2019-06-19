---
description: getInstance gibt ein Besucher-ID-Objekt für die festgelegte Experience Cloud-Organisations-ID zurück. Dies ist erforderlich, um das Besucher-ID-Objekt zu initialisieren, das mit s.visitor für AppMeasurement bereitgestellt wird.
keywords: ID-Dienst
seo-description: getInstance gibt ein Besucher-ID-Objekt für die festgelegte Experience Cloud-Organisations-ID zurück. Dies ist erforderlich, um das Besucher-ID-Objekt zu initialisieren, das mit s.visitor für AppMeasurement bereitgestellt wird.
seo-title: getInstance
title: getInstance
uuid: 259 b 88 a 6-e 3 d 0-4 aab-b 935-566099 bdab 98
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# getInstance{#getinstance}

getInstance gibt ein Besucher-ID-Objekt für die festgelegte Experience Cloud-Organisations-ID zurück. Dies ist erforderlich, um das Besucher-ID-Objekt zu initialisieren, das mit s.visitor für AppMeasurement bereitgestellt wird.

**Syntax**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*Instanziieren Sie die Besucherfunktion nicht* mit `var visitor = new Visitor`. Sie müssen den richtigen, hier aufgeführten Funktionsaufruf verwenden. Gilt für die Code-Bibliothek [!DNL VisitorAPI.js] Version 3.0 oder höher.

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

Wenn von `getInstance` keine bestehende Instanz gefunden wird, wird eine neue Instanz erstellt und zurückgegeben. Dies ähnelt der [`s_gi()` Funktion ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) in [!DNL AppMeasurement].

**Häufige Anwendung**

Die [!DNL Experience Cloud] ID-Dienst-API verwaltet eine Liste aller Instanzen, die für jede [!DNL Adobe Experience Cloud] Organisations-ID erstellt wurden. Sollte die Anwendung mithilfe der ID-Dienst-API keine Referenz an die Instanz senden, kann sie die Instanz durch Aufruf von `getInstance` erhalten, anstatt eine neue Instanz zu erzeugen. Damit ist auch die Unterstützung mehrerer Instanzen für verschiedene Organisationen mit derselben Webseite oder Anwendung möglich.

Dies ist hilfreich bei Anwendungen ohne eindeutige `init`-Phase, die die Besucher-API jedoch an mehreren Orten aufrufen müssen. Sie können `getInstance` an sämtlichen Orten aufrufen und der erste ausgeführte Aufruf führt zur Erstellung der Instanz. Die bestehende Instanz wird durch nachfolgende Aufrufe zurückgegeben.
