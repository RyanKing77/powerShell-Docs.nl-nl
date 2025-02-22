---
ms.date: 03/28/2019
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Modules met compatibele PowerShell-edities
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084722"
---
# <a name="modules-with-compatible-powershell-editions"></a>Modules met compatibele PowerShell-edities

Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.

- **Desktop-editie:** Gebaseerd op .NET Framework, geldt voor Windows PowerShell v4.0 en hieronder en de Windows PowerShell 5.1 op Windows-bureaublad, Windows Server, Windows Server Core en de meeste andere edities van Windows.
- **Core-editie:** Gebaseerd op .NET Core, is van toepassing op PowerShell Core 6.0 en hoger en Windows PowerShell 5.1 op verminderde footprint edities van Windows, zoals IoT voor Windows en Windows Nanoserver.

Zie voor meer informatie over PowerShell-edities [about_PowerShell_Editions][].

## <a name="declaring-compatible-editions"></a>Compatibel edities declareren

Auteurs van modules kunnen hun modules zo opstellen dat deze compatibel zijn met een of meer PowerShell-edities door de sleutel voor het modulemanifestbestand CompatiblePSEditions te gebruiken. Deze sleutel wordt alleen ondersteund in PowerShell 5.1 of hoger.

> [!NOTE]
> Nadat een module-manifest is opgegeven met de sleutel CompatiblePSEditions, kan het niet worden geïmporteerd op de PowerShell-versie 4 en lager.

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

Bij het ophalen van een lijst met beschikbare modules kunt u de lijst filteren op PowerShell-editie.

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a>Die gericht is op meerdere edities

Auteurs kunnen publiceren een één module die gericht is op een van beide of beide PowerShell edities (Desktop en Core).

Een één-module kan worden gebruikt voor Desktop- en Core-edities, die de module auteur heeft om toe te voegen vereist logica in beide velden RootModule of in de module-manifest $PSEdition-variabele. Modules kunnen twee sets gecompileerde dll-bestanden die gericht is op CoreCLR zowel FullCLR hebben. Hier volgen de verschillende opties voor het verpakken van uw module met de logica voor het laden van de juiste DLL-bestanden.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Optie 1: Verpakking van een module die zijn gericht op meerdere versies en meerdere edities van PowerShell

De inhoud van de module-map

- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

Contents of PSScriptAnalyzer.psd1 file

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

Hieronder logische laadt de vereiste assembly's, afhankelijk van de huidige editie of versie.

De inhoud van PSScriptAnalyzer.psm1 bestand:

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a>Optie 2: $PSEdition variabele in het PSD1-bestand gebruiken om de juiste DLL's en geneste/vereiste modules te laden

In PS 5.1 of hoger, wordt de globale variabele $PSEdition is toegestaan in het manifestbestand van de module. Met deze variabele, opgeven module-auteur de voorwaardelijke waarden in het manifestbestand van de module. $PSEdition variabele kan worden verwezen in de beperkte taalmodus of een gegevenssectie.

> [!NOTE]
> Nadat u een module-manifest is opgegeven met de sleutel CompatiblePSEditions of gebruikmaakt van `$PSEdition` variabele, het kan niet worden geïmporteerd op lagere versies van PowerShell.

Voorbeeld-module-manifestbestand met CompatiblePSEditions sleutel

```powershell
@{
    # Script module or binary module file associated with this manifest.
    RootModule = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrRM.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrRM.dll'
    }

    # Supported PSEditions
    CompatiblePSEditions = 'Desktop', 'Core'

    # Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
    NestedModules = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrNM1.dll',
        'coreclr\MyCoreClrNM2.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrNM1.dll',
        'clr\MyFullClrNM2.dll'
    }
}
```

### <a name="module-contents"></a>Module-inhoud

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

Gebruikers van de PowerShell Gallery vindt de lijst met modules die worden ondersteund op een specifieke editie van PowerShell met behulp van labels PSEdition_Desktop en PSEdition_Core.

Modules zonder PSEdition_Desktop en PSEdition_Core tags worden beschouwd als goed werken op het bureaublad van de PowerShell-edities.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a>Meer informatie

[Scripts met PSEditions](script-psedition-support.md)

[Ondersteuning op PowerShellGallery PSEditions](../how-to/finding-packages/searching-by-compatibility.md)

[Modulemanifest bijwerken](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
