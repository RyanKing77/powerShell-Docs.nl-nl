---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 3acd266a75bc61ffe4bce467cfb804ac7865c629
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057244"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>Een JEA-eindpunt maken en hier verbinding mee maken

Voor het maken van een JEA-eindpunt, moet u maken en registreren van een speciaal geconfigureerd PowerShell-sessie configuratiebestand, die kan worden gegenereerd met de **New-PSSessionConfigurationFile** cmdlet.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

Hiermee maakt u een sessie-configuratiebestand dat er als uitzien volgt:

```powershell
@{

    # Version number of the schema used for this document
    SchemaVersion = '2.0.0.0'

    # ID used to uniquely identify this document
    GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
    SessionType = 'RestrictedRemoteServer'

    # Directory to place session transcripts for this session configuration
    TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

    # Whether to run this session configuration as the machine's (virtual) administrator account
    RunAsVirtualAccount = $true

    # Groups associated with machine's (virtual) administrator account
    # RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
    RoleDefinitions = @{ 'CONTOSO\NonAdmin_Operators' = @{ 'RoleCapabilities' = 'Maintenance' } }
}
```

Bij het maken van een JEA-eindpunt, moeten de volgende parameters van de opdracht (en de bijbehorende sleutels in het bestand) worden ingesteld:

1. SessionType naar RestrictedRemoteServer
2. RunAsVirtualAccount naar **$true**
3. TranscriptPath naar de map waarin 'meekijk' Transcripten moeten worden opgeslagen na elke sessie
4. RoleDefinitions naar een hashtabel waarmee wordt gedefinieerd welke groepen hebben toegang tot welke 'Rolmogelijkheden'. Dit veld wordt gedefinieerd **die** kunt doen **wat** op dit eindpunt. Rolmogelijkheden zijn speciale bestanden die binnenkort worden beschreven.

Het veld RoleDefinitions wordt gedefinieerd welke groepen heeft toegang tot de mogelijkheden van welke rol. De mogelijkheid van een rol is een bestand dat u een verscheidenheid aan functies die worden weergegeven definieert voor het koppelen van gebruikers.
Rolmogelijkheden met kunt u de **New-PSRoleCapabilityFile** opdracht.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

Dit genereert een sjabloon voor rol-functie die er als uitzien volgt:

```powershell
@{
    # ID used to uniquely identify this document
    GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Company associated with this document
    CompanyName = 'Unknown'

    # Copyright statement for this document
    Copyright = '(c) 2015 Administrator. All rights reserved.'

    # Modules to import when applied to a session
    # ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

    # Aliases to make visible when applied to a session
    # VisibleAliases = 'Item1', 'Item2'

    # Cmdlets to make visible when applied to a session
    # VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # Functions to make visible when applied to a session
    # VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # External commands (scripts and applications) to make visible when applied to a session
    # VisibleExternalCommands = 'Item1', 'Item2'

    # Providers to make visible when applied to a session
    # VisibleProviders = 'Item1', 'Item2'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # Aliases to be defined when applied to a session
    # AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

    # Functions to define when applied to a session
    # FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

    # Variables to define when applied to a session
    # VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

    # Environment variables to define when applied to a session
    # EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

    # Type files (.ps1xml) to load when applied to a session
    # TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

    # Format files (.ps1xml) to load when applied to a session
    # FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

    # Assemblies to load when applied to a session
    # AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}
```

Om te worden gebruikt door een sessieconfiguratie JEA, moet de Rolmogelijkheden worden opgeslagen als een geldige PowerShell-module in een map met de naam 'RoleCapabilities'. Een module mogelijk meerdere rol mogelijkheid bestanden, indien gewenst.

Om te beginnen met de configuratie van welke cmdlets, functies, aliassen en scripts die een gebruiker toegang heeft tot bij het verbinden met een JEA-sessie, moet u uw eigen regels toevoegen aan de rol mogelijkheid bestand na de opmerkingen van sjablonen. Voor een stil in hoe u Rolmogelijkheden kunt configureren, bekijkt u de volledige [gids voor gebruikerservaring](http://aka.ms/JEA).

Tot slot zodra u klaar bent met het aanpassen van de sessieconfiguratie en aanverwante mogelijkheden van de rol, registreren van deze sessieconfiguratie en het eindpunt maken door te voeren `Register-PSSessionConfiguration`.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>Verbinding maken met een JEA-eindpunt

Verbinding maken met een JEA-eindpunt werkt op dezelfde manier verbinding te maken met een andere PowerShell-eindpunt werkt.
U hoeft uw JEA-eindpunt om naam te geven als de parameter 'ConfigurationName' voor **New-PSSession**, **Invoke-Command**, of **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```

Nadat u verbinding hebt gemaakt met de JEA-sessie, zich kunt u beperkt tot de opdrachten in de whitelist opgenomen in de rol-mogelijkheden die u toegang tot hebt uitgevoerd. Als u probeert een opdracht niet toegestaan voor uw rol uit te voeren, wordt u er een fout optreden.