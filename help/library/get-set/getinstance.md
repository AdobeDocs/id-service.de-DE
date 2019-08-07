---
description: getInstance gibt ein Besucher-ID-Objekt für die festgelegte Experience Cloud-Organisations-ID zurück. Dies ist erforderlich, um das Besucher-ID-Objekt zu initialisieren, das mit s.visitor für AppMeasurement bereitgestellt wird.
keywords: ID-Dienst
seo-description: getInstance gibt ein Besucher-ID-Objekt für die festgelegte Experience Cloud-Organisations-ID zurück. Dies ist erforderlich, um das Besucher-ID-Objekt zu initialisieren, das mit s.visitor für AppMeasurement bereitgestellt wird.
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

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
>*Wichtig:* Instanziieren Sie die Visitor-Funktion nicht mit `var visitor = new Visitor`. Sie müssen den richtigen, hier aufgeführten Funktionsaufruf verwenden. Gilt für die Code-Bibliothek [!UICONTROL VisitorAPI.js] Version 3.0 oder höher.

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

Wenn von `getInstance` keine bestehende Instanz gefunden wird, wird eine neue Instanz erstellt und zurückgegeben. This is similar to the [ `s_gi()` function ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) in [!DNL AppMeasurement].

**Häufige Anwendung**

Die [!DNL Experience Cloud] ID-Dienst-API enthält eine Liste aller Instanzen, die für jede [!DNL Adobe Experience Cloud]-Organisations-ID erstellt wurden. Sollte die Anwendung mithilfe der ID-Dienst-API keine Referenz an die Instanz senden, kann sie die Instanz durch Aufruf von `getInstance` erhalten, anstatt eine neue Instanz zu erzeugen. Damit ist auch die Unterstützung mehrerer Instanzen für verschiedene Organisationen mit derselben Webseite oder Anwendung möglich.

Dies ist hilfreich bei Anwendungen ohne eindeutige `init`-Phase, die die Besucher-API jedoch an mehreren Orten aufrufen müssen. Sie können `getInstance` an sämtlichen Orten aufrufen und der erste ausgeführte Aufruf führt zur Erstellung der Instanz. Die bestehende Instanz wird durch nachfolgende Aufrufe zurückgegeben.
