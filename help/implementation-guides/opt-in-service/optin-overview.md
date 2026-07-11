---
description: Mit dem Opt-in-Dienst können Sie Protokolle für den Besucher einrichten, um zu bestimmen, ob Sie ein Cookie auf dem Gerät oder Browser des Benutzers erstellen können, wenn dieser Ihre Site besucht.
title: Opt-in-Dienst
exl-id: 351da861-4faa-409b-b0ff-f4d2ce66700b
TQID: https://experienceleague.adobe.com/7XqAQ83gu6qQQfIWNB7Ui6aqtU-IbOxSMrYbMerHBCo
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 512
ht-degree: 89%

---

# Opt-in-Dienst{#opt-in-service}

Mit dem Opt-in-Dienst können Sie Protokolle für den Besucher einrichten, um zu bestimmen, ob Sie ein Cookie auf dem Gerät oder Browser des Benutzers erstellen können, wenn dieser Ihre Site besucht.

Der Opt-in-Dienst ist eine Erweiterung der ECID, mit der Sie steuern können, ob und welche CX Enterprise-Lösungen vor der Zustimmung des Benutzers auf Web-Seiten Cookies für Besuchende erstellen können. Mit dem Opt-in-Dienst können Sie auch Protokolle festlegen, die sich im Rahmen Ihres größeren Designs in Ihre Consent Management Platform (CMP) und bestehende Systeme integrieren lassen.

Mit dem Opt-in-Dienst können Sie festlegen, ob ein Besucher allen Adobe-Lösungen gleichzeitig zustimmen kann oder die Lösungen einzeln angezeigt werden, um die Zustimmung einzuholen. Sobald der Genehmigungsprozess abgeschlossen und vom Kunden aufgezeichnet wurde, können Sie die CMP-Besuchergenehmigungen aus allen Adobe-Lösungen abrufen.

Der Opt-in-Dienst kann mithilfe von [Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de) mit der [Opt-in-Erweiterung](../../implementation-guides/opt-in-service/launch.md) implementiert und konfiguriert werden.

Siehe [Einrichtung des Opt-in-Dienstes](../../implementation-guides/opt-in-service/getting-started.md) zu den ersten Schritten.

>[!NOTE]
>
>Der Opt-in-Dienst kann nur zur Einrichtung eines Systems verwendet werden, mit dem die Zustimmung der Benutzer zum Herunterladen von Adobe-Cookies eingeholt wird. Es können keine Zustimmungsvoreinstellungen von Benutzern erfasst werden und das Objekt kann auch nicht als Repository für Voreinstellungen verwendet werden.

>[!IMPORTANT]
>
>Der Inhalt dieses Dokuments ist keine Rechtsberatung und soll keine Rechtsberatung ersetzen. Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um sich über die Zustimmung und die Vorgehensweisen bei der Einrichtung Ihrer Opt-in-Implementierung zu informieren.

## Opt-in für alle CX Enterprise-Lösungen {#section-053e6224505542cf961896f0ca869e52}

Der Opt-in-Dienst ist ein Tool zum Einrichten eines Opt-in-Workflows, der Ihren Anforderungen entspricht. Es ermöglicht Ihnen, einen Workflow zu entwerfen, der vor und nach der Zustimmung des Benutzers oder Ihres Zustimmungsverantwortlichen durch Auslösen von Tags reagiert.

Mit dem Opt-in-Dienst können Sie Folgendes für die Zustimmungsverwaltung von Adobe-Lösungen einstellen:

* Geben Sie an, ob die Anforderungen für das Einholen der Zustimmung im Allgemeinen für einen Benutzer gelten.
* Geben Sie an, welche Lösungen Cookies generieren dürfen.
* Wenden Sie Standardeinstellungen für Lösungen an, deren Kategorie nicht ausdrücklich vom Benutzer zugestimmt oder abgelehnt wurde.
* Lösen Sie benutzerdefinierte Reaktionen auf der Grundlage von Änderungen an den Einwilligungseinstellungen des Benutzers aus, die es Ihnen erlauben, die Einstellungen des Benutzers beizubehalten oder zu ändern.

Mit dem Opt-in-Dienst können Sie Ihre Site so konfigurieren, dass einige Cookies mit einer Vorabzustimmung geladen werden, bevor der Benutzer eine Auswahl vornimmt. Sie können Opt-in-Dienste für Neukunden so einstellen, dass Cookies nach Zustimmung des Benutzers oder nach Bereitstellung einer Auswahl geladen werden können. Sie können auch Opt-in-Einwilligungen von Ihrer bestehenden Einverständnisverwaltungs-Plattform speichern und abrufen oder Opt-in-Berechtigungen einfach in einem Cookie speichern.

![](assets/Opt-in-approval.png)

Adobe-Lösungen können dann prüfen, ob der Tag genehmigt ist und Änderungen regeln und dann alle Opt-in-Kunden abrufen. Der Opt-in-Dienst ermöglicht Ihnen, Berechtigungen direkt über die JavaScript-Bibliotheken der Lösung oder über ECID (falls implementiert) abzurufen.

