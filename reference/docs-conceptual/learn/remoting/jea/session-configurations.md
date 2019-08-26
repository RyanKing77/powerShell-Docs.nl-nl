---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: JEA-sessie configuraties
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017879"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="a01e6-103">JEA-sessie configuraties</span><span class="sxs-lookup"><span data-stu-id="a01e6-103">JEA Session Configurations</span></span>

<span data-ttu-id="a01e6-104">Een JEA-eind punt wordt geregistreerd op een systeem door een Power shell-sessie configuratie bestand te maken en te registreren.</span><span class="sxs-lookup"><span data-stu-id="a01e6-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="a01e6-105">Met sessie configuraties definieert u wie het JEA-eind punt kan gebruiken en met welke rollen ze toegang hebben.</span><span class="sxs-lookup"><span data-stu-id="a01e6-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="a01e6-106">Ze definiëren ook algemene instellingen die van toepassing zijn op alle gebruikers van de JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="a01e6-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="a01e6-107">Een configuratie bestand voor de sessie maken</span><span class="sxs-lookup"><span data-stu-id="a01e6-107">Create a session configuration file</span></span>

<span data-ttu-id="a01e6-108">Als u een JEA-eind punt wilt registreren, moet u opgeven hoe dat eind punt is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="a01e6-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="a01e6-109">Er zijn veel opties om rekening mee te houden.</span><span class="sxs-lookup"><span data-stu-id="a01e6-109">There are many options to consider.</span></span> <span data-ttu-id="a01e6-110">De belangrijkste opties zijn:</span><span class="sxs-lookup"><span data-stu-id="a01e6-110">The most important options are:</span></span>

- <span data-ttu-id="a01e6-111">Wie heeft toegang tot het JEA-eind punt</span><span class="sxs-lookup"><span data-stu-id="a01e6-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="a01e6-112">Aan welke rollen ze worden toegewezen</span><span class="sxs-lookup"><span data-stu-id="a01e6-112">Which roles they be assigned</span></span>
- <span data-ttu-id="a01e6-113">Welke identiteits JEA worden gebruikt onder de kaften</span><span class="sxs-lookup"><span data-stu-id="a01e6-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="a01e6-114">De naam van het JEA-eind punt</span><span class="sxs-lookup"><span data-stu-id="a01e6-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="a01e6-115">Deze opties worden gedefinieerd in een Power shell-gegevens bestand `.pssc` met een extensie die een Power shell-sessie configuratie bestand wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="a01e6-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="a01e6-116">Het configuratie bestand van de sessie kan worden bewerkt met behulp van een tekst editor.</span><span class="sxs-lookup"><span data-stu-id="a01e6-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="a01e6-117">Voer de volgende opdracht uit om een leeg sjabloon configuratie bestand te maken.</span><span class="sxs-lookup"><span data-stu-id="a01e6-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="a01e6-118">Alleen de meest voorkomende configuratie opties zijn standaard opgenomen in het sjabloon bestand.</span><span class="sxs-lookup"><span data-stu-id="a01e6-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="a01e6-119">Gebruik de `-Full` Schakel optie voor het toevoegen van alle toepasselijke instellingen in het gegenereerde PSSC.</span><span class="sxs-lookup"><span data-stu-id="a01e6-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="a01e6-120">In `-SessionType RestrictedRemoteServer` het veld wordt aangegeven dat de sessie configuratie wordt gebruikt door JEA voor beveiligd beheer.</span><span class="sxs-lookup"><span data-stu-id="a01e6-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="a01e6-121">Sessies van dit type worden in de modus exclusief **taal** uitgevoerd en hebben alleen toegang tot de volgende standaard opdrachten (en aliassen):</span><span class="sxs-lookup"><span data-stu-id="a01e6-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="a01e6-122">Clear-host (CLS, Clear)</span><span class="sxs-lookup"><span data-stu-id="a01e6-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="a01e6-123">Afsluiten-PSSession (exsn, afsluiten)</span><span class="sxs-lookup"><span data-stu-id="a01e6-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="a01e6-124">Get-opdracht (GCM)</span><span class="sxs-lookup"><span data-stu-id="a01e6-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="a01e6-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="a01e6-125">Get-FormatData</span></span>
- <span data-ttu-id="a01e6-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="a01e6-126">Get-Help</span></span>
- <span data-ttu-id="a01e6-127">Measure-object (measure)</span><span class="sxs-lookup"><span data-stu-id="a01e6-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="a01e6-128">Out-standaard</span><span class="sxs-lookup"><span data-stu-id="a01e6-128">Out-Default</span></span>
- <span data-ttu-id="a01e6-129">Select-object (selecteren)</span><span class="sxs-lookup"><span data-stu-id="a01e6-129">Select-Object (select)</span></span>

<span data-ttu-id="a01e6-130">Er zijn geen Power shell-providers beschikbaar en ook geen externe Program ma's (uitvoer bare bestanden of scripts).</span><span class="sxs-lookup"><span data-stu-id="a01e6-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="a01e6-131">Zie [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes)voor meer informatie over taal modi.</span><span class="sxs-lookup"><span data-stu-id="a01e6-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="a01e6-132">De JEA-identiteit kiezen</span><span class="sxs-lookup"><span data-stu-id="a01e6-132">Choose the JEA identity</span></span>

<span data-ttu-id="a01e6-133">Achter de schermen heeft JEA een identiteit (account) nodig om te gebruiken bij het uitvoeren van de opdrachten van een verbonden gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a01e6-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="a01e6-134">U definieert welke identiteit JEA in het sessie configuratie bestand gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a01e6-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="a01e6-135">Lokaal virtueel account</span><span class="sxs-lookup"><span data-stu-id="a01e6-135">Local Virtual Account</span></span>

<span data-ttu-id="a01e6-136">Lokale virtuele accounts zijn handig wanneer alle rollen die zijn gedefinieerd voor het JEA-eind punt worden gebruikt voor het beheren van de lokale computer en een lokaal Administrator-account voldoende is om de opdrachten te kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a01e6-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="a01e6-137">Virtuele accounts zijn tijdelijke accounts die uniek zijn voor een specifieke gebruiker en alleen voor de duur van de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="a01e6-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="a01e6-138">Op een lidserver of werk station behoren virtuele accounts tot de groep Administrators van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="a01e6-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="a01e6-139">Op een Active Directory-domein controller behoren virtuele accounts tot de groep **domein Administrators** van het domein.</span><span class="sxs-lookup"><span data-stu-id="a01e6-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="a01e6-140">Als voor de rollen die zijn gedefinieerd door de sessie configuratie geen volledige beheerders bevoegdheden zijn vereist, kunt u de beveiligings groepen opgeven waarvan het virtuele account deel uitmaakt.</span><span class="sxs-lookup"><span data-stu-id="a01e6-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="a01e6-141">Op een lidserver of werk station moeten de opgegeven beveiligings groepen lokale groepen zijn, en niet groepen van een domein.</span><span class="sxs-lookup"><span data-stu-id="a01e6-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="a01e6-142">Wanneer een of meer beveiligings groepen worden opgegeven, wordt het virtuele account niet toegewezen aan de groep lokale of domein beheerders.</span><span class="sxs-lookup"><span data-stu-id="a01e6-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="a01e6-143">Virtuele accounts hebben tijdelijk het recht aanmelden als een service in het beveiligings beleid van de lokale server.</span><span class="sxs-lookup"><span data-stu-id="a01e6-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="a01e6-144">Als aan een van de opgegeven VirtualAccountGroups dit recht al is toegekend in het beleid, wordt het afzonderlijke virtuele account niet meer toegevoegd en verwijderd uit het beleid.</span><span class="sxs-lookup"><span data-stu-id="a01e6-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="a01e6-145">Dit kan handig zijn in scenario's zoals domein controllers waar revisies van het beveiligings beleid van de domein controller nauw keurig worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="a01e6-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="a01e6-146">Dit is alleen beschikbaar in Windows Server 2016 met de rollup van 2018 of hoger van november en Windows Server 2019 met de rollup van 2019 januari of hoger.</span><span class="sxs-lookup"><span data-stu-id="a01e6-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="a01e6-147">Door groep beheerd service account</span><span class="sxs-lookup"><span data-stu-id="a01e6-147">Group-managed service account</span></span>

<span data-ttu-id="a01e6-148">Een door een groep beheerd service account (GMSA) is de geschikte identiteit die moet worden gebruikt wanneer JEA-gebruikers toegang nodig hebben tot netwerk bronnen zoals bestands shares en webservices.</span><span class="sxs-lookup"><span data-stu-id="a01e6-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="a01e6-149">Gmsa's geven u een domein identiteit die wordt gebruikt voor verificatie met resources op elke computer in het domein.</span><span class="sxs-lookup"><span data-stu-id="a01e6-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="a01e6-150">De rechten die een GMSA biedt, worden bepaald door de resources die u wilt openen.</span><span class="sxs-lookup"><span data-stu-id="a01e6-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="a01e6-151">U hebt geen beheerders rechten op computers of services, tenzij de machine of service beheerder deze rechten expliciet heeft verleend aan de GMSA.</span><span class="sxs-lookup"><span data-stu-id="a01e6-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="a01e6-152">Gmsa's mag alleen worden gebruikt wanneer dit nodig is:</span><span class="sxs-lookup"><span data-stu-id="a01e6-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="a01e6-153">Het is lastig om de acties terug te traceren naar een gebruiker wanneer een GMSA wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a01e6-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="a01e6-154">Elke gebruiker deelt dezelfde run-as-identiteit.</span><span class="sxs-lookup"><span data-stu-id="a01e6-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="a01e6-155">U moet de transcripten en logboeken van Power shell-sessies controleren om afzonderlijke gebruikers met hun acties te correleren.</span><span class="sxs-lookup"><span data-stu-id="a01e6-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="a01e6-156">De GMSA heeft mogelijk toegang tot veel netwerk bronnen waartoe de verbinding van de gebruiker geen toegang nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="a01e6-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="a01e6-157">Probeer altijd de juiste machtigingen in een JEA-sessie te beperken om het principe van minimale bevoegdheden te volgen.</span><span class="sxs-lookup"><span data-stu-id="a01e6-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="a01e6-158">Door groepen beheerde service accounts zijn alleen beschikbaar op computers die lid zijn van een domein met behulp van Power shell 5,1 of nieuwer.</span><span class="sxs-lookup"><span data-stu-id="a01e6-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="a01e6-159">Zie het artikel [beveiligings overwegingen](security-considerations.md) voor meer informatie over het beveiligen van een JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="a01e6-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="a01e6-160">Transcripten van sessies</span><span class="sxs-lookup"><span data-stu-id="a01e6-160">Session transcripts</span></span>

<span data-ttu-id="a01e6-161">Het is raadzaam om een JEA-eind punt te configureren voor het automatisch vastleggen van transcripten van gebruikers sessies.</span><span class="sxs-lookup"><span data-stu-id="a01e6-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="a01e6-162">De transcripten van Power shell-sessies bevatten informatie over de gebruiker die verbinding maakt, de run as-identiteit die aan hen is toegewezen en de opdrachten die worden uitgevoerd door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a01e6-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="a01e6-163">Ze kunnen nuttig zijn voor een audit team dat moet weten wie een specifieke wijziging in een systeem heeft aangebracht.</span><span class="sxs-lookup"><span data-stu-id="a01e6-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="a01e6-164">Als u automatische transcriptie in het configuratie bestand voor de sessie wilt configureren, geeft u een pad naar een map op waarin de transcripten moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a01e6-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="a01e6-165">Transcripten worden naar de map geschreven door het **lokale systeem** account, waarvoor lees-en schrijf toegang tot de map is vereist.</span><span class="sxs-lookup"><span data-stu-id="a01e6-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="a01e6-166">Standaard gebruikers mogen geen toegang hebben tot de map.</span><span class="sxs-lookup"><span data-stu-id="a01e6-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="a01e6-167">Beperk het aantal beveiligings beheerders dat toegang heeft om de transcripten te controleren.</span><span class="sxs-lookup"><span data-stu-id="a01e6-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="a01e6-168">Gebruikers station</span><span class="sxs-lookup"><span data-stu-id="a01e6-168">User drive</span></span>

<span data-ttu-id="a01e6-169">Als uw gebruikers die verbinding maken, bestanden moeten kopiëren naar of van het JEA-eind punt, kunt u het gebruikers station inschakelen in het configuratie bestand van de sessie.</span><span class="sxs-lookup"><span data-stu-id="a01e6-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="a01e6-170">Het gebruikers station is een **PSDrive** die is toegewezen aan een unieke map voor elke gebruiker die verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="a01e6-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="a01e6-171">Met deze map kunnen gebruikers bestanden kopiëren naar of van het systeem zonder dat ze toegang hebben tot het volledige bestands systeem of de bestandssysteem provider weer geven.</span><span class="sxs-lookup"><span data-stu-id="a01e6-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="a01e6-172">De inhoud van het gebruikers station is permanente sessies voor situaties waarin de netwerk verbinding mogelijk wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="a01e6-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="a01e6-173">Standaard kunt u met het gebruikers station Maxi maal 50 MB gegevens per gebruiker opslaan.</span><span class="sxs-lookup"><span data-stu-id="a01e6-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="a01e6-174">U kunt de hoeveelheid gegevens beperken die een gebruiker kan verbruiken met het veld *UserDriveMaximumSize* .</span><span class="sxs-lookup"><span data-stu-id="a01e6-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="a01e6-175">Als u niet wilt dat gegevens in het gebruikers station permanent zijn, kunt u een geplande taak op het systeem configureren om elke avond automatisch de map op te schonen.</span><span class="sxs-lookup"><span data-stu-id="a01e6-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="a01e6-176">Het gebruikers station is alleen beschikbaar in Power shell 5,1 of nieuwer.</span><span class="sxs-lookup"><span data-stu-id="a01e6-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="a01e6-177">Zie [Power Shell-stations beheren](/powershell/scripting/samples/managing-windows-powershell-drives)voor meer informatie over PSDrives.</span><span class="sxs-lookup"><span data-stu-id="a01e6-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="a01e6-178">Roldefinities</span><span class="sxs-lookup"><span data-stu-id="a01e6-178">Role definitions</span></span>

<span data-ttu-id="a01e6-179">Roldefinities in een sessie configuratie bestand definiëren de toewijzing van **gebruikers** aan **rollen**.</span><span class="sxs-lookup"><span data-stu-id="a01e6-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="a01e6-180">Elke gebruiker of groep die in dit veld is opgenomen, krijgt toegang tot het JEA-eind punt wanneer het is geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="a01e6-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="a01e6-181">Elke gebruiker of groep kan slechts eenmaal als sleutel in de hashtabel worden opgenomen, maar kan meerdere rollen krijgen.</span><span class="sxs-lookup"><span data-stu-id="a01e6-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="a01e6-182">De naam van de functie mogelijkheid moet de naam zijn van het functie-Capability-bestand `.psrc` , zonder de extensie.</span><span class="sxs-lookup"><span data-stu-id="a01e6-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="a01e6-183">Als een gebruiker deel uitmaakt van meer dan één groep in de roldefinitie, krijgen ze toegang tot de rollen van elk.</span><span class="sxs-lookup"><span data-stu-id="a01e6-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="a01e6-184">Wanneer twee rollen toegang verlenen tot dezelfde cmdlets, wordt de meest strikte parameterset verleend aan de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a01e6-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="a01e6-185">Wanneer u lokale gebruikers of groepen in het veld roldefinities opgeeft, moet u ervoor zorgen dat u de computer naam, niet **localhost** of joker tekens, gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a01e6-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="a01e6-186">U kunt de naam van de computer controleren door de `$env:COMPUTERNAME` variabele te controleren.</span><span class="sxs-lookup"><span data-stu-id="a01e6-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="a01e6-187">Zoek volgorde van functie mogelijkheden</span><span class="sxs-lookup"><span data-stu-id="a01e6-187">Role capability search order</span></span>

<span data-ttu-id="a01e6-188">Zoals u in het bovenstaande voor beeld kunt zien, wordt naar de functie functionaliteit verwezen met de basis naam van het functie-Capability-bestand.</span><span class="sxs-lookup"><span data-stu-id="a01e6-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="a01e6-189">De basis naam van een bestand is de bestands naam zonder extensie.</span><span class="sxs-lookup"><span data-stu-id="a01e6-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="a01e6-190">Als er meerdere functie mogelijkheden beschikbaar zijn op het systeem met dezelfde naam, gebruikt Power shell de impliciete Zoek volgorde van de functie om het juiste bestandsbeheer bestand te selecteren.</span><span class="sxs-lookup"><span data-stu-id="a01e6-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="a01e6-191">JEA geeft **geen** toegang tot alle functie-Capability-bestanden met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="a01e6-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="a01e6-192">JEA maakt gebruik `$env:PSModulePath` van de omgevings variabele om te bepalen welke paden moeten worden gescand op functie-Capability-bestanden.</span><span class="sxs-lookup"><span data-stu-id="a01e6-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="a01e6-193">In elk van deze paden zoekt JEA naar geldige Power shell-modules die een submap ' RoleCapabilities ' bevatten.</span><span class="sxs-lookup"><span data-stu-id="a01e6-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="a01e6-194">Net als bij het importeren van modules, geven JEA de voor keur aan functie mogelijkheden die worden geleverd met Windows naar aangepaste functie mogelijkheden met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="a01e6-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="a01e6-195">Voor alle andere naam conflicten wordt de prioriteit bepaald aan de hand van de volg orde waarin Windows de bestanden in de map inventariseert.</span><span class="sxs-lookup"><span data-stu-id="a01e6-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="a01e6-196">De bestelling is niet gegarandeerd in alfabetische volg orde.</span><span class="sxs-lookup"><span data-stu-id="a01e6-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="a01e6-197">Het eerste functie-mogelijkheidsprofiel gevonden dat overeenkomt met de opgegeven naam wordt gebruikt voor de gebruiker die verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="a01e6-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="a01e6-198">Omdat de zoek volgorde van de functie mogelijkheden niet deterministisch is, wordt het **ten zeerste aanbevolen** om functie mogelijkheden unieke bestands namen te bieden.</span><span class="sxs-lookup"><span data-stu-id="a01e6-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="a01e6-199">Regels voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="a01e6-199">Conditional access rules</span></span>

<span data-ttu-id="a01e6-200">Alle gebruikers en groepen die zijn opgenomen in het veld **RoleDefinitions** , krijgen automatisch toegang tot JEA-eind punten.</span><span class="sxs-lookup"><span data-stu-id="a01e6-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="a01e6-201">Met regels voor voorwaardelijke toegang kunt u deze toegang verfijnen en moeten gebruikers deel nemen aan extra beveiligings groepen die niet van invloed zijn op de rollen waaraan ze zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="a01e6-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="a01e6-202">Dit is handig als u een just-in-time privileged Access Management-oplossing, smartcard verificatie of andere multi-factor Authentication-oplossing wilt integreren met JEA.</span><span class="sxs-lookup"><span data-stu-id="a01e6-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="a01e6-203">Regels voor voorwaardelijke toegang worden gedefinieerd in het veld RequiredGroups in een configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="a01e6-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="a01e6-204">Daar kunt u een hashtabel (optioneel genest) opgeven die gebruikmaakt van ' and ' en ' or '-sleutels om uw regels te maken.</span><span class="sxs-lookup"><span data-stu-id="a01e6-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="a01e6-205">Hier volgen enkele voor beelden van het gebruik van dit veld:</span><span class="sxs-lookup"><span data-stu-id="a01e6-205">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="a01e6-206">Regels voor voorwaardelijke toegang zijn alleen beschikbaar in Power shell 5,1 of nieuwer.</span><span class="sxs-lookup"><span data-stu-id="a01e6-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="a01e6-207">Andere eigenschappen</span><span class="sxs-lookup"><span data-stu-id="a01e6-207">Other properties</span></span>

<span data-ttu-id="a01e6-208">Sessie configuratie bestanden kunnen ook alles doen wat een functie-mogelijkheidsprofiel kan doen, alleen zonder de mogelijkheid om verbinding te maken tussen gebruikers en andere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="a01e6-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="a01e6-209">Als u alle gebruikers toegang wilt geven tot specifieke cmdlets, functies of providers, kunt u dit rechtstreeks doen in het configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="a01e6-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="a01e6-210">Voer uit `Get-Help New-PSSessionConfigurationFile -Full`voor een volledige lijst met ondersteunde eigenschappen in het configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="a01e6-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="a01e6-211">Een configuratie bestand voor een sessie testen</span><span class="sxs-lookup"><span data-stu-id="a01e6-211">Testing a session configuration file</span></span>

<span data-ttu-id="a01e6-212">U kunt een sessie configuratie testen met de cmdlet [test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) .</span><span class="sxs-lookup"><span data-stu-id="a01e6-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="a01e6-213">Het is raadzaam om uw sessie configuratie bestand te testen als u het `.pssc` bestand hand matig hebt bewerkt.</span><span class="sxs-lookup"><span data-stu-id="a01e6-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="a01e6-214">Testen zorgt ervoor dat de syntaxis juist is.</span><span class="sxs-lookup"><span data-stu-id="a01e6-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="a01e6-215">Als een sessie configuratie bestand deze test niet kan registreren, kan het niet worden geregistreerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="a01e6-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="a01e6-216">Configuratie bestand voor voorbeeld sessie</span><span class="sxs-lookup"><span data-stu-id="a01e6-216">Sample session configuration file</span></span>

<span data-ttu-id="a01e6-217">In het volgende voor beeld ziet u hoe u een sessie configuratie voor JEA maakt en valideert.</span><span class="sxs-lookup"><span data-stu-id="a01e6-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="a01e6-218">De roldefinities worden gemaakt en opgeslagen in de `$roles` variabele voor gemak en lees baarheid.</span><span class="sxs-lookup"><span data-stu-id="a01e6-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="a01e6-219">Dit is geen vereiste.</span><span class="sxs-lookup"><span data-stu-id="a01e6-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="a01e6-220">Sessie configuratie bestanden bijwerken</span><span class="sxs-lookup"><span data-stu-id="a01e6-220">Updating session configuration files</span></span>

<span data-ttu-id="a01e6-221">Als u de eigenschappen van een JEA-sessie configuratie wilt wijzigen, met inbegrip van de toewijzing van gebruikers aan rollen, moet u de [registratie ongedaan maken](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="a01e6-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="a01e6-222">Registreer de JEA-sessie configuratie vervolgens [opnieuw](register-jea.md) met een bijgewerkt sessie configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="a01e6-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a01e6-223">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="a01e6-223">Next steps</span></span>

- [<span data-ttu-id="a01e6-224">Een JEA-configuratie registreren</span><span class="sxs-lookup"><span data-stu-id="a01e6-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="a01e6-225">JEA-rollen ontwerpen</span><span class="sxs-lookup"><span data-stu-id="a01e6-225">Author JEA roles</span></span>](role-capabilities.md)