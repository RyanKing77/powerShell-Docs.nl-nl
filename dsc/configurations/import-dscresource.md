---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Import-DSCResource gebruiken
ms.openlocfilehash: e1c2c06d756a70c2de516f330e3123235ce740ba
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215401"
---
# <a name="using-import-dscresource"></a>Import-DSCResource gebruiken

`Import-DScResource`is een dynamisch sleutel woord dat alleen kan worden gebruikt binnen een configuratie script blok. Het `Import-DSCResource` sleutel woord voor het importeren van alle resources die nodig zijn in uw configuratie. Resources onder `$pshome` worden automatisch geïmporteerd, maar worden nog steeds beschouwd als best practice voor het expliciet importeren van alle resources die worden gebruikt in uw [configuratie](Configurations.md).

De syntaxis voor `Import-DSCResource` wordt hieronder weer gegeven.  Wanneer u modules op naam opgeeft, is het een vereiste om elk op een nieuwe regel te vermelden.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parameter  |Description  |
|---------|---------|
|`-Name`|De DSC-resource naam (s) die u moet importeren. Als de module naam is opgegeven, zoekt de opdracht naar deze DSC-resources in deze module; anders wordt met de opdracht gezocht in de DSC-resources in alle DSC-resource paden. Joker tekens worden ondersteund.|
|`-ModuleName`|De module naam of module specificatie.  Als u resources opgeeft om te importeren uit een module, probeert de opdracht alleen die resources te importeren. Als u alleen de module opgeeft, worden alle DSC-resources in de module geïmporteerd met de opdracht.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Voorbeeld: Import-Dscresource bieden binnen een configuratie gebruiken

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> Het opgeven van meerdere waarden voor de namen van resource namen en modules in dezelfde opdracht wordt niet ondersteund. Het kan een niet-deterministisch gedrag hebben over welke resource moet worden geladen, voor het geval dezelfde resource in meerdere modules bestaat. De onderstaande opdracht resulteert in een fout tijdens de compilatie.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Overwegingen bij het gebruik van alleen de para meter name:

- Het is een resource-intensieve bewerking, afhankelijk van het aantal modules dat op de computer is geïnstalleerd.
- Hiermee wordt de eerste resource geladen die met de opgegeven naam is gevonden. Als er meer dan één resource met dezelfde naam is geïnstalleerd, kan de verkeerde resource worden geladen.

Het aanbevolen gebruik moet worden opgegeven `–ModuleName` met de `-Name` para meter, zoals hieronder wordt beschreven.

Dit gebruik heeft de volgende voor delen:

- Het vermindert de invloed op de prestaties doordat het zoek bereik voor de opgegeven resource wordt beperkt.
- Hiermee wordt expliciet de module gedefinieerd waarmee de resource wordt gedefinieerd, zodat de juiste resource wordt geladen.

> [!NOTE]
> In Power shell 5,0 kunnen DSC-resources meerdere versies hebben en kunnen versies worden geïnstalleerd op een computer naast elkaar. Dit wordt geïmplementeerd door meerdere versies van een resource module te hebben die zich in dezelfde module map bevinden.
> Zie [resources met meerdere versies gebruiken](sxsresource.md)voor meer informatie.

## <a name="intellisense-with-import-dscresource"></a>IntelliSense met import-Dscresource bieden

Bij het ontwerpen van de DSC-configuratie in ISE biedt Power shell IntelliSence voor resources en resource-eigenschappen. Bron definities onder het `$pshome` pad naar de module worden automatisch geladen. Wanneer u resources importeert met behulp van het `Import-DSCResource` tref woord, worden de opgegeven resource definities toegevoegd en wordt IntelliSense uitgebreid met het schema van de geïmporteerde resource.

![Resource IntelliSense](../media/resource-intellisense.png)

> [!NOTE]
> Vanaf Power shell 5,0 is het tabblad voltooiings punt toegevoegd aan de ISE voor DSC-resources en de bijbehorende eigenschappen. Zie [resources](../resources/resources.md)voor meer informatie.

Bij het compileren van de configuratie gebruikt Power shell de geïmporteerde resource definities om alle resource blokken in de configuratie te valideren.
Elk resource blok wordt gevalideerd, met behulp van de schema definitie van de resource, voor de volgende regels.

- Alleen de eigenschappen die in het schema zijn gedefinieerd, worden gebruikt.
- De gegevens typen voor elke eigenschap zijn juist.
- De eigenschappen van de sleutels zijn opgegeven.
- Er wordt geen alleen-lezen-eigenschap gebruikt.
- Validatie van typen van de waarde-toewijzingen.

Houd rekening met de volgende configuratie:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Het compileren van deze configuratie resulteert in een fout.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Met IntelliSense en schema validatie kunt u meer fouten tijdens de parsering-en compilatie tijd ondervangen, waardoor complicaties tijdens de uitvoering worden voor komen.

> [!NOTE]
> Elke DSC-resource kan een naam hebben en een **FriendlyName** die is gedefinieerd in het schema van de resource. Hieronder vindt u de eerste twee regels van ' MSFT_ServiceResource. Shema. mof '.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Wanneer u deze bron in een configuratie gebruikt, kunt u **MSFT_ServiceResource** of **service**opgeven.

## <a name="powershell-v4-and-v5-differences"></a>Verschillen Power shell v4 en V5

Er zijn meerdere verschillen die u ziet tijdens het ontwerpen van configuraties in Power Shell 4,0 vs. Power shell 5,0 en hoger. In deze sectie worden de verschillen gemarkeerd die relevant zijn voor dit artikel.

### <a name="multiple-resource-versions"></a>Meerdere resource versies

Het installeren en gebruiken van meerdere versies van resources naast elkaar werd niet ondersteund in Power Shell 4,0. Als u problemen ondervindt bij het importeren van resources in uw configuratie, moet u ervoor zorgen dat er slechts één versie van de bron is geïnstalleerd.

In de onderstaande afbeelding zijn twee versies van de module **xPSDesiredStateConfiguration** geïnstalleerd.

![Er zijn meerdere resource versies opgelost](../media/multiple-resource-versions-broken.png)

Kopieer de inhoud van de gewenste module versie naar het hoogste niveau van de module directory.

![Er zijn meerdere resource versies opgelost](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a>Resource locatie

Bij het ontwerpen en compileren van configuraties kunnen uw resources worden opgeslagen in een map die is opgegeven door uw [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). In Power Shell 4,0 moeten alle DSC-resource modules zijn opgeslagen onder Program Files\WindowsPowerShell\Modules of `$pshome\Modules`. Vanaf Power shell 5,0 is deze vereiste verwijderd en kunnen resource modules worden opgeslagen in een map die is opgegeven door `PSModulePath`.

## <a name="see-also"></a>Zie ook

- [Resources](../resources/resources.md)
