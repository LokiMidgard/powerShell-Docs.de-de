---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxService“
ms.openlocfilehash: 9cab889368469f2c854a387b919aea58a49f2210
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187717"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC für Linux-Resource „nxService“

Die Ressource **nxService** in PowerShell DSC bietet einen Mechanismus zum Verwalten von Diensten auf einem Linux-Knoten.

## <a name="syntax"></a>Syntax

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschaften
|  Eigenschaft |  Beschreibung |
|---|---|
| Name| Der Name des Diensts/Daemons, der konfiguriert werden soll.|
| Controller| Der Typ des Dienstcontrollers, der beim Konfigurieren des Diensts verwendet werden soll.|
| Enabled| Gibt an, ob der Dienst beim Systemstart gestartet wird.|
| State| Überprüfen, ob der Dienst ausgeführt wird. Legen Sie diese Eigenschaft auf „Stopped“ fest, um sicherzustellen, dass der Dienst nicht ausgeführt wird. Durch Festlegen auf „Running“ wird sichergestellt, dass der Dienst ausgeführt wird.|
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="additional-information"></a>Weitere Informationen

Die Ressource **nxService** erstellt keine Dienstdefinition bzw. kein Skript für den Dienst, falls er nicht vorhanden ist. Sie können die PowerShell DSC-Ressource **nxFile** verwenden, um das Vorhandensein oder den Inhalt der Dienstdefinitionsdatei oder des Skripts zu verwalten.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Konfiguration des Diensts „httpd“ (für Apache HTTP Server), der mit dem Dienstcontroller **SystemD** registriert wurde.

```
Import-DSCResource -Module nx

Node $node {
#Apache Service
nxService ApacheService
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```