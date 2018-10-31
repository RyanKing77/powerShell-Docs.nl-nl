---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Schrijfhulp voor DSC-configuraties
ms.openlocfilehash: a4b5e688744b9a4519ce06d920ad8f11efeb99ad
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225689"
---
# <a name="writing-help-for-dsc-configurations"></a>Schrijfhulp voor DSC-configuraties

>Van toepassing op: Windows PowerShell 5.0

U kunt help op basis van een opmerking in DSC-configuraties gebruiken. Gebruikers hebben toegang tot de Help-informatie door het aanroepen van de configuratie-functie met `-?`, of met behulp van de [Get-Help](https://technet.microsoft.com/library/hh849696.aspx) cmdlet. Zie voor meer informatie over PowerShell-help op basis van een opmerking [about_Comment_Based_Help](https://technet.microsoft.com/library/hh847834.aspx).

Het volgende voorbeeld ziet u een script dat een configuratie- en opmerking op basis van de help voor deze bevat:

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.PARAMETER FilePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example. If you have multiple examples,
there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>

configuration HelpSample1
{
    param([string]$ComputerName,[string]$FilePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

## <a name="viewing-configuration-help"></a>Configuratie help weergeven

Als u de help voor een configuratie, gebruikt u de **Get-Help** cmdlet met de naam van de functie of type de naam van de functie gevolgd door `-?`. Hieronder volgt de uitvoer van de vorige functie wanneer doorgegeven aan **Get-Help**:

```powershell
PS C:\> Get-Help HelpSample1

NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName]
    <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


RELATED LINKS

REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

## <a name="see-also"></a>Zie ook
* [DSC-configuraties](configurations.md)