---
ms.date: 10/30/2018
keywords: DSC, powershell, configuratie en installatie
title: Problemen met DSC oplossen
ms.openlocfilehash: e1f36bbc97569ac0d65f003ee08f52ec174a4520
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404361"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="fb4ee-103">Problemen met DSC oplossen</span><span class="sxs-lookup"><span data-stu-id="fb4ee-103">Troubleshooting DSC</span></span>

<span data-ttu-id="fb4ee-104">_Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="fb4ee-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="fb4ee-105">In dit onderwerp wordt beschreven hoe problemen met DSC wanneer er zich problemen voordoen.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="fb4ee-106">WinRM-afhankelijkheid</span><span class="sxs-lookup"><span data-stu-id="fb4ee-106">WinRM Dependency</span></span>

<span data-ttu-id="fb4ee-107">Windows PowerShell Desired State Configuration (DSC), is afhankelijk van WinRM.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="fb4ee-108">WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="fb4ee-109">Voer `Set-WSManQuickConfig`, in een Windows PowerShell met verhoogde bevoegdheden om in te schakelen WinRM-sessie.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="fb4ee-110">Met behulp van Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="fb4ee-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="fb4ee-111">De [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet krijgt u informatie over de configuratiestatus van een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-111">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="fb4ee-112">Een uitgebreide object wordt geretourneerd die bevat belangrijke informatie over of de configuratie-uitvoering geslaagd of mislukt is.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="fb4ee-113">U kunt verdiepen in het object voor het detecteren van gegevens over de configuratie uitvoeren zoals:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="fb4ee-114">Alle resources die niet zijn geslaagd</span><span class="sxs-lookup"><span data-stu-id="fb4ee-114">All of the resources that failed</span></span>
- <span data-ttu-id="fb4ee-115">Een resource die opnieuw worden opgestart aangevraagd</span><span class="sxs-lookup"><span data-stu-id="fb4ee-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="fb4ee-116">META-configuratie-instellingen op het moment van de configuratie uitvoeren</span><span class="sxs-lookup"><span data-stu-id="fb4ee-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="fb4ee-117">Enzovoort.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-117">Etc.</span></span>

<span data-ttu-id="fb4ee-118">De volgende parameter ingesteld retourneert de statusinformatie voor de laatste configuratie uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="fb4ee-119">De volgende parameter ingesteld retourneert de statusinformatie voor alle voorgaande configuratie wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="fb4ee-120">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="fb4ee-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ReosurceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="fb4ee-121">Mijn script wordt niet uitgevoerd: Met behulp van DSC-logboeken op te sporen scriptfouten</span><span class="sxs-lookup"><span data-stu-id="fb4ee-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="fb4ee-122">Net als alle Windows-software, DSC registreert fouten en gebeurtenissen in [logboeken](/windows/desktop/EventLog/about-event-logging) die kunnen worden weergegeven in de [logboeken](https://support.microsoft.com/hub/4338813/windows-help).</span><span class="sxs-lookup"><span data-stu-id="fb4ee-122">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span>
<span data-ttu-id="fb4ee-123">Deze logboeken onderzoeken kan u helpen begrijpen waarom een bepaalde bewerking is mislukt, en hoe u fouten in de toekomst te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="fb4ee-124">Configuratiescripts schrijven is lastig, dus wilt bijhouden fouten gemakkelijker als u de auteur, gebruikt u de DSC-logboekresource om bij te houden van de voortgang van uw configuratie in het logboek voor DSC-analyse.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="fb4ee-125">Waar vind ik de logboeken voor DSC</span><span class="sxs-lookup"><span data-stu-id="fb4ee-125">Where are DSC event logs?</span></span>

<span data-ttu-id="fb4ee-126">DSC-gebeurtenissen zijn in Logboeken: **Toepassingen en Services Logboeken/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="fb4ee-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="fb4ee-127">De bijbehorende PowerShell-cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), kunnen ook worden uitgevoerd om de gebeurtenislogboeken weer te geven:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-127">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="fb4ee-128">Zoals hierboven beschreven, de naam van de primaire logboek van DSC wordt **Microsoft Windows -> DSC ->** (de logboeknamen van andere onder Windows niet hier worden weergegeven voor beknoptheid).</span><span class="sxs-lookup"><span data-stu-id="fb4ee-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="fb4ee-129">De primaire naam wordt toegevoegd aan de naam van het kanaal te maken van de naam van het volledige logboek.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="fb4ee-130">De DSC-engine schrijft voornamelijk naar drie verschillende typen logboeken: [Operationeel, analyse en foutopsporing logboeken](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="fb4ee-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span> <span data-ttu-id="fb4ee-131">Sinds de analytische en logboeken voor foutopsporing zijn standaard uitgeschakeld, moet u ze inschakelen in Logboeken.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="fb4ee-132">Om dit te doen, opent u Logboeken door te typen van Show-gebeurtenislogboek in Windows PowerShell; of klik op de **Start** klikken, klik op **Configuratiescherm**, klikt u op **Systeembeheer**, en klik vervolgens op **logboeken**.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="fb4ee-133">Op de **weergave** in Logboeken, klik daarna op **weergeven analytische en foutopsporing in logboeken**.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="fb4ee-134">De naam van het logboek voor de analytic channel is **Microsoft-Windows-Dsc/analytische**, en het kanaal voor foutopsporing **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="fb4ee-135">U kunt ook de [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) hulpprogramma voor het inschakelen van de logboeken, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-135">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="fb4ee-136">Wat bevatten de logboeken van de DSC?</span><span class="sxs-lookup"><span data-stu-id="fb4ee-136">What do DSC logs contain?</span></span>

<span data-ttu-id="fb4ee-137">DSC-logboeken worden gesplitst via de drie logboekkanalen op basis van het belang van het bericht.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="fb4ee-138">Het operationele logboek in DSC bevat alle foutberichten en kan worden gebruikt om een probleem te identificeren.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="fb4ee-139">De analytische logboek heeft een hoger aantal gebeurtenissen, en kunt identificeren waar fout(en) opgetreden.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="fb4ee-140">Dit kanaal bevat ook uitgebreide berichten (indien aanwezig).</span><span class="sxs-lookup"><span data-stu-id="fb4ee-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="fb4ee-141">Het logboek voor foutopsporing bevat de logboeken die kunnen u helpen begrijpen hoe de fouten zijn opgetreden.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="fb4ee-142">DSC-gebeurtenisberichten worden gestructureerd zodat elk gebeurtenisbericht begint met een taak-ID dat een DSC-bewerking een unieke aanduiding.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="fb4ee-143">In het volgende voorbeeld wordt geprobeerd om op te halen van het bericht uit de eerste gebeurtenis vastgelegd in het operationele logboek voor DSC.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="fb4ee-144">DSC-gebeurtenissen worden vastgelegd in een bepaalde structuur waarmee de gebruiker naar gebeurtenissen samenstellen van een DSC-taak.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="fb4ee-145">De structuur is als volgt:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="fb4ee-146">Verzamelen van gebeurtenissen van een enkele DSC-bewerking</span><span class="sxs-lookup"><span data-stu-id="fb4ee-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="fb4ee-147">DSC-gebeurtenislogboeken bevatten gebeurtenissen die worden gegenereerd door verschillende DSC-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="fb4ee-148">U zult meestal wel betrokken met de details over een bepaalde bewerking.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="fb4ee-149">Alle DSC-logboeken kunnen worden gegroepeerd op de taak-ID-eigenschap die uniek is voor elke DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="fb4ee-150">De taak-ID wordt weergegeven als de eerste eigenschapswaarde in alle DSC-gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="fb4ee-151">De volgende stappen wordt uitgelegd hoe verzamelt alle gebeurtenissen in een gegroepeerde matrix-structuur.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

<span data-ttu-id="fb4ee-152">Hier wordt de variabele `$SeparateDscOperations` logboeken gegroepeerd op de taak-id's bevat.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="fb4ee-153">Elk matrixelement van deze variabele vertegenwoordigt een groep gebeurtenissen vastgelegd door een andere bewerking voor DSC, waardoor er toegang tot meer informatie over de logboeken.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

<span data-ttu-id="fb4ee-154">U kunt de gegevens in de variabele ophalen `$SeparateDscOperations` met behulp van [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="fb4ee-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="fb4ee-155">Hieronder vindt u vijf scenario's waarin u gegevens wilt mogelijk voor het oplossen van DSC ophalen:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="fb4ee-156">1: Mislukte bewerkingen</span><span class="sxs-lookup"><span data-stu-id="fb4ee-156">1: Operations failures</span></span>

<span data-ttu-id="fb4ee-157">Alle gebeurtenissen hebben [niveaus](/windows/desktop/WES/defining-severity-levels).</span><span class="sxs-lookup"><span data-stu-id="fb4ee-157">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="fb4ee-158">Deze informatie kan worden gebruikt om de foutgebeurtenissen te identificeren:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="fb4ee-159">2: Details van bewerkingen uitvoeren in het afgelopen half uur</span><span class="sxs-lookup"><span data-stu-id="fb4ee-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="fb4ee-160">`TimeCreated`, een eigenschap van elke Windows-gebeurtenis staat de tijd waarop de gebeurtenis is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="fb4ee-161">Vergelijking van deze eigenschap met een bepaalde datum/tijd-object kan worden gebruikt om alle gebeurtenissen te filteren:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="fb4ee-162">3: Berichten van de meest recente bewerking</span><span class="sxs-lookup"><span data-stu-id="fb4ee-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="fb4ee-163">De meest recente bewerking wordt opgeslagen in de eerste index van de matrixgroep `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="fb4ee-164">Uitvoeren van query's van de groep berichten voor index 0 retourneert alle berichten voor de meest recente bewerking:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="fb4ee-165">4: Foutberichten voor recente mislukte bewerkingen worden geregistreerd</span><span class="sxs-lookup"><span data-stu-id="fb4ee-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="fb4ee-166">`$SeparateDscOperations[0].Group` bevat een verzameling van gebeurtenissen voor de meest recente bewerking.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="fb4ee-167">Voer de `Where-Object` cmdlet om de gebeurtenissen te filteren op basis van hun niveau weergavenaam.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="fb4ee-168">Resultaten worden opgeslagen in de `$myFailedEvent` variabele, die verder kan worden opgesplitst om op te halen van het gebeurtenisbericht weergegeven:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="fb4ee-169">5: Alle gebeurtenissen die worden gegenereerd voor een bepaalde taak-ID.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="fb4ee-170">`$SeparateDscOperations` is een matrix van groepen, die allemaal de naam op als de unieke taak-ID.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="fb4ee-171">Door het uitvoeren van de `Where-Object` cmdlet, u kunt deze groepen van gebeurtenissen met een bepaalde taak-ID ophalen:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="fb4ee-172">Met behulp van xDscDiagnostics voor het analyseren van DSC-Logboeken</span><span class="sxs-lookup"><span data-stu-id="fb4ee-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="fb4ee-173">**xDscDiagnostics** is een PowerShell-module die bestaat uit verschillende functies die kunnen helpen met het analyseren van DSC-fouten op uw computer.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="fb4ee-174">Aan de hand van deze functies kunnen u alle lokale evenementen van afgelopen DSC-bewerkingen of gebeurtenissen DSC op externe computers identificeren (met geldige referenties).</span><span class="sxs-lookup"><span data-stu-id="fb4ee-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="fb4ee-175">De term DSC-bewerking wordt hier gebruikt voor het definiëren van één unieke DSC uitvoering vanaf het begin tot het einde.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="fb4ee-176">Bijvoorbeeld, `Test-DscConfiguration` zou een afzonderlijke DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="fb4ee-177">Op deze manier elke andere cmdlet in DSC (zoals `Get-DscConfiguration`, `Start-DscConfiguration`, enzovoort), kan elke worden geïdentificeerd als afzonderlijke DSC-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="fb4ee-178">De functies worden beschreven op [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="fb4ee-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="fb4ee-179">Help-informatie is beschikbaar door uit te voeren `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="fb4ee-180">Details van DSC-bewerkingen ophalen</span><span class="sxs-lookup"><span data-stu-id="fb4ee-180">Getting details of DSC operations</span></span>

<span data-ttu-id="fb4ee-181">De `Get-xDscOperation` functie kunt u de resultaten van de DSC-bewerkingen die worden uitgevoerd op een of meerdere computers vinden en retourneert een object met het verzamelen van gebeurtenissen die worden geproduceerd door elke DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="fb4ee-182">Bijvoorbeeld, in de volgende uitvoer moet drie opdrachten zijn uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="fb4ee-183">Het eerste item doorgegeven en de andere twee is mislukt.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="fb4ee-184">Deze resultaten worden samengevat in de uitvoer van `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="fb4ee-185">U kunt ook opgeven dat u alleen de resultaten voor de meest recente bewerkingen met behulp van de `Newest` parameter:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="fb4ee-186">Details van de DSC-gebeurtenissen ophalen</span><span class="sxs-lookup"><span data-stu-id="fb4ee-186">Getting details of DSC events</span></span>

<span data-ttu-id="fb4ee-187">De `Trace-xDscOperation` cmdlet retourneert een object met een verzameling van gebeurtenissen, hun gebeurtenistypen, en het bericht uitvoer gegenereerd op basis van een bepaalde DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="fb4ee-188">Normaal gesproken wanneer u een fout vinden in een van de bewerkingen met behulp van `Get-xDscOperation`, u wilt traceren die bewerking om erachter te komen welke van de gebeurtenissen heeft een fout veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="fb4ee-189">Gebruik de `SequenceID` parameter om op te halen van de gebeurtenissen voor een bepaalde bewerking voor een specifieke computer.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="fb4ee-190">Als u bijvoorbeeld een `SequenceID` van 9, `Trace-xDscOperaion` ophalen van de tracering voor het DSC-bewerking die 9de van de laatste bewerking was:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="fb4ee-191">Geeft de **GUID** toegewezen aan een specifieke DSC-bewerking (zoals geretourneerd door de `Get-xDscOperation` cmdlet) om op te halen van de Gebeurtenisdetails voor de desbetreffende DSC-bewerking:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="fb4ee-192">Houd er rekening mee dat, aangezien `Trace-xDscOperation` cumuleert de gebeurtenissen van de analyse, foutopsporing, en operationele Logboeken, wordt gevraagd u deze logboeken inschakelen, zoals hierboven beschreven.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="fb4ee-193">U kunt ook kunt u informatie over de gebeurtenissen verzamelen door op te slaan van de uitvoer van `Trace-xDscOperation` in een variabele.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="fb4ee-194">U kunt de volgende opdrachten gebruiken om weer te geven van alle gebeurtenissen voor een bepaalde DSC-bewerking.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="fb4ee-195">Hiermee wordt weergegeven dat de resultaten hetzelfde als de `Get-WinEvent` cmdlet, zoals in de onderstaande uitvoer:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="fb4ee-196">Eerst gebruikt u in het ideale geval `Get-xDscOperation` naar een lijst met de laatste paar DSC configuratie wordt uitgevoerd op uw virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="fb4ee-197">Na deze kunt u een eenmalige bewerking (met de SequenceID of JobID) controleren met `Trace-xDscOperation` om te ontdekken wat er gedaan achter de schermen.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="fb4ee-198">Ophalen van gebeurtenissen voor een externe computer</span><span class="sxs-lookup"><span data-stu-id="fb4ee-198">Getting events for a remote computer</span></span>

<span data-ttu-id="fb4ee-199">Gebruik de `ComputerName` parameter van de `Trace-xDscOperation` cmdlet om op te halen van de gebeurtenisdetails op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="fb4ee-200">Voordat u dit doen kunt, hebt u een firewallregel extern beheer toestaan op de externe computer maken:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="fb4ee-201">Nu kunt u die computer in de aanroep van `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="fb4ee-202">Mijn resources bijwerken niet: Het opnieuw instellen van de cache</span><span class="sxs-lookup"><span data-stu-id="fb4ee-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="fb4ee-203">De DSC-engine in de cache opgeslagen voor resources die zijn geïmplementeerd als een PowerShell-module voor efficiëntie doeleinden.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="fb4ee-204">Dit kan echter problemen veroorzaken wanneer u deze voor het ontwerpen van een resource en tegelijkertijd testen omdat DSC versie in de cache wordt geladen tot het proces opnieuw is gestart.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="fb4ee-205">De enige manier om te maken van DSC laden van de nieuwere versie is het proces voor het hosten van de DSC-engine expliciet afsluiten.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="fb4ee-206">Op dezelfde manier bij het uitvoeren van `Start-DscConfiguration`, na het toevoegen en wijzigen van een aangepaste resource, de wijziging mogelijk niet uitgevoerd tenzij of tot, de computer opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="fb4ee-207">Dit is omdat DSC wordt uitgevoerd in de hostproces van de WMI-Provider (WmiPrvSE), en er zijn doorgaans veel exemplaren van WmiPrvSE tegelijk worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="fb4ee-208">Wanneer u het opnieuw opstarten, wordt het hostproces opnieuw is opgestart en wordt de cache is leeggemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="fb4ee-209">Is recyclen van de configuratie en de cache wissen zonder opnieuw opstarten, moet u stoppen en opnieuw opstarten het hostproces.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="fb4ee-210">Dit kan worden gedaan op basis van afzonderlijke instanties, waarbij u het proces identificeren, stoppen en opnieuw kunnen worden gestart.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="fb4ee-211">Of u kunt `DebugMode`, zoals hieronder wordt gedemonstreerd laden van de PowerShell DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="fb4ee-212">Om te bepalen welk proces als host fungeert voor de DSC-engine en voorkomen dat deze op basis van afzonderlijke instanties, kunt u de proces-ID van de WmiPrvSE die als host voor de DSC-engine fungeert weergeven.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="fb4ee-213">Klik, voor het bijwerken van de provider, stop de WmiPrvSE proces met behulp van de onderstaande opdrachten en voer **Start-DscConfiguration** opnieuw.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="fb4ee-214">Met behulp van fouten opsporen-modus</span><span class="sxs-lookup"><span data-stu-id="fb4ee-214">Using DebugMode</span></span>

<span data-ttu-id="fb4ee-215">U kunt configureren dat de DSC lokale Configuration Manager (LCM) te gebruiken `DebugMode` altijd de cache wissen wanneer het hostproces opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="fb4ee-216">Als de waarde **waar**, het ervoor zorgt dat de engine altijd laden van de PowerShell DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="fb4ee-217">Wanneer u klaar bent uw resource schrijven, kunt u dit instellen terug naar **FALSE** en de engine wordt het gedrag van de modules in het cachegeheugen.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="fb4ee-218">Hieronder volgt een demonstratie om weer te geven hoe `DebugMode` kunt automatisch vernieuwen voor de cache.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="fb4ee-219">Eerst kijken we de standaard-configuratie:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-219">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="fb4ee-220">U kunt zien dat `DebugMode` is ingesteld op **'None'**.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="fb4ee-221">Voor het instellen van de `DebugMode` demonstreren, gebruikt u de volgende PowerShell-resource:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

<span data-ttu-id="fb4ee-222">Maak nu een configuratie met behulp van de bovenstaande resource met de naam `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="fb4ee-223">U ziet dat de inhoud van bestand: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="fb4ee-224">Werk nu de code van de provider met het volgende script:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-224">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="fb4ee-225">Met dit script genereert een willekeurig getal en de code van de provider dienovereenkomstig bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="fb4ee-226">Met `DebugMode` ingesteld op false, de inhoud van het bestand '**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**"nooit worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="fb4ee-227">Stel nu `DebugMode` naar **"ForceModuleImport"** in uw configuratiescript:</span><span class="sxs-lookup"><span data-stu-id="fb4ee-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="fb4ee-228">Wanneer u het bovenstaande script opnieuw uitvoert, ziet u dat de inhoud van het bestand verschillende telkens is.</span><span class="sxs-lookup"><span data-stu-id="fb4ee-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="fb4ee-229">(U kunt uitvoeren `Get-DscConfiguration` om te controleren of het).</span><span class="sxs-lookup"><span data-stu-id="fb4ee-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="fb4ee-230">Hieronder volgt het resultaat van de twee aanvullende uitvoeringen (uw resultaat kunnen afwijken wanneer u het script uitvoert):</span><span class="sxs-lookup"><span data-stu-id="fb4ee-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="see-also"></a><span data-ttu-id="fb4ee-231">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fb4ee-231">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="fb4ee-232">Concepten</span><span class="sxs-lookup"><span data-stu-id="fb4ee-232">Concepts</span></span>

- [<span data-ttu-id="fb4ee-233">Maken van aangepaste Windows PowerShell Desired State Configuration Resources</span><span class="sxs-lookup"><span data-stu-id="fb4ee-233">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="fb4ee-234">Andere bronnen</span><span class="sxs-lookup"><span data-stu-id="fb4ee-234">Other Resources</span></span>

- [<span data-ttu-id="fb4ee-235">Windows PowerShell Desired State Configuration-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="fb4ee-235">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)