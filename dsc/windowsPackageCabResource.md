---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: WindowsPackageCab-Ressource in DSC
ms.openlocfilehash: 1d7c8d9bf45d2eda8734daa8877315d219662c75
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowspackagecab-resource"></a>WindowsPackageCab-Ressource in DSC

> Gilt für: Windows PowerShell 5.1 und höher.

Die Ressource **WindowsPackageCab** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Installieren oder Deinstallieren von Windows-CAB-Paketen auf einem Zielknoten.

Auf dem Zielknoten muss das DISM-PowerShell-Modul installiert sein. Weitere Informationen finden Sie unter [Verwenden von DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14). 


## <a name="syntax"></a>Syntax

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Name| Gibt den Namen des Pakets an, für das Sie einen bestimmten Zustand sicherstellen möchten.| 
| Ensure| Gibt an, ob das Paket installiert ist. Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass das Paket nicht installiert wird (oder deinstalliert wird, wenn es installiert ist). Legen Sie sie auf „Present“ (den Standardwert) fest, um sicherzustellen, dass das Paket installiert wird.|
| Pfad| Gibt den Pfad an, in dem das Paket gespeichert ist.| 
| LogPath| Gibt den vollständigen Pfad an, in dem der Anbieter eine Protokolldatei zum Installieren oder Deinstallieren des Pakets speichern soll.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.| 

## <a name="example"></a>Beispiel

In der folgenden Beispielkonfiguration werden Eingabeparameter verwendet, und es wird sichergestellt, dass die über den `$Name`-Parameter angegebene CAB-Datei installiert ist.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```

