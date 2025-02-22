---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Desired State Configuration (DSC) bekende problemen en beperkingen
ms.openlocfilehash: 6faf24795d14a93f265943029d9f6f1388f32263
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856194"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Desired State Configuration (DSC) bekende problemen en beperkingen

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Belangrijke wijziging: Certificaten die worden gebruikt voor het versleutelen/ontsleutelen van wachtwoorden in DSC-configuraties werkt mogelijk niet na de installatie van WMF 5.0 RTM

In WMF 4.0 en WMF 5.0 Preview-versies, DSC zou niet toestaan dat wachtwoorden in de configuratie met een lengte van meer dan 121 tekens. DSC is geforceerd korte om wachtwoorden te gebruiken, zelfs als langdurige en een sterk wachtwoord is gewenst is. Deze belangrijke wijziging kan wachtwoorden van willekeurige lengte in de DSC-configuratie.

**Oplossing:** Opnieuw maken van het certificaat met gegevenscodering of sleutel uitwisselen sleutel gebruik en Document versleuteling Enhanced Key usage (1.3.6.1.4.1.311.80.1). Zie voor meer informatie, [beveiligen CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>DSC-cmdlets kunnen mislukken na de installatie van WMF 5.0 RTM

`Start-DscConfiguration` en andere cmdlets DSC mislukken na de installatie van WMF 5.0 RTM met de volgende fout:

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

**Oplossing:** DSCEngineCache.mof verwijderen door het uitvoeren van de volgende opdracht uit in een verhoogde PowerShell-sessie (als Administrator uitvoeren):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>DSC-cmdlets werken niet als WMF 5.0 RTM boven op WMF 5.0 productie Preview is geïnstalleerd

**Oplossing:** Voer de volgende opdracht uit in een sessie met verhoogde bevoegdheden PowerShell (als administrator uitvoeren):

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM kunt in tot een instabiele status gaan tijdens het gebruik van Get-DscConfiguration in fouten opsporen-modus

Druk op CTRL + C om de verwerking van stoppen als LCM fouten opsporen-modus, `Get-DscConfiguration` kan leiden tot LCM om te gaan naar een instabiele status dergelijke die meerderheid van de DSC-cmdlets werken niet.

**Oplossing:** Niet druk op CTRL + C tijdens het opsporen van fouten `Get-DscConfiguration` cmdlet.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration reageren mogelijk niet in fouten opsporen-modus

Als LCM in fouten opsporen-modus, `Stop-DscConfiguration` reageert niet terwijl bij stoppen van een bewerking gestart door `Get-DscConfiguration`

**Oplossing:** Voltooien van de foutopsporing van de bewerking aan de slag door `Get-DscConfiguration` zoals wordt beschreven in [foutopsporing DSC-resources](/powershell/dsc/troubleshooting/debugResource).

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Er is geen uitgebreide foutberichten worden weergegeven in fouten opsporen-modus

Als LCM in **fouten opsporen-modus**, geen uitgebreide foutberichten van DSC-Resources worden weergegeven.

**Oplossing:** Uitschakelen **fouten opsporen-modus** om te zien uitgebreide berichten uit de bron

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Sleutelwoorden Invoke-dscresource bieden bewerkingen kunnen niet worden opgehaald door de cmdlet Get-DscConfigurationStatus

Nadat u `Invoke-DscResource` cmdlet voor het rechtstreeks aanroepen van een resource-methoden, de records van deze bewerking kan niet worden opgehaald via `Get-DscConfigurationStatus`.

**Oplossing:** Geen.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus retourneert pull cyclus bewerkingen als type **consistentie**

Wanneer een knooppunt is ingesteld op PULL vernieuwen-modus, voor elke pullbewerking uitgevoerd, `Get-DscConfigurationStatus` cmdlet rapporteert het bewerkingstype als **consistentie** in plaats van *initiële*

**Oplossing:** Geen.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Sleutelwoorden Invoke-dscresource bieden cmdlet retourneert geen bericht in de volgorde waarin die ze zijn gemaakt

De `Invoke-DscResource` cmdlet retourneert geen uitgebreide, waarschuwing, en foutberichten in de volgorde waarin ze zijn geproduceerd door LCM of de DSC-resource.

**Oplossing:** Geen.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>DSC-Resources kan niet eenvoudig worden opgespoord gebruikt in combinatie met sleutelwoorden Invoke-dscresource bieden

Wanneer de LCM wordt uitgevoerd in de foutopsporingsmodus `Invoke-DscResource` cmdlet geeft geen informatie over runspace verbinding maakt met voor foutopsporing. Zie voor meer informatie, [foutopsporing DSC-resources](/powershell/dsc/troubleshooting/debugResource).

**Oplossing:** Detecteren en te koppelen aan de runspace met behulp van cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` en `Debug-Runspace` fouten opsporen in de DSC-resource.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Verschillende gedeeltelijke configuratie documenten voor hetzelfde knooppunt geen identieke resourcenamen

Voor verschillende gedeeltelijke configuraties die zijn geïmplementeerd op één knooppunt, runtimefout identieke namen van resources oorzaak.

**Oplossing:** Gebruik verschillende namen voor zelfs dezelfde resources in verschillende gedeeltelijke configuraties.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration – UseExisting werkt niet met - referentie

Bij het gebruik van `Start-DscConfiguration` met **UseExisting** parameter, de **referentie** parameter wordt genegeerd. DSC gebruikt standaard procesidentiteit om door te gaan van de bewerking. Dit veroorzaakt fout als een andere referentie nodig is om door te gaan op een extern knooppunt.

**Oplossing:** Gebruik CIM-sessie voor externe DSC-bewerkingen:

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>IPv6-adressen aan de namen in de DSC-configuraties van knooppunt

IPv6-adressen als knooppuntnamen in scripts voor DSC-configuratie worden niet ondersteund in deze release.

**Oplossing:** Geen.

## <a name="debugging-of-class-based-dsc-resources"></a>Foutopsporing van `Class-Based` DSC-Resources

Foutopsporing voor DSC-Resources op basis van een klasse wordt niet ondersteund in deze release.

**Oplossing:** Geen.

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Variabelen en functies die zijn gedefinieerd binnen het bereik van $script in DSC-Resource op basis van een klasse zijn niet behouden in meerdere aanroepen naar een DSC-Resource

Meerdere opeenvolgende aanroepen naar `Start-DSCConfiguration` mislukt als de configuratie met behulp van een resource op basis van een klasse met variabelen of functies die zijn gedefinieerd in `$script` bereik.

**Oplossing:** Definieer alle variabelen en -functies in DSC-Resource-klasse zelf. Geen `$script` het bereik van variabelen/functies.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>DSC-Resource foutopsporing als een resource PSDscRunAsCredential

DSC-Resource foutopsporing bij het gebruik van een resource de **PSDscRunAsCredential** eigenschap in de configuratie wordt niet ondersteund in deze release.

**Oplossing:** Geen.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential wordt niet ondersteund voor samengestelde DSC-Resources

**Oplossing:** Referentie-eigenschap gebruiken indien beschikbaar. Voorbeeld van de ServiceSet en WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>Sleutelwoorden Get-dscresource bieden-syntaxis wordt PsDscRunAsCredential niet correct weergegeven

De **syntaxis** parameter komt niet overeen met **PsDscRunAsCredential** correct wanneer resource gemarkeerd als verplicht of dit wordt niet ondersteund.

**Oplossing:** Geen. Echter juiste metagegevens over het ontwerpen van de configuratie in ISE weerspiegelt **PsDscRunAsCredential** eigenschap bij het gebruik van IntelliSense.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature is niet beschikbaar in Windows 7

De **WindowsOptionalFeature** DSC-resource is niet beschikbaar in Windows 7. Deze resource is vereist voor de DISM-module en de DISM-cmdlets zijn beschikbaar vanaf Windows 8 en nieuwere versies van het Windows-besturingssysteem.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Voor klasse op basis van DSC-resources, sleutelwoorden Import-dscresource bieden - ModuleVersion werkt mogelijk niet zoals verwacht

Als de compilatie-knooppunt meerdere versies van een module DSC-resource op basis van een klasse heeft `Import-DscResource -ModuleVersion` heeft niet de opgegeven versie kiezen en resulteert in de volgende fout bij schemacompilatie.

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Oplossing:** De vereiste versie importeren door te definiëren de **ModuleSpecification** object toe aan de **ModuleName** parameter met de **RequiredVersion** sleutel die is opgegeven als volgt:

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Sommige DSC-resources, zoals registerresource kunnen beginnen met een lang duren om de aanvraag te verwerken.

**Oplossing 1:** Een geplande taak periodiek opschonen van de volgende map maken.

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Oplossing 2:** Wijzigen van de DSC-configuratie voor het opschonen van de *CommandAnalysis* map aan het einde van de configuratie.

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
