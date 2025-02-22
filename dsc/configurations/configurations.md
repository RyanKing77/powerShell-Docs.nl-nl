---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: DSC-configuraties
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080168"
---
# <a name="dsc-configurations"></a>DSC-configuraties

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC-configuraties zijn PowerShell-scripts die een speciaal type functie definiëren.
Voor het definiëren van een configuratie die u gebruikt het sleutelwoord PowerShell **configuratie**.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Sla het script als een `.ps1` bestand.

## <a name="configuration-syntax"></a>Syntaxis van de configuratie

Een configuratiescript bestaat uit de volgende onderdelen:

- De **configuratie** blokkeren. Dit is het buitenste scriptblok. U de gegevens definiëren met behulp van de **configuratie** trefwoord en een naam geven. In dit geval is de naam van de configuratie 'MyDscConfiguration'.
- Een of meer **knooppunt** blokken. Dit definieert de knooppunten (computers of virtuele machines) die u wilt configureren. In de bovenstaande configuratie, er is een **knooppunt** blokkeren die gericht is op een computer met de naam 'TEST-PC1'. Het knooppunt blok kan meerdere computernamen accepteren.
- Een of meer resource-blokken. Dit is waar de eigenschappen voor de resources waarmee deze wordt geconfigureerd in de configuratie wordt ingesteld. In dit geval zijn er twee blokken van de resource, die elk de resource "WindowsFeature" aanroepen.

Binnen een **configuratie** blokkeren, kunt u alles wat u normaal gesproken in een PowerShell-functie kan doen. Bijvoorbeeld, in het vorige voorbeeld, kan als u niet wilt harde code de naam van de doelcomputer in de configuratie u toevoegen een parameter voor de naam van het knooppunt:

In dit voorbeeld, geeft u de naam van het knooppunt door door te geven als de **ComputerName** parameter wanneer u de configuratie compileren. De naam van de standaardwaarde is "localhost".

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

De **knooppunt** blok kunt ook meerdere computernamen accepteren. In het bovenstaande voorbeeld kunt u ofwel de `-ComputerName` parameter of pass een door komma's gescheiden lijst met computers rechtstreeks naar de **knooppunt** blokkeren.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

Bij het opgeven van een lijst van computers aan de **knooppunt** blok, uit in een configuratie, moet u matrix-notatie gebruiken.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>De configuratie compileren

Voordat u kunt een configuratie gerapporteerd, moet u tijdens het compileren in een MOF-document.
U doen dit door het aanroepen van de configuratie, zoals u zou een PowerShell-functie aanroepen.
De laatste regel van het voorbeeld met alleen de naam van de configuratie, roept de configuratie.

> [!NOTE]
> Voor het aanroepen van een configuratie, moet de functie in het globale bereik (net als bij een andere PowerShell-functie).
> Kunt u dit laten gebeuren ofwel door "dotsourcing" het script, of door het uitvoeren van het configuratiescript met F5 of door te klikken op de **-Script uitvoeren** knop in de ISE.
> Het script dot-bron, voert u de opdracht `. .\myConfig.ps1` waar `myConfig.ps1` is de naam van het scriptbestand waarmee de configuratie bevat.

Bij het aanroepen van de configuratie, het:

- Oplossing voor alle variabelen
- Hiermee maakt een map in de huidige map met dezelfde naam als de configuratie.
- Hiermee maakt u een bestand met de naam _knooppuntnaam_.mof in de nieuwe map waar _knooppuntnaam_ is de naam van het doelknooppunt van de configuratie.
  Als er meer dan één knooppunt, wordt een MOF-bestand worden gemaakt voor elk knooppunt.

> [!NOTE]
> Het MOF-bestand bevat alle van de configuratie-informatie voor het doelknooppunt. Als gevolg hiervan is het belangrijk om veilig te houden.
> Zie voor meer informatie, [beveiligen van het MOF-bestand](../pull-server/secureMOF.md).

Compileren van de eerste configuratie boven resultaten in de volgende mapstructuur:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Als de configuratie heeft een parameter, zoals in het tweede voorbeeld nodig heeft om te worden opgegeven bij het compileren. Hier ziet u dat zou als volgt uitzien:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>Met behulp van nieuwe resources in uw configuratie

Als u de vorige voorbeelden hebt uitgevoerd, u mogelijk opgevallen dat u zijn gewaarschuwd dat u een resource zonder expliciet importeren gebruikten.
DSC wordt nu geleverd met 12 resources als onderdeel van de module PSDesiredStateConfiguration.

De cmdlet [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), kan worden gebruikt om te bepalen welke resources zijn geïnstalleerd op het systeem en beschikbaar zijn voor gebruik door de LCM.
Zodra deze modules zijn geplaatst `$env:PSModulePath` en goed worden herkend door [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ze nog steeds nodig om te worden geladen in uw configuratie.

**Sleutelwoorden import-dscresource bieden** is een dynamische trefwoord dat alleen kan worden herkend binnen een **configuratie** blok, het is niet een cmdlet.
**Sleutelwoorden import-dscresource bieden** ondersteunt twee parameters:

- **ModuleName** is de aanbevolen manier voor het gebruik van **sleutelwoorden Import-dscresource bieden**. De naam van de module met de resources die worden geïmporteerd (evenals een string-matrix van modulenamen) worden geaccepteerd.
- **Naam** is de naam van de resource te importeren. Dit is niet de beschrijvende naam die wordt geretourneerd als "Naam" door [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), maar de naam van de klasse die wordt gebruikt wanneer de resource-schema definiëren (geretourneerd als **ResourceType** door [Get-sleutelwoorden dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).

Voor meer informatie over het gebruik van `Import-DSCResource`, Zie [met behulp van importeren sleutelwoorden-dscresource bieden](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>Verschillen in PowerShell v4 en versie 5

Er zijn verschillen in waar DSC-resources moeten worden opgeslagen in PowerShell 4.0. Zie voor meer informatie, [Resourcelocatie](import-dscresource.md#resource-location).

## <a name="see-also"></a>Zie ook

- [Windows PowerShell Desired State Configuration-overzicht](../overview/overview.md)
- [DSC-Resources](../resources/resources.md)
- [De Local Configuration Manager configureren](../managing-nodes/metaConfig.md)
