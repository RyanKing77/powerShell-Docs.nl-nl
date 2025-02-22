---
title: Wat is er nieuw in PowerShell Core 6.0
description: Nieuwe functies en wijzigingen die zijn uitgebracht in PowerShell Core 6.0?
ms.date: 08/06/2018
ms.openlocfilehash: e1218a38398f4d86829cf2b4ba6a3a882675eaab
ms.sourcegitcommit: 09f02ccef56ef30e7a9ca901f8d3713724960c68
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843920"
---
# <a name="whats-new-in-powershell-core-60"></a>Wat is er nieuw in PowerShell Core 6.0

[PowerShell Core 6.0][github] is een nieuwe versie van PowerShell die cross-platform (Windows, macOS en Linux), open-source en gebouwd voor heterogene omgevingen en de hybride cloud.

## <a name="moved-from-net-framework-to-net-core"></a>Verplaatst van .NET Framework naar .NET Core

Maakt gebruik van PowerShell Core [.NET Core 2.0][] als de runtime.
.NET core 2.0 kunt PowerShell Core werkt op meerdere platforms (Windows, macOS en Linux).
PowerShell Core wordt ook aangegeven dat de API-set die worden aangeboden door .NET Core 2.0 moet worden gebruikt in PowerShell-cmdlets en scripts.

Windows PowerShell gebruikt de .NET Framework-runtime voor het hosten van de PowerShell-engine.
Dit betekent dat de API-set die worden aangeboden door .NET Framework beschikbaar gesteld door Windows PowerShell.

De API's gedeeld tussen .NET Core en .NET Framework zijn gedefinieerd als onderdeel van [.NET Standard][].

Zie voor meer informatie over hoe dit van invloed is op compatibiliteit tussen PowerShell Core en Windows PowerShell-module/script, [Backwards compatibiliteit met Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Ondersteuning voor macOS en Linux

PowerShell biedt nu officieel ondersteuning voor macOS en Linux, met inbegrip van:

- Windows 7, 8.1 en 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server semi-Annual-kanaal][semi-annual]
- Ubuntu 14.04 en 16.04 17.04
- Debian 8,7 + en 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

Pakketten voor de volgende platformen ook bijdrage aan onze community heeft geleverd, maar ze zijn niet officieel ondersteund:

- Linux boog
- Kali Linux
- AppImage (werkt op meerdere platforms voor Linux)

We hebben ook experimentele (niet-ondersteunde) releases voor de volgende platformen:

- Windows op ARM32/ARM64
- Raspbian (Stretch)

Een aantal wijzigingen zijn aangebracht in PowerShell Core 6.0 zodat deze beter werkt op niet-Windows-systemen.
Sommige hiervan zijn belangrijke wijzigingen, die ook invloed hebben op Windows.
Andere resources zijn alleen aanwezig of is van toepassing in niet-Windows-installaties van PowerShell Core.

- Ondersteuning toegevoegd voor systeemeigen opdracht bij globbing op Unix-platforms.
- De `more` functionaliteit respecteert de Linux `$PAGER` en wordt standaard ingesteld op `less`.
  Dit betekent dat u kunt nu jokertekens gebruiken met systeemeigen binaire bestanden en/of opdrachten (bijvoorbeeld `ls *.txt`). (#3463)
- Afsluitende backslash, wordt automatisch tijdens het afhandelen van systeemeigen opdrachtargumenten escape. (#4965)
- Negeer de `-ExecutionPolicy` overschakelen tijdens het uitvoeren van PowerShell op niet-Windows-platforms omdat het ondertekenen van het script wordt momenteel niet ondersteund. (#3481)
- Vaste ConsoleHost in acht neemt `NoEcho` op Unix-platforms. (#3801)
- Vaste `Get-Help` ter ondersteuning van hoofdlettergevoelig patroon overeen op de Unix-platforms. (#3852)
- `powershell` Man-pagina toegevoegd aan het pakket

### <a name="logging"></a>Logboekregistratie

Op Mac OS, PowerShell maakt gebruik van de native `os_log` API's om aan te melden van Apple [aanmeldingssysteem unified][os_log].
Op Linux, PowerShell gebruikt [Syslog][], een oplossing alomtegenwoordige logboekregistratie.

### <a name="filesystem"></a>Bestandssysteem

Een aantal wijzigingen zijn aangebracht in macOS en Linux voor de ondersteuning van oudsher niet ondersteund op Windows tekens in de bestandsnaam:

- Paden die aan de cmdlets zijn nu slash-agnostische (zowel / en \ werken als mapscheiding)
- XDG Base Directory specificatie is nu in acht genomen en wordt standaard gebruikt:
  - Het pad van het Linux/macOS-profiel bevindt zich in `~/.config/powershell/profile.ps1`
  - De geschiedenis opslaan pad bevindt zich in `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Het pad naar module bevindt zich in `~/.local/share/powershell/Modules`
- Ondersteuning voor bestands- en mapnamen met het teken puntkomma's op Unix. (#4959)
- Ondersteuning voor scriptnamen van het of de volledige paden met komma's. (#4136) (Dank aan [ @TimCurwick ](https://github.com/TimCurwick)!)
- Detecteren wanneer `-LiteralPath` wordt gebruikt voor het onderdrukken van jokertekens voor navigatie-cmdlets. (#5038)
- Bijgewerkt `Get-ChildItem` meer lijkt te werken de * nix `ls -R` en de Windows `DIR /S` systeemeigen opdrachten.
  `Get-ChildItem` retourneert nu symbolische koppelingen worden aangetroffen tijdens een recursieve zoekopdracht en niet de mappen zoeken die het doel van deze koppelingen. (#3780)

### <a name="case-sensitivity"></a>Hoofdlettergevoeligheid

Linux en Mac OS zijn meestal hoofdlettergevoelig terwijl Windows behoud van de aanvraag is niet hoofdlettergevoelig.
In het algemeen is PowerShell niet hoofdlettergevoelig.

Omgevingsvariabelen zijn bijvoorbeeld hoofdlettergevoelig in macOS en Linux, dus het hoofdlettergebruik van de `PSModulePath` omgevingsvariabele is gestandaardiseerd. (#3255) `Import-Module` wordt onderscheid gemaakt bij het gebruik van een bestandspad om te bepalen van de module-naam. (#5097)

## <a name="support-for-side-by-side-installations"></a>Ondersteuning voor side-by-side-installaties

PowerShell Core is geïnstalleerd, geconfigureerd en afzonderlijk uitgevoerd vanaf Windows PowerShell.
PowerShell Core is een 'draagbare' ZIP-pakket.
Met behulp van het ZIP-pakket, kunt u een willekeurig aantal versies overal op schijf, met inbegrip van lokaal op een toepassing die met PowerShell als een afhankelijkheid.
Side-by-side-installatie wordt het gemakkelijker te test nieuwe versies van PowerShell en migreren van bestaande scripts na verloop van tijd.
Side-by-side kan ook achterwaartse compatibiliteit zoals scripts kunnen worden vastgemaakt aan specifieke versies die ze nodig hebben.

> [!NOTE]
> Het installatieprogramma op basis van MSI op Windows biedt standaard een InPlace-update te installeren.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>De naam van gewijzigd `powershell(.exe)` naar `pwsh(.exe)`

De naam van de binaire voor PowerShell Core is gewijzigd van `powershell(.exe)` naar `pwsh(.exe)`.
Deze wijziging biedt een deterministische manier voor gebruikers om uit te voeren PowerShell Core op virtuele machines voor de ondersteuning van side-by-side Windows PowerShell en PowerShell Core-installaties.
`pwsh` is het ook veel korter en beter te typen.

Aanvullende wijzigingen aan `pwsh(.exe)` van `powershell.exe`:

- Is de eerste positionele parameter uit `-Command` naar `-File`.
  Deze wijziging wordt het gebruik van opgelost `#!` (ook bekend als een shebang) in PowerShell-scripts die worden uitgevoerd van niet-PowerShell schalen op niet-Windows-platforms.
  Het betekent ook dat u opdrachten kunt uitvoeren `pwsh foo.ps1` of `pwsh fooScript` zonder op te geven `-File`.
  Deze wijziging is echter vereist dat u expliciet opgeven `-c` of `-Command` tijdens het uitvoeren van opdrachten zoals `pwsh.exe -Command Get-Command`. (#4019)
- PowerShell Core accepteert de `-i` (of `-Interactive`) switch om aan te geven van een interactieve shell. (#3558) Hiermee kunt PowerShell om te worden gebruikt als een standaardshell op Unix-platforms.
- Parameters verwijderd `-importsystemmodules` en `-psconsoleFile` van `pwsh.exe`. (#4995)
- Gewijzigd `pwsh -version` en ingebouwde Help-informatie voor `pwsh.exe` om uit te lijnen met andere hulpprogramma's voor native modus. (#4958 & #4931) (Bedankt [ @iSazonov ](https://github.com/iSazonov))
- Ongeldig argument foutberichten voor `-File` en `-Command` en afsluitcodes die consistent zijn met Unix-standaarden (#4573)
- Toegevoegd `-WindowStyle` parameter op Windows. (#4573) Updates voor installaties op basis van het pakket op niet-Windows-platforms zijn op deze manier in-place updates.

## <a name="backwards-compatibility-with-windows-powershell"></a>Achterwaartse compatibiliteit met Windows PowerShell

Het doel van de PowerShell Core is om als compatibel blijven mogelijk met Windows PowerShell.
Maakt gebruik van PowerShell Core [.NET Standard][] 2.0 voor binaire compatibiliteit met bestaande .NET-assembly's.
Veel PowerShell-modules zijn afhankelijk van deze assembly's (vaak tijden dll-bestanden), zodat ze verder wilt werken met .NET Core .NET Standard te kunnen.
PowerShell Core bevat ook een heuristiek om te zoeken in bekende mappen, zoals waar de Global Assembly Cache bevindt zich doorgaans op schijf--om afhankelijkheden van .NET Framework-dll-bestand te zoeken.

U meer informatie over .NET Standard in de [.NET Blog][], in dit [YouTube][] video en via dit [FAQ][] op GitHub.

Aanbevolen inspanningen zijn aangebracht om ervoor te zorgen dat de PowerShell-modules voor taal en 'ingebouwde' (zoals `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, enzovoort) werken op dezelfde manier als in Windows PowerShell.
In veel gevallen met behulp van de community, hebben we nieuwe mogelijkheden en oplossingen voor problemen toegevoegd voor deze cmdlets.
In sommige gevallen, vanwege een ontbrekende afhankelijkheid in onderliggende lagen voor .NET, functionaliteit is verwijderd of is niet beschikbaar.

De meeste van de modules die worden geleverd als onderdeel van Windows (bijvoorbeeld `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, enzovoort) en andere Microsoft-producten, waaronder Azure en Office zijn niet *expliciet* overgezet naar. Nog NET Core.
Het PowerShell-team werkt met deze productgroepen en teams om te valideren en hun bestaande modules voor PowerShell Core-poort.
Met .NET Standard en [CDXML][], veel van deze traditionele Windows PowerShell-modules lijkt te werken in PowerShell Core, maar ze zijn niet officieel gevalideerd en ze zijn niet officieel ondersteund.

Door het installeren van de [ `WindowsPSModulePath` ][windowspsmodulepath] -module, kunt u Windows PowerShell-modules gebruiken door de Windows PowerShell toe te voegen `PSModulePath` aan uw PowerShell Core `PSModulePath`.

Installeer eerst de `WindowsPSModulePath` module op basis van de PowerShell Gallery:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Na de installatie van deze module worden uitgevoerd de `Add-WindowsPSModulePath` cmdlet om toe te voegen van de Windows PowerShell `PSModulePath` PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker-ondersteuning

PowerShell Core voegt ondersteuning toe voor Docker-containers voor alle grote platforms die wordt ondersteund (met inbegrip van meerdere Linux-distributies, Windows Server Core en Nano Server).

Voor een volledige lijst, bekijk de labels op [ `microsoft/powershell` op Docker Hub][docker-hub].
Zie voor meer informatie over Docker en PowerShell Core [Docker][] op GitHub.

## <a name="ssh-based-powershell-remoting"></a>SSH op basis van PowerShell voor externe toegang

De PowerShell Remoting Protocol (PSRP) werkt nu met het protocol Secure Shell (SSH) naast de traditionele PSRP op basis van WinRM.

Dit betekent dat u cmdlets, zoals kunt `Enter-PSSession` en `New-PSSession` en verifiëren met behulp van SSH.
U moet doen, is PowerShell registreren als een subsysteem met een SSH op basis van een OpenSSH-server en kunt u uw bestaande op basis van SSH verifiëren mechanismen (zoals wachtwoorden of persoonlijke sleutels) met de traditionele `PSSession` semantiek.

Zie voor meer informatie over het configureren en gebruiken van externe toegang op basis van SSH, [PowerShell voor externe toegang via SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>Standaardcodering is UTF-8 zonder een stuklijst, met uitzondering van New-ModuleManifest

In het verleden Windows PowerShell-cmdlets, zoals `Get-Content`, `Set-Content` verschillende coderingen, zoals ASCII- en UTF-16 wordt gebruikt.
De verschillen in de Antwoordcodering gemaakt problemen wanneer een combinatie van cmdlets zonder op te geven een codering.

UTF-8 zonder een Byte Order Mark (BOM) niet-Windows-platforms traditioneel gebruiken als de standaardversleuteling aan voor tekstbestanden.
Meer Windows-toepassingen en hulpprogramma's zijn verplaatst van UTF-16 en naar stuklijst zonder UTF-8-codering.
PowerShell Core Hiermee wijzigt u de standaardversleuteling voldoen aan de bredere ecosystemen.

Dit betekent dat alle ingebouwde cmdlets die gebruikmaken van de `-Encoding` parameter gebruikt de `UTF8NoBOM` waarde is standaard.
De volgende cmdlets worden beïnvloed door deze wijziging:

- Inhoud toevoegen
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Out-File
- Selecteer-tekenreeks
- Send-MailMessage
- Set-Content

Deze cmdlets ook zijn bijgewerkt zodat de `-Encoding` parameter accepteert universeel `System.Text.Encoding`.

De standaardwaarde van `$OutputEncoding` is ook gewijzigd in UTF-8.

Als een best practice, moet u expliciet coderingen instellen in scripts met behulp van de `-Encoding` parameter voor het produceren van deterministische gedrag verschillende platforms.

`New-ModuleManifest` cmdlet heeft geen **Encoding** parameter. De codering van de module-manifest (.psd1)-bestand gemaakt met `New-ModuleManifest` cmdlet is afhankelijk van de omgeving: als het PowerShell Core die worden uitgevoerd op Linux vervolgens codering is UTF-8 (geen BOM); anders codering UTF-16 (met BOM) is. (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Ondersteuning voor backgrounding van pijplijnen met en-teken (`&`) (#3360)

Plaatsen `&` aan het einde van een pijplijn zorgt ervoor dat de pijplijn worden uitgevoerd als een PowerShell-taak.
Wanneer u een pijplijn is backgrounded, wordt een taakobject geretourneerd.
Zodra de pijplijn wordt uitgevoerd als een taak, alle van de standaard `*-Job` cmdlets kunnen worden gebruikt voor het beheren van de taak.
Variabelen (proces-specifieke variabelen worden genegeerd) in de pijplijn gebruikt worden automatisch gekopieerd naar de taak zodat `Copy-Item $foo $bar &` gewoon werkt.
De taak wordt ook uitgevoerd in de huidige map in plaats van de basismap van de gebruiker.
Zie voor meer informatie over PowerShell-taken, [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Semantisch versiebeheer

- Aangebracht `SemanticVersion` compatibel is met `SemVer 2.0`. (#5037) (Bedankt [ @iSazonov ](https://github.com/iSazonov)!)
- Standaard gewijzigd `ModuleVersion` in `New-ModuleManifest` naar `0.0.1` SemVer afgestemd. (#4842) (Bedankt [ @LDSpits ](https://github.com/LDSpits))
- Toegevoegd `semver` als een type accelerator voor `System.Management.Automation.SemanticVersion`. (#4142) (Dank aan [ @oising ](https://github.com/oising)!)
- Vergelijking van de ingeschakeld een `SemanticVersion` exemplaar en een `Version` exemplaar dat is opgesteld met `Major` en `Minor` Versiewaarden.

## <a name="language-updates"></a>Taalupdates

- Implementeren zodat gebruikers Unicode-tekens als argumenten, tekenreeksen of namen van variabelen gebruiken kunnen parseren Unicode-escape. (#3958) (Dank aan [ @rkeithhill ](https://github.com/rkeithhill)!)
- Toegevoegde nieuwe escape-teken voor ESC: `` `e``
- Ondersteuning toegevoegd voor het converteren van de enum-waarden voor de tekenreeks (#4318) (Bedankt [ @KirkMunro ](https://github.com/KirkMunro))
- Vaste casten één element matrix aan een generieke verzameling. (#3170)
- Toegevoegde teken bereik overbelasting naar de `..` operator, dus `'a'..'z'` tekens retourneert op basis van een' naar 'z'. (#5026) (Bedankt [ @IISResetMe ](https://github.com/IISResetMe)!)
- Vaste toewijzing van variabele alleen-lezen-variabelen niet overschrijven
- Lokale variabelen van automatische variabelen naar 'DottedScopes' pushen wanneer dotting script-cmdlets (#4709)
- Gebruik van 'Singleline, Multiline' optie in splitsingsoperator inschakelen (#4721) (Bedankt [ @iSazonov ](https://github.com/iSazonov))

## <a name="engine-updates"></a>Engine-updates

- `$PSVersionTable` vier nieuwe eigenschappen heeft:
  - `PSEdition`: Deze optie is ingesteld op `Core` op PowerShell Core en `Desktop` op Windows PowerShell
  - `GitCommitId`: Dit is de Git-doorvoer-ID van de Git-branch of tag waarop PowerShell is gebouwd.
    Bij builds voor vrijgegeven, deze waarschijnlijk zijn hetzelfde als `PSVersion`.
  - `OS`: Dit is een OS-versie-tekenreeks geretourneerd door `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Dit wordt geretourneerd door `[System.Environment]::OSVersion.Platform` is ingesteld op `Win32NT` op Windows, `Unix` op Mac OS en `Unix` op Linux.
- Verwijderd de `BuildVersion` eigenschap `$PSVersionTable`.
  Deze eigenschap is nauw verbonden met de build-versie van Windows.
  In plaats daarvan raden wij aan dat u `GitCommitId` om op te halen van de exacte build-versie van PowerShell Core. (#3877) (Dank aan [ @iSazonov ](https://github.com/iSazonov)!)
- Verwijder `ClrVersion` eigenschap `$PSVersionTable`.
  Deze eigenschap is niet van belang voor .NET Core en is alleen voor specifieke verouderde doeleinden die niet van toepassing op PowerShell in .NET Core blijven behouden.
- Drie nieuwe automatische variabelen om te bepalen of PowerShell wordt uitgevoerd in een bepaald besturingssysteem toegevoegd: `$IsWindows`, `$IsMacOs`, en `$IsLinux`.
- Voeg `GitCommitId` naar PowerShell Core banner.
  Nu kunt u niet om uit te voeren `$PSVersionTable` als u PowerShell om de versie te downloaden begint! (#3916) (Dank aan [ @iSazonov ](https://github.com/iSazonov)!)
- Toevoegen van een JSON-configuratiebestand met de naam `powershell.config.json` in `$PSHome` voor het opslaan van enkele instellingen die vereist zijn voor en opstarttijd (bijvoorbeeld `ExecutionPolicy`).
- Pijplijn niet blokkeren bij het uitvoeren van Windows EXE
- De inventarisatie van COM-verzamelingen is ingeschakeld. (#4553)

## <a name="cmdlet-updates"></a>Cmdlet-updates

### <a name="new-cmdlets"></a>Er zijn nieuwe cmdlets

- Voeg `Get-Uptime` naar `Microsoft.PowerShell.Utility`.
- Voeg `Remove-Alias` opdracht. (#5143) (Bedankt [ @PowershellNinja ](https://github.com/PowershellNinja)!)
- Voeg `Remove-Service` aan Management-module. (#4858) (Bedankt [ @joandrsn ](https://github.com/joandrsn)!)

### <a name="web-cmdlets"></a>Web-cmdlets

- Certificaat-verificatie-ondersteuning voor cmdlets voor web toevoegen. (#4646) (Bedankt [ @markekraus ](https://github.com/markekraus))
- Ondersteuning voor inhoud headers toevoegen aan de web-cmdlets. (#4494 & #4640) (Bedankt [ @markekraus ](https://github.com/markekraus))
- Ondersteuning voor meerdere koppeling koptekst toevoegen aan Web-Cmdlets. (#5265) (Bedankt [ @markekraus ](https://github.com/markekraus)!)
- Ondersteuning voor koppeling header paginering in web-cmdlets (#3828)
  - Voor `Invoke-WebRequest`, wanneer het antwoord bevat de header van een koppeling maken we een eigenschap RelationLink als een woordenlijst die de URL's en `rel` kenmerken en zorg ervoor dat de URL's zijn absolute te vereenvoudigen voor ontwikkelaars om te gebruiken.
  - Voor `Invoke-RestMethod`, wanneer het antwoord bevat een koppeling header geven we weer een `-FollowRelLink` switch automatisch volgen `next` `rel` koppelingen totdat ze niet meer bestaat of één keer wordt bereikt de optionele `-MaximumFollowRelLink` parameterwaarde.
- Voeg `-CustomMethod` parameter voor web-cmdlets om toe te staan voor niet-standaard methode termen. (#3142) (Dank aan [ @Lee303 ](https://github.com/Lee303)!)
- Voeg `SslProtocol` ondersteuning voor Web-Cmdlets. (#5329) (Bedankt [ @markekraus ](https://github.com/markekraus)!)
- Toevoegen van Multipart ondersteuning voor web-cmdlets. (#4782) (Bedankt [ @markekraus ](https://github.com/markekraus))
- Voeg `-NoProxy` voor web-cmdlets zodat ze het hele systeem proxy-instellingen kunnen negeren. (#3447) (Dank aan [ @TheFlyingCorpse ](https://github.com/TheFlyingCorpse)!)
- Gebruiker Agent van de Web-Cmdlets nu rapporten de OS-platform (#4937) (Bedankt [ @LDSpits ](https://github.com/LDSpits))
- Voeg `-SkipHeaderValidation` overschakelen naar de web-cmdlets voor de ondersteuning van headers toe te voegen zonder het valideren van de headerwaarde. (#4085)
- Web-cmdlets voor het HTTPS-certificaat van de server niet valideren als vereist inschakelen.
- Verificatieparameters toevoegen aan de web-cmdlets. (#5052) (Bedankt [ @markekraus ](https://github.com/markekraus))
  - Voeg `-Authentication` waarmee de drie opties: Basic, OAuth en Bearer.
  - Voeg `-Token` ophalen OAuth en Bearer-opties voor het bearer-token.
  - Voeg `-AllowUnencryptedAuthentication` authentication dat is opgegeven voor een transportschema dan HTTPS overslaan.
- Voeg `-ResponseHeadersVariable` naar `Invoke-RestMethod` waarmee het vastleggen van antwoordheaders. (#4888) (Bedankt [ @markekraus ](https://github.com/markekraus))
- Corrigeer de web-cmdlets voor het HTTP-antwoord opnemen in de uitzondering als de statuscode van het antwoord niet geslaagd is. (#3201)
- Web-cmdlets wijzigen `UserAgent` van `WindowsPowerShell` naar `PowerShell`. (#4914) (Bedankt [ @markekraus ](https://github.com/markekraus))
- Voeg expliciete `ContentType` detectie `Invoke-RestMethod` (#4692)
- Web-cmdlets oplossen `-SkipHeaderValidation` om te werken met niet-standaard gebruikersagent headers. (#4479 & #4512) (Bedankt [ @markekraus ](https://github.com/markekraus))

### <a name="json-cmdlets"></a>JSON-cmdlets

- Voeg `-AsHashtable` naar `ConvertFrom-Json` om terug te keren een `Hashtable` in plaats daarvan. (#5043) (Bedankt [ @bergmeister ](https://github.com/bergmeister)!)
- Gebruik kleurcodes indelingsfunctie met `ConvertTo-Json` uitvoer. (#2787) (Dank aan @kittholland!)
- Voeg `Jobject` ondersteuning van serialisatie `ConvertTo-Json`. (#5141)
- Los `ConvertFrom-Json` deserialiseren van een matrix met tekenreeksen uit de pijplijn die samen een volledige JSON-tekenreeks te maken.
  Dit wordt soms vorm doorbreekt waar het parseren van JSON opgelost. (#3823)
- Verwijder de `AliasProperty "Count"` gedefinieerd voor `System.Array`.
  Hiermee verwijdert u de overbodige `Count` eigenschap op sommige `ConvertFrom-Json` uitvoer. (#3231) (Dank aan [ @PetSerAl ](https://github.com/PetSerAl)!)

### <a name="csv-cmdlets"></a>CSV-cmdlets

- `Import-Csv` biedt nu ondersteuning voor de W3C Extended Log File Format (#2482) (Bedankt [ @iSazonov ](https://github.com/iSazonov)!)
- Voeg `PSTypeName` ondersteuning voor `Import-Csv` en `ConvertFrom-Csv`. (#5389) (Bedankt [ @markekraus ](https://github.com/markekraus)!)
- Controleer `Import-Csv` ondersteunen `CR`, `LF`, en `CRLF` als scheidingstekens regel. (#5363) (Bedankt [ @iSazonov ](https://github.com/iSazonov)!)
- Controleer `-NoTypeInformation` de standaard op `Export-Csv` en `ConvertTo-Csv`. (#5164) (Bedankt [ @markekraus ](https://github.com/markekraus)!)

### <a name="service-cmdlets"></a>Service-cmdlets

- Voeg eigenschappen toe `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, en `StartupType` naar de `ServiceController` objecten die worden geretourneerd door `Get-Service`. (#4907) (Bedankt [ @joandrsn ](https://github.com/joandrsn))
- Voeg functionaliteit voor het instellen van referenties voor `Set-Service` opdracht. (#4844) (Bedankt [ @joandrsn ](https://github.com/joandrsn))

### <a name="other-cmdlets"></a>Andere cmdlets

- Voeg een parameter voor `Get-ChildItem` met de naam `-FollowSymlink` die symlinks op aanvraag, met controles voor koppeling lussen passeert. (#4020)
- Update `Add-Type` ter ondersteuning van `CSharpVersion7`. (#3933) (Dank aan [ @iSazonov ](https://github.com/iSazonov))
- Verwijder de `Microsoft.PowerShell.LocalAccounts` module vanwege het gebruik van niet-ondersteunde API's tot een betere oplossing is gevonden. (#4302)
- Verwijder de `*-Counter` -cmdlets in `Microsoft.PowerShell.Diagnostics` vanwege het gebruik van niet-ondersteunde API's tot een betere oplossing is gevonden. (#4303)
- Voeg ondersteuning toe voor `Invoke-Item -Path <folder>`. (#4262)
- Voeg `-Extension` en `-LeafBase` verandert in een `Split-Path` zodat u paden tussen de extensie en de rest van de bestandsnaam splitsen. (#2721) (Dank aan [ @powercode ](https://github.com/powercode)!)
- Voeg parameters toe `-Top` en `-Bottom` naar `Sort-Object` voor bovenste/onderste N sorteren
- Een proces bovenliggende proces stellen door toe te voegen de `CodeProperty "Parent"` naar `System.Diagnostics.Process`. (#2850) (Dank aan [ @powercode ](https://github.com/powercode)!)
- MB gebruiken in plaats van KB voor geheugenkolommen van het `Get-Process`
- Voeg `-NoNewLine` overschakelen voor `Out-String`. (#5056) (Bedankt [ @raghav710 ](https://github.com/raghav710))
- `Move-Item` cmdlet zich houdt aan `-Include`, `-Exclude`, en `-Filter` parameters. (#3878)
- Toestaan dat `*` moet worden gebruikt in het registerpad voor `Remove-Item`. (#4866)
- Voeg `-Title` naar `Get-Credential` en lever een geïntegreerde ervaring de prompt ervaring verschillende platforms.
- Voeg de `-TimeOut` parameter `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` cmdlets hebt nu toegang tot bestand handtekening timestamp. (#4061)
- Verwijder niet-ondersteunde `-ShowWindow` overschakelen van `Get-Help`. (#4903)
- Los `Get-Content -Delimiter` geretourneerde (#3706) het scheidingsteken niet opnemen in de matrixelementen (Bedankt [ @mklement0 ](https://github.com/mklement0))
- Voeg `Meta`, `Charset`, en `Transitional` parameters `ConvertTo-HTML` (#4184) (Bedankt [ @ergo3114 ](https://github.com/ergo3114))
- Voeg `WindowsUBR` en `WindowsVersion` eigenschappen `Get-ComputerInfo` resultaat
- Voeg `-Group` parameter `Get-Verb`
- Voeg `ShouldProcess` ondersteuning `New-FileCatalog` en `Test-FileCatalog` (corrigeert `-WhatIf` en `-Confirm`). (#3074) (Dank aan [ @iSazonov ](https://github.com/iSazonov)!)
- Voeg `-WhatIf` overschakelen naar `Start-Process` cmdlet (#4735) (Bedankt [ @sarithsutha ](https://github.com/sarithsutha))
- Voeg `ValidateNotNullOrEmpty` te veel bestaande parameters.

## <a name="tab-completion"></a>Tab-aanvulling

- Het type Deductie in de tab-aanvulling op basis van waarden van variabelen runtime verbeterd. (#2744) (Dank aan [ @powercode ](https://github.com/powercode)!) Hiermee kunt de tab-Aanvulling in dergelijke situaties:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Tab-aanvulling voor hash-tabel toevoegen `-Property` van `Select-Object`. (#3625) (Dank aan [ @powercode ](https://github.com/powercode))
- Inschakelen van argument automatisch aanvullen voor `-ExcludeProperty` en `-ExpandProperty` van `Select-Object`. (#3443) (Dank aan [ @iSazonov ](https://github.com/iSazonov)!)
- Is een fout opgelost in de tab-Aanvulling kunnen `native.exe --<tab>` aanroep in systeemeigen completer mogelijk maakt. (#3633) (Dank aan [ @powercode ](https://github.com/powercode)!)

## <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

We hebben een aantal belangrijke wijzigingen in PowerShell Core 6.0 geïntroduceerd.
Meer informatie over deze in detail zien [belangrijke wijzigingen in PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Foutopsporing

- Ondersteuning voor step-in Foutopsporing op afstand voor `Invoke-Command -ComputerName`. (#3015)
- Binder logboekregistratie voor foutopsporing in PowerShell Core inschakelen

## <a name="filesystem-updates"></a>Bestandssysteem updates

- Schakel het gebruik van de provider van het bestandssysteem via een UNC-pad. ($4998)
- `Split-Path` werkt nu met UNC-toegangspunten
- `cd` er geen argumenten zijn werkt nu als `cd ~`
- Vaste PowerShell Core om gebruik van de paden die meer dan 260 tekens lang zijn. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Oplossingen voor problemen en verbeterde prestaties

We hebben aangebracht *veel* verbeteringen in prestaties via PowerShell, zoals in de opstarttijd, verschillende ingebouwde cmdlets en interactie met systeemeigen binaire bestanden.

We hebben ook een aantal fouten in PowerShell Core opgelost.
Voor een volledige lijst van wijzigingen en correcties, Bekijk onze [changelog][] op GitHub.

## <a name="telemetry"></a>Telemetrie

- PowerShell Core 6.0 toegevoegd om telemetrie naar de consolehost rapport twee waarden (#3620):
  - de OS-platform (`$PSVersionTable.OSDescription`)
  - de exacte versie van PowerShell (`$PSVersionTable.GitCommitId`)

Als u opt-out van deze telemetrische gegevens, maken `POWERSHELL_TELEMETRY_OPTOUT` omgevingsvariabele met een van de volgende waarden: `true`, `1` of `yes`.
Het maken van de variabele omzeilt alle telemetrie zelfs vóór de eerste uitvoering van PowerShell.
We zijn ook van plan op het blootstellen van deze telemetrische gegevens en de inzichten die we verzamelen van de telemetrie in de [community dashboard][community-dashboard].
U vindt meer informatie over hoe deze worden gebruikt in deze [blogbericht][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: breaking-changes-ps6.md
[changelog]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET Blog]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[FAQ]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
